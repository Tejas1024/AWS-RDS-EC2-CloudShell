# AWS-MiniProject-Guide.md

# AWS Mini Project: Web App on EC2 with Private RDS in VPC (Best Practice)

## Goal

- Web application runs on a public EC2
- RDS (DB) runs privately (not internet-exposed)
- Both inside a custom, secured VPC

---

## Architecture Diagram (Text)

[Internet]
|
[Public Subnet in VPC] -- EC2 (Web Server)
|
[Private Subnet in VPC] -- RDS (DB)

 

---

## Step-by-Step Setup

### 1. VPC

- Create VPC (e.g., my-vpc)
- Add two subnets:
    - Public Subnet (Internet-facing, for EC2)
    - Private Subnet (no Internet, for RDS)
- Attach an IGW to VPC (public subnet needs Internet)
- Routing: 
    - Public RT → IGW
    - Private RT → (no Internet)

### 2. EC2 (Web Server)

- Launch EC2 in public subnet of the VPC
- Security group:
    - Inbound: HTTP (80), SSH (22)
- Connect and set up Nginx or Apache:
    ```
    sudo apt update
    sudo apt install nginx -y
    sudo systemctl start nginx
    ```

### 3. RDS (DB)

- Create RDS (MySQL/Postgres), place in private subnet
- Security group:
    - Inbound: Permit DB port (e.g., 3306) from EC2’s SG only
- Do NOT enable public access
- Set DB username/password

### 4. Security Groups

- EC2 SG: Allows inbound HTTP (80), SSH (22), outbound ALL
- RDS SG: Allows inbound from EC2’s SG on DB port, outbound ALL

### 5. IAM Roles

- IAM role for EC2: Permit S3/CloudWatch access if needed

---

## Summary Table

| Component       | Description                        | Placement          | Access                |
|-----------------|------------------------------------|--------------------|-----------------------|
| VPC             | Isolated virtual network           | -                  | Controls connections  |
| Public Subnet   | For EC2/web                        | VPC                | Internet              |
| Private Subnet  | For DB/RDS                         | VPC                | No public internet    |
| EC2 SG          | Firewall for EC2                   | EC2                | HTTP, SSH in          |
| RDS SG          | Firewall for RDS                   | RDS                | DB port from EC2 only |
| IAM Role        | AWS API permissions                | EC2                | S3, CloudWatch, etc.  |

---

## Final Result

- EC2 web app: public
- RDS: private, only accessible by EC2
- Everything inside secured VPC
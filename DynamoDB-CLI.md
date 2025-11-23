# DynamoDB-CLI.md

# DynamoDB & AWS CLI – Essential Beginner Notes

## DynamoDB

- Fully managed NoSQL (non-relational) serverless DB by AWS
- Stores without rows/columns (Key-Value, Document, Table)
- Auto-scales, high-availability, fast for high-velocity workloads

| Use Cases                  |
|----------------------------|
| Caching                    |
| IoT device data            |
| Realtime analytics/logging |
| Game leaderboards          |

---

## AWS CLI (Command Line Interface)

- Terminal-based tool to control/manage AWS services by command
- Good for coding, automation, DevOps pipelines

---

## AWS Access – 3 Ways

- **AWS Console**: Web UI (browser)
- **AWS CLI**: Command line on your system
- **AWS SDK**: APIs for Python, Java, etc

---

## AWS CLI Setup Steps

1. **Create IAM User**
    - Console → IAM → Add User → Attach policy (e.g., AdministratorAccess)
    - Get Access Key ID & Secret

2. **Install AWS CLI**
    - Windows: Download from official AWS CLI page
    - Linux/Mac: Usually pre-installed or can run `pip install awscli` or `sudo apt install awscli`

3. **Configure**
    ```
    aws configure
    ```
    - Enter access key, secret, region (ap-south-1 etc), format (json).

4. **Verify**
    ```
    aws --version
    ```
    - If version prints, install and config is correct.

---

## Basic CLI Commands

- `aws s3 ls`
- `aws ec2 describe-instances`

---

## Summary Table

| Concept      | Description                                         |
|--------------|-----------------------------------------------------|
| DynamoDB     | AWS NoSQL DB (serverless, managed)                  |
| AWS CLI      | Terminal tool to run AWS commands                   |
| IAM User     | Credentials for secure AWS CLI usage                |
| Access Keys  | Provide to aws configure                            |
| Command Ex.  | aws s3 ls, aws ec2 describe-instances               |

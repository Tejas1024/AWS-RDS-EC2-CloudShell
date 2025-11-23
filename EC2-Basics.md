# EC2-Basics.md

# Amazon EC2 (Elastic Compute Cloud) – Beginner Notes

## What is EC2?

- Rent virtual servers in AWS cloud (IaaS)
- Run applications, websites, custom software — accessible from anywhere
- Resize (CPU, RAM, storage) and pay-as-you-go
- Launched by AWS in 2006

---

## Key Components

| Component    | Description/Role                                      |
|--------------|------------------------------------------------------|
| Instance     | Virtual server you launch                            |
| EBS          | Elastic Block Store – main persistent disk           |
| Volume       | Storage drive attached to instance                   |
| Snapshot     | Backup point-in-time copy of a volume                |
| AMI          | Prebuilt template (OS + software + config)           |
| ELB          | Elastic Load Balancer to spread traffic              |
| ASG          | Auto Scaling Group (dynamically adds/removes EC2s)   |

---

## EC2 Instance Types

| Type                  | Use Case                               |
|-----------------------|----------------------------------------|
| General Purpose       | Web servers, dev/test                  |
| Compute Optimized     | High-performance compute, analytics    |
| Memory Optimized      | In-memory DBs, big data                |
| Storage Optimized     | Heavy read/write, data warehouses      |
| High-Performance (HPC)| Simulations, research, GPU apps        |
| Accelerated Computing | ML/AI, video, GPU-based                |

---

## EC2 Pricing

- Free: 750 hours/month (t2.micro, Free Tier)
- Pay only for consumed resources (hourly)

---

## How to Launch EC2 Instance (Linux/Ubuntu)

1. AWS Console → EC2
2. Click Launch Instance
3. Name, pick AMI (Ubuntu, Windows, etc.)
4. Choose Free Tier eligible (e.g., t2.micro)
5. Select/create a Key Pair (for SSH)
6. Add storage (e.g., gp3, min. 8GB)
7. Launch

---

## Basic Linux Commands

| Task                 | Command Example                          |
|----------------------|------------------------------------------|
| Create directory     | mkdir dir_name                           |
| List files           | ls                                       |
| Create file          | touch file.txt                           |
| Edit file            | nano file.txt / vi file.txt              |
| Go into directory    | cd folder                                |
| Delete file          | rm file.txt                              |
| Back one directory   | cd ..                                    |
| Delete folder        | rmdir dir_name / rm -r dir_name          |
| Show file content    | cat file.txt                             |
| Who am I?            | whoami                                   |
| Where am I?          | pwd                                      |

---

## Summary

- EC2 = On-demand, scalable server
- EBS = Storage
- AMI = Image/template for new EC2s
- ELB = Distributes load
- ASG = Auto adds/removes VMs
- Use Linux basics to manage files/folders/installs

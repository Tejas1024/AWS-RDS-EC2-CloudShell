# CloudShell-Commands.md

# AWS CloudShell Commands – Cheat Sheet

CloudShell: AWS browser-based CLI access, no local install needed.

---

## S3 (Simple Storage Service)

| Task            | Command Example                             |
|-----------------|---------------------------------------------|
| List buckets    | aws s3 ls                                   |
| Make bucket     | aws s3 mb s3://bucket-name                  |
| Remove bucket   | aws s3 rb s3://bucket-name                  |
| Upload file     | aws s3 cp your-file.txt s3://bucket-name/   |
| Download file   | aws s3 cp s3://bucket-name/file.txt .       |
| Delete file     | aws s3 rm s3://bucket-name/file.txt         |

---

## EC2 (Virtual Servers)

| Task             | Command Example                                                                                |
|------------------|------------------------------------------------------------------------------------------------|
| List instances   | aws ec2 describe-instances                                                                     |
| Launch instance  | aws ec2 run-instances --image-id ami-XX --instance-type t2.micro --key-name my-key --tag-specifications 'ResourceType=instance,Tags=[{Key=Name,Value="MyInstance"}]' |
| Stop instance    | aws ec2 stop-instances --instance-ids i-XXX                                                    |
| Start instance   | aws ec2 start-instances --instance-ids i-XXX                                                   |
| Terminate        | aws ec2 terminate-instances --instance-ids i-XXX                                               |

---

## Lambda (Serverless Compute)

| Task                   | Command Example                                    |
|------------------------|----------------------------------------------------|
| List functions         | aws lambda list-functions                          |
| Create (local zip)     | aws lambda create-function --function-name myfun --runtime python3.8 --role arn:aws:iam::acct:role/lambda-role --handler myfun.lambda_handler --zip-file fileb://function.zip |
| Create (from S3)       | aws lambda create-function --function-name myfun --runtime python3.8 --role arn:aws:iam::acct:role/lambda-role --handler myfun.lambda_handler --code S3Bucket=bucket,S3Key=function.zip |

---

## IAM

| Task                  | Command Example                                         |
|-----------------------|--------------------------------------------------------|
| List users            | aws iam list-users                                     |
| Create user           | aws iam create-user --user-name myuser                 |
| Attach policy         | aws iam attach-user-policy --user-name myuser --policy-arn arn:aws:iam::aws:policy/AdministratorAccess |

---

## VPC (Networking)

| Task                  | Command Example                                |
|-----------------------|------------------------------------------------|
| List VPCs             | aws ec2 describe-vpcs                          |
| Create VPC            | aws ec2 create-vpc --cidr-block 10.0.0.0/16    |

---

## CloudWatch

| Task              | Command Example                 |
|-------------------|---------------------------------|
| List alarms       | aws cloudwatch describe-alarms  |

---

## SNS (Notifications)

| Task                   | Command Example                                                        |
|------------------------|------------------------------------------------------------------------|
| Create topic           | aws sns create-topic --name MyTopic                                    |
| List topics            | aws sns list-topics                                                    |
| Subscribe (email)      | aws sns subscribe --topic-arn arn:aws:sns:region:acct-id:Topic --protocol email --notification-endpoint you@email.com |
| Publish message        | aws sns publish --topic-arn arn:aws:sns:region:acct-id:Topic --message "Text" --subject "Subj"                 |
| List subscriptions     | aws sns list-subscriptions-by-topic --topic-arn arn:aws:sns:region:acct-id:Topic |

---

## Workflow Example

- Create VPC
- Launch EC2 (in public subnet)
- Launch RDS (in private subnet)
- Give EC2 IAM role if needed
- Store files/code in S3
- Use CloudWatch for monitoring/alerts
- Send notifications with SNS
- Automate with Lambda

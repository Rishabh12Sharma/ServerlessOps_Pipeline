# 🚀 Serverless Ops Pipeline: End-to-End Cloud-Native DevOps Project

A fully integrated DevOps project simulating real-world CI/CD workflows, infrastructure provisioning, monitoring, and automation — built for aspiring DevOps engineers.

---

## Project Overview

This Serverless Ops Pipeline enables users to:
- Upload input files through a frontend hosted on S3 + CloudFront
- Automatically trigger processing via Lambda and S3 events
- Use pre-signed URLs for secure uploads
- Deploy and manage infrastructure using Terraform
- Automate pipelines via GitHub Actions
- Monitor health and logs via CloudWatch

---

## The Flow (How It Works)

1. User visits frontend site through browser  
2. Navigates through all the sections  
3. Uploads screenshot / PDF file  
4. Backend generates a pre-signed URL  
5. File is uploaded securely to S3  
6. S3 event triggers Lambda execution  
7. Lambda processes the file and logs results in CloudWatch  
8. SNS alert is sent after successful processing  

---

## Tech Stack

| Layer             | Tools & Services                        |
|------------------|------------------------------------------|
| Frontend         | HTML/CSS + S3 + CloudFront               |
| Backend (Event)  | AWS Lambda (Python)                      |
| Infrastructure   | Terraform (modular setup & remote backend) |
| CI/CD            | GitHub Actions                           |
| Monitoring       | CloudWatch                               |
| Notification     | SNS (Email alerts)                       |
| Security         | IAM Roles, Policies, Bucket Permissions  |

---

## What's Covered in this Project

### Infrastructure Auto-Provisioning with Terraform
- Automated infrastructure using Terraform  
- Remote backend with S3 (state) + DynamoDB (locking)  

---

### End-to-End CI/CD Automation with GitHub Actions
- Automated workflows for:
  - Frontend deployment (S3 + CloudFront)
  - Lambda deployment
  - Terraform provisioning  

---

### Cloud-Native Hosting (Serverless)
- Static frontend hosted on S3 + CloudFront  
- Backend powered by AWS Lambda  
- Fully serverless, scalable, and cost-efficient  

---

### Secure File Upload (Pre-Signed URLs)
- Secure upload without exposing S3  
- Direct upload using pre-signed URLs  
- Event-driven processing via S3 triggers  

---

### Monitoring & Alerting
- CloudWatch logs for observability  
- SNS email alerts on file processing  
- Error tracking and debugging support  

---

### Modular & Scalable Design
- Clean folder structure  
- Easily extendable architecture  
- Ready for adding more features  

---

## Folder Structure

```
DevOps-Accelerator-Project
├── .github
│   └── workflows
│       ├── backend-deploy.yml
│       ├── frontend.yml
│       └── terraform.yml
├── backend
│   └── lambda
│       ├── generate-presigned-url
│       │   ├── lambda.zip
│       │   └── main.py
│       └── process-uploaded-file
│           ├── lambda.zip
│           └── main.py
├── frontend
│   └── index.html
├── gigs
│   ├── project-generator
│   └── qa-bot
├── infra
│   └── terraform
│       ├── main.tf
│       ├── outputs.tf
│       ├── terraform.tfvars
│       └── variables.tf
└── README.md
└── .gitignore

```

## Deployment Instructions

### 1. Prerequisites

- AWS CLI configured locally (`aws configure`)

- Terraform should be installed

- Node.js or Python (depending on Lambda)

- GitHub repository created (for CI/CD)


### 2. Infrastructure Setup with Terraform

- Always navigate to the terraform folder when running below commands in same sequence:
	- `terraform init`
	
		-  To initialize and setup everything. [*Need to run this whenever new changes are made to terraform files or its dependent resources like lambda folders in backend.*]
	- `terraform validate`
		- To verify if the configs are corrected defined or not.
	- `terraform plan`
		- To confirm what all resources are going to be built.

	#### Important note: 
	- Do NOT run `terraform apply`locally.  
	- Need all changes to go through CI/CD so we push to remote directly and apply will run through pipeline.


### 3. GitHub Actions CI/CD

- CI/CD runs on push to `main` branch.

- Auto-deploys updated Lambda code (backend), terraform scripts or frontend.

- Uses GitHub Secrets to authenticate with AWS


---

### 4. Deployment Execution guidance
````md
If you'd like to replicate this project [DevOps Accelerator] on your own AWS account, follow the detailed steps below.

---

##  Prerequisites

- AWS Account (with Administrator Access)
- AWS CLI installed (`aws configure` will be used)
- Git & GitHub account
- Terraform v1.3+ installed
- Node.js (for future extensibility)

---

##  Set Up AWS Credentials

1. Log into AWS Console → IAM → **Create User**
2. After user creation, under the **Users** tab:
   - Click your newly created user
   - Go to **Security credentials** → Create **Access Key**
   - Skip tags, **download the CSV** (Important: don’t close until downloaded)
3. Assign permissions:
   - Go to **Permissions** → Add permissions
   - Choose **Attach policies directly**
   - Search for `AdministratorAccess` and attach
4. In terminal, run:
   ```bash
   aws configure
````

* Enter Access Key ID and Secret Key from the CSV
* Leave region/format blank (or use `us-east-1`)

---

## 🖥️ Frontend UI
<img width="1918" height="967" alt="Screenshot 2026-04-15 110152" src="https://github.com/user-attachments/assets/cf779c90-ff86-4863-abd0-f9d40b2eb08a" />

<br>

<img width="1918" height="967" alt="Screenshot 2026-04-15 110228" src="https://github.com/user-attachments/assets/70a4afad-c557-4b01-b388-c71027103512" />

<br>

<img width="1918" height="972" alt="Screenshot 2026-04-15 110302" src="https://github.com/user-attachments/assets/f9af912d-3af6-48cc-a3c2-52bdcf95aa06" />

<br>

## 🪣 S3 Buckets
<img width="1918" height="967" alt="Screenshot 2026-04-15 113130" src="https://github.com/user-attachments/assets/27917dba-fb19-4bfe-8e1a-549fe633f105" />

<br>

## 📊 CloudWatch Logs
<img width="1918" height="962" alt="Screenshot 2026-04-15 113533" src="https://github.com/user-attachments/assets/0dbee1f5-85a6-4e55-abe0-4ab9eceb64ba" />

<br>

<img width="1918" height="967" alt="Screenshot 2026-04-15 114647" src="https://github.com/user-attachments/assets/528b3b17-2662-4d2c-8ceb-aa3787f9f0dd" />

<br>

<img width="1918" height="972" alt="Screenshot 2026-04-15 114906" src="https://github.com/user-attachments/assets/a0b614f5-78c3-4e18-a86d-cf55f253a3b9" />

<br>

## 📣 SNS Email
<img width="1461" height="497" alt="Screenshot 2026-04-15 114312" src="https://github.com/user-attachments/assets/07b53035-6030-42d4-82fc-716c39695224" />

<br>

## 🔁 GitHub Actions (CI/CD)
<img width="1918" height="872" alt="image" src="https://github.com/user-attachments/assets/b4d57703-e746-42e0-a128-7d1ce64af65f" />

<br>




🔥 Happy DevOps-ing!







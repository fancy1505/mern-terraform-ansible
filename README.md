# MERN Application Deployment on AWS using Terraform & Ansible

## Assignment Objective

Gain practical experience in deploying a MERN stack application on AWS using Infrastructure as Code (Terraform) and Configuration Management (Ansible).

**Application Used:**
TravelMemory (MERN Stack Application)

Repository:
https://github.com/UnpredictablePrashant/TravelMemory

---

# Project Overview

This project automates the deployment of a MERN (MongoDB, Express.js, React.js, Node.js) application on AWS.

The infrastructure is provisioned using Terraform, while application configuration and deployment are automated using Ansible.

The architecture follows cloud security best practices by separating the application and database layers into public and private subnets.

---

# Architecture

```text
                    Internet
                        |
                Internet Gateway
                        |
                 Public Subnet
                        |
                Web Server EC2
               (Node.js + React)
                        |
                    Port 27017
                        |
                 Private Subnet
                        |
                 MongoDB EC2
```

Additional AWS Resources:

* VPC
* Public Subnet
* Private Subnet
* Internet Gateway
* NAT Gateway
* Elastic IP
* Route Tables
* Security Groups
* IAM Roles

---

# Part 1 – Infrastructure Setup with Terraform

## 1. AWS Setup and Terraform Initialization
<img width="1499" height="261" alt="image" src="https://github.com/user-attachments/assets/a214de5a-0986-4a29-97bc-124453db3173" />
<img width="1117" height="272" alt="image" src="https://github.com/user-attachments/assets/c4cd92b7-1b02-4e74-9346-a400508d0618" />
<img width="1175" height="625" alt="image" src="https://github.com/user-attachments/assets/28b61540-204c-4a1d-864b-9afdfa45a2b0" />
<img width="1175" height="625" alt="image" src="https://github.com/user-attachments/assets/52c58b8f-401c-412f-9ceb-7af473066bc1" />
<img width="1125" height="313" alt="image" src="https://github.com/user-attachments/assets/54379918-9c51-449c-a162-569ab6386d25" />
<img width="1101" height="591" alt="image" src="https://github.com/user-attachments/assets/57d5bca6-953f-4fd9-96da-8d8cf1e6a2a6" />
<img width="1058" height="562" alt="image" src="https://github.com/user-attachments/assets/c2abaed7-13ce-4b85-9b78-320210e1c130" />
<img width="1079" height="426" alt="image" src="https://github.com/user-attachments/assets/66eb043c-79ee-4c71-8ed8-295262e2aad2" />
<img width="1113" height="276" alt="image" src="https://github.com/user-attachments/assets/14955dc7-b6e3-4831-aac4-834a520c0315" />
<img width="1579" height="215" alt="image" src="https://github.com/user-attachments/assets/25656b28-3e78-4646-99d1-a0a4d7c6c496" />

# Benefits:

* Public resources accessible from the internet
* Database isolated in private network
* Secure outbound internet access through NAT Gateway


Completed:

* AWS CLI configured
* AWS account authenticated
* Terraform initialized
* AWS provider configured

Commands:

```bash
terraform init
terraform validate
terraform plan
terraform 

## 2. VPC and Network Configuration
```
Implemented:

* Custom VPC
* Public Subnet
* Private Subnet
* Internet Gateway
* NAT Gateway
* Elastic IP
* Public Route Table
* Private Route Table
* Route Table Associations

---
<img width="992" height="1319" alt="image" src="https://github.com/user-attachments/assets/8aaeafaf-709a-4fd4-84eb-b2ad9365f01e" />
<img width="1182" height="377" alt="image" src="https://github.com/user-attachments/assets/e8db79ed-2d90-4909-a6b8-e56df9601c82" />
<img width="1072" height="663" alt="image" src="https://github.com/user-attachments/assets/9fdd4625-32ba-43fb-866a-bd4360cdd068" />
<img width="1134" height="544" alt="image" src="https://github.com/user-attachments/assets/d6355c96-29d7-4df3-845b-30ef3cec7c57" />
<img width="1396" height="193" alt="image" src="https://github.com/user-attachments/assets/c5210194-bfb4-4b6d-a687-75f110961782" />
<img width="1439" height="231" alt="image" src="https://github.com/user-attachments/assets/b6db73b6-1c36-4dc2-b1d8-de8b3d68a1dc" />


---

## 3. EC2 Instance Provisioning

Provisioned:

### Web Server EC2

* Public Subnet
* Public IP enabled
* SSH access enabled
* <img width="1111" height="550" alt="image" src="https://github.com/user-attachments/assets/8acf922b-042f-4ba6-8235-2f9b65f09231" />
<img width="1360" height="758" alt="image" src="https://github.com/user-attachments/assets/96dd6d93-2c6b-4838-8658-fcef064e72b5" />
<img width="1362" height="508" alt="image" src="https://github.com/user-attachments/assets/c901a4dd-059e-4ff2-9686-ce043b84b531" />


### MongoDB EC2

* Private Subnet
* No public IP
* Accessible only through internal VPC networking
<img width="1401" height="800" alt="image" src="https://github.com/user-attachments/assets/45490e1d-961e-4141-99d2-4b7e3157e160" />

---

## 4. Security Groups and IAM Roles


### Web Security Group

Allowed:

* SSH (22)
* HTTP (80)
* Application Port
* <img width="1226" height="631" alt="image" src="https://github.com/user-attachments/assets/123bbd3f-7aaa-4cab-80b2-7ea53c8c45b4" />
<img width="2509" height="1279" alt="image" src="https://github.com/user-attachments/assets/deea8471-f9a5-49a4-8f1c-ea1fb07d03ea" />


### Database Security Group

Allowed:

* MongoDB Port (27017)
* Access only from Web Server Security Group

Security Features:

* Restricted inbound access
* Least privilege principle
* Private database deployment

---


## 5. Terraform Outputs

Generated Outputs:

* Web Server Public IP
* Internal Database IP
  



Used by Ansible for deployment automation.

---

# Part 2 – Configuration and Deployment with Ansible

## 1. Ansible Configuration

Implemented:

* Inventory configuration
* SSH authentication using PEM key
* EC2 connectivity validation

Verification:

```bash
ansible all -m ping
```
<img width="973" height="396" alt="image" src="https://github.com/user-attachments/assets/c45df398-09d3-4ecd-81e5-b5a62e48575c" />


---

## 2. Web Server Setup

Automated using Ansible:
<img width="1074" height="378" alt="image" src="https://github.com/user-attachments/assets/12cd53e2-ba71-4402-8d4f-27620a3aefd4" />
<img width="1104" height="441" alt="image" src="https://github.com/user-attachments/assets/74d8b735-1045-4883-b017-26a27f96e92d" />

* Git installation
* Node.js installation
* NPM installation
* Repository cloning
* Dependency installation

Application Repository:

https://github.com/UnpredictablePrashant/TravelMemory

---

## 3. Database Server Setup

Automated using Ansible:

* MongoDB installation
* MongoDB service configuration
* MongoDB startup configuration
* Database connectivity verification

Database Security:

* Private subnet deployment
* Internal access only

---

## 4. Application Deployment

Configured:

* Backend environment variables
* Frontend configuration
* Backend dependency installation
* Frontend dependency installation

Deployment Steps:

1. Clone repository
2. Install backend packages
3. Install frontend packages
4. Configure environment variables
5. Start application services

---

## 5. Security Hardening

Implemented:

* SSH Key Authentication
* Security Group Restrictions
* Database Isolation in Private Subnet
* Controlled MongoDB Access
* NAT Gateway for secure outbound communication
<img width="1366" height="282" alt="image" src="https://github.com/user-attachments/assets/4703a11c-3230-4f42-9552-04a99454977d" />
<img width="1294" height="716" alt="image" src="https://github.com/user-attachments/assets/c92b062c-0a3c-460f-aeb5-23792614ca83" />

---

# Repository Structure
<img width="1281" height="372" alt="image" src="https://github.com/user-attachments/assets/d5c08587-85d4-481b-b632-bcb8b1a7b41d" />
<img width="1215" height="655" alt="image" src="https://github.com/user-attachments/assets/2fa21c56-d96f-4c2e-a9b4-b37cadcecac3" />

```text
mern-terraform-ansible/
│
├── ansible/
│   ├── ansible.cfg
│   ├── deploy.yml
│   ├── inventory.ini
│   ├── mongodb.yml
│   └── webserver.yml
│
├── terraform/
│   ├── provider.tf
│   ├── main.tf
│   ├── variables.tf
│   ├── outputs.tf
│   └── terraform.tfvars
│
├── backend/
│
├── frontend/
│
└── README.md
```
<img width="1201" height="895" alt="image" src="https://github.com/user-attachments/assets/108e8d3a-5fcc-401d-b11f-87ca09610b52" />
<img width="1212" height="1385" alt="image" src="https://github.com/user-attachments/assets/185d9e8a-bf61-42d0-bae7-d0f7452d99dd" />
<img width="1215" height="655" alt="image" src="https://github.com/user-attachments/assets/c9a150b8-784a-4bb8-96ed-9f229c1d0ae4" />

---

# Verification Results

Successfully Verified:

* VPC Creation
* Public & Private Subnets
* Internet Gateway
* NAT Gateway
* Route Tables
* Security Groups
* EC2 Provisioning
* SSH Connectivity
* MongoDB Installation
* MongoDB Network Access
* Node.js Installation
* Application Deployment
* 
<img width="1214" height="594" alt="image" src="https://github.com/user-attachments/assets/a16c91ca-2ff3-4f53-b990-765cfa412e3c" />
<img width="1224" height="636" alt="image" src="https://github.com/user-attachments/assets/a942a520-4a7e-4980-9d36-de87e7db3404" />
<img width="1177" height="404" alt="image" src="https://github.com/user-attachments/assets/59c1bae0-7de6-4d9a-9814-18dc0eb02629" />
<img width="1207" height="490" alt="image" src="https://github.com/user-attachments/assets/81907f22-d820-48b4-98c9-2a27a7f3a365" />
<img width="1346" height="793" alt="image" src="https://github.com/user-attachments/assets/3228d20c-cfaa-4e5f-88d2-8a32d639d23c" />
<img width="1430" height="974" alt="image" src="https://github.com/user-attachments/assets/07e73774-0f96-46c3-a82f-e84495f6bc34" />
<img width="1381" height="803" alt="image" src="https://github.com/user-attachments/assets/36d1f314-c4f2-4133-b7f7-3c10e7a799ab" />
<img width="1272" height="921" alt="image" src="https://github.com/user-attachments/assets/f2e6d8b1-69ab-476b-8568-efca5ce2120c" />
<img width="1275" height="989" alt="image" src="https://github.com/user-attachments/assets/18345f19-cc17-40f2-b5bb-9f002a03b18e" />
<img width="1278" height="675" alt="image" src="https://github.com/user-attachments/assets/caad5668-f3e9-40b5-b612-0ab429022164" />

---
# VERIFIED OUTPUT post Deployment
<img width="1289" height="666" alt="image" src="https://github.com/user-attachments/assets/1a0c37a8-73fc-4bc5-8ae5-507bcc3d97a8" />
<img width="1475" height="746" alt="image" src="https://github.com/user-attachments/assets/7f275804-3d38-4e60-8808-b10ba462071f" />
<img width="1510" height="712" alt="image" src="https://github.com/user-attachments/assets/4d71dcdf-ccb0-45c0-a334-d228cf867931" />
<img width="1561" height="496" alt="image" src="https://github.com/user-attachments/assets/20f877d6-8600-4375-8741-0b1f4f660c2e" />

# Skills Demonstrated

* AWS Cloud
* Terraform
* Ansible
* Infrastructure as Code (IaC)
* Linux Administration
* EC2 Management
* Networking
* Security Groups
* MongoDB
* Node.js
* React.js
* Git & GitHub
* DevOps Automation

---

## ☕ AWS Static Café Website

A hands-on AWS project demonstrating how to deploy, secure, protect, optimize, and replicate a static website using Amazon S3.

This project was completed as part of an AWS cloud architecture lab and follows AWS best practices for hosting static websites, version control, lifecycle management, and disaster recovery.

---

## 📖 Project Overview

The objective of this project was to build and manage a static website for a fictional café using Amazon S3.

The implementation covers the complete lifecycle of hosting a static website in AWS, including:

* Static website hosting
* Public website access
* Object versioning
* Lifecycle management
* Cross-Region Replication (CRR)

---

## 🏗️ Architecture

![Laptop showing a cafe website with pastries and cakes and a browser address bar; to the right, an AWS diagram with two regions and S3 buckets connected by an arrow labeled Amazon S3 CRR. Visible text includes http://<bucket-name>.s3-website-<region>.amazonaws.com and http://mybucket-s3-website-us-east-1.amazonaws.com, header text Café, AWS Cloud, Region 1, Region 2, and Amazon S3 bucket. The scene is instructional and inviting in tone.](./assets/image.png)

The static café website is hosted in an Amazon S3 bucket configured for Static Website Hosting.

Object versioning protects against accidental overwrites and deletions. Lifecycle policies optimize storage costs, and Cross-Region Replication (CRR) copies new objects to a secondary AWS Region for disaster recovery.

## 🛠️ Technologies Used

- Amazon Web Services (AWS)
- Amazon S3
- IAM
- S3 Bucket Policies
- Static Website Hosting
- S3 Versioning
- Lifecycle Rules
- Cross-Region Replication (CRR)
- HTML
- CSS

---

# Project Tasks

## Challenge 1 — Launching a Static Website

### Task 1 — Prepare Website Files

- Downloaded the project assets.
- Extracted:
  - `index.html`
  - `css/`
  - `images/`

---

### Task 2 — Create an S3 Bucket

Created an Amazon S3 bucket in:

- **Region:** `us-east-1 (N. Virginia)`

Configured:

- Static Website Hosting
- Enabled ACLs
- Disabled Block Public Access
- Configured `index.html` as the default document

---

### Task 3 — Upload Website

Uploaded:

```
index.html
css/
images/
```

Verified that the website loads successfully using the S3 Website Endpoint.

---

### Task 4 — Configure Public Access

Created an S3 Bucket Policy that allows public read access to website objects.

Example policy:

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "PublicRead",
      "Effect": "Allow",
      "Principal": "*",
      "Action": "s3:GetObject",
      "Resource": "arn:aws:s3:::YOUR_BUCKET_NAME/*"
    }
  ]
}
```

This automatically makes uploaded website objects publicly accessible.

---

# Challenge 2 — Protect Website Data

## Task 5 — Enable Versioning

Enabled bucket versioning to protect against:

- Accidental deletion
- Accidental overwrite

Updated the website by modifying the HTML background colors:

| Original | Updated |
|----------|---------|
| aquamarine | gainsboro |
| orange | cornsilk |

Uploaded the updated file and verified:

- Multiple versions of `index.html`
- Previous versions remain recoverable

---

## Benefits of Versioning

- Protects critical website assets
- Enables rollback to previous versions
- Prevents accidental data loss

---

# Challenge 3 — Optimize Storage Costs

## Task 6 — Configure Lifecycle Rules

Created two lifecycle rules.

### Rule 1

Move previous object versions to:

- **S3 Standard-Infrequent Access**

After:

- **30 Days**

---

### Rule 2

Delete previous object versions after:

- **365 Days**

---

## Lifecycle Benefits

- Reduces storage costs
- Automatically archives old versions
- Automatically removes expired versions

---

# Challenge 4 — Disaster Recovery

## Task 7 — Cross-Region Replication

Created:

- Source Bucket
- Destination Bucket

Enabled:

- Versioning on both buckets
- Cross-Region Replication (CRR)

Configured replication using the provided IAM role:

```
CafeRole
```

Replication settings:

- Replicate entire bucket
- Replicate new objects only
- Do not replicate existing objects

Verified:

- Newly uploaded files replicated successfully
- Object versions replicated
- Delete markers replicated correctly

---

## AWS Best Practices Demonstrated

✅ Static Website Hosting

✅ Least Privilege Access

✅ Public Read Bucket Policy

✅ Object Versioning

✅ Data Protection

✅ Lifecycle Management

✅ Cost Optimization

✅ Cross-Region Replication

✅ Disaster Recovery

---

## Skills Demonstrated

- AWS Cloud Fundamentals
- Amazon S3
- Static Website Deployment
- Bucket Policy Configuration
- IAM Role Integration
- Object Versioning
- Lifecycle Management
- Disaster Recovery Planning
- Cross-Region Replication
- Cloud Cost Optimization

---
## Working endpoint
http://traci-cafe-amzn-bucket.s3-website-us-east-1.amazonaws.com/

## Learning Outcomes
Through this project, I gained practical experience in:

* Hosting static websites on Amazon S3
* Configuring public access securely
* Managing website object versions
* Implementing lifecycle policies to optimize storage costs
* Replicating data across AWS Regions for high durability
* Applying AWS Well-Architected Framework best practices for security, reliability, and operational excellence

---

## Key AWS Services Used

| Service | Purpose |
|----------|---------|
| Amazon S3 | Static website hosting |
| IAM | Replication permissions |
| S3 Versioning | Protect website data |
| Lifecycle Rules | Cost optimization |
| Cross-Region Replication | Disaster recovery |

---

## Author
**Ese Daniel**
**Cloud & Software Engineer**


---

## License
This project is for educational and portfolio purposes.
# 🌐 AWS Static Website Hosting (S3 + CloudFront)

## 📌 Overview

This project demonstrates how to host a static website using Amazon S3 and enhance it with CloudFront CDN for better performance and HTTPS support.

---

## 🛠️ Services Used

* Amazon S3 (Storage & Hosting)
* CloudFront (CDN & HTTPS)

---

## 🚀 Step-by-Step Deployment

### 1. Create S3 Bucket

* Go to AWS S3
* Create a bucket with a unique name
* Select region (e.g., ap-south-1)
* Disable "Block all public access"

---

### 2. Upload Website Files

* Upload index.html (and other static files)
* Ensure index.html is in the root of the bucket

---

### 3. Enable Static Website Hosting

* Go to Properties tab
* Enable Static Website Hosting
* Set:

  * Index document → index.html

---

### 4. Configure Bucket Policy

* Go to Permissions → Bucket Policy
* Add public read access:

{
"Version": "2012-10-17",
"Statement": [
{
"Sid": "PublicRead",
"Effect": "Allow",
"Principal": "*",
"Action": "s3:GetObject",
"Resource": "arn:aws:s3:::YOUR-BUCKET-NAME/*"
}
]
}

---

### 5. Access Website

* Copy S3 endpoint URL
* Open in browser

---

### 6. Create CloudFront Distribution

* Go to CloudFront
* Create Distribution
* Select S3 bucket as origin
* Set Viewer Protocol Policy → Redirect HTTP to HTTPS
* Set Default Root Object → index.html (optional)

---

### 7. Access via CloudFront

* Use CloudFront domain:
  https://your-distribution.cloudfront.net

---

### 8. (Optional) Cache Invalidation

* Go to CloudFront → Invalidations
* Create invalidation:
  /*
* Used to refresh updated content

---

## 🌐 Architecture

User → CloudFront (CDN) → S3 (Static Website)

---

## 💡 Key Learnings

* Static website hosting using S3
* CDN concept using CloudFront
* Importance of bucket policies and permissions
* HTTPS enablement using CloudFront
* Cache management with invalidations

---

## ❗ Common Errors & Fixes

### 403 Forbidden / Access Denied

* Check bucket policy
* Disable block public access

### 404 NoSuchKey

* Ensure index.html is in root directory

### Website not updating

* Create CloudFront invalidation

---

## 💼 Use Case

* Portfolio websites
* Landing pages
* Documentation sites

---

## 🧠 Interview Tip

“I hosted a static website using S3 and improved its performance and security by integrating CloudFront CDN with HTTPS and caching.”

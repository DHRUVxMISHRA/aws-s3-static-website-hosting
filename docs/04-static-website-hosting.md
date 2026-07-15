# 🌐 Hosting a Static Website with Amazon S3

In this stage of the project, I configured an Amazon S3 bucket to host a fully functional **static website**.

The website consists of HTML, CSS, JavaScript, and image files that are stored inside an S3 bucket and made publicly accessible through the Amazon S3 Static Website Hosting feature.

---

# 🎯 Objective

The goal of this implementation was to:

- Upload website files to Amazon S3
- Configure the bucket for Static Website Hosting
- Define the default Index and Error documents
- Allow public access to the website
- Configure a Bucket Policy for public read access
- Access the website using the generated S3 Website Endpoint

---

# 🏗️ Architecture

```
Browser
    │
    ▼
S3 Website Endpoint
    │
    ▼
Amazon S3 Bucket
    │
    ├── index.html
    ├── error.html
    ├── css/
    ├── js/
    └── images/
```

---

# 🚀 Implementation Steps

### 1. Upload Website Files

Uploaded the website assets into the S3 bucket.

```
index.html
error.html
css/
js/
images/
```

---

### 2. Enable Static Website Hosting

Configured the bucket to host a static website by enabling **Static Website Hosting**.

Configured:

- **Index Document:** `index.html`
- **Error Document:** `error.html`

This generated an S3 Website Endpoint that serves the website to users.

---

### 3. Configure Public Access

Since Amazon S3 buckets are private by default, Block Public Access was disabled for this bucket to allow public website hosting.

> This configuration was applied only to this bucket and not to the entire AWS account.

---

### 4. Configure Bucket Policy

Attached a Bucket Policy granting public read access to all website objects.

The policy allows anonymous users to perform:

- `s3:GetObject`

on every object inside the bucket.

---

### 5. Verify Website

After configuration, the website became accessible through the generated S3 Website Endpoint.

Verified:

- Home page loads successfully
- Images load correctly
- CSS styling is applied
- JavaScript executes successfully
- Invalid URLs display the custom error page

---

# 📂 Project Structure

```
website/
│
├── index.html
├── error.html
├── css/
├── js/
└── images/
```

---

# 🔐 Security Notes

This project exposes the bucket publicly **only for educational purposes**.

In production environments, the recommended architecture is:

```
Users
    │
    ▼
Amazon CloudFront
    │
Origin Access Control (OAC)
    │
    ▼
Private Amazon S3 Bucket
```

This approach improves security and performance while keeping the bucket private.

---

# ✅ Outcome

Successfully deployed a static website using Amazon S3 by configuring:

- Website Hosting
- Index Document
- Error Document
- Public Access
- Bucket Policy
- Website Endpoint

The website is now accessible directly through the Amazon S3 Static Website Hosting URL.

---

## 📖 Previous Section

⬅️ **Previous:** [03 - Understanding Amazon S3 Key Concepts](03-s3-key-points.md)

## 📖 Next Section

➡️ **Next:** [05 - Amazon S3 Versioning](05-versioning.md)

# 🔄 Configuring Amazon S3 Replication

This section demonstrates how Amazon S3 Replication was configured to automatically copy objects from one S3 bucket to another.

Replication improves data availability, disaster recovery, and backup strategies by maintaining a synchronized copy of objects in a destination bucket.

---

# 🎯 Objective

The objectives of this implementation were to:

- Configure Amazon S3 Replication
- Create source and destination buckets
- Enable Versioning on both buckets
- Configure Same Region Replication (SRR)
- Verify automatic object replication
- Understand the role of IAM in replication

---

# 🏗️ Architecture

```
                Upload Object
                      │
                      ▼
        Source S3 Bucket (Mumbai)
                      │
          Replication Rule (SRR)
                      │
             IAM Replication Role
                      │
                      ▼
     Destination S3 Bucket (Mumbai)
```

---

# 🚀 Implementation Steps

### 1. Create Two S3 Buckets

Created two buckets:

```
Source Bucket

demo-bucket-dhruv-x
```

```
Destination Bucket

demo-bucket-dhruv-x-replica
```

The destination bucket was initially empty.

---

### 2. Enable Versioning

Enabled Versioning on both buckets.

This is a mandatory requirement before replication can be configured.

---

### 3. Create a Replication Rule

Inside the source bucket:

```
Management

↓

Replication Rules

↓

Create Replication Rule
```

Configured the rule with:

- Rule Status: Enabled
- Rule Scope: All Objects
- Priority: Default

---

### 4. Select Destination Bucket

Selected the destination bucket in the same AWS Region.

This implementation used:

```
Same Region Replication (SRR)
```

---

### 5. Configure IAM Role

Allowed AWS to automatically create the required IAM Role.

The IAM Role grants Amazon S3 permission to:

- Read objects from the source bucket
- Copy objects to the destination bucket

---

### 6. Configure Additional Options

Used the default replication settings.

The following optional features were available:

- Replication Time Control (RTC)
- Replication Metrics
- Delete Marker Replication
- Replica Modification Sync

---

### 7. Replicate Existing Objects

Enabled replication for existing objects.

Amazon S3 automatically created a Batch Operations job to copy previously uploaded objects.

---

### 8. Verify Replication

After the replication job completed, the destination bucket contained copies of all project files, including:

```
index.html

error.html

assets/

images/

README.md

LICENSE.md
```

Version IDs were also successfully replicated.

---

# 📂 Replication Workflow

```
Create Source Bucket
        │
        ▼
Create Destination Bucket
        │
        ▼
Enable Versioning
        │
        ▼
Create Replication Rule
        │
        ▼
AWS Creates IAM Role
        │
        ▼
Upload Objects
        │
        ▼
Objects Automatically Copied
```

---

# ✅ Practical Outcome

Successfully configured Amazon S3 Same Region Replication.

Verified that:

- Versioning was enabled on both buckets
- Replication rule was created successfully
- IAM Role was automatically generated
- Existing objects were replicated using Batch Operations
- New uploads are replicated automatically
- Object versions were preserved in the destination bucket

---

# 📌 Key Observations

- Replication requires two separate buckets.
- Versioning must be enabled before replication can be configured.
- Replication is asynchronous and may take a short time to complete.
- Existing objects require Batch Replication.
- New objects are automatically copied after the replication rule is active.

---

# 📖 Previous Section

⬅️ **Previous:** [05 - Amazon S3 Versioning](05-s3-versioning.md)

## 📖 Next Section

➡️ **Next:** [07 - Amazon S3 Storage Classes](07-storage-classes.md)

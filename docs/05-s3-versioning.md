# 🔄 Implementing Amazon S3 Versioning

In this stage of the project, Amazon S3 **Versioning** was enabled to protect objects from accidental deletion and overwriting.

Versioning allows Amazon S3 to preserve previous versions of an object instead of permanently replacing or deleting it.

---

# 🎯 Objective

The objectives of this implementation were to:

- Enable Versioning on an S3 bucket
- Understand how Amazon S3 stores multiple versions of an object
- Observe Version IDs assigned to uploaded objects
- Verify how overwriting objects creates new versions
- Understand Delete Markers and Versioning behavior
- Explore storage implications of Versioning

---

# 🏗️ Implementation Workflow

```
Create S3 Bucket
        │
        ▼
Enable Versioning
        │
        ▼
Upload Object
        │
        ▼
Modify & Upload Again
        │
        ▼
Amazon S3 Creates New Version
        │
        ▼
Previous Version Preserved
```

---

# 🚀 Implementation Steps

### 1. Open Bucket Properties

Navigate to the S3 bucket and open the **Properties** tab.

Locate the **Bucket Versioning** section.

---

### 2. Enable Versioning

Click **Edit** and change the Versioning status from:

```
Disabled
```

to

```
Enabled
```

Save the changes.

---

### 3. Upload an Object

Uploaded an object to the bucket.

Example:

```
index.html
```

---

### 4. Display Object Versions

Enabled **Show Versions** in the Objects tab.

Initially, the uploaded object showed:

```
Version ID

null
```

because it had been uploaded before Versioning was enabled.

---

### 5. Upload the Same File Again

Uploaded the same object again after enabling Versioning.

Amazon S3 created a new Version ID while preserving the previous version.

Example:

```
Current Version

Version ID:
Z_RSR48hHST...

↓

Previous Version

Version ID:
null
```

This confirmed that Versioning stores multiple versions instead of replacing the existing object.

---

# 📂 Version History

```
index.html

│

├── Version 3 (Current)

├── Version 2

└── Version 1
```

Each version is assigned a unique Version ID and remains available until deleted.

---

# 🗑️ Object Deletion Behavior

With Versioning enabled, deleting an object does **not** immediately remove its data.

Instead, Amazon S3 creates a **Delete Marker**, making the object appear deleted while preserving previous versions.

```
Delete Marker (Current)

↓

Version 3

↓

Version 2

↓

Version 1
```

Removing the Delete Marker restores access to the object.

---

# 💰 Storage Considerations

Every object version consumes storage and is billed separately.

As more versions are created, storage usage increases.

To reduce long-term storage costs, Versioning is commonly combined with **Lifecycle Rules** to archive or delete older versions automatically.

---

# 🔐 Security Considerations

Amazon S3 also supports **MFA Delete**, which requires Multi-Factor Authentication before:

- Deleting object versions
- Changing Versioning configuration

This provides additional protection for sensitive workloads.

---

# ✅ Practical Outcome

Successfully configured Versioning on the S3 bucket and verified that:

- Versioning was enabled successfully
- Existing objects retained their previous versions
- New uploads generated unique Version IDs
- Previous versions remained recoverable
- Delete operations create Delete Markers instead of immediately removing data

---

# 📖 Previous Section

⬅️ **Previous:** [04 - Hosting a Static Website with Amazon S3](04-static-website-hosting.md)

## 📖 Next Section

➡️ **Next:** [06 - Amazon S3 Replication](06-s3-replication.md)

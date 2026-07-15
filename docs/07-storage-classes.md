# 💾 Exploring Amazon S3 Storage Classes

This section demonstrates the different Amazon S3 Storage Classes available for optimizing storage costs based on data access patterns.

During this project, the storage class of objects was examined and updated through the AWS Management Console to understand how Amazon S3 manages frequently accessed, infrequently accessed, and archived data.

---

# 🎯 Objective

The objectives of this implementation were to:

- Understand the purpose of Amazon S3 Storage Classes
- Compare available storage classes
- View and modify an object's storage class
- Learn when each storage class should be used
- Understand how Lifecycle Rules automate storage optimization

---

# 🏗 Storage Class Categories

Amazon S3 organizes storage classes based on how frequently data is accessed.

```
Amazon S3

│

├── Frequently Accessed
│     ├── S3 Standard
│     └── Intelligent-Tiering
│
├── Infrequently Accessed
│     ├── Standard-IA
│     └── One Zone-IA
│
└── Archive Storage
      ├── Glacier Instant Retrieval
      ├── Glacier Flexible Retrieval
      └── Glacier Deep Archive
```

---

# 🚀 Implementation Steps

### 1. Open an Object

Inside the S3 bucket, selected an uploaded object.

Example:

```
index.html
```

Opened the object details page.

---

### 2. View Current Storage Class

Verified the object's default storage class.

Initially, the object was stored in:

```
S3 Standard
```

---

### 3. Edit Storage Class

Selected **Edit** next to the Storage Class section.

AWS displayed the available storage classes:

- S3 Standard
- Intelligent-Tiering
- Standard-IA
- One Zone-IA
- Glacier Instant Retrieval
- Glacier Flexible Retrieval
- Glacier Deep Archive

---

### 4. Change Storage Class

Selected a different storage class and saved the changes.

If bucket versioning is enabled, Amazon S3 creates a new object version with the updated storage class.

---

### 5. Review Available Options

Compared the storage classes based on:

- Access frequency
- Retrieval speed
- Cost
- Availability
- Recommended use cases

This demonstrated how storage costs can be optimized without changing application behavior.

---

# 📊 Storage Class Comparison

| Storage Class | Best Used For |
|---------------|---------------|
| S3 Standard | Frequently accessed application data |
| Intelligent-Tiering | Unknown or changing access patterns |
| Standard-IA | Infrequently accessed backups |
| One Zone-IA | Reproducible, non-critical data |
| Glacier Instant Retrieval | Rarely accessed archives requiring instant retrieval |
| Glacier Flexible Retrieval | Long-term backups |
| Glacier Deep Archive | Compliance and long-term archival |

---

# 🔄 Lifecycle Integration

Instead of manually changing storage classes, Amazon S3 supports Lifecycle Rules that automatically transition objects based on age.

Example workflow:

```
S3 Standard

↓

Standard-IA

↓

Glacier Flexible Retrieval

↓

Glacier Deep Archive
```

This helps reduce long-term storage costs automatically.

---

# ✅ Practical Outcome

Successfully explored Amazon S3 Storage Classes by:

- Viewing the default storage class of uploaded objects
- Updating the storage class through the AWS Console
- Comparing storage options for different workloads
- Understanding retrieval times and pricing considerations
- Learning how Lifecycle Rules automate storage optimization

---

# 📌 Key Observations

- S3 Standard is the default storage class.
- Different storage classes are designed for different access patterns.
- Lower storage costs often come with retrieval fees or longer retrieval times.
- Glacier storage classes are intended for archival data.
- Lifecycle Rules provide automated storage optimization.

---

# 📖 Previous Section

⬅️ **Previous:** [06 - Amazon S3 Replication](06-s3-replication.md)

## 📖 Next Section

➡️ **Next:** [08 - Lifecycle Rules](08-lifecycle-rules.md)

# Project 02 — S3 Storage Management

## Overview
As part of the CloudBridge startup simulation, I set up Amazon S3 as the company's core file storage solution. The goal was to store internal company files durably, maintain a version history of every file change, and automatically clean up old versions to keep storage costs under control.

## What I Built
- Created an S3 bucket: `cloudbridge-company-files-mr-01` in ap-south-1 (Mumbai)
- Uploaded files to simulate real company file storage
- Configured a Lifecycle Policy to automatically delete non-current versions after a set period — no manual cleanup needed
- Enabled S3 Versioning after initial setup so every future file update creates a new version rather than overwriting the original

## Architecture
Developer/Admin
|
S3 Bucket(cloudbridge-company-files-mr-01)
├── Versioning ENABLED

│   └── Every upload creates a new version

└── Lifecycle Rule

└── Auto-delete non-current versions after X days
## Key Concepts
- **S3 Buckets** — globally unique containers for object storage
- **Object Storage** — files stored as objects with metadata, not in a traditional file system
- **Versioning** — every overwrite creates a new version; nothing is silently lost or overwritten
- **Lifecycle Policies** — automated rules that expire old versions based on age, reducing storage costs without manual intervention

## AWS Services Used
| Service | Purpose |
|---|---|
| Amazon S3 | Core object storage |
| S3 Versioning | File version history |
| S3 Lifecycle Rules | Automated cleanup of old versions |

## Screenshots
| File | Description |
|---|---|
| files-uploaded.png | Files uploaded to the S3 bucket |
| lifecycle-config.png | Lifecycle rule configuration |
| lifecycle-confirmed.png | Lifecycle rule active in console |
| versioning-enabled.png | Versioning enabled on the bucket |

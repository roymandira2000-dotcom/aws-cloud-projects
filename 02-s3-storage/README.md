
 Amazon S3 Storage Management
Project Overview
This project demonstrates core Amazon S3 features using a real AWS account under the CloudBridge startup scenario. It covers bucket creation, file uploads, versioning, and automated lifecycle management — foundational skills for any cloud engineering role.
________________________________________
Business Context
CloudBridge needed a centralized, durable storage solution for internal company files. The requirement was to maintain file history through versioning while automatically cleaning up old versions to control storage costs.
________________________________________
What I Built
•	Created an S3 bucket: cloudbridge-company-files-mr-01 in ap-south-1 (Mumbai)
•	Uploaded files to the bucket to simulate real company file storage
•	Enabled S3 Versioning to maintain a history of all file changes
•	Configured a Lifecycle Policy to automatically delete old (non-current) versions and keep storage costs under control
________________________________________
AWS Services Used
Service	Purpose
Amazon S3	Object storage for company files
S3 Versioning	Maintain history of file changes
S3 Lifecycle Rules	Auto-delete old versions to manage cost
________________________________________
Architecture
Developer / Admin
       │
       ▼
  S3 Bucket (cloudbridge-company-files-mr-01)
       │
       ├── Versioning ENABLED
       │     └── Every upload creates a new version
       │
       └── Lifecycle Rule
             └── Delete non-current versions automatically
________________________________________
Key Concepts Learned
•	S3 Buckets — globally unique namespaced containers for object storage
•	Object Storage — files stored as objects with metadata, not in a file system hierarchy
•	Versioning — once enabled, every overwrite creates a new version; nothing is silently lost
•	Lifecycle Policies — rules that automatically transition or expire objects/versions based on age, reducing manual overhead and cost
________________________________________
Screenshots
Screenshot	Description
files-uploaded.png	Files successfully uploaded to the S3 bucket
versioning-enabled.png	Versioning enabled on the bucket
lifecycle-config.png	Lifecycle rule configured to delete old versions
lifecycle-confirmed.png	Lifecycle rule active and confirmed in console
________________________________________
Region
ap-south-1 — Asia Pacific (Mumbai)
________________________________________
Part of the CloudBridge Portfolio
This is Project 02 of the CloudBridge AWS Portfolio — a hands-on series of real AWS projects built to demonstrate cloud engineering skills
06	Lambda — Serverless Functions


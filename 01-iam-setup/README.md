# Project 1 — Secure Team Access Setup

## Real World Scenario
CloudBridge startup needed secure AWS access for 
their 3-member team. Each person needed different 
permissions based on their role.

## Architecture
Root Account (locked away)
    └── mandira-admin (admin user + MFA enabled)
        ├── Group: developers
        │   └── ravi-developer (EC2 + S3 full access)
        ├── Group: data-analysts
        │   └── priya-analyst (S3 read only)
        └── Group: managers
            └── arjun-manager (Billing read only)

## What I built
- 3 IAM user groups with different permission levels
- 3 IAM users assigned to appropriate groups
- MFA enabled on admin account
- Tested least privilege — priya-analyst correctly 
  denied EC2 access

## Key concepts demonstrated
- Principle of least privilege
- Managing permissions through groups
- MFA for security
- Implicit deny in action

## Proof of least privilege
priya-analyst got API Error on EC2 because 
her group only has S3 read access

## AWS CLI commands used
aws iam list-users
aws iam list-groups

## What I learned
New IAM users have zero permissions by default.
Groups make permission management scalable.

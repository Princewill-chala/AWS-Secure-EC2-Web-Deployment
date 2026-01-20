# AWS-Secure-EC2-Web-Deployment

## Overview
This project demonstrates the secure deployment of a production-ready static website on Amazon Web Services (AWS) using an EC2 instance running Ubuntu 22.04.
It follows cloud security best practices, including proper IAM usage, network hardening with security groups, key-based authentication, Elastic IP assignment, and basic Linux server hardening.

The goal is to simulate a real-world cloud deployment scenario and document it professionally for DevOps and Cloud Security portfolios.

## Architecture
```yaml
                 ┌──────────────────────────┐
                 │        IAM USER          │
                 │  (EC2-Admins Group)     │
                 │  - No Root Access       │
                 └───────────┬─────────────┘
                             │
                      AWS Console / CLI
                             │
                             v
┌──────────────┐     ┌─────────────────────────────┐
│   User PC    │────▶│   EC2 Instance (Ubuntu)     │
│ (SSH :22)    │     │   - t2.micro                │
│ (Key Pair)   │     │   - Security Group Firewall │
└──────┬───────┘     │   - Root Login Disabled     │
       │             │   - Sudo User Created       │
       │             └─────────────┬──────────────┘
       │                           │
       │                     Apache Web Server
       │                           │
       │                    /var/www/html
       │                           │
       │                     Static Website
       │                           │
       └───────────┐               v
                   │        Elastic IP (Public)
                   │               │
                   └──────────────▶│
                                   v
                            Internet Users
                         (HTTP Port 80 Open)

```
### **Core Components:**
- AWS IAM (Least-privilege access)
- EC2 (t3.micro, Ubuntu 22.04)
- Security Groups (Firewall rules)
- SSH Key Pair (Secure access)
- Elastic IP (Persistent public access)
- Web Server (Apache)





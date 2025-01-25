# nextcloud-aws-deployment
AWS Ubuntu server with nextcloud running with accessible through a cloudflare tunnel.
## Overview
This project documents the process of deploying Nextcloud on an AWS EC2 instance running Ubuntu 22.04 LTS, with secure remote access via Cloudflare.

## Features
- Secure cloud storage with Nextcloud
- Encrypted access via SSL (Let's Encrypt)
- User account management (Juan and Julie)
- Automated cron jobs for background tasks

## Prerequisites
- AWS account with access to EC2
- Registered domain (Cloudflare)
- Basic Linux and networking knowledge

## Project Architecture
- AWS EC2 Ubuntu 22.04 LTS
- Apache, MySQL, PHP (LAMP stack)
- Cloudflare DNS for domain management
- # Nextcloud AWS Deployment Guide

## Step 1: Launching an EC2 Instance
1. Choose Ubuntu 22.04 LTS AMI
2. Instance type: `t2.medium`
3. Configure security groups:
   - SSH (22) - Your IP
   - HTTP (80) - 0.0.0.0/0
   - HTTPS (443) - 0.0.0.0/0
4. Attach key pair and launch the instance.

## Step 2: SSH into the Instance
```bash
ssh -i aws_key.pem ubuntu@your-public-ip

## Step 3: Install LAMP Stack
- sudo apt update && sudo apt install apache2 mysql-server php libapache2-mod-php -y

### Step 4: Add Configuration Files**
- Create a `config/` directory to store important files such as:
  - Apache configuration (`nextcloud.conf`)
  - MySQL database setup (`db_config.sql`)
  - Cloudflare DNS settings (`cloudflare_dns_config.txt`)

---

## Step 5: Add Screenshots**
1. Take screenshots of:
   - AWS EC2 instance setup
   - Cloudflare DNS settings
   - Nextcloud web interface
2. Save them in a `screenshots/` directory in your project.

---

## Step 6: Add Cron Job Instructions**
Create a `cron-jobs.md` file to document the background job setup:

```markdown
# Cron Jobs Setup for Nextcloud

To ensure smooth operation of Nextcloud:

```bash
sudo crontab -u www-data -e

Add the following line (without #):

javascript
Copy
Edit
*/15 * * * * php -f /var/www/nextcloud/cron.php


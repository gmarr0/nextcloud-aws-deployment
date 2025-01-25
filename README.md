# NextCloud AWS Deployment
AWS Ubuntu server with nextcloud accessible through a cloudflare tunnel.
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

ssh -i aws_key.pem ubuntu@your-public-ip

## Step 3: Install LAMP Stack
- sudo apt update && sudo apt install apache2 mysql-server php libapache2-mod-php -y

### Step 4: Configuration Files
- Create a `config/` directory to store important files such as:
  - Apache configuration (`nextcloud.conf`)
![Apache config file](https://github.com/user-attachments/assets/882b3221-a954-41ad-86b8-bbf194a2b274)
  - Nextcloud Configuration File
![Nextcloud configuration file add your Cloudflare domain](https://github.com/user-attachments/assets/d3b4d3f9-7a4f-4b43-9abb-b7acacdb0569)
---

## Interfaces
   - AWS EC2 instance setup
     ![Aws EC2 Ubuntu  Instance Running ](https://github.com/user-attachments/assets/f7394666-981a-4259-b2e5-911809310849)
   - Cloudflare DNS settings (`cloudflare_dns_config.txt`)
     ![cloudflare DNS settings](https://github.com/user-attachments/assets/974dd766-0b2f-4493-8ba2-83e71e897931)
   - Nextcloud web interface
![nextcloud darthserverflare com working !](https://github.com/user-attachments/assets/3d900eff-9ab8-4a9c-bebd-c5b9651911fe)

## (Bonus) Step 5: Add Cron Job Instructions
Create a `cron-jobs.md` file to document the background job setup:


## Cron Jobs Setup for Nextcloud

To ensure smooth operation of Nextcloud:

sudo crontab -u www-data -e

Add the following line (without #):

Copy
Edit
*/15 * * * * php -f /var/www/nextcloud/cron.php
![cron jobs set up for self updating](https://github.com/user-attachments/assets/7cd2a020-835b-4ad9-8f04-1b867a5554e1)

## Mobile Camera Roll upload
Nextcloud Mobile Settings to upload camera roll & Camera Roll Uploading
![setting to upload camera roll](https://github.com/user-attachments/assets/fb150d82-f232-4282-bd1d-7d6f2ae1946a)
![camera roll uploading](https://github.com/user-attachments/assets/b6759d11-84b0-420b-abe1-21e463f1e397)


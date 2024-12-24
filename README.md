# Testing-Linux-and-Servers

This repository contains the implementation for setting up a secure, monitored, and well-maintained development environment for new developers Sarah and Mike. The tasks include system monitoring, user management, and automated backup configuration.

---

## Table of Contents

1. [Task 1: System Monitoring Setup](#task-1-system-monitoring-setup)
2. [Task 2: User Management and Access Control](#task-2-user-management-and-access-control)
3. [Task 3: Backup Configuration for Web Servers](#task-3-backup-configuration-for-web-servers)
4. [Report and Challenges](#report-and-challenges)
5. [Submission](#submission)

---

## Task 1: System Monitoring Setup

### Objective
Configure a monitoring system to ensure the health, performance, and capacity planning of the development environment.

### Steps
1. **Installed monitoring tools:**
    - Install `htop`:
      ```bash
      sudo apt update
      sudo apt install htop -y
      ```
    - Install `nmon`:
      ```bash
      sudo apt update
      sudo apt install nmon -y
      ```
2. **Configured disk usage monitoring:**
    - Use `df` for overall disk space monitoring:
      ```bash
      df -h
      ```
    - Use `du` for directory-level disk usage analysis:
      ```bash
      du -sh /path/to/directory
      ```
3. **Implemented process monitoring:**
    - Identify resource-intensive processes using `htop`:
      ```bash
      htop
      ```
    - Use `ps aux` for detailed process information:
      ```bash
      ps aux --sort=-%mem
      ```
4. **Set up logging:**
    - Save monitoring outputs to `/var/logs/monitoring.log` using scheduled scripts:
      ```bash
      htop -b -n 1 > /var/logs/monitoring.log
      ```

### Outputs
- Screenshots of `htop`, `nmon`, and disk usage commands.
- Example log file: `monitoring.log`

---

## Task 2: User Management and Access Control

### Objective
Create user accounts and configure secure access controls for Sarah and Mike.

### Steps
1. **Created user accounts:**
    - Add Sarah:
      ```bash
      sudo adduser Sarah
      ```
    - Add Mike:
      ```bash
      sudo adduser Mike
      ```
2. **Created dedicated directories:**
    - Create Sarah's workspace:
      ```bash
      sudo mkdir -p /home/Sarah/workspace
      ```
    - Create Mike's workspace:
      ```bash
      sudo mkdir -p /home/Mike/workspace
      ```
3. **Set permissions:**
    - Ensure only Sarah has access to her workspace:
      ```bash
      sudo chmod 700 /home/Sarah/workspace
      sudo chown Sarah:Sarah /home/Sarah/workspace
      ```
    - Ensure only Mike has access to his workspace:
      ```bash
      sudo chmod 700 /home/Mike/workspace
      sudo chown Mike:Mike /home/Mike/workspace
      ```
4. **Enforced password policies:**
    - Configure password expiration every 30 days:
      ```bash
      sudo chage -M 30 Sarah
      sudo chage -M 30 Mike
      ```

### Outputs
- Screenshots of user creation and permission setups.
- Documentation of password policy enforcement.

---

## Task 3: Backup Configuration for Web Servers

### Objective
Automate backups for Sarah's Apache server and Mike's Nginx server, ensuring data integrity and recovery.

### Steps
1. **Configured backup scripts:**
    - Sarah's Apache backup script:
      ```bash
      #!/bin/bash
      tar -czf /backups/apache_backup_$(date +%F).tar.gz /etc/httpd/ /var/www/html/
      ```
    - Mike's Nginx backup script:
      ```bash
      #!/bin/bash
      tar -czf /backups/nginx_backup_$(date +%F).tar.gz /etc/nginx/ /usr/share/nginx/html/
      ```
2. **Scheduled cron jobs:**
    - Sarah's backup cron job:
      ```bash
      crontab -e
      0 0 * * 2 /path/to/apache_backup.sh
      ```
    - Mike's backup cron job:
      ```bash
      crontab -e
      0 0 * * 2 /path/to/nginx_backup.sh
      ```
3. **Verified backup integrity:**
    - List contents of the compressed files:
      ```bash
      tar -tvf /backups/apache_backup_$(date +%F).tar.gz
      tar -tvf /backups/nginx_backup_$(date +%F).tar.gz
      ```

### Outputs
- Backup files in `/backups/` directory.
- Verification logs showing successful backup contents.

---

## Report and Challenges

### Summary
- Successfully installed and configured monitoring tools (`htop`, `nmon`).
- User accounts and secure directories set up for Sarah and Mike with enforced password policies.
- Automated backups configured for Apache and Nginx servers with verified integrity.

### Challenges
1. **Monitoring Tools**:
   - Initial issues with nmon installation resolved by updating system packages.
2. **User Management**:
   - Permissions conflict resolved by ensuring correct ownership using `chown`.
3. **Backup Automation**:
   - Debugged cron job configurations for correct scheduling.

---

## Submission

The full implementation and supporting files are available in this repository. Access the project at: [GitHub Repository Link](#).


## Author
- Aakash Rawat 

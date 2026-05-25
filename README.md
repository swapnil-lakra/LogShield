# LogShield : Zero-Downtime Log Management Automation for Ubuntu VPS

> Accomplished 0 disk-full outages in 90 days as measured by UptimeRobot (free tier), by implementing an automated log rotation & alerting cron job that prevented ~18 hours of downtime and saved ~₹37,000 in potential revenue loss.

**Company**: B2C e-commerce store (fashion accessories), bootstrapped (₹48,000–₹55,000/month revenue) running on a single DigitalOcean Droplet (Ubuntu 22.04 LTS, 2 vCPU / 4 GB RAM).

**Pain**: Every 72–96 hours (roughly every 3–4 days), /var/log reached 100% capacity due to overflowing WooCommerce, Apache, and PHP error logs. This disk saturation crashed Apache and MySQL, causing 3–6 hours of site downtime with 500 Internal Server Errors. Financial loss ≈ ₹6,200 per downtime.

**Constraints**: ₹0 budget for tooling (no paid monitoring tools allowed). Only SSH shell access and Postfix (email) were available. Required to securely retain the last 7 days of logs for GST audit compliance.

**Risk of Inaction**: Weekly unplanned outages, dropping Google rankings, rising customer bounce rates, and continuous revenue loss for the business.

**My Solution**: Engineered a custom cron-driven Bash script that executes daily at 2:00 AM to automatically rotate logs, compress large files using gzip, and purge logs older than 7 days. Configured real-time email alerts via Postfix if disk usage crosses 80%, and debugged/fixed the system's default logrotate configuration.
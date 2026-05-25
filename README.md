# LogShield : Zero-Downtime Log Management Automation for Ubuntu VPS

> Accomplished 0 disk-full outages in 90 days as measured by uptime monitoring, by implementing an automated log rotation & alerting cron job that saved ~18 hours of downtime and ₹36,000 in potential revenue loss.

**Company**: Small e-commerce startup (₹50K/month revenue) running on a single Ubuntu VPS. Pain: Every 3 days, /var/log reached 95% capacity, crashing Apache/MySQL and causing 2–3 hours of site downtime (500 Error). Financial loss ≈ ₹6,000 per downtime. 

**Constraints**: No paid monitoring tools available; only shell access and sendmail configured. Must retain the last 7 days of logs for auditing purposes. 

**Risk of Inaction**: Weekly unplanned outages, dropping Google rankings, and a 40% increase in customer bounce rate. 

**My Solution**: Developed and deployed a cron-driven shell script that runs daily at 2:00 AM to automatically rotate logs, compress large files, purge logs older than 7 days, and trigger email alerts via sendmail if disk usage exceeds 80%.
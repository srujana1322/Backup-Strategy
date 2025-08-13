Script:
#!/bin/bash
directories="/home	/etc	/var/www"
backup_location="/backup"
timestamp=$(date +%Y%m%d_%H%M%S)
backup_file="$backup_location/backup_$timestamp.tar.gz"

tar -czf $backup_file $directories find $backup_location -type f -mtime
+7 -name "*.tar.gz" -exec rm {} \;
echo "Backup completed: $backup_file" | mail -s "Backup Notification" admin@mycomp.com



This script creates a backup of essential directories (/home, /etc, /var/www) and saves it to a designated backup location with a timestamped filename. It includes a cleanup mechanism that deletes backups older than 7 days, efficiently managing storage space. The administrator receives an email notification upon completion.

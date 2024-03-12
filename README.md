# BASHBackup
Bash Script for Automated DB Backup
#!/bin/bash
#   MySQL database credentials
DB_USER="your_username"
DB_PASS="your_password"
DB_NAME="your_database"

#Backup Directory
BACKUP_DIR="/path/to/backup/directory"

#   Time stamp (Format: YYYY MM DD)
TIMESTAMP=$(date +"%Y%m%d")

#   Backup file name
BACKUP_FILE="$BACKUP_DIR/$DB_NAME-$TIMESTAMP.sql"

#Dump the MySQL database
mysqldump -u$DB_USER -p$DB_PASS $DB_NAME > $BACKUP_FILE

#   Check if the backup was successful
if [ $? -eq 0 ]; then
    echo "Database backup successfully created: $BACKUP_FILE"
else
    echo "Error: Database backup failed"
fi

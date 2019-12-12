Backup SLA:

- Coverage:			Automated backup schedules for Cron should be created via running Ansible 
                    playbook for MySQL database, ansible configuration for webserver, WordPress, 
					DNS agent and server setup, and backup system itself. The files mentioned 
					above should be backed up to the backup server onsite and to the AWS cloud 
					service.
					
					Ansible vault password should be backed up on physical media, stored in a 
					secure locker in 2 different office locations. Additionally, digital copy 
					of ansible vault password is stored on Ansible managing node.
					
- RPO:				Acceptable data loss for the data stored in the database is the amount of 
                    data generated in 2 working days.
					
					Acceptable data loss for the service configuration files is 1 week.

- Versioning:		For the MySQL database, incremental backups should be created on everyday 
                    basis, full backups - once a week, on Sunday.
					
					For Ansible setup files incremental backups should be created every week 
					on Sunday, full backups - once a month.

- Retention:		MySQL database backups should be stored for 1 month.
					
					Ansible configuration files backups should be stored for 3 months.

- Usability:		Backup recovery is verified by having all the services configured by Ansible 
                    files operational. Data should be restored to the state of last available backup 
					(1 day prior).

- Restoration criteria:      Restoration is required in case of MySQL data getting compromised 
                    or lost, and in case of service operation disruption due to intentional or 
					unintentional misconfiguration, or in case of service transfer.

- RTO:				Recovery time shouldn't exceed 1 day.
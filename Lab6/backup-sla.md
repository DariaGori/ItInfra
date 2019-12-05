Backup SLA:

- Coverage			Automated backup should be created via Ansible for MySQL database, ansible 
                    configuration for webserver, WordPress, DNS agent and server setup, and backup 
					system itself. The files mentioned above should be backed up to the backup 
					server onsite and to the cloud service.
					
					Ansible vault password should be backed up on physical media, stored in a secure 
					locker in 2 different ofice locations. Additionally, digital copy of ansible 
					vault password is stored on Ansible managing node.
					
- RPO				Acceptable data loss for the data stored in the database is the amount of data
                    generated in 2 working days.
					
					Acceptable data loss for the service configuration files is difficult to estimate,
					because the adjustments to the configuration files may heavily vary in significance.
					However, these files are rarely altered after the initial creation.


- Versioning		For the MySQL database, incremental backups should be created on everyday basis,
                    full backups - once a week, on Sunday.
					
					For Ansible setup files incremental backups should be created every week on Sunday,
					full backups - once a month.

- Retention			MySQL database incremental backups should be stored for 1 month. The last full backup
                    of each calendar month should be kept for half a year, the rest should be removed in 
					1 month.
					
					Ansible configuration files incremental backups should be stored for 3 months, full 
                    backups - for a year.

- Usability			Backup recovery is verified by having all the services configured by Ansible files
                    operational. Data should be restored to the state of last available backup (1 day 
					prior).

- Restoration       Restoration is required in case of MySQL data getting compromised or lost, and in case
  criteria		    of service operation disruption due to intentional or unintentional misconfiguration,
                    or in case of service transfer.

- RTO				Recovery time shouldn't exceed 1 day.
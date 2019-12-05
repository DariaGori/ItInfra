Restoration is performed by system user "backup_user".

Commands for service restoration:
- MySQL database
  duplicity --no-encryption restore rsync://{{bserver}}//srv/backup/mysql_db/mysql.{{ db_name }}.sql /home/{{ user }}/mysql.{{ db_name }}.sql
  mysql {{ db_name }} < /home/{{ user }}/mysql.{{ db_name }}.sql

- Ansible configuration files restoration:
  duplicity --no-encryption restore rsync://{{bserver}}//srv/backup/{{ directory }} /home/{{ mgm_user }}/			for bind master

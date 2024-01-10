Install and configure infrastructure with Ansible:

    ansible-playbook infra.yaml

Restore MySQL data from the backup:

    Connect to timofeimih-1, port and host are in hosts file of ansible infrastructure source files
    ssh -p[PORT_NUMBER] ubuntu@[HOST] (for example ssh -p3849 ubuntu@193.40.156.67)
    sudo -u backup duplicity --no-encryption restore rsync://timofeimih@backup.timofeimih.pro/mysql /home/backup/restore/mysql
    sudo mysql -e "CREATE DATABASE IF NOT EXISTS agama"
    sudo mysql agama < /home/backup/restore/mysql/agama.sql

Results can be checked by going into mysql as root user and checking the tables by using following list of commands:

	mysql
	use agama;
	select * from item; 

Restore InfluxDB data from the backup:

    Connect to timofeimih-3, port and host are in "hosts" file of ansible infrastructure source files
    ssh -p[PORT_NUMBER] ubuntu@[HOST] (for example ssh -p3849 ubuntu@193.40.156.67)
    sudo -u backup duplicity --no-encryption restore rsync://timofeimih@backup.timofeimih.pro/influxdb /home/backup/restore/influxdb
    sudo service telegraf stop
    sudo -u backup influx -execute 'DROP DATABASE telegraf'
    sudo -u backup influxd restore -portable -database telegraf /home/backup/restore/influxdb

Results can be checked by going into mysql as root user and checking the tables by using following list of commands:

	influx
	use telegraf
	show measurements

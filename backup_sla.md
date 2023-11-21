Backup approach for:
	Database servers:
		Backup coverage: every 4 hours, all database servers
		RPO: 10 minutes
		Versioning and retention: 100 versions saved for 360 days
		Usability checks: every 30 days
		Restoration criteria: in case of server data damaged
		RTO: 8 hours
	InfluxDB
	Backup coverage: every 4 hours, all influxdb servers
		RPO: 10 minutes
		Versioning and retention: 100 version saved for 360 days
		Usability checks: every 30 days
		Restoration criteria: in case of server data damaged
		RTO: 8 hours
	Ansible repository 
		Backup coverage: once a day, all ansible resotories
		RPO: 24 hours
		Versioning and retention: 10 versions saved for 360 days
		Usability checks: every 30 days
		Restoration criteria: in case of server unaivalibity
		RTO: 20 hours



Backup coverage -- what is backed up and what is not
RPO (recovery point objective)
Versioning and retention -- how many backup versions are stored and for how long
Usability checks -- how is backup usability verified
Restoration criteria -- when should backup be restored
RTO (recovery time objective)
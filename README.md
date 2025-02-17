# IT Infrastructure Services Course Practical & Ansible Code

This repository contains the practical implementation and Ansible code developed as part of the "IT Infrastructure Services" course. In this project, I created a mock startup and integrated various services including:

- **Bind**
- **Docker**
- **Grafana**
- **HAProxy**
- **InfluxDB**
- **Keepalived**
- **MySQL**
- **Nginx**
- **Prometheus**
- **uWSGI**

Some of these services have redundancy settings to ensure high availability and failover in case of failure.

## Backup Strategy

### 1. **Database Servers**

- **Backup Coverage**: All database servers, are backed up every 24 hours.
- **RPO (Recovery Point Objective)**: 24 hours.
- **Versioning & Retention**: 100 versions, retained for 360 days.
- **Usability Checks**: Every 30 days.
- **Restoration Criteria**: In case of server data corruption.
- **RTO (Recovery Time Objective)**: 8 hours.

### 2. **InfluxDB Servers**

- **Backup Coverage**: All InfluxDB servers, are backed up every 24 hours.
- **RPO**: 10 minutes.
- **Versioning & Retention**: 100 versions, retained for 360 days.
- **Usability Checks**: Every 30 days.
- **Restoration Criteria**: In case of server data corruption.
- **RTO**: 24 hours.

### 3. **Ansible Repositories**

- **Backup Coverage**: All Ansible repositories, are backed up once a day.
- **RPO**: 24 hours.
- **Versioning & Retention**: 10 versions, retained for 360 days.
- **Usability Checks**: Every 30 days.
- **Restoration Criteria**: In case of server unavailability.
- **RTO**: 20 hours.

## Redundancy Settings

Several services in this project have redundancy configurations to ensure high availability and minimize downtime in case of failures:

- **Keepalived**: Used to provide redundancy for critical services, such as database servers and application servers. It ensures automatic failover by monitoring the health of services and switching to a backup server in case of failure.
  
- **HAProxy**: Configured with multiple backend servers to provide load balancing and redundancy. In case of failure in one backend server, HAProxy will route traffic to the available servers.
  
- **MySQL**: Set up with master-slave replication to ensure data redundancy

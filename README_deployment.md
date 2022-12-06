# Manufacturing Process Management System (MPMS)

## Purpose

MPMS provides end-to-end (i.e., from order reception until product delivery) manufacturing process management and orchestration of activities by:

 - modeling processes and agents
 - executing in automated way the processes by assigning activities to agents
 - providing process monitoring for a complete status overview of the manufacturing processes

## Overview
A process application for a Manufacturing Process Management System for [SHOP4CF](https://www.shop4cf.eu/) project.
Developed by [Information Systems](https://www.tue.nl/en/research/research-groups/industrial-engineering/information-systems-ieis/) research group of [TUe](https://www.tue.nl/en/) and [European Dynamics](https://www.eurodyn.com/).

*This project has been generated as a Spring Boot application (Spring Boot version 2.4.3) embedding [Camunda Platform](https://camunda.com/products/camunda-platform/), Community Edition v7.15.0. More info can be found on [Camunda Spring Boot Integration](https://docs.camunda.org/manual/7.15/user-guide/spring-boot-integration//).

## How to deploy it?

**Prerequisites:**
 - Deployment requires requires [Docker Compose](https://docs.docker.com/compose/install/) v3.8 or above.
 - During initial installation, internet access is required in order to download:
	 - ***openjdk:11.0.13-jre-slim***  (appears in `Dockerfile`)
	 - ***image: postgres:14-alpine***  (for both `shop4cf-mpms-core-postgres` and `shop4cf-mpms-app-postgres` containers)
	 - ***image: adminer:4.8.1*** (optional image)


**Deploy the docker services:**
 - Unpack the docker package that you just downloaded from RAMP:
![docker package file explorer](https://surfdrive.surf.nl/files/index.php/s/sv1Unera5sZwOtY/download)
 - Configure parameters in **`.env`** file
	 - e.g., OrionLD CB url:port, DB ports, passwords
 - Open a terminal, navigate to the **`docker`** folder and run:
	> docker-compose up -d --build
![docker-compose up console](https://surfdrive.surf.nl/files/index.php/s/oXUH6icbvH6z56w/download)
 - To see the console of the *`shop4cf-mpms`* application, run:
	> docker logs shop4cf-mpms -f
	![camunda-platform logs console](https://surfdrive.surf.nl/files/index.php/s/iE1n0PkpUP4nGHs/download)
	 - when you see the following at the end, everything is ready (or search for the red-highlighted logs):
	 ![camunda-platform logs console ready](https://surfdrive.surf.nl/files/index.php/s/A7k5683H19F5d81/download)

## How to use it?

**Access MPMS web applications on:**
[http://\[host_address\]:\[port\]/camunda/app/welcome/default/#!/login](http://%5Bhost_address%5D:%5Bport%5D/camunda/app/welcome/default/#!/login)
![MPMS welcome](https://surfdrive.surf.nl/files/index.php/s/yynJ1lijOD7xCF1/download)

 - Configure users of the web applications on **Admin**
 - *Start Processes* or react on *Tasks* on **Tasklist**:
![MPMS Tasklist](https://surfdrive.surf.nl/files/index.php/s/ohMYfdjCTrBSoxu/download)

 - Monitor processes on **Cockpit**:
 ![MPMS Cockpit](https://surfdrive.surf.nl/files/index.php/s/4PajvrZfOwrYYY9/download)
 ![MPMS Cockpit](https://surfdrive.surf.nl/files/index.php/s/NqztPQ9G1h94xSG/download)
 - [Optional] Manage DB data on **Adminer**:
 ![MPMS Cockpit](https://surfdrive.surf.nl/files/index.php/s/RDZNATlSUFkF383/download)

## Environment Restrictions
Built and tested against Camunda Platform version 7.15.0, Spring Boot version 2.4.3.

## Known Limitations

## Improvements Backlog

## License
Provided under various open source licenses (mainly [Apache License 2.0](http://www.apache.org/licenses/LICENSE-2.0.html) and [MIT](http://opensource.org/licenses/MIT)). Third-party libraries or application servers included are distributed under their respective licenses. Full list including optional dependencies can be found on [Camunda - Third party libraries](https://docs.camunda.org/manual/7.15/introduction/third-party-libraries/).

## Version History
	 
- **Version 1.0** (15-Nov-2021)
       
    Initial version of MPMS with:
	 - Core functionality
	    - FIWARE  integration
		    - Subscriptions to entities
		    - Receive notifications from subscriptions
		    - Post entities
	    - DB integration
		    - Postgres "Process Engine" DB (for persisting engine's runtime data)
		    - Postgres "Application" DB (for storing definitions and relevant business data)

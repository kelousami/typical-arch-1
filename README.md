/!\ PLEASE DO NOT USE THIS IN PRODUCTION !!!
THIS IS ONLY FOR EDUCATION PURPOSE /!\

# Ansible & Docker example
In this "experimental" example, I'm creating several centos:7 images using Docker.
All images include SSH Server (so to provision them easily with Ansible)
Each image is targeted to specific usage, including: 
- Load-balancer 
- Reverse proxy
- Backend middleware (application server)
- Database
- Monitoring server (will also include tools such elastic search, for production usage)

Targeted technologies
- Ansible
- Docker

Also covered technologies :
- Nginx
- Wildfly 10 (with Oracle JDK 8)
- Postgresql
- Shinken & Elastic-search

-> This is still in progress ..


/!\ PLEASE DO NOT USE THIS IN PRODUCTION !!!
THIS IS ONLY FOR EDUCATION PURPOSE /!\


# Method


# Principles
- Limit root and previligied users actions as much as possible
- Create and target users with specific usage to specific machines and apps.
- Limit users permissions to targeted machines and apps.
- Separate concerns. Those actions need to be done separatly: 
    -- Hosting machine (OS) creation, 
    -- Hosting machine configuration,
    -- Midlleware binary install, 
    -- Middleware instance creations,
    -- Middleware instance configuration and 
    -- Application deployment
- Idempotence. The result of an action does not change if we run multiple times 
under the same conditions.
- Every actions must be verifiable.
- Verify success/failure/skip completion of each action.
- Unless it's the first action, any action must have knwoledge of previous
  action completion status (success/failure/skip) and perform according to it.
- Actions with no dependecies on others, can and should be run alone without
  need to run the whole action list.


# Steps 
Direct application of method and principles on a specific need (requirement) 
leads to those steps:
- Create or use existing host
- Configure the host
    - Install pre-requisite modules (sshd, filewalld ..)
    - Open ports
    - Create users
- Install middleware packages
- Create middleware instances
- Configure middleware instances
- Start instances 
- Deploy applications


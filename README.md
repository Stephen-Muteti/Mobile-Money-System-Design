# Mobile-Money-System-Design

This repository contains an end-to-end documentation on how to create a Secure, Scalable and Highly available Mobile Money System. The design conforms to modern system design approaches and technologies and may reference several System Design Papers by different scholars. It is imperative to note that this design assumes a cloud native infrastructure and leverages on a **distributed, containerized microservices architecture**

# Deployment Design
The system should be deployed in three availability zones (3 AZs). Two AZs should be used for the Production environment while the third AZ remains as an Remote Disaster Recovery (RDR) site.
The deployment design document in this repository covers the Env setup, the network setup and the DB setup.

**Env Setup**
The physical sites should be situated in different regions to further strengthen the AZ design. There should be careful design considerations around the AZ site selections so that the agreed upon **RPO** and **RTO** values are not violated. To control the Quorum availability another special AZ that does not rely on the previous 3 AZs is deployed to contain the logic for:
1. Disaster Recovery
2. Switchover
3. The selection of the master DB Node within a cluster (I will delve into this later)

**The Network Setup**
The tenant network is partitioned into production and test environments each with similar structural zones: MGT Zone, DATA Zone, APP Zone & DMZ Zone. The Zones are logically 
separated for security enhancement and reduce complexity in managing any connections. The production environment is the one that has the running system while the test environment houses the infrastructure meant for user acceptance testing and training.
The network subnets of the environments adhere to the naming convention VPC-EnvAZ-ZONE-Subnet e.g. VPC-Pr1-DATA-Subnet.
While coming up with the VPC, it’s paramount that we pay keen attention to the necessary and allowable connections between the different zones within and across Azs (ACLs).
At the DB layer, only the application services in the same stripe can be connected.

NOTE:
➢ The UAT test bed networking is a dual-AZ networking.
➢ The Training test bed networking is a single-AZ networking.
➢ The Config test bed networking is a single-AZ networking.
➢ The test beds share the MGT Zones
VPC-Test1-MGT-Subnet (for UAT & Config)
VPC-Test2-MGT-Subnet (for UAT & Training)

# PIM Solution
PIM is done using **CyberArk** PIM Solution. See the attached design document

# Log Management
See the attached document on how logs could be collected and used for tracing actions by O & M personnel.

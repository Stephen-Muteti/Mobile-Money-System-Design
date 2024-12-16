# Mobile-Money-System-Design

This repository contains an end-to-end documentation on how to create a Secure, Scalable and Highly available Mobile Money System. This is a reflection of what I was actually dealing with in Huawei Technologies but does not contain any documents created by Huawei. The design conforms to modern system design approaches and technologies and may reference several System Design Papers by different scholars.

# Deployment Design
The system should be deployed in three availability zones (3 AZs). Two AZs should be used for the Production environment while the third AZ remains as an Remote Disaster Recovery (RDR) site.
The deployment design document in this repository covers the Env setup, the network setup and the DB setup.

# PIM Solution
PIM is done using **CyberArk** PIM Solution. See the attached design document

# Log Management
See the attached document on how logs could be collected and used for tracing actions by O & M personnel.

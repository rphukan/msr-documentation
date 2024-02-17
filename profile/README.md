# About the Org
It contains some repos which are going to be used by all the applications within the org. Like
- some shared libraries for handling the security aspects of the applications
- few core services which need to be run first
- some shared services
- a document service for handling documents

and some application specific repos like
- lending-services for the LOS

and some other repos like
- Terraform scripts for GCP
- Open API specifications
- Config files for the config server

# The mono repos
## security-libraries
Some shared libraries (jars) for handling the security across different microservices. Visit the link below for more details.
[security-libraries](securitylibraries.md)
## core-services
These are the core services which hanldes things like authentication, service discovery, config management, smart routing etc. Click the link below for more details.
[core-services](coreservices.md)
## shared-services
Some common services shared across different applications within the org. More details on the link below
[shared-services](sharedservices.md)
## documents-service
The document managment solution for the org. More details on the link below
[documents-service](documentsservice.md)
## lending-services
These constitute the LOS application. Click on the link below for more details
[lending-services](lendingservices.md)
## others
There are some more repos for Terraform Scrpts, APi spec etc. More details about it is on the link below
[others](others.md)

## Identity And Access Management
We are using the open source [Keycloak](https://www.keycloak.org) for Identity and Access Management. More details about it is on the link below
[Identity Provider](identityprovider.md)
## MongoDB
Some of the applications within the org uses the MongoDB document database. More details about it is on the link below
[MongoDB](mongodb.md)

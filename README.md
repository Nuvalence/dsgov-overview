# Digital Suite for Government
The Digital Suite for Govenrment (DSGov) is a collection of cloud-native, open source, reusable platform components. These components are intended to be used as *"Solution Accelerators"* for common public sector use cases, such as administration of geovernment services and citizen applications for benefits.

Solution Accelerators are different from off the shelf software components in that they are meant to be starting points for a solution, forked from their baseline and customized to solve the problems at hand. DSGov Solution Accelerator components are built to serve a baseline of common solution needs while providing foundations and frameworks for handling cross cutting concerns, such as localization, security, scalability, observability and high availability.

## DSGov Components
![DSGov Components](images/DSGov%20Components.jpg)

### Web Portals
The [dsgov-web](https://github.com/Nuvalence/dsgov-web) repository is a NX mono-repo containing 2 Angular single page application web portals. Both portals are built to provide access to business data configures in [Work Manager](https://github.com/Nuvalence/dsgov-work-manager).

The Public Portal is built to allow citizens to complete applications and track their progress as well as view existing records related to themselves.

The Agency Portal is includes dashboards for viewing work in progress, such as applications requiring review as well as an admin console for configuring data and workflow for implemented processes.

### Work Manager
The [dsgov-work-manager](https://github.com/Nuvalence/dsgov-work-manager) repository contains a Spring Boot API for managing data nad process state for custom configured business processes. Work Manager handles configuration and state management for user defined transaction types. 

Transaction configuration can be thought of in terms of 3 pillars of the system that make transaction flexible to address many use cases without software engineer intervention.

1. **Configurable Workflows** - The transaction lifecycle of user tasks, statuses and automation is governed by a workflow configuration using a 3rd party open source software package called Camunda. 

2. **Dynamic Data Schemas** - Transactions contain a DynamicEntity (data attribute) that is free form data, stored in Work Manager's database as a JSON blob. The structure of DynamicEntity data per type of transaction is governed by a Schema configuration that describes the entity's attribute types as well as other configuration governing how they are processed.

3. **Dynamic Forms** - The web based user interfaces used for interacting with transactions include the embedding of user configurable forms (both for collecting user input and displaying dynamic data informationally). The Agency Portal Admin Console includes a drag and drop form builder for defining this configuration.

### User Management
The [dsgov-user-management](https://github.com/Nuvalence/dsgov-user-management) repository contains a Spring Boot API to handle user profile/preferences storage and permission management API. Provides identity provider agnostic user tracking to other APIs.

### Document Management
The [dsgov-document-management](https://github.com/Nuvalence/dsgov-document-management) repository contains a Spring Boot API for managing storage of user provided files (images, PDFs, etc...). The service handles virus scanning of uploaded content using ClamAV and quarantine of infected files. Additionally, custom document processors can be implemented to perform analysis on uploaded documents. There are implementations of 2 processors using Googles Document AI service included in the current baseline.

### Portal API
The [dsgov-portal-api](https://github.com/Nuvalence/dsgov-portal-api) repository contains a companion backend for the two web portals, implemented as a Spring Boot API. This companion API handles Identity Provider logout and collection of client side log events.

### Notification Service
The [dsgov-notification-service](https://github.com/Nuvalence/dsgov-notification-service) repository contains a Spring Boot API for orchestrating Email and SMS notifications.

### Audit Service
The [dsgov-audit-service](https://github.com/Nuvalence/dsgov-audit-service) repository contains a Spring Boot API that provides secure storage and retrieval of audit events, logged by other APIs.

## Additional Components

### DSGov Libraries
The [dsgov-libs](https://github.com/Nuvalence/dsgov-libs) repository contains a collection of Java libraries usefull to DSGov APIs written in Spring Boot. Libraries are published to Maven Central and include:

* **dsgov-auth**: Encoding of authentication and authorization contract between DSGov componets via issuance of JWTs.
* **dsgov-logging**: Common application logging conventions, including correlation ID management for distributed tracing.
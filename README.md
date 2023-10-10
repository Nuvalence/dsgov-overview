# Digital Suite for Government
The Digital Suite for Government (DSGov) is a collection of cloud-native, open-source, reusable platform components that accelerate the delivery of feature-rich, endlessly customizable solutions for mission-critical public sector use cases, such as licensing & permits, claims management, and driver & vehicle services.

[Solution Accelerators](https://nuvalence.io/dsgov/) are different from pre-built products and off-the-shelf software components in that they are meant to be the **starting point** for an end-to-end solution, forked from their baseline and customized according to your organization's unique requirements and priorities. DSGov components are built to deliver core capabilities atop a powerful foundation and using proven frameworks that account for cross-cutting concerns, such as localization, security, scalability, observability, and high availability.

## DSGov Components
![DSGov Components](images/DSGov%20Components.jpg)

### Web Portals
The [dsgov-web](https://github.com/Nuvalence/dsgov-web) repository is an NX mono-repo containing two Angular single-page application web portals. Both portals are built to provide access to business data configured in [Work Manager](https://github.com/Nuvalence/dsgov-work-manager).

The **Public Portal** empowers constituents to initiate and submit online applications (including document uploads), monitor progress on agency decisions, and access their personalized transaction history.

The **Agency Portal** enables the agency workforce to efficiently process digital transactions, including centralized dashboards, review & decision workflows, and complete audit history. This portal also offers an Admin Console for no-code data and workflow configuration.

### Work Manager
The [dsgov-work-manager](https://github.com/Nuvalence/dsgov-work-manager) repository contains a Spring Boot API to manage data and process state for custom-configured business processes. Work Manager handles configuration and state management for user-defined transaction types. 

End users can easily configure transactions across a wide variety of use cases, with little or no engineering intervention. This system includes:

1. **Configurable Workflows**. The transaction lifecycle of user tasks, statuses, and automation is governed by a workflow configuration using a third-party open source software package called Camunda. 

2. **Dynamic Data Schemas**. Transactions contain a DynamicEntity (data attribute) that is free-form data, stored in Work Manager's database as a JSON blob. The structure of DynamicEntity data is governed at the transaction-type level by a Schema configuration that describes the entity's attribute types, as well as other configuration governing how they are processed.

3. **Dynamic Forms**. The web-based user interfaces rely on embedded user-configurable forms to collect user input, and to display dynamic data informationally. This configuration can be defined in the Agency Portal Admin Console, which offers a drag-and-drop form builder.

### User Management
The [dsgov-user-management](https://github.com/Nuvalence/dsgov-user-management) repository contains a Spring Boot API to handle user profile/preferences storage and permission management API. It also provides identity provider-agnostic user tracking to other APIs.

### Document Management
The [dsgov-document-management](https://github.com/Nuvalence/dsgov-document-management) repository contains a Spring Boot API to manage storage of user-provided files (for example, images and PDFs). The service handles virus scanning of uploaded content using ClamAV, as well as quarantine of infected files. Additionally, custom document processors can be implemented to perform analysis on uploaded documents. The current DSGov baseline includes implementations of two processors using Google's Document AI service.

### Portal API
The [dsgov-portal-api](https://github.com/Nuvalence/dsgov-portal-api) repository contains a companion backend for the two web portals, implemented as a Spring Boot API. This companion API handles Identity Provider logout and collection of client-side log events.

### Notification Service
The [dsgov-notification-service](https://github.com/Nuvalence/dsgov-notification-service) repository contains a Spring Boot API to orchestrate Email and SMS notifications.

### Audit Service
The [dsgov-audit-service](https://github.com/Nuvalence/dsgov-audit-service) repository contains a Spring Boot API that provides secure storage and retrieval of audit events logged by other APIs.

## Additional Components

### DSGov Libraries
The [dsgov-libs](https://github.com/Nuvalence/dsgov-libs) repository contains a collection of Java libraries useful to DSGov APIs written in Spring Boot. Libraries are published to Maven Central, and include:

* **dsgov-auth**: Encoding of authentication and authorization contract between DSGov components via issuance of JWTs.
* **dsgov-logging**: Common application logging conventions, including correlation ID management for distributed tracing.

## Acknowledgement & Involvement
DSGov was built, released, and is actively maintained by [Nuvalence](http://nuvalence.io/) engineers, product managers, and designers based on several years of experience delivering innovative, high-quality solutions to our public sector clients.

We welcome contributions by the community at large, particularly public-sector professionals committed to delivering experiences that delight the tech-savvy public and workforce.

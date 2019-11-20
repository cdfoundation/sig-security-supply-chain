# Software Supply Chain Framework

This document provides an overview of the Software Supply Chain. It describes goals, defines key concepts, and provides an overview of user scenarios. Finally, it describes the current status of the industry-wide effort and upcoming milestones.

## Overview

The Software Supply Chain is a complex system of producers and consumers including developers, packagers, application and service providers, and end customers

## Definitions
Key concepts in the Software Supply Chain include producers, consumers, artifacts, metadata (Bills of Materials), repositories, policy, and enforcement.
 
### Artifacts

An artifact is a component of software, from small to large. Artifacts include the following:
* Snippet (a byte range in a file)
* File
* Package - grouping of files
* Package repository - grouping of packages
* Container - grouping of packages and files
* Cloud Service - grouping of containers, packages and files
* Installed System – grouping of packages and files

### Artifact Metadata (Software Bill of Materials)
Artifact metadata, also known as a Software Bill of Materials (SBOM) describes artifacts. Elements of artifact metadata include the following:
*	Identity (name, producer, version, hash)
*	Authenticity (cryptographic signatures)
*	Build information (tools, environment, configuration)
*	Intellectual property information (license)
*	Relationships with other artifacts (describes, contains)

### Artifact Repositories
An artifact repository is a service that distributes artifact metadata and may also distribute artifacts. Artifact repositories are responsible for the following tasks:
*	Signing metadata
*	Managing cryptographic key distribution, revocation, and replacement
*	Distributing artifacts and/or metadata
Some examples of repositories include the following source code repositories, container registries, package repositories, installed package databases.

### Artifact Policy
Artifact policy describes requirements for artifact consumption, including the following:
*	Allowed producers
*	Allowed licenses
*	Allowed build environments
*	Required security steps (e.g. scanning)
*	Required certifications (e.g. SDL, industry audits)
*	Expected order of steps in the chain (e.g. to prevent man in the middle attacks)

### Policy Enforcement
Policy enforcement is responsible for inspecting consumed artifacts and enforcing policy, including the following:
*	Signature verification
*	Artifact hash validation
*	License validation
*	Build/build environment validation (e.g. reproducible build)
*	Required steps validation
*	Required certification validation

### User Scenarios

The following table provides an overview of Software Supply Chain user scenarios.


| Scenario       | Description  | Metadata      | Policy |
| :------------- | :---------- | :----------- | :--------- |
|  Identity | Enable unambiguous referral to software components, e.g. to consume, purchase, transfer, inventory, or associate with outside databases, e.g. security vulnerability | Unique identity | Allowed identities |
|Build Security|Enable validation of choices made for securing software during the creation process (pedigree)|Information about build environment|Allowed build environments|
|Authenticity|Enable validation of the software provider (provenance)|Cryptographic signature|Allowed signatures|
|Integrity|Enable validation of whether software (or the SBOM itself) has been altered, e.g. during transmission or on deployed systems|
SBOM signature, component hashes|Allowed hash and signature types|
|License|Enable validation of proper and legal use of software|Intellectual property information|Allowed intellectual property|
|Chain of Custody|Enable validation that software has completed expected steps in expected order, e.g. including security and compliance audits|Steps in the chain|Allowed and required steps and order|


[//]: # 'Additional user scenarios can be found in the user scenarios folder.'

# Software Supply Chain Security Framework

This document provides an overview of the Software Supply Chain Security Framework. It describes the mission, defines key concepts, and provides a summary of user scenarios.

## Overview

The Software Supply Chain is a complex system of producers and consumers including developers, packagers, application and service providers, and end customers

## Mission

Participants across the software supply chain can produce and consume trustworthy software.


## User Scenarios

The following table provides an overview of Software Supply Chain Security user scenarios.


| Scenario       | Description  |
| :------------- | :---------- |
|  Identity | Enable unambiguous referral to software components, e.g. to consume, purchase, transfer, inventory, or associate with outside databases, e.g. security vulnerability |
|Build Security|Enable validation of choices made for securing software during the creation process (pedigree)|
|Authenticity|Enable validation of the software provider (provenance)|
|Integrity|Enable validation of whether software has been altered, e.g. during transmission or on deployed systems|
|License|Enable validation of proper and legal use of software|
|Chain of Custody|Enable validation that software has completed expected steps in expected order, e.g. including security and compliance audits|

Following are several example user scenarios.

### Example Scenario - Identity

1. Developer commits code
2. Code is used in many places:
    * Incorporated into packages
    * Packages are installed on various end user systems
    * Packages are installed in various containers
    * Containers are used in various cloud services
3. Later, a vulnerability is identified in the developer's commit
4. Scanning tools are able to identify all files, packages, installed systems, containers and cloud services that contain the commit.    
### Example Scenario - Integrity
1. Developer commits code
2. Build system verifies integity
    * Was source doe provided by an allowed committer
    * Is the source code received the same as what was committed?
3. Build system outputs build artifacts
4. Release system verifies integrity
    * Were the build artificats provided by an allowed builder?
    * Were the build artifacts received the same as what the builder produced?

## Definitions
Key concepts in the Software Supply Chain Security Framework include producers, consumers, artifact stores, metadata stores, metadata, policy, and enforcement.

|Producers||||Consumers|
|:-----:|:-----:|:-----:|:-----:|:-----:|
|Artifact Stores<br>+<br>Metadata Stores|->|Artifacts<br>+<br>Metadata|->|Policy<br>+<br>Enforcement|
 
### Producers

Producers produce software **artifacts** and also metadata describing artifacts. They distribute artifact metadata via **metadata stores**.

### Consumers

Consumers consume artifacts and metadata. They write **policy** describing attributes of artifacts they are willing to consume. In the process of consuming artifacts, they apply policy **enforcement**.

### Artifact Stores
Artifact stores distribute artifacts.

Artifact stores are provided by the following:
* source code repositories
* container registries
* package repositories

### Metadata Stores
Metadata stores distributes artifact metadata. They are responsible for the following tasks:
*	Signing metadata
*	Managing distribution, revocation, and replacement of cryptographic keys
*	Distributing metadata

Metadata stores are provided by the following:
* source code repositories
* container registries
* package repositories
* installed package databases

### Artifacts

Artifacts are components of software, from small to large. Artifacts include the following:
* Snippet (a byte range in a file)
* File
* Package - grouping of files
* Package repository - grouping of packages
* Container - grouping of packages and files
* Cloud Service - grouping of containers, packages and files
* Installed System – grouping of packages and files

### Metadata
Artifact metadata describes artifacts. Metadata includes the following attributes:
*	Identity (name, producer, version, hash)
*	Authenticity (cryptographic signatures)
*	Build information (tools, environment, configuration)
*	Intellectual property information (license)
*	Relationships with other artifacts (describes, contains)

### Policy
Policy describes requirements for artifact consumption, including the following:
*	Allowed producers
*	Allowed licenses
*	Allowed build environments
*	Required security steps (e.g. scanning)
*	Required certifications (e.g. SDL, industry audits)
*	Expected order of steps in the chain (e.g. to prevent man in the middle attacks)

### Enforcement
Enforcement is responsible for inspecting incoming artifacts and enforcing policy. Enforcement handles verification and validation including the following:
*	Signature verification
*	Artifact hash validation
*	License validation
*	Build/build environment validation (e.g. reproducible build)
*	Required steps validation
*	Required certification validation

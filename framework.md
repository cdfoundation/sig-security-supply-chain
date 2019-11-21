# Software Supply Chain Security Framework

This document provides an overview of the Software Supply Chain Security Framework. It describes the mission, defines key concepts, and provides a summary of user scenarios.

## Overview

The Software Supply Chain is a complex system of producers and consumers including developers, packagers, application and service providers, and end customers

## Mission

Participants across the software supply chain (developers, packagers, application and service providers, and end customers) can produce and consume trustworthy software.

## Definitions
Key concepts in the Software Supply Chain include producers, consumers, artifacts, metadata stores, metadata, policy, and enforcement.

|Producers||Consumers|
|:-----:|:-----:|:-----:|
|Artifacts <br> ------- <br> Metadata Stores| ->  Metadata  -> |Policy <br> ------- <br> Enforcement|
 
### Producers

Producers produce software **artifacts** and also metadata describing artifacts. They distribute artifact metadata via **metadata stores**.

### Consumers

Consumers consume artifacts and artifact metadata. They write **policy** describing attributes of artifacts they are willing to consume. In the process of consuming artifacts, they apply policy **enforcement**.

### Artifacts

Artifacts are components of software, from small to large. Artifacts include the following:
* Snippet (a byte range in a file)
* File
* Package - grouping of files
* Package repository - grouping of packages
* Container - grouping of packages and files
* Cloud Service - grouping of containers, packages and files
* Installed System – grouping of packages and files

### Metadata Stores
Metadata stores distributes artifact metadata. They are responsible for the following tasks:
*	Signing metadata
*	Managing distribution, revocation, and replacement of cryptographic keys
*	Distributing metadata

Metadata stores are provided by the following:
* source code repositories
* container registries
* package repositories
* installed package databases.

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


Additional user scenarios can be found in the [scenarios](scenarios) folder.

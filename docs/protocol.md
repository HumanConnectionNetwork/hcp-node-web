# Human Connection Protocol (HCP)

Version: Draft 0.1

---

# Introduction

The **Human Connection Protocol (HCP)** is an open protocol for creating, storing, querying and exchanging humanitarian records between independent systems.

The protocol does **not** define a centralized platform.

Instead, it defines a common language that enables interoperability between organizations while allowing each participant to maintain ownership and control of its own data.

---

# Purpose

The purpose of HCP is to make humanitarian information interoperable.

The protocol enables different software systems to exchange structured humanitarian records without requiring a shared database or a central authority.

---

# Scope

HCP specifies:

* record representation
* identifiers
* validation rules
* synchronization model
* capabilities
* interoperability requirements

HCP does **not** specify:

* database technology
* programming language
* user interface
* hosting platform
* organizational workflows

Those decisions belong to each implementation.

---

# Terminology

The key words **MUST**, **MUST NOT**, **SHOULD**, **SHOULD NOT**, and **MAY** in this document are to be interpreted as described in RFC 2119.

---

# Protocol Objectives

HCP has the following objectives.

## Interoperability

Independent systems MUST be able to exchange compatible humanitarian records.

---

## Decentralization

No implementation SHALL require a central server.

Every Node operates independently.

---

## Extensibility

The protocol MUST allow future extensions without breaking compatibility.

---

## Technology Independence

The protocol MUST remain independent from:

* databases
* operating systems
* programming languages
* cloud providers

---

# HCP Node

An HCP Node is any software that correctly implements this specification.

A Node MAY expose:

* REST APIs
* command-line interfaces
* messaging interfaces
* mobile interfaces
* other compatible transports

The transport mechanism is outside the scope of HCP.

---

# Capabilities

Every Node SHOULD expose its supported capabilities.

Examples include:

* protocol version
* supported record types
* authentication methods
* synchronization support
* signature support

Capability discovery allows compatible Nodes to negotiate supported features.

---

# Humanitarian Record

The Humanitarian Record is the fundamental unit of information in HCP.

A record represents structured humanitarian information.

Examples include:

* person registration
* aid request
* family relationship
* medical observation
* shelter registration
* resource availability
* organization reference

The protocol defines how records are represented.

The protocol does not define how organizations use them internally.

---

# Record Identity

Every record MUST have a globally unique identifier.

Identifiers MUST remain stable throughout the lifetime of the record.

Identifiers MUST NOT be reused.

---

# Record Lifecycle

A record typically follows these stages.

```text
Created
    │
Validated
    │
Updated
    │
Shared
    │
Archived
```

Implementations MAY support additional internal states.

---

# Record Validation

Before accepting a record, a Node MUST verify:

* identifier validity
* required fields
* schema compliance
* protocol version compatibility

Implementations MAY perform additional validation.

---

# Record Updates

Records MAY be updated.

Updates SHOULD preserve previous versions whenever possible.

Implementations SHOULD support audit history.

---

# Search

Nodes SHOULD support searching humanitarian records.

Search MAY include:

* exact identifiers
* names
* dates
* organizations
* probabilistic matching

The protocol does not prescribe a specific search algorithm.

---

# Identity Resolution

Identity resolution is implementation-dependent.

A Node MAY estimate that multiple records describe the same person.

The protocol never guarantees legal identity.

Instead, implementations MAY calculate confidence scores using available evidence.

---

# Synchronization

Nodes MAY synchronize records with other trusted Nodes.

Synchronization SHOULD support:

* incremental updates
* conflict detection
* duplicate avoidance
* metadata preservation

Synchronization is optional.

Nodes remain fully functional without federation.

---

# Trust

Trust is intentionally outside the protocol.

HCP does not define trusted organizations.

HCP does not define trusted governments.

HCP does not define trusted databases.

Each organization decides which Nodes to trust.

---

# Authentication

Authentication mechanisms are implementation-specific.

Examples include:

* OAuth
* JWT
* API Keys
* Mutual TLS
* Digital certificates

The protocol only requires authenticated requests when implementations choose to protect resources.

---

# Authorization

Authorization policies are implementation-specific.

The protocol defines no user roles.

Each implementation determines access permissions.

---

# Privacy

Organizations remain responsible for complying with applicable privacy legislation.

HCP provides interoperability.

It does not replace legal obligations regarding personal information.

---

# Security

Implementations SHOULD provide:

* encrypted communication
* authentication
* authorization
* audit logging
* request validation
* rate limiting

Additional security mechanisms MAY be implemented.

---

# Extensibility

Future protocol versions MAY introduce:

* new record types
* additional capabilities
* alternative transports
* digital signatures
* federation improvements
* semantic extensions

Extensions SHOULD preserve backward compatibility whenever possible.

---

# Versioning

Every implementation MUST identify the HCP protocol version it supports.

Backward compatibility SHOULD be maintained between minor versions.

Breaking changes MUST increment the major version.

---

# Compliance

An implementation is considered HCP-compatible if it:

* correctly represents HCP records;
* follows this specification;
* preserves protocol semantics;
* exposes declared capabilities accurately.

Implementations MAY extend functionality provided those extensions do not violate the core specification.

---

# Out of Scope

The following are intentionally outside the scope of HCP:

* humanitarian policies
* aid prioritization
* funding decisions
* beneficiary selection
* operational procedures
* internal organizational workflows
* database architecture
* frontend design

These concerns belong to the organizations using HCP.

---

# Guiding Principle

The protocol is founded on a single architectural principle:

> **Humanitarian information should be portable, interoperable and decentralized.**

Organizations should be free to collaborate without giving up ownership of their data.

HCP exists to provide the common language that makes this collaboration possible.

# Human Connection Protocol (HCP)

# Data Model Specification

Version: Draft 0.1

---

# Introduction

This document defines the canonical data model used by the Human Connection Protocol (HCP).

The purpose of this specification is to ensure that all HCP implementations represent humanitarian information in a compatible way, regardless of the programming language, database engine or platform used.

This document defines **what** information exists within HCP.

The Protocol Specification defines **how** that information is exchanged.

---

# Design Principles

The HCP data model is based on the following principles.

## Record-Oriented

HCP models humanitarian **records**, not people.

Every record represents an observation, registration or statement made by an organization, operator or automated system.

---

## Evidence-Based

Information should be supported by evidence whenever possible.

Records are intended to describe observed facts, not assumptions.

---

## Decentralized

No record is considered globally authoritative.

Different organizations may create different records describing the same individual.

---

## Immutable Identity

Records have permanent identifiers.

People do not.

Identity resolution is performed separately and probabilistically.

---

## Extensible

New object types may be added without changing existing definitions.

---

# Core Objects

The HCP data model is composed of the following core objects.

```text
Record
Person
Organization
Identity
Evidence
Reference
Attachment
Capability
Node
```

---

# Record

The Record is the primary object of HCP.

Every humanitarian interaction produces one Record.

Examples:

* person registration
* aid request
* medical visit
* shelter admission
* food distribution
* family relationship
* status update

A Record MUST have:

* unique identifier
* creation timestamp
* creator organization
* protocol version

A Record MAY include:

* person
* attachments
* evidence
* references
* metadata

---

# Person

A Person object represents the descriptive information contained within a humanitarian record.

It is **not** a globally unique identity.

Different records may contain different Person objects referring to the same human being.

Typical attributes include:

* given name
* family name
* aliases
* date of birth
* estimated age
* gender
* nationality
* languages
* contact information

All attributes are optional unless required by the implementation.

---

# Organization

Represents the organization responsible for creating or maintaining records.

Examples:

* NGOs
* hospitals
* shelters
* government agencies
* volunteer groups

Typical attributes:

* identifier
* legal name
* display name
* country
* contact information

---

# Identity

Identity represents a probabilistic association between multiple records.

It does **not** represent legal identity.

Identity objects MAY contain:

* confidence score
* matching method
* related records
* supporting evidence

Identity resolution is implementation-specific.

---

# Evidence

Evidence supports information contained in a record.

Examples:

* identity document
* medical report
* interview
* photograph
* witness statement

Evidence MAY contain:

* type
* description
* source
* timestamp
* verification status

---

# Reference

References establish relationships between records.

Examples:

* duplicate of
* parent of
* sibling of
* caregiver of
* created from
* supersedes

References help build humanitarian context without duplicating information.

---

# Attachment

Represents external files associated with a record.

Examples:

* images
* PDFs
* scanned documents
* audio
* video

Attachments SHOULD be referenced rather than embedded whenever practical.

---

# Capability

Capability describes the features supported by an HCP Node.

Examples:

* supported protocol version
* authentication methods
* synchronization support
* signature support
* available record types

Capabilities allow Nodes to negotiate compatible behavior.

---

# Node

Represents an implementation of HCP.

A Node MAY expose:

* REST API
* synchronization endpoint
* public capabilities
* health status

Nodes own records.

Nodes do not own people.

---

# Relationships

```text
Node
 │
 ├── Organization
 │
 ├── Record
 │      │
 │      ├── Person
 │      ├── Evidence
 │      ├── Attachment
 │      └── Reference
 │
 └── Capability
```

---

# Identity Resolution

Multiple Records MAY describe the same individual.

Identity resolution attempts to associate these records.

Example:

```text
Record A
    │
    ├──── 93% probability
    │
Record B
```

The protocol does not guarantee correctness.

Implementations MAY use different matching algorithms.

---

# Required Metadata

Every object SHOULD contain standard metadata.

Recommended fields include:

* id
* createdAt
* updatedAt
* createdBy
* protocolVersion

Additional metadata MAY be added by implementations.

---

# Versioning

The schema is versioned independently from software implementations.

Implementations MUST indicate which Data Model Specification version they support.

---

# Future Objects

Future versions of HCP may introduce additional objects, including:

* Household
* Case
* Resource
* Event
* Location
* Service
* Consent
* Assessment
* Incident

These additions SHOULD preserve backward compatibility whenever possible.

---

# Guiding Principle

The HCP data model is intentionally simple.

It represents humanitarian information through structured, interoperable records while allowing organizations to maintain complete ownership of their own data.

The model describes observations, relationships and evidence—not absolute truth.

This distinction enables decentralized collaboration without requiring a central authority or a universal identity database.

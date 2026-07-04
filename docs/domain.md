# Human Connection Protocol (HCP)

# Domain Specification

Version: Draft 0.1

---

# Introduction

This document defines the business domain of the Human Connection Protocol (HCP).

Unlike the Protocol Specification, which defines how Nodes communicate, and the Data Model Specification, which defines the structure of objects, this document defines the meaning and behavior of those objects.

It answers questions such as:

* What is a Record?
* What is an Identity?
* What responsibilities does a Node have?
* What actions are allowed?
* What actions are forbidden?

---

# Core Principle

The Human Connection Protocol does **not** attempt to model objective truth.

Instead, HCP models **humanitarian statements**.

Every Record represents a statement made by an identifiable actor at a specific point in time.

The protocol allows those statements to be verified, related and exchanged.

The protocol never claims they are universally true.

---

# Domain Philosophy

The HCP domain follows six fundamental principles.

## 1. Records are immutable historical facts

A Record represents that:

> "An organization declared this information at this moment."

The historical fact is the declaration itself.

Not necessarily the information contained within it.

---

## 2. Organizations own their records

Every Record belongs to the organization that created it.

Other Nodes may synchronize copies.

Ownership never changes.

---

## 3. Identity is inferred

People are never stored as global identities.

Instead, Nodes infer that multiple Records probably refer to the same individual.

Identity is therefore a computation.

Not stored truth.

---

## 4. Evidence increases confidence

Evidence strengthens trust.

Evidence never guarantees certainty.

---

## 5. Nodes cooperate voluntarily

Synchronization only occurs between Nodes that choose to collaborate.

No Node has authority over another.

---

## 6. The protocol is neutral

HCP does not make humanitarian decisions.

It only enables interoperable information exchange.

---

# Domain Entities

The HCP domain is composed of the following business entities.

```text
Node
Organization
Record
Identity
Evidence
Reference
Attachment
Capability
```

Each entity has clearly defined responsibilities.

---

# Record

## Purpose

A Record is the fundamental business entity of HCP.

Everything in the protocol revolves around Records.

Every humanitarian event creates exactly one new Record.

Examples include:

* person registration
* family registration
* medical consultation
* aid request
* shelter admission
* volunteer registration
* organization registration
* resource availability
* incident report

---

## Responsibilities

A Record is responsible for representing:

* who created the information
* when it was created
* what was observed
* which evidence supports it
* which relationships exist

---

## Allowed Operations

A Record MAY:

* be created
* be queried
* receive additional references
* receive additional evidence
* be superseded by a newer Record
* be synchronized

---

## Forbidden Operations

A Record MUST NOT:

* change its identifier
* change its creator organization
* lose historical traceability

Implementations SHOULD avoid physical deletion.

---

# Identity

## Purpose

Identity is **not** a person.

Identity represents the probability that multiple Records describe the same individual.

Identity is produced by an Identity Resolution process.

---

## Responsibilities

Identity groups Records.

It does not replace them.

---

## Example

```text
Record A
      \
       \
        Identity (94%)
       /
      /
Record B
```

The confidence score belongs to the Identity.

Never to the Records.

---

## Allowed Operations

Identity MAY:

* include Records
* remove Records
* update confidence
* merge with another Identity
* split into multiple Identities

---

## Forbidden Operations

Identity MUST NOT replace the original Records.

The original declarations always remain independent.

---

# Organization

## Purpose

Represents the actor responsible for creating humanitarian information.

Organizations are the owners of their Records.

---

## Responsibilities

Organizations may:

* create Records
* validate Records
* synchronize Records
* publish Capabilities

Organizations define their own operational policies.

The protocol does not.

---

# Node

## Purpose

A Node is an implementation of HCP.

It exposes protocol capabilities to clients.

---

## Responsibilities

Every Node SHOULD be capable of:

* creating Records
* querying Records
* resolving Identities
* exposing Capabilities
* synchronizing with other Nodes

---

## A Node is NOT

A Node is not:

* a humanitarian organization
* a central server
* a database
* a government registry

It is software.

Nothing more.

---

# Evidence

## Purpose

Evidence supports claims made by a Record.

Evidence increases confidence.

It never guarantees correctness.

---

## Examples

Evidence may include:

* identity documents
* photographs
* interviews
* medical reports
* witness statements
* official certificates

---

## Responsibilities

Evidence helps implementations:

* validate information
* resolve Identities
* reduce ambiguity

---

# Reference

## Purpose

References connect Records.

They describe relationships.

They never duplicate information.

---

## Examples

Possible relationships include:

* duplicate_of
* parent_of
* child_of
* spouse_of
* caregiver_of
* linked_to
* supersedes

Future protocol versions may define additional relationship types.

---

# Attachment

## Purpose

Attachments represent external digital resources associated with a Record.

Examples include:

* photographs
* PDFs
* scans
* videos
* audio recordings

Attachments SHOULD be integrity-protected using cryptographic hashes.

---

# Capability

## Purpose

Capabilities describe what a Node supports.

Examples include:

* supported HCP version
* authentication methods
* synchronization
* digital signatures
* search features
* supported transports

Capabilities allow interoperability between heterogeneous implementations.

---

# Domain Services

Some behaviors do not belong to a single entity.

They belong to the domain itself.

---

## Identity Resolution Service

Determines the probability that multiple Records refer to the same individual.

The algorithm is implementation-specific.

---

## Search Service

Provides efficient discovery of Records.

Implementations may combine:

* exact search
* fuzzy search
* probabilistic search

---

## Synchronization Service

Coordinates information exchange between trusted Nodes.

Synchronization never transfers ownership.

Only copies.

---

## Validation Service

Ensures that Records comply with the protocol before persistence.

Validation precedes storage.

---

# Domain Rules

The following business rules define the behavior of HCP.

## Rule 1

Everything begins with a Record.

---

## Rule 2

Every Record belongs to exactly one Organization.

---

## Rule 3

Every Record is created by exactly one Node.

---

## Rule 4

Identity never replaces Records.

---

## Rule 5

Evidence strengthens trust.

---

## Rule 6

References create relationships.

They do not duplicate data.

---

## Rule 7

Nodes exchange Records.

They never exchange ownership.

---

## Rule 8

The protocol defines interoperability.

Organizations define humanitarian policies.

---

# Domain Workflow

A typical flow is illustrated below.

```text
Observation
      │
      ▼
Record Created
      │
      ▼
Validation
      │
      ▼
Persistence
      │
      ▼
Evidence Attached
      │
      ▼
Identity Resolution
      │
      ▼
Synchronization (Optional)
```

Every stage is independent.

Implementations may add internal steps without violating the protocol.

---

# Separation of Responsibilities

The HCP architecture intentionally separates concerns.

| Layer          | Responsibility                        |
| -------------- | ------------------------------------- |
| Protocol       | Defines communication rules           |
| Data Model     | Defines object structures             |
| Domain         | Defines business meaning and behavior |
| Implementation | Executes the domain logic             |

This separation allows multiple implementations to remain compatible while evolving independently.

---

# Final Principle

The HCP Domain is centered on a single concept:

> **A Record is a verifiable humanitarian statement made by an identifiable actor at a specific moment in time.**

Everything else in the protocol—Identity, Evidence, References, Capabilities and Synchronization—exists to organize, validate and exchange those statements without creating a centralized source of truth.

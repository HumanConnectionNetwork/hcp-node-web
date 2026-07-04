# Human Connection Protocol (HCP)

# Glossary

Version: Draft 0.1

---

# Purpose

This glossary defines the official terminology used throughout the Human Connection Protocol (HCP) specification.

All HCP documentation SHOULD use these definitions consistently.

If a term appears in multiple specifications, the definition provided here takes precedence unless explicitly stated otherwise.

---

# Actor

An **Actor** is any identifiable entity capable of performing an action within the HCP ecosystem.

Examples include:

* Organizations
* Human operators
* Software applications
* Bots
* HCP Nodes

Actors create, modify, validate or exchange humanitarian information.

---

# Attachment

An **Attachment** is a digital resource associated with a Record.

Examples include:

* Images
* PDF documents
* Audio recordings
* Videos
* Scanned documents

Attachments are referenced by Records but remain independent resources.

---

# Capability

A **Capability** describes a feature supported by an HCP Node.

Examples include:

* Supported protocol version
* Authentication methods
* Synchronization support
* Digital signatures
* Search features

Capabilities allow Nodes to negotiate interoperability.

---

# Client

A **Client** is any software that communicates with an HCP Node.

Examples include:

* Web applications
* Mobile applications
* Telegram bots
* Desktop software
* External APIs

Clients consume Node services.

They are not part of the protocol itself.

---

# Domain

The **Domain** represents the business rules that define the meaning and behavior of HCP objects.

The Domain is independent from:

* programming languages
* databases
* user interfaces

---

# Evidence

**Evidence** is information that supports the claims contained within a Record.

Evidence increases confidence.

Evidence does not establish absolute truth.

---

# Federation

**Federation** is the voluntary collaboration between independent HCP Nodes.

Federation enables information exchange while preserving organizational autonomy.

Federation is optional.

---

# HCP

**Human Connection Protocol (HCP)** is the open specification that defines how humanitarian information is represented and exchanged.

HCP is technology-independent.

---

# HCP Node

An **HCP Node** is a software implementation of the Human Connection Protocol.

Its responsibilities include:

* Creating Records
* Searching Records
* Resolving Identities
* Publishing Capabilities
* Synchronizing with other Nodes

A Node is software.

It is not a humanitarian organization.

---

# Identity

An **Identity** is a probabilistic association between multiple Records.

Identity represents confidence that those Records describe the same subject.

Identity is inferred.

It is never considered absolute truth.

---

# Identity Resolution

**Identity Resolution** is the process of determining whether multiple Records are likely to describe the same subject.

Different implementations may use different algorithms.

---

# Implementation

An **Implementation** is any software that correctly follows the HCP specification.

Examples include:

* Web Nodes
* Mobile Nodes
* Enterprise Nodes
* Embedded Nodes

All compliant implementations are considered equal.

---

# Metadata

**Metadata** is descriptive information about an object.

Typical metadata includes:

* Identifier
* Creation date
* Creator
* Protocol version

Metadata describes objects without altering their business meaning.

---

# Node

See **HCP Node**.

---

# Organization

An **Organization** is an entity responsible for creating or managing humanitarian Records.

Organizations own their Records.

Organizations do not own the protocol.

---

# Protocol

A **Protocol** is a standardized set of rules that allows independent systems to communicate.

HCP defines communication rules.

It does not define organizational policies.

---

# Record

A **Record** is the fundamental business object of HCP.

A Record represents a humanitarian statement made by an identifiable actor at a specific point in time.

Records are the central element of the protocol.

Everything else exists to support, relate or exchange Records.

---

# Reference

A **Reference** is a relationship between two or more Records.

References create semantic connections without duplicating information.

Examples include:

* duplicate_of
* parent_of
* caregiver_of
* linked_to
* supersedes

---

# Repository

A **Repository** is the persistence mechanism used by an implementation to store domain objects.

Repository implementations are outside the scope of the protocol.

---

# Schema

A **Schema** defines the structural representation of an object.

Schemas describe:

* Fields
* Data types
* Constraints
* Relationships

Schemas do not define business behavior.

---

# Signature

A **Signature** is a cryptographic proof that allows verification of the integrity and origin of information.

Future versions of HCP may define standard digital signature mechanisms.

---

# Subject

A **Subject** is the entity described by a Record.

A Subject is intentionally generic.

Examples include:

* A person
* A family
* An organization
* A shelter
* A medical facility
* A resource
* An event
* An incident

A Subject is **not** limited to human beings.

---

# Synchronization

**Synchronization** is the exchange of Records between trusted HCP Nodes.

Synchronization transfers copies of information.

It never transfers ownership.

---

# Trust

**Trust** is the decision made by an Organization or Node to accept information from another Node.

Trust relationships are external to the protocol.

HCP provides mechanisms for verification.

It does not define trust policies.

---

# Validation

**Validation** is the process of ensuring that an object complies with the HCP specification.

Validation occurs before persistence or synchronization.

---

# Verification

**Verification** is the process of confirming that information is authentic, internally consistent or supported by Evidence.

Verification may include:

* Signature validation
* Evidence review
* Schema validation
* Integrity checks

Verification increases confidence.

It does not guarantee correctness.

---

# Version

A **Version** identifies a specific release of an HCP specification.

Implementations SHOULD declare which specification versions they support.

---

# Vocabulary Principles

The HCP vocabulary follows four principles:

1. Every technical term has a single official meaning.
2. Business concepts are independent of implementation details.
3. Protocol terminology remains stable across software implementations.
4. New terms should be added to this glossary before being used in future specifications.

---

# Final Definition

The Human Connection Protocol defines a shared vocabulary for humanitarian interoperability.

When every implementation uses the same words to describe the same concepts, independent systems can collaborate without ambiguity, regardless of the technology used to build them.

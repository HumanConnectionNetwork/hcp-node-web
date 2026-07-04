# HCP Node Architecture

## Overview

The **HCP Node Web** project is the reference web implementation of an **HCP Node**.

An HCP Node is an independent software component that implements the **Human Connection Protocol (HCP)**, allowing organizations to create, search, validate and exchange humanitarian records using a common, open standard.

The architecture intentionally separates the **protocol** from its **implementation**.

* **HCP** defines *how humanitarian information is represented and exchanged*.
* **HCP Node Web** is one possible implementation of that specification.

Any software written in any programming language may become an HCP Node as long as it correctly implements the protocol.

---

# Design Principles

The architecture follows these principles.

## 1. Decentralization

There is no central server.

Every organization owns and operates its own Node.

Nodes may communicate with each other, but none has authority over another.

---

## 2. Interoperability

Every Node speaks the same language.

The protocol defines:

* record structure
* identifiers
* validation rules
* synchronization rules
* capabilities

The implementation is free to choose its internal technologies.

---

## 3. Local Ownership

Each Node stores and manages its own data.

Organizations decide:

* what to store
* what to publish
* what to synchronize
* what to keep private

HCP never requires a global database.

---

## 4. Extensibility

The protocol is designed to evolve.

New record types, capabilities and integrations can be added without breaking existing Nodes.

---

## 5. Vendor Neutrality

No company, institution or organization owns the protocol.

Any developer may implement HCP.

No implementation receives special privileges.

---

# High-Level Architecture

```text
                  External Systems
                         │
 ┌───────────────────────┼───────────────────────┐
 │                       │                       │
 │                 Telegram Bot             Mobile App
 │                       │                       │
 └───────────────────────┼───────────────────────┘
                         │
                  HCP REST API
                         │
                 HCP Node Services
                         │
     ┌───────────────────┼───────────────────┐
     │                   │                   │
 Record Service   Search Service   Sync Service
     │                   │                   │
     └───────────────────┼───────────────────┘
                         │
                Local Data Storage
                         │
                Human Connection Protocol
                         │
                  Other HCP Nodes
```

---

# Layers

The application is organized into logical layers.

## Presentation Layer

Responsible for user interaction.

Examples:

* Web interface
* Administration dashboard
* Record forms
* Search interface

This layer never contains business rules.

---

## API Layer

Exposes the Node capabilities through REST endpoints.

Responsibilities include:

* request validation
* authentication
* authorization
* serialization
* response formatting

The API should remain independent from the frontend.

---

## Domain Layer

The domain layer contains the core business logic.

Examples:

* Record creation
* Identity resolution
* Validation rules
* Record updates
* Capability discovery

This is the heart of the application.

Everything else depends on it.

---

## Persistence Layer

Responsible for storing information.

The persistence mechanism is intentionally abstract.

Possible implementations include:

* SQLite
* PostgreSQL
* MySQL
* MongoDB
* Cloud databases

The protocol never depends on a specific database technology.

---

## Synchronization Layer

Responsible for communication between Nodes.

Future responsibilities include:

* Node discovery
* Capability negotiation
* Record synchronization
* Conflict detection
* Signature verification
* Trust validation

This layer allows independent Nodes to collaborate without centralization.

---

# Core Components

## Record Service

Creates and updates humanitarian records.

Responsible for validating required fields before persistence.

---

## Search Service

Provides efficient record lookup.

Supports searching by identifiers and probabilistic matching based on available attributes.

---

## Identity Service

Helps associate multiple records that may refer to the same individual.

Identity resolution is probabilistic and improves as additional evidence becomes available.

The service does not establish legal identity.

It estimates the likelihood that records describe the same person.

---

## Capability Service

Publishes what a Node supports.

Examples:

* supported protocol version
* authentication methods
* synchronization features
* available record types

This allows Nodes to negotiate compatible communication.

---

## Synchronization Service

Coordinates information exchange between Nodes.

Future versions may support:

* incremental synchronization
* digital signatures
* trust levels
* conflict resolution
* federation

---

# Data Flow

A typical operation follows these steps:

1. A client submits a request.
2. The API validates the request.
3. The Domain Layer applies business rules.
4. The Persistence Layer stores the information.
5. The Node returns a standardized response.
6. Synchronization with other Nodes may occur asynchronously if configured.

---

# External Clients

An HCP Node is designed to serve multiple types of clients simultaneously.

Examples include:

* Telegram bots
* Mobile applications
* Web portals
* Hospital systems
* NGO management systems
* Emergency response platforms
* Government integrations
* Third-party applications

Clients never communicate directly with each other.

They communicate exclusively through the Node API.

---

# Trust Model

Trust is not centralized.

Each organization determines:

* which Nodes it trusts
* which records it accepts
* which organizations may synchronize
* which information remains private

Trust relationships exist outside the protocol.

The protocol only provides mechanisms for verification.

---

# Scalability

The architecture supports growth by allowing:

* multiple Nodes
* independent deployments
* different storage engines
* different authentication providers
* multiple client applications

No architectural component requires a single global infrastructure.

---

# Relationship with HCP

HCP Node Web is the reference implementation of the Human Connection Protocol.

The protocol exists independently from this repository.

Future implementations may include:

* CLI Nodes
* Embedded Nodes
* Mobile Nodes
* Enterprise Nodes
* Cloud-native Nodes
* Government implementations

All are considered equal as long as they correctly implement the HCP specification.

---

# Architectural Summary

The HCP architecture is based on a simple principle:

> **Humanitarian information should be interoperable without becoming centralized.**

Each Node remains independent.

Each organization retains ownership of its data.

The protocol provides the common language that enables collaboration across the humanitarian ecosystem.


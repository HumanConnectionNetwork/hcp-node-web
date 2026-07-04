# hcp-node-web
Reference implementation of an HCN Web Node for managing HCP records, recipient validation, donor connections, and decentralized humanitarian trust.

# Human Connection Protocol (HCP) Node Web

> Reference implementation of an HCP Node for the Human Connection Network ecosystem.

![License](https://img.shields.io/badge/license-Apache%202.0-blue.svg)

---

# What is HCP?

The **Human Connection Protocol (HCP)** is an open protocol for creating, storing and exchanging humanitarian records between independent organizations, applications and communities.

Instead of creating another centralized platform, HCP defines a common language that allows different systems to work together while each organization keeps control of its own data.

Think of HCP as:

* HTTP for humanitarian records.
* SMTP for humanitarian information.
* A common language that enables interoperability.

---

# What is an HCP Node?

An **HCP Node** is a software implementation of the Human Connection Protocol.

It allows organizations, volunteers, applications and automated agents to:

* Create humanitarian records.
* Search existing records.
* Validate information.
* Synchronize with other HCP Nodes.
* Exchange standardized humanitarian data.

An HCP Node is **not** a central server.

Every organization can operate its own Node while remaining compatible with the entire ecosystem.

---

# Why HCP?

Humanitarian information is often:

* duplicated,
* fragmented,
* incompatible,
* difficult to verify,
* isolated inside organizations.

This creates unnecessary delays and duplicated efforts during humanitarian operations.

HCP addresses this problem by defining a shared protocol instead of another centralized database.

---

# Project Goals

This repository provides the official web reference implementation of an HCP Node.

Its objectives are:

* implement the HCP specification;
* expose a standard REST API;
* provide a web interface for operators;
* demonstrate best implementation practices;
* serve as a reference for other implementations.

---

# What an HCP Node CAN do

* Create humanitarian records.
* Search records.
* Update records.
* Validate records.
* Sign records.
* Synchronize information.
* Publish supported capabilities.
* Exchange data with compatible Nodes.

---

# What an HCP Node DOES NOT do

An HCP Node does **not**:

* manage humanitarian aid;
* distribute money;
* decide who receives assistance;
* replace NGOs or governments;
* centralize global information;
* own humanitarian data.

Each organization remains the owner of its own information.

---

# Architecture

```
                Applications
                      │
          Telegram Bots / Web Apps
                      │
               HCP Node Web
                      │
              HCP REST API
                      │
             Local Data Storage
                      │
             Human Connection Protocol
                      │
         Other Independent HCP Nodes
```

---

# Repository Structure

```
hcp-node-web/

docs/
src/
public/
tests/

README.md
LICENSE
package.json
```

Project documentation is located inside the **docs/** directory.

---

# Technology Stack

Planned technologies:

* Next.js
* React
* TypeScript
* Tailwind CSS
* SQLite (development)
* PostgreSQL-compatible storage (production-ready deployments)
* REST API
* OpenAPI

The architecture is designed to allow alternative storage engines without changing the protocol.

---

# Development Status

Current stage:

> Foundation and protocol definition.

Upcoming milestones include:

* Core domain model
* REST API
* Authentication
* Web dashboard
* Synchronization engine
* Digital signatures
* Federation support

---

# Installation

Clone the repository:

```bash
git clone https://github.com/HumanConnectionNetwork/hcp-node-web.git
```

Install dependencies:

```bash
npm install
```

Run the development server:

```bash
npm run dev
```

---

# Documentation

Detailed documentation is available in:

```
docs/

architecture.md
protocol.md
api.md
security.md
deployment.md
roadmap.md
```

---

# Contributing

Contributions are welcome.

Before submitting code, please:

1. Read the documentation.
2. Open an issue for major changes.
3. Follow the project's coding conventions.
4. Include tests whenever possible.

This project aims to become a long-term open standard, so consistency and documentation are as important as the code itself.

---

# Ecosystem

HCP is part of the Human Connection Network ecosystem.

The ecosystem includes:

* HCP Protocol
* HCP Node Web
* HCP Bot integrations
* Human Connection Network
* RedConexionHumana.org deployments
* Third-party implementations

---

# License

Licensed under the Apache License 2.0.

See the LICENSE file for details.

---

# Vision

Our goal is not to build the largest humanitarian platform.

Our goal is to make humanitarian systems interoperable.

When organizations can exchange trustworthy information through a common protocol, they spend less time managing fragmented data and more time helping people.

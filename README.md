# Campaigns & Channels — Multi-Layer Enterprise Application Framework

A highly structured, graduate-level Python application framework demonstrating clean architecture principles and enterprise-grade design patterns. Built as the capstone project for IT566 (Computer Scripting Techniques) at Marymount University, this system models "Campaigns and Channels" using a completely decoupled, n-tier design.

## 🏛️ Architectural Overview
Rather than utilizing standard flat scripting, this project implements a strict separation of concerns, aligning with **Domain-Driven Design (DDD)** and **Clean Architecture** principles to ensure high maintainability, testability, and horizontal scalability.

```text
               ┌───────────────────────────────────────┐
               │          presentation_layer           │  <-- User Interface & Input Parsing
               └───────────────────┬───────────────────┘
                                   ▼
               ┌───────────────────────────────────────┐
               │             service_layer             │  <-- Use Case Orchestration Boundary
               └───────────────────┬───────────────────┘
                                   ▼
               ┌───────────────────────────────────────┐
               │            business_layer             │  <-- Core Domain Entities & Rules
               └───────────────────┬───────────────────┘
                                   ▼
               ┌───────────────────────────────────────┐
               │    data_layer / persistence_layer     │  <-- Data Access Objects (DAO)
               └───────────────────┬───────────────────┘
                                   ▼
                      ┌────────────┴────────────┐
                      ▼                         ▼
           ┌──────────────────────┐  ┌──────────────────────┐
           │    MySQL Engine      │  │    SQLite Engine     │
           └──────────────────────┘  └──────────────────────┘

Layer Breakdowns:
Presentation Layer: Interfaces with the end-user, managing input validations and output formatting completely decoupled from any business logic.

Service Layer: Orchestrates execution flows, handling transactions and acting as the secure boundary between the outer client and internal logic.

Business & Domain Layer: Houses pure, framework-agnostic business logic, validation rules, and core domain state modeling.

Data & Persistence Layers: Implements modular repository design patterns, abstracting raw database calls away from upper application execution.

🚀 Key Engineering Solutions & Patterns
Dual-Engine Database Portability: Features an abstract data layer allowing seamless data mapping and runtime execution swapping between local lightweight storage (SQLite) and enterprise-scale relational engines (MySQL).

Domain-Driven Design (DDD): Isolates core business domain logic from data structures and presentation interfaces, guaranteeing that database migrations or UI redesigns require zero structural changes to underlying business code.

Config-Driven Application Bootstrapping: Implements a decoupled configurations management pipeline within /config, loading environment profiles dynamically rather than hardcoding systemic parameters.

🛠️ Tech Stack
Language: Python 3.x

Database Drivers: MySQL Connector, native sqlite3 driver

Architecture Style: Layered n-Tier / Domain-Driven Design (DDD)

📂 Repository Layout
/app_framework: Main application framework package.

/config: Bootloader initializations, parameters parsing, and environment setup files.

/database: Storage subsystem holding raw data scripts, initialization engines, and driver factories for MySQL and SQLite.

/src/Campaigns_and_Channels: Core business logic partitioned cleanly into independent architectural layers (business_layer, data_layer, domain, persistence_layer, presentation_layer, service_layer).

⚙️ Setup & Installation
Prerequisites
Python 3.8+

(Optional) Local MySQL Server instance

Local Development
Clone the repository:

Bash
git clone [https://github.com/liamprogulske/IT566-Campaigns-Framework.git](https://github.com/liamprogulske/IT566-Campaigns-Framework.git)
cd IT566-Campaigns-Framework
Establish and activate a local virtual environment:

Bash
python -m venv venv
# On Windows (PowerShell):
.\venv\Scripts\activate
# On macOS/Linux:
source venv/bin/activate
Configure your target database credentials within the /app_framework/config module, and execute the primary runtime bootstrapper file to launch the interface environment.

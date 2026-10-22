 <div align="center">

<img src="https://readme-typing-svg.demolab.com?font=Inter&weight=700&size=36&duration=3000&pause=1000&color=2563EB&center=true&vCenter=true&width=800&lines=Airport+Management+System;OOAD+%26+UML+PROJECT;Airport+Management+System" alt="Airport Management System animated heading" />

<br/>

![Project](https://img.shields.io/badge/Project-Airport%20Management%20System-2563EB?style=for-the-badge)
![OOAD](https://img.shields.io/badge/Focus-OOAD-0F766E?style=for-the-badge)
![UML](https://img.shields.io/badge/Modeling-UML-7C3AED?style=for-the-badge)
![Diagrams](https://img.shields.io/badge/Diagrams-7%20UML%20Views-F59E0B?style=for-the-badge)

<br/>

> **A UML-based design of an Airport Management System** that models passenger check-in, boarding passes, baggage processing, security and immigration clearance, flight and gate management, boarding, and supporting airport services.

<br/>

**OOAD Project Review · Team 7**

</div>

---

## 📋 Table of Contents

- [🎯 Project Overview](#-project-overview)
- [✨ System Features](#-system-features)
- [👥 Actors & Responsibilities](#-actors--responsibilities)
- [🏗️ System Architecture](#️-system-architecture)
- [📊 Passenger Operations Flow](#-passenger-operations-flow)
- [🧩 UML Diagrams](#-uml-diagrams)
  - [Use Case Diagram](#1-use-case-diagram)
  - [Class Diagram](#2-class-diagram)
  - [Sequence Diagrams](#3-sequence-diagrams)
  - [State Chart Diagram](#4-state-chart-diagram)
  - [Activity Diagram](#5-activity-diagram)
  - [Component Diagram](#6-component-diagram)
  - [Deployment Diagram](#7-deployment-diagram)
- [✈️ Flight Lifecycle](#️-flight-lifecycle)
- [🗂️ Core System Entities](#️-core-system-entities)
- [✅ Key Benefits](#-key-benefits)
- [👨‍💻 Team Members](#-team-members)
- [📝 Notes](#-notes)

---

## 🎯 Project Overview

The **Airport Management System (AMS)** is designed to streamline and coordinate airport operations from passenger check-in to final boarding. It represents the interactions between passengers and airport personnel and the services needed to manage baggage, security and immigration clearance, flight status, gates, traveller buses, assistance requests, lounge access, and operational reports.

The project applies **Object-Oriented Analysis and Design (OOAD)** principles. UML diagrams describe the system from multiple perspectives: functional requirements, static structure, chronological interactions, workflows, state transitions, software components, and deployment architecture.

### Project Objectives

- Model the main actors and functions involved in airport operations.
- Represent key airport entities and their relationships.
- Document time-ordered interactions for check-in, baggage processing, security, and boarding.
- Illustrate the passenger journey and flight lifecycle.
- Show the logical software components and their dependencies.
- Represent the intended deployment across client devices, application services, database, and notification services.

### Project Scope

- Passenger registration and login
- Flight tracking and gate status
- Passenger check-in and boarding-pass generation
- Baggage management
- Security and immigration clearance
- Gate allocation and boarding
- Traveller-bus management
- Special-assistance requests and lounge access
- Flight management and operational reporting
- Notifications

---

## ✨ System Features

| Feature | Description |
|---|---|
| 👤 Passenger Management | Registration, login, and passenger-related operations |
| 🎫 Check-in & Boarding Pass | Check-in processing and boarding-pass generation |
| 🧳 Baggage Management | Register and track baggage-processing status |
| 🛂 Security Clearance | Record security verification outcomes |
| 🛃 Immigration Clearance | Represent immigration verification by authorized personnel |
| ✈️ Flight Management | Manage flight schedules, status, delays, and cancellations |
| 🚪 Gate Management | Allocate gates and support boarding operations |
| 🚌 Traveller-Bus Management | Represent passenger transfer coordination |
| ♿ Assistance & Lounge Access | Handle assistance requests and lounge-access operations |
| 🔔 Notifications | Represent SMS/email notifications for relevant updates |
| 📈 Reports | Support operational reporting for administrators |

---

## 👥 Actors & Responsibilities

```mermaid
flowchart LR
    P([Passenger])
    CS([Check-in Staff])
    SP([Security Personnel])
    IO([Immigration Officer])
    GA([Gate Agent])
    BD([Bus Driver])
    AD([Administrator])

    subgraph AMS[Airport Management System]
        PM[Passenger Management]
        CI[Check-in]
        BG[Baggage Management]
        SC[Security Clearance]
        IC[Immigration Clearance]
        GM[Gate & Boarding Management]
        TB[Traveller-Bus Management]
        FM[Flight Management]
        RP[Operational Reports]
        AS[Assistance & Lounge Access]
    end

    P --> PM
    P --> CI
    P --> FM
    P --> AS
    CS --> CI
    CS --> BG
    SP --> SC
    IO --> IC
    GA --> GM
    BD --> TB
    AD --> FM
    AD --> GM
    AD --> RP
```

| Actor | Main Responsibilities |
|---|---|
| Passenger | Register/login, check in, receive boarding pass, track flights, request assistance, and access lounge services |
| Check-in Staff | Assist with check-in and baggage processing |
| Security Personnel | Perform and record security verification |
| Immigration Officer | Perform immigration clearance |
| Gate Agent | Manage gate-side boarding operations |
| Bus Driver | Support traveller-bus transportation |
| Administrator | Manage flights and operational information and generate reports |

---

## 🏗️ System Architecture

The following is a logical architecture view based on the project presentation. It groups the airport system into client access, application services, persistent data, and notifications. It does not imply that the project has already been deployed.

```mermaid
flowchart TB
    subgraph CLIENTS["Client Layer"]
        WEB[Passenger Web Browser]
        MOB[Passenger Mobile App]
        STAFF[Airport Staff Terminal]
        ADMIN[Administrator Device]
    end

    subgraph APP["Airport Management Application"]
        API[Airport Management API]
        AUTH[Authentication]
        PASS[Passenger Management]
        BOOK[Booking & Check-in]
        FLIGHT[Flight Management]
        BAG[Baggage Management]
        CLEAR[Security & Immigration]
        GATE[Gate & Boarding]
        SUPPORT[Bus, Assistance & Lounge]
        REPORT[Reporting]
    end

    DB[(Airport Management Database)]
    NOTIFY[Notification Service<br/>SMS / Email]

    WEB --> API
    MOB --> API
    STAFF --> API
    ADMIN --> API

    API --> AUTH
    API --> PASS
    API --> BOOK
    API --> FLIGHT
    API --> BAG
    API --> CLEAR
    API --> GATE
    API --> SUPPORT
    API --> REPORT

    AUTH --> DB
    PASS --> DB
    BOOK --> DB
    FLIGHT --> DB
    BAG --> DB
    CLEAR --> DB
    GATE --> DB
    SUPPORT --> DB
    REPORT --> DB

    FLIGHT --> NOTIFY
    BOOK --> NOTIFY
    GATE --> NOTIFY
```

### Architecture Layers

- **Client layer:** Passenger, staff, and administrator access points.
- **Application layer:** Logical services for authentication, passengers, bookings, flights, baggage, clearance, gates, support services, and reporting.
- **Data layer:** Central database for storing and retrieving operational information.
- **Notification layer:** SMS/email notification integration.

---

## 📊 Passenger Operations Flow

```mermaid
sequenceDiagram
    actor P as Passenger
    participant AMS as Airport Management System
    participant DB as Airport Database
    participant SEC as Security Personnel
    participant GATE as Gate Service
    participant NOTIFY as Notification Service

    P->>AMS: Log in and search for flight
    AMS->>DB: Retrieve flight information
    DB-->>AMS: Return flight details
    AMS-->>P: Display available flight information

    P->>AMS: Submit booking / check-in request
    AMS->>DB: Validate booking and update check-in
    DB-->>AMS: Return booking status

    alt Booking is valid
        AMS-->>P: Provide boarding-pass details
        AMS->>NOTIFY: Request confirmation notification
        NOTIFY-->>P: Send confirmation
        P->>SEC: Present for security verification
        SEC->>AMS: Submit verification outcome
        AMS->>DB: Record clearance status

        alt Security cleared
            AMS-->>P: Proceed to gate
            P->>GATE: Present for boarding
            GATE->>AMS: Validate boarding status
            AMS->>DB: Update boarding record
            AMS-->>P: Confirm boarding outcome
        else Security requires review
            AMS-->>P: Further verification required
        end
    else Booking is invalid
        AMS-->>P: Display validation error
    end
```

This sequence is a high-level summary of the passenger workflow. The detailed check-in, baggage/security, and boarding sequences appear below.

---

# 🧩 UML Diagrams

## 1. Use Case Diagram

**Purpose:** Shows the actors that interact with the Airport Management System and the functions available to them.

```mermaid
flowchart LR
    Passenger([Passenger])
    CheckInStaff([Check-in Staff])
    Security([Security Personnel])
    Immigration([Immigration Officer])
    GateAgent([Gate Agent])
    BusDriver([Bus Driver])
    Admin([Administrator])

    subgraph SYSTEM["Airport Management System"]
        UC1([Register / Login])
        UC2([Check-in])
        UC3([Generate Boarding Pass])
        UC4([Manage Baggage])
        UC5([Security Clearance])
        UC6([Immigration Clearance])
        UC7([Allocate Gate])
        UC8([Board Passenger])
        UC9([Manage Traveller Bus])
        UC10([Track Flight])
        UC11([Request Assistance])
        UC12([Manage Lounge Access])
        UC13([Manage Flights])
        UC14([Generate Reports])
    end

    Passenger --> UC1
    Passenger --> UC2
    Passenger --> UC3
    Passenger --> UC10
    Passenger --> UC11
    Passenger --> UC12

    CheckInStaff --> UC2
    CheckInStaff --> UC3
    CheckInStaff --> UC4
    Security --> UC5
    Immigration --> UC6
    GateAgent --> UC7
    GateAgent --> UC8
    BusDriver --> UC9
    Admin --> UC7
    Admin --> UC9
    Admin --> UC13
    Admin --> UC14
```

### Key Points

- Actors represent people or roles that interact with the system.
- Use cases represent system functions.
- The system boundary separates the system's functions from external actors.
- Connections show participation in a function; they do not by themselves specify detailed authorization rules.

---

## 2. Class Diagram

**Purpose:** Shows the static structure of the system through classes, attributes, operations, and relationships.

```mermaid
classDiagram
    class Passenger {
        +passengerId
        +name
        +contactDetails
        +register()
        +login()
        +checkIn()
        +requestAssistance()
    }

    class AirportStaff {
        +staffId
        +name
        +role
        +authenticate()
    }

    class CheckInStaff {
        +verifyPassenger()
        +completeCheckIn()
    }

    class SecurityPersonnel {
        +verifySecurity()
        +recordClearance()
    }

    class ImmigrationOfficer {
        +verifyDocuments()
        +recordClearance()
    }

    class GateAgent {
        +allocateGate()
        +boardPassenger()
    }

    class BusDriver {
        +manageTransfer()
    }

    class Administrator {
        +manageFlights()
        +generateReports()
    }

    class Flight {
        +flightId
        +flightStatus
        +departureTime
        +arrivalTime
        +updateStatus()
    }

    class Booking {
        +bookingId
        +bookingStatus
        +createBooking()
        +updateBooking()
    }

    class BoardingPass {
        +passId
        +seatNumber
        +gateNumber
        +generate()
    }

    class Baggage {
        +baggageId
        +baggageStatus
        +updateStatus()
    }

    class Gate {
        +gateId
        +gateStatus
        +allocate()
    }

    class TravellerBus {
        +busId
        +busStatus
        +assignTransfer()
    }

    class AssistanceRequest {
        +requestId
        +requestStatus
        +createRequest()
    }

    class Lounge {
        +loungeId
        +accessStatus
        +checkAccess()
    }

    class Notification {
        +notificationId
        +message
        +send()
    }

    AirportStaff <|-- CheckInStaff
    AirportStaff <|-- SecurityPersonnel
    AirportStaff <|-- ImmigrationOfficer
    AirportStaff <|-- GateAgent
    AirportStaff <|-- BusDriver
    AirportStaff <|-- Administrator

    Passenger "1" --> "0..*" Booking : makes
    Booking "0..*" --> "1" Flight : for
    Booking "1" --> "0..1" BoardingPass : issues
    Passenger "1" --> "0..*" Baggage : checks
    Flight "0..*" --> "1" Gate : assigned gate
    Passenger "1" --> "0..*" AssistanceRequest : submits
    Passenger "0..*" --> "0..*" Lounge : accesses
    Flight --> Notification : status updates
```

### Relationship Types Represented

- **Inheritance:** Specialized staff roles inherit shared properties and behavior from `AirportStaff`.
- **Association:** Passengers make bookings; bookings relate to flights.
- **Dependency:** Operational workflows use relevant services such as check-in, clearance, gate management, and notifications.
- **Composition:** A strong ownership relationship can be used where the final detailed model defines a component's lifecycle as dependent on its parent.

> The presentation identifies the major classes and relationship types but does not define every attribute, method, or multiplicity. Those details in this recreated diagram are illustrative and should be aligned with the final class diagram if exact matching is required.

---

## 3. Sequence Diagrams

**Purpose:** Show the chronological messages exchanged between actors and system objects.

### 3.1 Passenger Check-in

```mermaid
sequenceDiagram
    actor P as Passenger
    participant AMS as Airport Management System
    participant CS as Check-in Service
    participant DB as Airport Database
    participant BP as Boarding Pass Service
    participant NS as Notification Service

    P->>AMS: Log in and request check-in
    AMS->>CS: Validate check-in request
    CS->>DB: Retrieve booking and flight details
    DB-->>CS: Return booking information

    alt Booking is valid
        CS->>DB: Save check-in status
        CS->>BP: Generate boarding pass
        BP-->>CS: Return boarding pass details
        CS-->>AMS: Check-in successful
        AMS-->>P: Display boarding pass
        AMS->>NS: Request confirmation notification
        NS-->>P: Send confirmation
    else Booking is invalid
        CS-->>AMS: Return validation failure
        AMS-->>P: Display check-in error
    end
```

**Workflow:** The passenger requests check-in; the system validates the booking and flight details, records successful check-in, and generates a boarding pass. An invalid booking results in an error.

### 3.2 Baggage Processing & Security Clearance

```mermaid
sequenceDiagram
    actor P as Passenger
    participant CS as Check-in Staff
    participant AMS as Airport Management System
    participant BS as Baggage Service
    participant SEC as Security Personnel
    participant DB as Airport Database

    P->>CS: Present booking and baggage
    CS->>AMS: Submit baggage details
    AMS->>BS: Register baggage
    BS->>DB: Save baggage record
    DB-->>BS: Confirm saved record
    BS-->>AMS: Baggage registered
    AMS-->>P: Confirm baggage processing

    P->>SEC: Present for security screening
    SEC->>AMS: Submit screening result
    AMS->>DB: Record security clearance

    alt Security cleared
        DB-->>AMS: Clearance recorded
        AMS-->>P: Proceed to next airport stage
    else Security not cleared
        DB-->>AMS: Clearance status recorded
        AMS-->>P: Further verification required
    end
```

**Workflow:** Baggage details are registered and stored. Security personnel submit a screening result, and the system records the clearance outcome.

### 3.3 Passenger Boarding

```mermaid
sequenceDiagram
    actor P as Passenger
    participant AMS as Airport Management System
    participant FS as Flight Service
    participant GS as Gate Service
    participant GA as Gate Agent
    participant DB as Airport Database
    participant NS as Notification Service

    P->>AMS: Check flight and gate status
    AMS->>FS: Retrieve current flight status
    FS->>DB: Read flight information
    DB-->>FS: Return flight and gate details
    FS-->>AMS: Return current status
    AMS-->>P: Display flight information

    GA->>AMS: Start boarding
    AMS->>GS: Validate boarding status
    GS->>DB: Retrieve passenger and flight records
    DB-->>GS: Return records

    alt Passenger is eligible to board
        GS->>DB: Update boarding status
        GS-->>AMS: Boarding confirmed
        AMS->>NS: Send boarding update
        AMS-->>P: Confirm boarding
    else Passenger is not eligible
        GS-->>AMS: Boarding validation failed
        AMS-->>P: Show boarding issue
    end
```

**Workflow:** The passenger checks the flight and gate status. When boarding begins, the system validates boarding eligibility and records the result.

### 3.4 Traveller-Bus Transportation

```mermaid
sequenceDiagram
    actor P as Passenger
    participant AMS as Airport Management System
    participant TS as Traveller-Bus Service
    participant DB as Airport Database
    actor BD as Bus Driver

    P->>AMS: View transfer information
    AMS->>TS: Request bus assignment and status
    TS->>DB: Retrieve transfer details
    DB-->>TS: Return transfer information
    TS-->>AMS: Return bus details
    AMS-->>P: Display transfer information
    BD->>TS: Update transfer status
    TS->>DB: Save transfer status
    DB-->>TS: Confirm update
    TS-->>AMS: Transfer status updated
```

This conceptual sequence represents the traveller-bus management capability listed in the project presentation.

---

## 4. State Chart Diagram

**Purpose:** Models flight states and the events that cause transitions during the flight lifecycle.

```mermaid
stateDiagram-v2
    [*] --> Scheduled

    Scheduled --> Delayed : Delay announced
    Delayed --> Boarding : Ready for boarding
    Scheduled --> Boarding : Ready on time

    Scheduled --> Cancelled : Flight cancelled
    Delayed --> Cancelled : Flight cancelled
    Boarding --> Cancelled : Boarding cancelled

    Boarding --> Departed : Departure
    Departed --> Arrived : Arrival

    Arrived --> [*]
    Cancelled --> [*]
```

| State | Meaning |
|---|---|
| Scheduled | The flight is planned |
| Delayed | The flight has been delayed |
| Boarding | Passenger boarding has begun |
| Departed | The flight has left |
| Arrived | The flight has reached its destination |
| Cancelled | The flight will not operate as scheduled |

**Primary path:** `Scheduled → Boarding → Departed → Arrived`

**Alternate paths:** A flight may be delayed or cancelled before departure.

---

## 5. Activity Diagram

**Purpose:** Represents the passenger workflow and its decision points.

```mermaid
flowchart TD
    Start((Start)) --> Login[Login to system]
    Login --> Search[Search for flight]
    Search --> Booking[Book or retrieve booking]
    Booking --> CheckIn[Complete check-in]
    CheckIn --> Pass[Generate boarding pass]
    Pass --> Security[Security verification]
    Security --> Decision{Security verified?}

    Decision -- Yes --> Gate[Proceed to gate]
    Gate --> Boarding[Board flight]
    Boarding --> End((End))

    Decision -- No --> Failed[Stop normal boarding flow]
    Failed --> Review[Further verification or assistance]
    Review --> End2((End))
```

### Workflow Steps

1. Login to the system.
2. Search for a flight.
3. Book or retrieve a booking.
4. Complete check-in.
5. Generate a boarding pass.
6. Verify security clearance.
7. Proceed to the gate and board if verification succeeds.
8. If verification fails, stop the normal boarding flow and seek further review.

---

## 6. Component Diagram

**Purpose:** Shows the logical software components and their dependencies.

```mermaid
flowchart TB
    USERS[Passengers and Airport Staff]

    subgraph AMS["Airport Management System"]
        AUTH[Authentication]
        PASS[Passenger Management]
        BOOK[Booking Management]
        FLIGHT[Flight Management]
        BAG[Baggage Management]
        SEC[Security and Clearance]
        BP[Boarding Pass Management]
        GATE[Gate and Boarding Management]
        STAFF[Staff Management]
        REPORT[Reports]
        SUPPORT[Assistance and Lounge Access]
    end

    DB[(Airport Database)]
    NOTIFY[Notification Service<br/>SMS / Email]

    USERS --> AUTH
    USERS --> PASS
    USERS --> BOOK
    USERS --> FLIGHT
    USERS --> BAG
    USERS --> SEC
    USERS --> BP
    USERS --> GATE
    USERS --> SUPPORT

    AUTH --> DB
    PASS --> DB
    BOOK --> DB
    FLIGHT --> DB
    BAG --> DB
    SEC --> DB
    BP --> DB
    GATE --> DB
    STAFF --> DB
    REPORT --> DB
    SUPPORT --> DB

    FLIGHT --> NOTIFY
    BOOK --> NOTIFY
    GATE --> NOTIFY
```

**Explanation:** Separate components handle authentication, passenger management, booking, flights, baggage, security, boarding passes, gates, staff, assistance, and reports. The components use the airport database for persistent data, and the notification service represents SMS/email communications.

---

## 7. Deployment Diagram

**Purpose:** Shows the intended deployment environment across client devices, application services, data storage, and notification infrastructure.

```mermaid
flowchart TB
    subgraph CLIENTS["Client Devices"]
        WEB[Passenger Web Browser]
        MOBILE[Passenger Mobile App]
        TERMINAL[Airport Staff Terminal]
        ADMIN[Administrator Device]
    end

    NETWORK((HTTPS Communication))

    subgraph SERVER["Application Server"]
        API[Airport Management API]
        AUTH[Authentication Service]
        FLIGHT[Flight Management]
        PASS[Passenger Management]
        BAG[Baggage Management]
        GATE[Gate Management]
        REPORT[Reporting Service]
        NOTIFYINT[Notification Integration]
    end

    DB[(Airport Management Database)]
    NS[External Notification Server<br/>SMS / Email]

    WEB --> NETWORK
    MOBILE --> NETWORK
    TERMINAL --> NETWORK
    ADMIN --> NETWORK
    NETWORK --> API

    API --> AUTH
    API --> FLIGHT
    API --> PASS
    API --> BAG
    API --> GATE
    API --> REPORT

    AUTH --> DB
    FLIGHT --> DB
    PASS --> DB
    BAG --> DB
    GATE --> DB
    REPORT --> DB

    API --> NOTIFYINT
    NOTIFYINT --> NS
```

### Deployment Elements

- **Client devices:** Passenger browsers, mobile apps, staff terminals, and administrator devices.
- **Communication:** Client requests are represented as HTTPS communication.
- **Application server:** Hosts the Airport Management API and logical airport services.
- **Database:** Stores and retrieves operational information.
- **Notification server:** Represents SMS and email communication services.

> This diagram represents the logical deployment described in the presentation. It does not assert that these services have been implemented or deployed to a live airport environment.

---

## ✈️ Flight Lifecycle

```mermaid
flowchart LR
    A[Scheduled] --> B{Operational update}
    B -->|On time| C[Boarding]
    B -->|Delay| D[Delayed]
    B -->|Cancellation| E[Cancelled]
    D -->|Ready| C
    D -->|Cancelled| E
    C -->|Departure| F[Departed]
    C -->|Boarding cancelled| E
    F --> G[Arrived]
```

This lifecycle captures the primary flight states and the alternative delay/cancellation paths described in the project presentation.

---

## 🗂️ Core System Entities

| Entity / Class | Responsibility |
|---|---|
| Passenger | Represents a traveller using airport services |
| AirportStaff | Common representation of airport personnel |
| CheckInStaff | Supports passenger check-in |
| SecurityPersonnel | Records security verification |
| ImmigrationOfficer | Performs immigration clearance |
| GateAgent | Supports gate allocation and boarding |
| BusDriver | Supports traveller-bus operations |
| Administrator | Manages flight-related information and reports |
| Flight | Represents a scheduled flight and its lifecycle |
| Booking | Represents a passenger's booking |
| BoardingPass | Represents boarding-pass information |
| Baggage | Represents baggage and its processing status |
| Gate | Represents a gate and its allocation status |
| TravellerBus | Represents traveller-bus transportation |
| AssistanceRequest | Represents a passenger assistance request |
| Lounge | Represents lounge-access information |
| Notification | Represents a system notification |

---

## ✅ Key Benefits

- Helps reduce passenger waiting time and gate congestion.
- Improves coordination between airport departments.
- Organizes passenger, baggage, and flight management.
- Supports flight and gate status updates.
- Models security, boarding, and traveller transportation workflows.
- Provides a structured foundation for future system implementation.

---

## 👨‍💻 Team Members

**Team 7 — Object-Oriented Analysis and Design using UML**

| Name | Roll Number |
|---|---|
| Pranav Vedula | 24B11CS355 |
| Posa Kaveri | 24B11CS352 |
| M. Satya Harsha Vardhan Reddy | 24B11CS275 |
| Bodhanapu Suhas | 24B11CS049 |

---

## 📝 Notes

- This repository documentation is based on the **Airport Management System — OOAD Project Review** presentation.
- The README includes Mermaid recreations of the seven UML diagram types covered in the presentation: Use Case, Class, Sequence, State Chart, Activity, Component, and Deployment.
- Some class attributes, operation names, relationships, and service boundaries are illustrative where the presentation does not provide detailed specifications.
- Mermaid diagrams are rendered by GitHub in supported Markdown views.

### Viewing the Diagrams

1. Save this document as `README.md`.
2. Add it to the root of your OOADUML GitHub repository.
3. Commit and push the file.
4. Open the repository page to view the rendered diagrams.

---

<div align="center">

**OOAD Project Review · Team 7**

*Airport Management System — Modeling airport operations with UML*

</div>

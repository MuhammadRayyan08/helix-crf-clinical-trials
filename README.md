# Helix Pharma Clinical Report Form (CRF) Portal

[![Client: Helix Pharma](https://img.shields.io/badge/Client-Helix_Pharma-blue?style=flat-square)]()
[![Partner: Softsols Pakistan](https://img.shields.io/badge/Partner-Softsols_Pakistan-slate?style=flat-square)]()
[![Stack: Next.js / Prisma](https://img.shields.io/badge/Stack-Next.js_%2F_Prisma-black?style=flat-square)]()
[![Database: PostgreSQL](https://img.shields.io/badge/Database-PostgreSQL-336791?style=flat-square)]()
[![Type: Case Study](https://img.shields.io/badge/Type-Clinical_Portal_Case_Study-purple?style=flat-square)]()

Systems architecture and implementation case study for the centralized **Clinical Report Form (CRF)** data capture portal built for **Helix Pharma** across 9 clinical drug trials in Pakistan.

---

## Role & Scope

* **Role:** Full-Stack Developer (Team Project)
* **Context:** Built under Softsols Pakistan for Helix Pharma clinical study coordinators.
* **Scope of Ownership:** Contributed to the Next.js and Prisma web portal: structured multi-study database schemas, built role-gated clinical input forms (baseline exams, follow-ups, adverse event logs), and implemented patient consent modules.

---

## System Flow

```mermaid
flowchart TD
    subgraph Clinical Users [Hospital Trial Sites]
        PI[Principal Investigator / Doctor]
        CRC[Study Coordinator]
        ADMIN[Trial Administrator]
    end

    subgraph Portal Interface [Next.js App Router]
        AUTH[Role-Gated Authentication]
        STUDY[Study Selector - 9 Trial Protocols]
        FORMS[Patient CRF Input Forms]
        AE[Adverse Event Logging]
        AUTH --> STUDY --> FORMS --> AE
    end

    subgraph Data & Schema Tier [Prisma & PostgreSQL]
        PRISMA[Prisma ORM Client]
        DB[(PostgreSQL Database)]
        AUDIT[Change Log Tracking]
        FORMS --> PRISMA
        AE --> PRISMA
        PRISMA --> DB
        PRISMA --> AUDIT
    end

    PI --> AUTH
    CRC --> AUTH
    ADMIN --> AUTH
```

---

## Technical Highlights

* **Multi-Study Protocol Schemas:** Structured relational data models with Prisma to isolate patient visits, lab values, and symptom scores across 9 distinct clinical trials.
* **Clinical Input Validation:** Built form validation rules to ensure required medical observations, vital signs, and medication dosages are accurately entered before submission.
* **Adverse Event Logging:** Implemented structured tracking for reporting unexpected clinical events, severity gradings, and follow-up resolutions.
* **Role-Based Access Control:** Structured role boundaries separating hospital site coordinators, attending physicians, and administrative auditors.

---

## Tech Stack

* **Frontend & Backend:** Next.js (App Router, Server Actions), React
* **Language:** TypeScript
* **ORM & Database:** Prisma ORM, PostgreSQL
* **Styling:** Tailwind CSS

---

## Notice

Clinical trial protocols, patient personal health information, and proprietary drug datasets belong strictly to Helix Pharma and Softsols Pakistan. This repository documents system architecture and software specifications.

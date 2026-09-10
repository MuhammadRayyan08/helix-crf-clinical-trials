# Helix Pharma Clinical Report Form (CRF) & Clinical Trial Engine

[![Client: Helix Pharma](https://img.shields.io/badge/Client-Helix_Pharma-blue?style=flat-square)]()
[![Partner: Softsols Pakistan](https://img.shields.io/badge/Partner-Softsols_Pakistan-slate?style=flat-square)]()
[![Compliance: GCP / 21 CFR Part 11](https://img.shields.io/badge/Compliance-GCP_%2F_21_CFR_Part_11-green?style=flat-square)]()
[![Type: Case Study](https://img.shields.io/badge/Type-Clinical_Trials_Case_Study-purple?style=flat-square)]()

Systems architecture and engineering case study for the multi-center **Electronic Data Capture (EDC) & Case Report Form (CRF)** system deployed for **Helix Pharma** across 9 national Phase III/IV clinical trials.

---

## Role & Ownership

* **Role:** Full-Stack Clinical Systems Developer
* **Context:** Built under Softsols Pakistan for Helix Pharma clinical research teams.
* **Scope of Ownership:** Append-only cryptographic audit trail, role-based investigator form access controls, and GCP-compliant data validation pipelines.

---

## Architecture Pipeline

```mermaid
flowchart TD
    subgraph Clinical Trial Site [Hospital Investigation Unit]
        PI[Principal Investigator]
        CRC[Clinical Research Coordinator]
        MONITOR[Clinical Research Associate / Monitor]
    end

    subgraph Data Capture Tier [Secure Web Portal]
        FORM[Electronic Case Report Form Engine]
        VAL[Real-Time Range & Type Validator]
        QUERY[Query Resolution Flagging]
        FORM --> VAL --> QUERY
    end

    subgraph Audit & Security Tier [Express.js Core]
        AUDIT[Immutable Append-Only Audit Trail Engine]
        ROLES[Strict Protocol Role-Based Gatekeeper]
        LOCK[Protocol Locking & Freeze State Engine]
        AUDIT --- ROLES --- LOCK
    end

    subgraph Storage [Secure Database]
        DB[(Trial Data & Signed Audit Records)]
        QUERY --> AUDIT --> DB
    end

    PI --> FORM
    CRC --> FORM
    MONITOR --> QUERY
```

---

## Core Technical Highlights

* **Immutable Audit Trail:** Compliant with Good Clinical Practice (GCP) and FDA 21 CFR Part 11; records user identity, UTC timestamps, previous values, and medical justifications for any modifications to patient trial data.
* **Multi-Center Form Engine:** Configurable CRF templates capturing adverse event (AE) reporting, drug dosing schedules, and laboratory bio-markers across 9 national trial sites.
* **Query Resolution Workflow:** Integrated flag-and-resolve workflow allowing clinical monitors to challenge ambiguous values and investigators to document clarifying addenda.
* **Data Lock & Archival:** Cryptographic site-freezing protocols ensuring complete dataset immutability prior to statistical analysis.

---

## Tech Stack

* **Frontend:** Next.js, React, Tailwind CSS
* **Backend:** Node.js, Express.js REST API
* **Database:** MongoDB with write-locked audit collections
* **Standards:** GCP, ICH E6(R2), FDA 21 CFR Part 11 guidelines

---

## Notice

Proprietary clinical trial protocols, patient subject identities, and drug efficacy datasets belong to Helix Pharma and Softsols Pakistan. This repository documents software architecture and audit compliance specifications.

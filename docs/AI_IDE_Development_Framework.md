⚙️ AI IDE Development Framework
The Standard PRD → Design Doc → Execution Workflow for AI-Accelerated Engineering
🧠 I. Overview

The AI IDE Development Framework defines how Teamfront engineers design, model, and build modern software using AI IDEs such as Cursor, Antigravity, Claude Code, Continue.dev, Windsurf, and Amazon Q.

This framework is tool-agnostic and focuses on creating repeatable, predictable, domain-driven, AI-accelerated development across all Teamfront product companies.

📝 II. How PRDs Are Created in the AI Era

PRDs are never written manually.

They are generated from real conversations.

PRD Creation Workflow

Record the meeting (Zoom + Fathom).

Export the transcript.

Paste the transcript into ChatGPT.

Instruct ChatGPT to extract:

Summary

Problem

Goals

Non-goals

Personas (Field Service Office Admins, Technicians, Estimators, Owners)

Requirements

Edge cases

Success metrics

Risks

Save the final version as:

/docs/<feature>/PRD.md


The PRD defines WHAT we are building.

🏗️ III. How Design / Architecture Docs Are Created

The PRD answers WHAT.
The Design Doc answers HOW.

Design Docs are also generated through ChatGPT, using the PRD as the source of truth.

Each Design Doc must define:

Domain Modeling

Entities

Value Objects

Aggregates

Domain Events (plain objects)

Invariants

Relationships

Application Layer

Commands

Queries

Validators

Slice boundaries

API Layer

Endpoints

Request and response DTOs

System Constraints

Business rules

Error handling

Non-functional requirements

Performance constraints

Permissions

Save as:

/docs/<feature>/DESIGN.md


This becomes the engineering contract for the AI IDE.

📁 IV. Required Folder Structure

Every feature must follow:

/docs
  /<feature>/
    PRD.md
    DESIGN.md
    EXECUTION_PLAN.md


This standardizes how AI loads and interprets requirements.

📘 V. Execution Plan (What the AI IDE Follows Step-By-Step)

The execution plan provides the step-by-step instructions that AI IDEs follow.

Save as:

/docs/<feature>/EXECUTION_PLAN.md

Execution Plan Defines:

Phase order

What is built in each phase

Naming conventions

Slice sequencing

When/where to stop

FE ↔ BE alignment rules

Acceptance criteria

This turns AI IDEs into deterministic execution engines.

🛠️ VI. AI IDE Build Phases (Teamfront Standard)

The phases below match how Teamfront modernizes legacy systems and builds greenfield features with AI.

⚙️ Phase 1 — Backend Foundations

Generate exactly what DESIGN.md specifies:

Entities

Aggregates

Value Objects

Domain Events

Repositories

DTOs

Commands

Queries

Validators

Mappers

Empty Controllers

Rules

No domain logic

No integration logic

No frontend code

Stop when scaffolding is complete

🖥️ Phase 2 — Frontend Foundations

AI generates:

Routes

Navigation entry

Screen shells

Forms

Tables

Modals

TypeScript interfaces

Empty service methods

🔗 Phase 3 — FE ↔ BE Wiring

AI performs:

DTO ↔ TS interface syncing

Service → API wiring

Form field → command mapping

Error format alignment

Type corrections

This eliminates API contract drift.

🧩 Phase 4 — Domain Logic + UX Behavior

AI implements:

Totals

Validation

Invariants

Tax logic

Payment logic

Error states

Loading states

UX behaviors

🎨 Phase 5 — Final Polish

AI adds:

Sorting

Filtering

Pagination

Search

Empty states

Loading skeletons

PDF or email actions

Cleanup

Tests

This produces a production-grade feature.

🧾 VII. Example: Invoicing (DDD-Aligned)

This is modeled using your architectural standards.

Invoice Domain

Invoice (aggregate root)

LineItem (value object)

InvoiceTotals (value object)

Transaction Domain

Transaction (aggregate root)

Tax Domain

TaxRate

Email Integration Domain

EmailSendRequest

📐 VIII. Invoicing Vertical Slices
invoice/

CreateInvoice

AddLineItem

RemoveLineItem

RecalculateTotals

FinalizeInvoice

GetInvoice

ListInvoices

transaction/

InitiateTransaction

ApplyPaymentToInvoice

GetTransaction

ListTransactions

tax/

GetTaxRate

CalculateTax

integration.email/

SendInvoiceEmail

SendPaymentReceipt

🚀 IX. Invoicing Execution Plan
Phase 1

Backend foundations:
entities, aggregates, DTOs, commands, queries, validators, empty controllers.

Phase 2

Frontend foundations:
screens, tables, forms, TS interfaces, empty services.

Phase 3

Wiring:
services → controllers, type syncing, DTO alignment.

Phase 4

Domain logic:
totals, tax, finalize, payment rules.

Phase 5

Polish:
sorting, filtering, emailing, pagination, UX refinements.

⭐ X. Why This Framework Works

AI handles repetitive engineering

Engineers enforce domain correctness

Architecture becomes standardized

FE and BE always match

Drift goes to zero

Modernization becomes continuous

Features ship 3–5× faster

This is the Teamfront AI-First Engineering Operating System.

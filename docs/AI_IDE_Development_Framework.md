# ⚙️ AI IDE Development Framework
### The Standard PRD → Design Doc → Execution Workflow for AI-Accelerated Engineering

---

## 🧠 I. Overview

The AI IDE Development Framework defines how Teamfront engineers design, model, and build modern software using AI IDEs such as Cursor, Antigravity, Claude Code, Continue.dev, Windsurf, and Amazon Q.

This framework is tool-agnostic and focuses on creating repeatable, predictable, domain-driven, AI-accelerated development across all Teamfront product companies.

---

## 📝 II. How PRDs Are Created in the AI Era

PRDs are never written manually.  
They are generated directly from real conversations.

### PRD Creation Workflow

Record the meeting (Zoom + Fathom).  
Export the transcript.  
Paste the transcript into ChatGPT.  
Ask ChatGPT to extract:

- Summary  
- Problem  
- Goals  
- Non-goals  
- Personas (Admins, Estimators, Technicians, Owners)  
- Requirements  
- Edge cases  
- Success metrics  
- Risks  

Save as:  
`/docs/<feature>/PRD.md`

The PRD defines WHAT we are building.

---

## 🏗️ III. How Design / Architecture Docs Are Created

The PRD answers WHAT.  
The Design Doc answers HOW.

### Each Design Doc Must Define

### Domain Model
- Entities  
- Value objects  
- Aggregates  
- Domain events  
- Invariants  
- Relationships  

### Application Layer
- Commands  
- Queries  
- Validators  
- Vertical slice boundaries  

### API Layer
- Endpoints  
- Request DTOs  
- Response DTOs  

### System Constraints
- Business rules  
- Error handling  
- Performance requirements  
- Permissions  

Save as:  
`/docs/<feature>/DESIGN.md`

---

## 📁 IV. Required Folder Structure

Every feature must follow: /docs // PRD.md DESIGN.md EXECUTION_PLAN.md

---

# 🚀 V. Execution Plan (AI IDE Build Instructions)

The Execution Plan tells the AI IDE exactly how to build the feature — step-by-step, phase-by-phase.

Save as:  
`/docs/<feature>/EXECUTION_PLAN.md`

### The Execution Plan Defines:

- Phase order  
- What is built in each phase  
- Naming conventions  
- Vertical slice sequencing  
- Stop points  
- FE ↔ BE alignment rules  
- Acceptance criteria  

---

# 🛠️ VI. AI IDE Build Phases

## Phase 1 — Backend Foundations (No Logic)

Generate:

- Entities  
- Aggregates  
- Value objects  
- Domain events  
- Repositories  
- Commands  
- Queries  
- Validators  
- Mappers  
- Empty controllers  

Stop here. No business logic.

---

## Phase 2 — Frontend Foundations

Generate:

- Routes  
- Screens  
- Forms  
- Lists/tables  
- Modals  
- TS interfaces  
- Empty API services  

---

## Phase 3 — FE ↔ BE Wiring

- Sync request/response DTOs  
- Map services to controllers  
- Unify error formats  
- Fix FE/BE contract mismatches  

---

## Phase 4 — Domain Logic + UX Behavior

Implement:

- Totals  
- Taxes  
- Validation  
- Business rules  
- State transitions  
- Loading/error states  

---

## Phase 5 — Polish + Enhancements

Add:

- Sorting  
- Filtering  
- Search  
- Pagination  
- Empty states  
- Loading skeletons  
- PDF/email/export actions  
- Tests  

---

# 📘 VII. Invoice Domain Example

### Entities
- Invoice  
- InvoiceLineItem  
- InvoiceTotals  
- Transaction  
- TaxRate  

---

## Vertical Slices

### /invoice/
- CreateInvoice  
- AddLineItem  
- RemoveLineItem  
- RecalculateTotals  
- FinalizeInvoice  
- GetInvoice  
- ListInvoices  

### /transaction/
- InitiateTransaction  
- ApplyPayment  
- GetTransaction  
- ListTransactions  

### /tax/
- GetTaxRate  
- CalculateTax  

### /integration.email/
- SendEmail (always generic and integration agnostic) 

---

# ⭐ VIII. Why This Framework Works

- AI automates execution  
- Humans guide architecture  
- Eliminates FE/BE drift  
- Ships features 3–5× faster  
- Creates consistency across all Teamfront companies  
- Perfect for modernization and new feature development  

This is the AI-First Engineering Operating System for Teamfront.

---

# 🎉 End of Document




```md
# ⚙️ AI IDE Development Framework
### *The Standard PRD → Design Doc → Execution Workflow for AI-Accelerated Engineering*

---

## 🧠 I. Overview

The AI IDE Development Framework defines how Teamfront engineers design, model, and build modern software using AI IDEs such as Cursor, Antigravity, Claude Code, Continue.dev, Windsurf, and Amazon Q.

This framework is tool-agnostic and focuses on creating repeatable, predictable, domain-driven, AI-accelerated development across all Teamfront product companies.

---

## 📝 II. How PRDs Are Created in the AI Era

PRDs are never written manually.
They are generated from real conversations.

### PRD Creation Workflow

Record the meeting (Zoom + Fathom).  
Export the transcript.  
Paste the transcript into ChatGPT.  
Instruct ChatGPT to extract:

- Summary  
- Problem  
- Goals  
- Non-goals  
- Personas (Field Service Office Admins, Technicians, Estimators, Owners)  
- Requirements  
- Edge cases  
- Success metrics  
- Risks  

Save the final version as:

`/docs/<feature>/PRD.md`

The PRD defines **WHAT** we are building.

---

## 🏗️ III. How Design / Architecture Docs Are Created

The PRD answers WHAT.  
The Design Doc answers HOW.

Design Docs are generated through ChatGPT, using the PRD as the source of truth.

### Each Design Doc must define:

**Domain Modeling**
- Entities  
- Value Objects  
- Aggregates  
- Domain Events (plain objects)  
- Invariants  
- Relationships  

**Application Layer**
- Commands  
- Queries  
- Validators  
- Vertical slice boundaries  

**API Layer**
- Endpoints  
- Request and response DTOs  

**System Constraints**
- Business rules  
- Error handling  
- Non-functional requirements  
- Performance constraints  
- Permissions  

Save as:

`/docs/<feature>/DESIGN.md`

This becomes the engineering contract for the AI IDE.

---

## 📁 IV. Required Folder Structure

Every feature must follow:

```
/docs
/<feature>/
   PRD.md
   DESIGN.md
   EXECUTION_PLAN.md
```

This standardizes how AI loads and interprets requirements.

---

## 📘 V. Execution Plan (AI IDE Instructions)

The Execution Plan tells the AI IDE exactly how to build the feature.

Save as:

`/docs/<feature>/EXECUTION_PLAN.md`

### The Execution Plan Defines:

- Phase order  
- What is built in each phase  
- Naming conventions  
- Slice sequencing  
- Stop points  
- FE ↔ BE alignment rules  
- Acceptance criteria  

This makes AI-driven execution deterministic.

---

# 🛠️ VI. AI IDE Build Phases (Teamfront Standard)

Below is the universal workflow used across all Teamfront companies.

---

## ⚙️ Phase 1 — Backend Foundations (NO logic yet)

Generate exactly what DESIGN.md specifies:

- Entities  
- Aggregates  
- Value Objects  
- Domain Events  
- Repositories  
- DTOs  
- Commands  
- Queries  
- Validators  
- Mappers  
- Empty Controllers  

### Rules:

- No domain logic  
- No integration logic  
- No frontend code  
- STOP when scaffolding matches DESIGN.md  

---

## 🖥️ Phase 2 — Frontend Foundations

AI generates:

- Routes  
- Navigation entry  
- Screens  
- Forms  
- Tables  
- Modals  
- TypeScript interfaces  
- Empty API services  

### Rules:

- Structural scaffolding only  
- No business logic  
- No API communication yet  

---

## 🔗 Phase 3 — FE ↔ BE Wiring

AI connects:

- DTOs ↔ TS interfaces  
- Services ↔ Controllers  
- Commands ↔ Form fields  
- Error formats ↔ UI error states  
- Type alignment across FE and BE  

This eliminates API contract drift.

---

## 🧠 Phase 4 — Domain Logic + UX Behavior

AI implements:

- Totals  
- Validation  
- Invariants  
- Tax logic  
- Payment logic  
- Domain rules  
- Error handling  
- Loading states  
- UX behaviors  

---

## 🎨 Phase 5 — Final Polish

AI adds:

- Sorting  
- Filtering  
- Pagination  
- Search  
- Loading skeletons  
- Empty states  
- PDF/Email actions  
- Cleanup  
- Tests  

This produces a production-ready feature.

---

# 🧾 VII. Example Domain: Invoicing (DDD-Aligned)

### Entities / Aggregates

- `Invoice` (aggregate root)  
- `InvoiceLineItem` (value object)  
- `InvoiceTotals` (value object)  
- `Transaction` (aggregate root)  
- `TaxRate`  

---

## 📐 VIII. Invoicing Vertical Slices

### invoice/
- CreateInvoice  
- AddLineItem  
- RemoveLineItem  
- RecalculateTotals  
- FinalizeInvoice  
- GetInvoice  
- ListInvoices  

### transaction/
- InitiateTransaction  
- ApplyPaymentToInvoice  
- GetTransaction  
- ListTransactions  

### tax/
- GetTaxRate  
- CalculateTax  

### integration.email/
- SendInvoiceEmail  
- SendPaymentReceipt  

---

# 🚀 IX. Invoicing Execution Plan

### Phase 1 — Backend Foundations
Generate:
- All entities  
- Commands/queries  
- DTOs  
- Validators  
- Mappers  
- Repositories  
- Empty controllers  

Stop when scaffolding exists.

### Phase 2 — Frontend Foundations
Generate:
- Invoice list  
- Invoice detail  
- Invoice create/edit  
- Forms & modals  
- TS interfaces  
- Empty API services  

### Phase 3 — Wiring
- API ↔ FE  
- DTO syncing  
- Type alignment  
- Route → Controller mapping  

### Phase 4 — Domain Logic
- Totals logic  
- Tax calculation  
- Validation  
- Payment rules  

### Phase 5 — Polish
- Filters  
- Sorting  
- Pagination  
- PDF/Email send  
- UX cleanup  

---

# ⭐ X. Why This Framework Works

- AI handles mechanical work  
- Humans enforce domain correctness  
- Standardization eliminates drift  
- FE and BE always match  
- Multi-product consistency  
- Modernization becomes continuous  
- Features ship 3–5× faster  

This is the **Teamfront AI-First Engineering Operating System**.

---

# ✅ End of Document
```

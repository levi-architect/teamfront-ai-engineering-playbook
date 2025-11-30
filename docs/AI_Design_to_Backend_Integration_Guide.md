# 🔗 AI Design → Backend Integration Guide  
### *How UI → API → Domain Wiring Is Done Using AI IDEs*

---

## 🧭 I. Overview

This guide defines **how design-driven frontend flows connect to backend domain logic** using AI IDEs (Cursor, Windsurf, Continue, Claude Code, etc.).

It is **tool-agnostic** and focuses on:

- Clean separation between UI, API, and domain  
- Consistent vertical slice generation  
- Predictable integration patterns  
- AI-friendly, reproducible wiring  
- Zero guesswork for frontend ↔ backend contracts  

This ensures any AI IDE can correctly generate and bind the entire flow.

---

## 🎨 II. The Design-Driven Flow (Figma → Frontend → API)

### The UI always starts from design:

1. Stakeholders define behavior in Figma  
2. Designers create structured frames & component states  
3. A design-to-code generator (Builder, Make, Locofy, etc.) exports:  
   - Components  
   - Props  
   - Layouts  
   - Hooks or placeholder functions  
4. Files are committed into the frontend repository inside a feature slice

The result:  
A **ready-to-wire UI**, not a blank screen.

---

## 🚀 III. Creating the Backend Contracts From UI

After UI is generated, the AI IDE is instructed to extract:

- Required API endpoints  
- Request DTOs  
- Response DTOs  
- Error conditions  
- Validation rules  
- Domain models touched  
- Commands/queries required  

This ensures backend development is driven by **actual UI behavior**, not “developer guesses.”

### Example AI IDE prompt:

> “Cursor, analyze this feature UI. Extract every API needed, input fields, response shapes, validation rules, and generate formal API contracts for each endpoint.”

---

## 🧩 IV. Vertical Slice Backend Integration

All backend logic adheres to **vertical slice architecture**:

### A single “feature slice” contains:

- **Commands**
- **Queries**
- **Handlers**
- **DTOs**
- **Validators**
- **Domain services**
- **Repositories**
- **Events**
- **API Controller**

### Folder Example

```
/src
  /application
    /invoice
      /command
      /query
      /handler
      /dto
      /mapper
  /domain
    /invoice
  /api
    /invoice
```

This architecture ensures AI IDEs generate predictable, uniform slices.

---

## 🔌 V. Integration Rules (Critical)

### **1. UI NEVER talks to domain or persistence.  
   UI → Service → API → Application Layer → Domain**

### **2. API Controllers MUST be thin.**  
Only map requests → commands and return responses.

### **3. No business logic in controllers. Ever.**

### **4. Commands for state-changing operations.**  
Examples:
- CreateInvoiceCommand  
- ApplyPaymentCommand  
- UpdateCustomerAddressCommand  

### **5. Queries for reads.**  
Examples:
- GetInvoiceDetailsQuery  
- ListCustomerInvoicesQuery  
- GetSubscriptionUsageQuery  

### **6. All integration must use reusable generic patterns.**

#### ❌ Bad  
`SendInvoiceEmailRequest`  
`SendPaymentSuccessEmail`  

#### ✅ Good  
`SendEmailRequest` with:
- `templateKey`
- `model`
- `recipient`

This matches enterprise patterns (Stripe, HubSpot, Salesforce).

---

## 🛠 VI. Backend Execution Flow (AI IDE Automated)

AI IDEs follow this consistent pipeline:

### **PHASE 1 — Generate Contracts**
- Request/response DTOs  
- Controller stubs  
- Command/query definitions  
- Empty handlers  

### **PHASE 2 — Build Domain Logic**
- Entities  
- Value objects  
- Domain services  
- Validation rules  
- Events  

### **PHASE 3 — Wire Everything**
- Handlers implement logic  
- Mappers map DTO ↔ entity  
- Repositories integrate persistence  
- Events emitted & logged  

### **PHASE 4 — Confirm Frontend Compatibility**
AI validates:

- UI request models match API request DTOs  
- UI response models match API response DTOs  
- Required fields exist  
- Validation rules enforced  

This removes 70% of integration bugs.

---

## 🔄 VII. End-to-End Example (UI → API → Domain)

### Feature: “Send Invoice”

**UI**  
User clicks “Send Invoice” → passes:  
- invoiceId  
- deliveryType (email/SMS)  

**AI IDE extracts API:**  
`POST /invoice/send`  

**Request DTO:**  
```
{
  invoiceId: string,
  deliveryType: string
}
```

**Command:**  
`SendInvoiceCommand`

**Handler:**  
1. Load invoice  
2. Validate status  
3. Use generic `SendEmailRequest`  
4. Emit `InvoiceSentEvent`  
5. Return response  

**AI IDE binds UI → service → API → handler automatically.**

---

## 🧱 VIII. Reusable Integration Layer (Critical)

Integrations **must NEVER be feature-specific.**  
They must be generic building blocks.

### Supported integration types:
- Email  
- SMS  
- Webhooks  
- Payment Provider  
- Internal Notifications  
- Storage  
- Third-party REST  

### Example (generic email):

```
SendEmailRequest:
  templateKey: "invoice.sent"
  model:
    invoiceNumber: "12345"
    amount: "200.00"
  recipient: "customer@example.com"
```

This pattern allows reuse across the entire organization.

---

## 📦 IX. MCP Integration (Optional)

If MCP (Model Context Protocol) is used:

- UI describes “intent”
- MCP transforms it into API instructions
- Backend responds with domain-safe outputs
- AI IDE completes wiring

This is the future of AI-native applications.

---

## 🧪 X. QA Automation With AI IDEs

AI automatically verifies:

- API endpoints respond correctly  
- Domain invariants hold  
- Validation rules enforced  
- Frontend ↔ backend contract alignment  
- Events triggered  
- Side effects completed  

This shifts QA from manual to AI-driven.

---

## 🏁 XI. Summary

This guide defines:

- How UI generates backend contracts  
- How AI IDEs build commands/queries  
- How to integrate frontend ↔ backend cleanly  
- How domain logic remains pure  
- How integrations stay generic  
- How the entire pipeline becomes AI-accelerated  

This creates a **consistent, predictable, scalable** system across all Teamfront product companies.


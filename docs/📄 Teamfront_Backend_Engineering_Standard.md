# 🏗️ Teamfront Backend Engineering Standard  
### *Sharp • Strict • AI-First • DDD-CQRS • Multi-Product Architecture*

This document defines the **backend engineering standards** used across all Teamfront product companies.  
These standards ensure:

- Predictable structure  
- High integrity of business logic  
- Clean architectural boundaries  
- AI-accelerated development  
- Multi-tenant safety  
- Long-term maintainability  
- Consistency across teams  

This document is **authoritative**.  
All engineers and all AI IDE tools (Cursor, Windsurf, Continue, Claude Code) MUST follow it.

---

# 📘 1. Architectural Patterns Overview (Short)

Teamfront recognizes multiple architectural styles across its products:

### ✔ Vertical Slice Architecture (Teamfront Standard)
Preferred for all new development.  
Best for AI-IDE tooling.  
Best for multi-tenant SaaS.  
Best for CQRS.  
Best for maintainability.

### ✔ Clean Architecture / Onion (.NET Core legacy)
Supported where already implemented.  
Still follows: Domain → Application → Infra → API.

### ✔ Hexagonal / Ports & Adapters
Used selectively for integrations (payments, webhooks, email).

### ✔ Modular Monolith
Used in large legacy applications requiring module separation.

**All patterns MUST follow the same principles:**
- Pure domain  
- Clear CQRS  
- API as adapter  
- Infrastructure isolated  
- AI should accelerate, not invent architecture  

The rest of this document defines the **Teamfront-standard Vertical Slice Architecture**.

---

# 🧱 2. Vertical Slice Structure (Teamfront Standard)

Each bounded context (e.g., invoice, customer, payment) uses this structure:

```
/<slice>
   /api
   /application
   /domain
   /infrastructure
```

### Slice = Consistent, isolated, AI-friendly unit.

The standard subfolders:

```
/api
    dto/
    controllers/

/application
    command/
    query/
    handler/
    validator/
    mapper/
    eventhandler/
    service/
    log/

/domain
    aggregate/      ← or /core/
    valueobject/
    event/

/infrastructure
    entity/
    repositoryimpl/
    projection/
    integration/
```

---

# 🧠 3. Domain Layer (Pure — No Entities)

Domain contains:
- Aggregate roots  
- Value objects  
- Domain events  
- Invariants  
- Pure business methods  

Domain MUST NOT contain:
- ORM entities  
- Framework annotations  
- Persistence fields  
- Repositories  
- DTOs  
- Mappers  
- Queries  
- Logging  
- Controllers  
- External API calls  

### Domain Rule:
> **Domain models represent business meaning, not database shape.**

---

# 🧩 4. Application Layer (CQRS)

Application contains:
- Commands  
- Queries  
- Command Handlers  
- Query Handlers  
- Validators  
- Application Services (light orchestration)  
- Event Handlers  
- Mappers  
- LogEvent models  

Application MUST NOT contain:
- Business rules  
- Persistence logic  
- Controller logic  
- HTTP details  

### Command Rules:
- Mutate state  
- One handler per command  
- Naming: `CreateXCommand`, `AddXCommand`, `UpdateXCommand`  

### Query Rules:
- Read-only  
- No aggregates returned  
- Projection-only  

### Application Services:
Used ONLY for multi-step workflows involving multiple aggregates.

---

# 🚪 5. API Layer (Adapter)

API contains:
- Controllers  
- Request/Response DTOs  

Controllers MUST be:
- Thin  
- Declarative  
- One action → One command or query  
- Zero business logic  

Controller Responsibilities:
1. Accept DTO  
2. Map DTO → Command/Query  
3. Dispatch to bus  
4. Return Response DTO  

---

# 🏛️ 6. Infrastructure Layer (Persistence + Providers)

Infrastructure contains:
- ORM entities  
- Table mappings  
- Repository implementations  
- Read projections  
- Email/SMS/payment/webhook providers  
- External integrations  
- Persistence utilities  

Infrastructure MUST NOT contain:
- Business rules  
- Domain logic  
- CQRS handlers  
- Controllers  

Infrastructure implements, domain defines.

---

# 🔌 7. Repositories

Repository interfaces live in domain.  
Implementations live in infrastructure.

Rules:
- Do not expose ORM entities  
- Do not return aggregates from queries  
- Do not mix read/write concerns  
- No SQL in domain/application  
- Must use mappers  

---

# 📣 8. Domain Events & Event Handlers

Domain events:
- Past tense (`InvoiceSentEvent`)  
- Raised in aggregates only  
- Plain objects  

Application event handlers:
- Process domain events  
- Trigger integrations  
- Trigger workflows  
- Must be idempotent  
- Must be small and focused  

---

# 📝 9. Event Logging Standard (Unified)

Teamfront uses a unified LogEvent model:

```
LogEvent {
    eventType
    aggregateId
    timestamp
    payloadJson
}
```

Logged during event dispatch:
1. Log event  
2. Notify event handler  
3. Clear buffer  

Location:
```
/application/log/
```

This provides:
- Observability  
- Debugging capability  
- Audit trails  
- Analytics value  

---

# 🤖 10. AI-First Backend Rules (Cursor, Windsurf, Continue)

AI IDEs MUST:
- Follow slice structure EXACTLY  
- Never introduce ORM into domain  
- Never move files across layers  
- Generate commands/queries in correct folder  
- Generate handler/validator/mapper consistently  
- Respect naming conventions  
- Validate DTO ↔ Command alignment  
- Validate FE ↔ API contract alignment  

AI IDEs MUST NOT:
- Invent new architectural patterns  
- Generate business logic in controllers  
- Modify domain models directly  
- Place annotations in domain models  

Developers MUST:
- Provide PRD.md + DESIGN.md + EXECUTION_PLAN.md to AI tools  
- Validate outputs line-by-line  
- Use GitHub Desktop for visual diffing  

---

# 🧪 11. Testing Standards

### Unit Tests:
- Domain behavior  
- Value object correctness  
- Command handler logic (mocking repo)  

### Integration Tests:
- Controller → handler → domain → repo (in-memory DB)  
- Event handler + fake providers  

### Query Tests:
- Projection correctness  
- Pagination  
- Filtering  

---

# 🛡️ 12. Multi-Tenant Safety

Every slice MUST enforce tenant/org isolation:

- All queries filter by tenant  
- All commands validate tenant context  
- Domain events include tenant metadata  
- Infrastructure must enforce RLS  
- Controllers must never assume global access  

---

# ⛔ 13. Prohibited Practices

These violations are architectural failures:

- Business logic in controllers  
- Business logic in handlers  
- Domain calling repositories  
- Returning aggregates in API  
- ORM entities in domain  
- DTOs in domain  
- Cross-slice coupling  
- Mixed read/write handlers  
- One-off integration classes  
- Query handlers writing data  
- Using `var` in backend code  
- Circular dependencies  
- Hard-coded provider logic  

---

# 🏁 14. Summary

Teamfront’s backend architecture is:

- Vertical-slice first  
- Domain-pure  
- CQRS-clean  
- AI-accelerated  
- Multi-tenant safe  
- Enterprise-grade  
- Consistent across teams  
- Built for modernization and scale  

This standard defines **how backend must be written** across all Teamfront products.  
AI tools and all engineers MUST comply.


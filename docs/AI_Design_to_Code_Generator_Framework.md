# 🎨 AI Design-to-Code Generator Framework  
### *Teamfront’s Standard for Converting UI/UX Designs Into Production-Ready Frontend Code*

---

## 🌐 I. Overview

The **AI Design-to-Code Generator Framework** defines how Teamfront converts product designs into real frontend code using:

- Figma (or equivalent design source)  
- AI-powered design-to-code generators (Builder.io, Make, Plasmic, Locofy, TeleportHQ, etc.)  
- MCP (Model Context Protocol) for syncing generated output  
- AI IDEs (Cursor, Windsurf, Claude Code, Continue.dev)  
- Teamfront FE & BE engineering standards  

This framework is **tool-agnostic**.  
Any generator can be swapped in without changing the workflow.

The purpose is simple:

> **Turn design → UI components → production code quickly, consistently, and aligned with Teamfront architecture.**

---

## 🧭 II. Purpose of This Framework

This framework defines:

- How designs enter the system  
- How generators produce code skeletons  
- How AI IDEs finalize production logic  
- How generated UI is integrated into Teamfront’s vertical slice architecture  
- Folder structure, naming, and code quality standards  
- How MCP automates syncing  
- Expected outputs at each phase  

This ensures all Teamfront product companies (Arborgold, Xcelerate, ServiceMonster, Chargetic, etc.) follow one consistent, modern workflow.

---

## 🖼️ III. Design Source Requirements (Figma or Equivalent)

UI/UX designs must use:

- Layout grids  
- Style tokens (color, spacing, typography)  
- Component variants  
- Reusable primitives (buttons, inputs, cards, modals)  
- Clear hierarchy  
- Proper auto-layout  
- Mobile-first or responsive rules  

This ensures any design-to-code generator can read and interpret structure.

Design is the **source of truth** → code is the output.

---

## 🏗️ IV. Code Generator Requirements (Tool-Agnostic)

The generator (Builder.io, Make, Plasmic, etc.) must:

- Convert designs → component skeletons  
- Preserve original layout  
- Map variants to props  
- Apply design tokens correctly  
- Export clean, minimal JSX/TSX  
- Avoid generating business logic  
- Output files into correct folder structure  
- Be compatible with MCP syncing  

Generator output is **UI ONLY**.  
No business logic, no API calls, no domain behavior.

---

## ⚠️ V. What the Generator Must NOT Do

- Must NOT generate services  
- Must NOT generate state management  
- Must NOT generate API calls  
- Must NOT define domain logic  
- Must NOT rewrite FE folder structure  
- Must NOT introduce custom non-token CSS  
- Must NOT create backend bindings  

The generator handles **structure**, not **logic**.

AI IDE handles logic.  
Domain architecture handles behavior.

---

## 🔌 VI. MCP Sync Requirements

MCP (Model Context Protocol) ensures generated code appears in the correct repo without manual copying.

MCP must sync output to:

```
/src/app/<feature>/components/
```

Rules:

- Sync only component skeletons  
- No overwriting of logic files  
- Small atomic PRs  
- PR names tied to the feature  
- Include PRD.md + DESIGN.md for AI context  

MCP = continuous design → code synchronization.

---

## 📁 VII. Required Folder Structure

Every feature must follow:

```
/docs/<feature>/PRD.md
/docs/<feature>/DESIGN.md
/docs/<feature>/EXECUTION_PLAN.md

/frontend/src/app/<feature>/
    components/
    models/
    services/
    state/
```

Generator output always goes in:

```
/src/app/<feature>/components/
```

The AI IDE will extend the output with:

- props  
- state  
- integration  
- validation  
- logic  

---

## 🛠️ VIII. End-to-End Workflow

### **PHASE 1 — Design Preparation (UX/PM)**

1. Finalize Figma frame(s)  
2. Use tokens for all spacing, colors, and typography  
3. Ensure components use variants  
4. Set auto-layout everywhere  
5. Clean structure (names, hierarchy, no random layers)  

---

### **PHASE 2 — Generate UI Code Skeletons (Design-to-Code Generator)**

Steps:

1. Import Figma frame  
2. Auto-convert to component(s)  
3. Map Figma layers → component structure  
4. Map variations → props  
5. Apply design tokens  
6. Export JSX/TSX  
7. MCP syncs into repo  

Stop when UI skeleton compiles cleanly.

---

### **PHASE 3 — AI IDE Processing (Cursor/Windsurf/etc.)**

Open the feature in the AI IDE with PRD.md + DESIGN.md.

Ask AI IDE to:

- Clean JSX  
- Add proper props  
- Add TypeScript types  
- Add responsive behavior  
- Add state management (Zustand, Akita, etc. depending on project)  
- Add error/loading/empty states  
- Remove auto-generated noise  
- Break large screens into atomic components  

AI IDE is responsible for upgrading the skeleton into production-ready code.

---

### **PHASE 4 — Domain & API Integration**

Using the backend DESIGN.md + EXECUTION_PLAN.md:

- Wire UI → services  
- Wire services → backend endpoints  
- Implement validation  
- Implement user flows  
- Implement computed states  
- Add domain rules  
- Add visual states (loading, errors, permissions)  

AI IDE handles 70% of this.  
Engineers enforce architecture + patterns.

---

### **PHASE 5 — Final Polish & QA**

Add:

- sorting  
- filtering  
- pagination  
- search  
- accessibility tweaks  
- keyboard navigation  
- responsive edge cases  
- QA adjustments  

Once UI → domain → backend is consistent, the feature is ready.

---

## 🎨 IX. Best Practices (Teamfront Standard)

- Never hardcode styles  
- Use tokens only  
- Componentize aggressively  
- Extract logic into hooks  
- Keep components small and pure  
- Pass props, not global state  
- Follow atomic design principles  
- Leverage variants for all style changes  
- Keep layout + style AI-generated, logic AI-refined  

---

## ❌ X. Anti-Patterns (Never Allowed)

- Inline styles outside tokens  
- Repeating UI patterns without components  
- Deeply nested components with logic inside  
- Overwriting MCP-synced files incorrectly  
- Using multiple design systems  
- Copy-pasting JSX outside the generator process  
- Letting generator add business logic  

---

## 💾 XI. Expected Outputs Per Feature

Each feature must include:

```
PRD.md  
DESIGN.md  
EXECUTION_PLAN.md  

/src/app/<feature>/components/
    <Component>.tsx
/src/app/<feature>/models/
    <feature>.types.ts
/src/app/<feature>/services/
    <feature>.service.ts
/src/app/<feature>/state/
    <feature>.store.ts
```

The design-to-code generator produces the UI skeleton.  
The AI IDE produces the final implementation.  
The engineer enforces architecture.

---

## 🚀 XII. Summary

The AI Design-to-Code Generator Framework standardizes:

- How designs become code  
- How generators are used  
- How MCP syncs output  
- How AI IDEs finalize implementation  
- How FE code integrates with BE slices  
- How consistency is enforced across Teamfront products  

This enables:

- Faster UI development  
- Higher quality  
- Predictable handoffs  
- Scalable architecture  
- PE-grade engineering maturity  

---

## ✍️ X. Authorship

**Levi Garner**  
CTO/AI Engineering Leader & System Architect  

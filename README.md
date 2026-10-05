# Banking-Suites

I need you to perform a deep cross-validation of the project artifacts, documentation, repositories, and existing research available to you.

This is NOT just a document-summary task.

The goal is to determine whether the proposed Commercial Banking implementation can reuse existing Banking Suite capabilities and architecture instead of reinventing functionality that already exists in Retail or Commercial use cases.

## CONTEXT

We have uploaded/provided several types of artifacts:

1. **Prototype**
   - Contains the screens, user journeys, flows, and functionality that have already been designed/delivered.
   - Treat this as the product/UI reference.

2. **Product Roadmap**
   - Describes what the Product team wants to build and the expected journey/capabilities.
   - Treat this as the product/business direction.

3. **Commercial Architecture Framework**
   - Describes the architecture and the proposed integration with Thought Machine / Banking Suite.
   - This has been reviewed previously by the Banking Suite team.
   - The intention is to follow the existing Banking Suite architecture wherever possible.

4. **Banking Suite**
   - Existing Retail capabilities and some Commercial capabilities already exist.
   - We want to reuse existing services, repositories, architecture, patterns and capabilities wherever appropriate.

5. **GitHub repositories**
   - Repository access has been provided.
   - These must be checked directly instead of assuming that documentation accurately reflects the current implementation.

6. **Banking Suite Confluence**
   - Existing technical documentation, architecture, standards and implementation guidance are available here.

7. **Existing research / analysis**
   - Previous research was performed using these artifacts and repositories.
   - It produced recommendations around:
     - Data model
     - Repositories to reuse
     - Existing Banking Suite services
     - New Commercial-owned repositories
     - Frontend/backend ownership
     - Hierarchy management
     - Entitlements
     - Other Commercial-specific capabilities

---

# PRIMARY OBJECTIVE

Determine:

### What already exists?
### What can be reused?
### What needs to be extended?
### What needs to be newly built?
### What belongs to Commercial-owned repositories?
### What should remain in Banking Suite?
### Are there conflicts between documents and actual code?
### Are the previous research conclusions actually supported by the repositories?

Do NOT assume the previous research is correct.

Validate it against the source documents and actual repository code.

---

# STEP 1 — BUILD A SOURCE INVENTORY

First identify every available source:

| Source | Type | Purpose | Relevant areas |
|---|---|---|---|
| Prototype | Product | UI/flows | |
| Roadmap | Product | Future capabilities | |
| Architecture Framework | Architecture | System design | |
| Banking Suite Confluence | Documentation | Existing capabilities | |
| GitHub repositories | Code | Actual implementation | |
| Existing research | Analysis | Previous conclusions | |

For each source, explain what authority it should have.

For example:

- Prototype → UI/flow reference
- Roadmap → product/business intent
- Architecture → technical architecture
- Repository → actual implementation truth
- Confluence → documented standards/capabilities

---

# STEP 2 — PROTOTYPE ANALYSIS

Analyze the prototype completely.

Extract:

- Screens
- User journeys
- Major workflows
- Functional capabilities
- Entities
- Data captured
- Actions
- Integrations implied by the UI
- Roles/users
- Entitlements/authorization requirements
- Dependencies

Create:

## Prototype Capability Map

| Capability | Screen/Flow | Entity | Backend requirement | Existing Banking Suite capability? |
|---|---|---|---|---|

Do not determine the final answer yet. This is only the baseline.

---

# STEP 3 — ROADMAP ANALYSIS

Analyze the product roadmap.

Identify:

- Epics
- Features
- Capabilities
- Business priorities
- Dependencies
- MVP scope
- Future scope
- Commercial-specific functionality

Map roadmap items to the prototype.

| Roadmap item | Prototype flow | Match? | Missing functionality |
|---|---|---|---|

Identify anything in the roadmap that is NOT represented in the prototype and vice versa.

---

# STEP 4 — COMMERCIAL ARCHITECTURE FRAMEWORK

Analyze the architecture framework deeply.

Extract:

- Components
- Services
- Systems
- Integration points
- Banking Suite dependencies
- Thought Machine integration
- Data ownership
- API boundaries
- Frontend/backend boundaries
- Commercial-owned components
- Reusable Banking Suite components
- New components
- Authentication/authorization
- Entitlements
- Hierarchy management
- Data models
- Event flows

Create a high-level architecture diagram in text.

Example:

Commercial Frontend
        ↓
Commercial Backend
        ↓
Existing Banking Suite Services
        ↓
Thought Machine

But use the ACTUAL architecture and component names from the documentation.

---

# STEP 5 — GITHUB REPOSITORY VALIDATION

This is extremely important.

For every important component/service/repository mentioned in the documents:

1. Find the repository.
2. Inspect its structure.
3. Identify the relevant implementation.
4. Verify whether the documented functionality actually exists.
5. Identify the exact files/classes/modules.
6. Determine whether the implementation is reusable for Commercial.

Create:

| Capability | Document says | Repository found | Actual implementation | Reusable? |
|---|---|---|---|---|

If documentation says:

"Banking Suite already provides X"

do NOT accept that statement without checking the repository where possible.

If the repository contradicts the documentation, flag it.

---

# STEP 6 — BANKING SUITE REUSE ANALYSIS

This is one of the most important outputs.

For every major Commercial capability, classify it as:

### A — Reuse directly
Existing Banking Suite functionality can be consumed as-is.

### B — Extend existing capability
Existing Banking Suite functionality exists but requires extension/configuration.

### C — Commercial-owned implementation
Capability is sufficiently Commercial-specific that Commercial should own the implementation.

### D — New capability
No suitable implementation exists and it needs to be built.

Create:

| Capability | Existing Banking Suite | Recommendation | Reason | Repository |
|---|---|---|---|---|

Pay special attention to:

- Hierarchy Management
- Entitlements
- Authorization
- Organization services
- Feature flags
- Frontend
- Backend
- Data model
- APIs
- Vault/secrets
- Common/shared services
- Integration with Thought Machine

---

# STEP 7 — DATA MODEL ANALYSIS

Compare the Commercial requirements with the existing Banking Suite data model.

Identify:

- Existing entities
- Reusable entities
- Extendable entities
- Commercial-specific entities
- Relationships
- Ownership
- Required new fields
- Required new tables/models

Create:

| Entity | Existing? | Existing location | Can reuse? | Changes required |
|---|---|---|---|---|

Then propose the minimum required Commercial data model.

Do not redesign unnecessarily.

---

# STEP 8 — REPOSITORY OWNERSHIP

Determine which repositories should own which functionality.

For example:

| Functionality | Existing Banking Suite Repo | Commercial Repo | Recommendation |
|---|---|---|---|

Determine:

- Which existing repositories should be consumed
- Which should be extended
- Which new Commercial frontend repository is required
- Which new Commercial backend repository is required
- Which shared services should remain shared

The principle should be:

**Reuse before rebuild.**

But do not force reuse when the architecture or ownership model says Commercial must own the capability.

---

# STEP 9 — DOCUMENT CONFLICT CHECK

Cross-check ALL major documents against each other.

Look specifically for:

- Different service names
- Different repository names
- Different API paths
- Different data models
- Different ownership
- Different architecture
- Different technology versions
- Different authorization models
- Different entitlement behavior
- Different frontend standards
- Different assumptions about existing services

Create:

| Topic | Document A says | Document B says | Repository says | Conflict? | Resolution |
|---|---|---|---|---|---|

If you cannot resolve a conflict, mark:

**Needs Architect/SME Confirmation**

Do not guess.

---

# STEP 10 — TECHNOLOGY / VERSION CHECK

Verify technology versions from the actual repository configuration.

For example:

- React version
- Node version
- Java version
- Spring Boot version
- Angular if applicable
- Build tools
- CI/CD tools
- DevOps tooling
- Other important dependencies

Do not rely solely on documentation.

Check actual:

- package.json
- pom.xml
- build.gradle
- Dockerfiles
- CI/CD configuration
- configuration files
- lock files

If documentation says one version and the repository uses another, flag it.

---

# STEP 11 — R5–R9 CONNECTION

I will be presenting:

- R5 — frontend-react-standard.md
- R6 — confluence-sme-entitlements.md
- R7 — confluence-standards-process.md
- R8 — Org-services-flags-authz-template.md
- R9 — confluence-business-banking-vault.md

Explain how these documents fit into the larger Commercial architecture.

For each R5–R9:

- What does it define?
- Why is it required?
- Which architecture component does it affect?
- Which repository implements it?
- Is it already implemented?
- Can Banking Suite functionality be reused?
- What does Commercial need to build?
- Are there contradictions with other documents?

---

# STEP 12 — EXISTING RESEARCH VALIDATION

There is already a research/analysis output that proposes:

- Data model
- Repository reuse
- Banking Suite services
- Commercial-owned repositories
- Frontend/backend ownership
- Hierarchy management
- Entitlements
- Other implementation recommendations

Review those conclusions.

For EVERY major recommendation, classify it as:

### VERIFIED
Supported by repository/documentation.

### PARTIALLY VERIFIED
Some evidence exists but confirmation is required.

### NOT VERIFIED
No supporting evidence found.

### CONTRADICTED
Repository/documentation indicates something different.

Create:

| Existing Research Recommendation | Evidence | Status | Corrected Recommendation |
|---|---|---|---|

---

# STEP 13 — FINAL TARGET ARCHITECTURE

After all validation is complete, produce a recommended architecture based on evidence.

Separate:

### Existing Banking Suite
What we should reuse.

### Commercial-owned
What we should build ourselves.

### Extensions
What we should extend from existing capabilities.

### Integrations
What connects the systems.

Provide a clear architecture flow.

---

# STEP 14 — MVP IMPLEMENTATION PLAN

Based on all the analysis, create an implementation roadmap.

### Phase 1 — Foundation
- Repository setup
- Architecture setup
- Common services
- Security
- Configuration
- Vault

### Phase 2 — Core capabilities
- Data model
- Organization/hierarchy
- Entitlements
- Authorization

### Phase 3 — Business capabilities
- Features from roadmap/prototype

### Phase 4 — Frontend
- React standards
- UI flows
- API integration

Adjust these phases based on the actual project rather than blindly following this example.

---

# STEP 15 — FINAL EXECUTIVE SUMMARY

At the end, give me:

## 1. What we already have

## 2. What we can reuse

## 3. What we need to extend

## 4. What we need to build

## 5. What Commercial must own

## 6. What Banking Suite should own

## 7. Major architecture decisions

## 8. Major conflicts found

## 9. Open questions requiring architect/SME confirmation

## 10. Recommended next steps

---

# CRITICAL RULES

1. **Do not trust a document blindly.**
2. **Do not trust the previous research blindly.**
3. **Verify important claims against actual repositories.**
4. **Cross-reference multiple sources.**
5. **Never invent missing information.**
6. Clearly distinguish:
   - Documented
   - Verified in code
   - Inferred
   - Recommended
   - Needs confirmation
7. Prefer existing Banking Suite capabilities where technically and architecturally appropriate.
8. Do not recommend rebuilding something that already exists without explaining why reuse is not appropriate.
9. Do not recommend reuse merely because something looks similar; verify compatibility and ownership.
10. Use exact repository names, paths, services, classes and configuration wherever available.
11. Do not modify any repository files.
12. Do not implement anything yet.
13. The final output must help the engineering team decide **what to build, what to reuse, where to build it, and why**.

The most important question throughout the analysis is:

> **"Is this already available somewhere in Banking Suite, and if yes, can Commercial consume or extend it instead of rebuilding it?"**

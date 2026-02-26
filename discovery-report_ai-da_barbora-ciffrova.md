# Discovery Report — AI Data Analyst
## Student: Barbora Ciffrova
## Date: February 26, 2026
## Client: EuroHealth Insurance AG

---

## 1) Stakeholder analysis

Hans Muller (CIO, sponsor) wants cost reduction, platform unification, and compliance readiness by Aug 2026.
Stefan Weber (CISO, Security governance) needs policy enforcement, auditability, and data security.
Katarina Novak (IT Ops Director) wants practical constraints on deployment, SLAs, and interoperability.
Jan Kovar (Helpdesk Lead) and his colleagues fear replacement.
Shadow AI/tools owners (HR chatbot, Claims LangChain, Finance PoC) are non-governed pockets that threaten risk/gaps.
External parties are board, compliance, and EU AI Act timeline.

## 2) Key findings and implications

### Finding A: AI agents are not unified and do not collaborate together.

Implication: Include a Policy-as-Code layer (PDP/PEP), audit trails, and a single LLM gateway with controlled adapters.

### Finding B: No cloud usage.

Implication: Design plan for internal data stores; no reliance on public cloud fallbacks.

### Finding C: Knowledge base is outdated and no one is responsible for keeping it up to date.

Implication: Include knowledge-management plan, knowledge-base refresh, lifecycle ownership, and automatic drift monitoring.

### Finding D: Shadow AI exists and is ungoverned; regulatory risk if left untracked.

Implication: Establish discovery and policy enforcement for shadow tools; plan for risk scoring, inventory, and remediation pathways.

## 3) Technical/functional requirements to investigate

Multi-agent orchestration.
PII handling, data retention policies, audit-logging schema aligned to Art.12 (EU AI Act), budgetary controls requiring human oversight from certain amount.
Define metrics, owner, refresh frequency of knowledge base.

## 4) Risks

Policy drift risk: Without immutable policies, agents may bypass controls as policies change.
Data leakage risk: PII in KB or shared data could be exposed if governance is weak.
Adoption risk: Jan’s fear could derail rollout; misalignment with business value.
KB drift risk: Stale knowledge leads to incorrect responses; undermines trust.
Scope creep risk: Shadow AI expands beyond planned integrations; governance gaps widen.
Budget and timeline risk: EUR 180K budget may not cover infra and governance tooling; schedule must reflect policy enforcement and change management.

## 5) Recommended next steps (first 2 weeks)

Week 1:
- Create a two-column exercise for Hans: capture exact policy controls you will codify (P0: mandatory, P1: recommended, P2: aspirational) and map them to audit/test cases.
- Inventory and classify shadow AI assets (HR chatbot, Claims PoC, Finance GPT); assign risk scores; propose remediation/containment plan.
- Define 3 concrete end-to-end automation candidates with clear tool integrations (e.g., ServiceNow ticket triage, knowledge-base refresh trigger, escalation to human) and required authorizations.
- Draft a KB governance plan: ownership, refresh frequency, and a drift-detection mechanism with a 30-day lookback window.

Week 2:
- Draft a policy-driven architecture diagram: L1 Data Ingestion, L2 Agent Builder, L3 AI Core, L4 Policy-as-Code, L5 Human-in-the-Loop; annotate on-prem constraints.
- Define a 1-page FRIA-ready risk assessment outline per high-risk category; identify data governance controls to satisfy Art.9, Art.11, Art.12.
- Propose a staged rollout plan (Phase 1 EN/DE; CZ in Phase 2), with change-management milestones and a simple measurement plan for Jan and his team.
- Prepare a KPI dashboard outline for Hans’s board: cost savings, deflection rates, auto-resolve rate, CSAT delta, compliance posture, and audit readiness status.

## 6) Dependencies on other roles in the team

AI-PM: clear business requirements, success metrics, feature scoping, release cadence, risk acceptance.
AI-SEC: Co-create the policy-as-code rules, data retention, audit logging, and human oversight requirements, data handling rules, audit logging requirements.
AI-DS: Design data pipelines, measurement dashboards, model readiness, data quality, and SLA metrics; ensure observability aligns with Art.12 compliance.
FDE: Provide on-prem data pipeline infrastructure, storage, and monitoring capabilities, scope hardware and logging requirements within budget.
Stakeholders (Hans, Stefan, Katarina, Jan): Clarify ownership, decision rights, and escalation paths, incorporate their concerns into the governance design and adoption plan.

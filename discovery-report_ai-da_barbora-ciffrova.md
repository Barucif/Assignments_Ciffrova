## 1) Stakeholder analysis (from data analyst role)

Hans Muller (CIO, sponsor) wants cost reduction, platform unification, and compliance readiness by Aug 2026.
Stefan Weber (CISO, Security governance) needs policy enforcement, auditability, and data security.
Katarina Novak (IT Ops Director) wants practical constraints on deployment, SLAs, and interoperability.
Jan Kovar (Helpdesk Lead) and his colleagues fear replacement.
Shadow AI/tools owners (HR chatbot, Claims LangChain, Finance PoC) are non-governed pockets that threaten risk/gaps.
External parties are board, compliance, and EU AI Act timeline.

## 2) Key findings and implications for your workstream

Finding A: AI agents are not unified and do not collaborate together.

Implication: Include a Policy-as-Code layer (PDP/PEP), audit trails, and a single LLM gateway with controlled adapters.

Finding B: No cloud usage.

Implication: Design plan for internal data stores; no reliance on public cloud fallbacks.

Finding C: Knowledge base is outdated and no one is responsible for keeping it up to date.

Implication: Include knowledge-management plan, knowledge-base refresh, lifecycle ownership, and automatic drift monitoring.

Finding D: Shadow AI exists and is ungoverned; regulatory risk if left untracked.

Implication: Establish discovery and policy enforcement for shadow tools; plan for risk scoring, inventory, and remediation pathways.

3) Technical/functional requirements you need to investigate

Policy-as-Code: Define mandatory rules (e.g., no PII in training data; immutable audit logs for N years; budgetary guardrails above €X require human oversight; data localization requirements). Confirm with Hans a concrete list and acceptance criteria.
AI Gateway and L2 constrained autonomy: Detail an LLM gateway architecture with routing, token budgets, memory discipline, and multi-agent orchestration. Confirm required tools/integrations (ServiceNow actions; HR/Claims/Finance connectors) and their required authorizations.
Data governance: Data lineage, access controls, PII handling, data retention policies, audit-logging schema aligned to Art.12 (EU AI Act). Define what must be captured for FRIA/Audit readiness.
KB quality management: Define metrics, owner, refresh cadence, and automated tests for KB relevance/recency.
On-prem compute plan: Estimate CPU/GPU requirements within EUR 180K budget; assess feasibility of a GPU upgrade path; determine maintenance headcount.
Monitoring and drift: KPIs for faithfulness, accuracy, and KB drift; plan for drift detection and remediation triggers.
Shadow AI inventory: Create a shadow-audit appendix listing HR chatbot, Claims LangChain, Finance PoC; define remediation path and governance controls.

4) Risks specific to your area

Policy drift risk: Without immutable policies, agents may bypass controls as policies change.
Data leakage risk: PII in KB or shared data could be exposed if governance is weak.
Adoption risk: Jan’s fear could derail rollout; misalignment with business value.
KB drift risk: Stale knowledge leads to incorrect responses; undermines trust.
Scope creep risk: Shadow AI expands beyond planned integrations; governance gaps widen.
Budget and timeline risk: EUR 180K budget may not cover infra and governance tooling; schedule must reflect policy enforcement and change management.

5) Recommended next steps (first 2 weeks)

Week 1:

- Create a two-column exercise for Hans: capture exact policy controls you will codify (P0: mandatory, P1: recommended, P2: aspirational) and map them to audit/test cases.

- Inventory and classify shadow AI assets (HR chatbot, Claims PoC, Finance GPT); assign risk scores; propose remediation/containment plan.

- Define 3 concrete end-to-end automation candidates with clear tool integrations (e.g., ServiceNow ticket triage, knowledge-base refresh trigger, escalation to human) and required authorizations.

- Draft a KB governance plan: ownership, refresh cadence, and a drift-detection mechanism with a 30-day lookback window.

Week 2:

- Draft a policy-driven architecture diagram: L1 Data Ingestion, L2 Agent Builder, L3 AI Core, L4 Policy-as-Code, L5 Human-in-the-Loop; annotate on-prem constraints.

- Define a 1-page FRIA-ready risk assessment outline per high-risk category; identify data governance controls to satisfy Art.9, Art.11, Art.12.

- Propose a staged rollout plan (Phase 1 EN/DE; CZ in Phase 2), with change-management milestones and a simple measurement plan for Jan and his team.

- Prepare a KPI dashboard outline for Hans’s board: cost savings, deflection rates, auto-resolve rate, CSAT delta, compliance posture, and audit readiness status.

6) Dependencies on other roles in the team

AI-PM (you): Align discovery findings with architecture decisions; ensure KPI definitions map to business outcomes. Secure stakeholder buy-in for L2 constrained autonomy.
AI-SEC (policy and compliance): Co-create the policy-as-code rules, data retention, audit logging, and human oversight requirements; deliver an initial policy YAML/JSON skeleton for review.
AI-DS (data science / dashboards): Design data pipelines, measurement dashboards, drift detection, and SLA metrics; ensure observability aligns with Art.12 compliance.
FDE (foundational data engineering): Provide on-prem data pipeline infrastructure, storage, and monitoring capabilities; scope hardware and logging requirements within budget.
AI-PM and Stakeholders (Hans, Stefan, Katarina, Jan): Clarify ownership, decision rights, and escalation paths; incorporate their concerns into the governance design and adoption plan.
Shadow AI owners: Create a plan to inventory, evaluate, and either govern or retire shadow tools; define a sunset or integration path to the unified platform.

Your deliverable now

A structured discovery report draft with the six sections (stakeholder analysis, key findings, requirements, risks, next steps, dependencies).
For each finding, include: (a) what Hans said, (b) what it implies technically, (c) one concrete decision you propose for the first two weeks.
Use Hans by name in quotes where possible to anchor quotes; translate business statements into technical implications.

Two quick rhetorical checks you should perform in your draft

The 5 Layers of the Unsaid: for every major finding, add at least one implicit truth from Layer 1–5 (gap, people, constraints, timeline, commercial opportunity). Example: If Hans says “on-prem only,” add Layer 3/4 reasoning about why cloud is off-limits and what that means for feasibility and risk.
The “Compared to what?” lens: for every KPI or target you propose, briefly contrast with the current baseline and shadow-AI state to show incremental value and risk.

If you want, paste your draft and I’ll perform a rapid review against:

The 5 Layers framework
L2 Constrained Autonomy alignment (not L0 or L3)
Inclusion of shadow AI governance and enterprise risk framing
A concrete two-column exercise mapping Hans’s quotes to technical implications

One concrete action you can take right now

Draft the Stakeholder Analysis section ( bullets for Hans, Stefan, Katarina, Jan, shadow AI owners ) with 1-2 lines each on role, concern, and decision authority. Then write 1-2 lines per stakeholder linking to your first two-week actions. This will anchor your report and help you push beyond surface observations.

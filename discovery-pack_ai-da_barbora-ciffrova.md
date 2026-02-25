# Discovery Packet v1 — [AI Data Analyst]
## Student: [Barbora Ciffrova]
## Date: February 23, 2026
## Client: EuroHealth Insurance AG

---

## Part 1: Discovery Questions (10)

### Question 1: [Question text]
**Why this matters:** [1-2 sentences]
**Red flag (bad answer):** [What it would tell us]
**KAF component:** [Core / Ingestion / Policy-as-Code /
  Run Safe / HITL / Interop]


### Question 1: [Where does ServiceNow (incl. Moveworks) fall short today—specifically for governance, cross‑department scaling, or regulatory adaptation—and what have you tried already to close those gaps?]
**Why this matters:** [Surfaces the delta between “feature” automation and “industrialized” AI (governance/scale). Avoids re‑selling what they already own.]
**Red flag (bad answer):** [“It’s mostly accuracy/tuning.” → Indicates they see a model problem, not an operating model/governance gap.]
**KAF component:** [AI Core / Interop]

### Question 2: [When a regulation or internal policy changes, what is the path from decision to production behavior change, and how long does it take (days, weeks, months) end‑to‑end?]
**Why this matters:** [Measures governance‑to‑production latency; a key maturity indicator.]
**Red flag (bad answer):** [“Quarterly release train.” → Policy updates are slow/manual; not EU AI Act‑ready.]
**KAF component:** [AI Core / Policy-as-Code]

### Question 3: [Which AI rules must be technically impossible to bypass—even by admins—and therefore encoded as Policy‑as‑Code (e.g., ‘no PII in training’, ‘mandatory human approval above €X impact’, ‘immutable audit log for N years’)?]
**Why this matters:** [Converts governance from documents to executable controls; clarifies non‑negotiables.]
**Red flag (bad answer):** [We rely on process discipline.” → No technical enforcement; audit risk.]
**KAF component:** [Policy-as-Code]

  ### Question 4: [Could you reconstruct a full audit trail for one AI‑assisted resolution right now—model/version, prompts/tools used, retrieved sources, approvals, and final action—without vendor intervention?]
**Why this matters:** [Tests Digital Trust and ownership of evidence; essential for audits and incident review.]
**Red flag (bad answer):** [“We’d need the vendor to pull logs.” → Weak enterprise ownership and portability.]
**KAF component:** [Run Safe]

  ### Question 5: [What data sources are in scope for the agent today, how is PII excluded from training, and what controls ensure content freshness and revocation of outdated knowledge?]
**Why this matters:** [On‑prem and ‘no PII in training’ require disciplined ingestion, curation, and lifecycle management.]
**Red flag (bad answer):** [“We uploaded a SharePoint export once.” → Stale KB; weak lineage/PII boundary.]
**KAF component:** [Ingestion / Run Safe]

  ### Question 6: [Which agentic workflows must the system plan and execute end‑to‑end, and which tools/integrations are required (e.g., ServiceNow actions, HR/Claims/Finance systems) with what authorizations?]
**Why this matters:** [Defines the action surface and the MCP/connector plan for scale beyond IT.]
**Red flag (bad answer):** [“Read‑only answers only.” → No closed‑loop actions; value limited to Q&A.]
**KAF component:** [Core / Interop]

  ### Question 7: [Where is human‑in‑the‑loop mandatory today (risk, cost, customer impact), and what confidence/impact thresholds trigger escalation or override?]
**Why this matters:** [Defines the control points that keep automation safe and auditable.]
**Red flag (bad answer):** [“We’ll add humans later if needed.” → No guardrails; high operational risk.]
**KAF component:** [Policy-as-Code / HITL]

  ### Question 8: [What runtime monitoring and validation exist (quality, safety, drift, cost), and how do you block/rollback when thresholds are breached?]
**Why this matters:** [Proves ‘Run Safe’ in production; reduces incident MTTR and compliance exposure.]
**Red flag (bad answer):** [“We check metrics monthly.” → No real‑time safeguards; failure to contain bad behavior.]
**KAF component:** [Core / Run Safe]

  ### Question 9: [What is your on‑prem architecture for LLMs and retrieval today—hosting model, network segmentation, data egress, secrets management—and where must EuroHealth retain data/control vs the vendor?]
**Why this matters:** [Aligns solution to on‑prem constraints, sovereignty, and incident containment.]
**Red flag (bad answer):** [“Model runs in a vendor cloud we don’t control.” → Conflicts with on‑prem and sovereignty needs.]
**KAF component:** [Core / Interop]

  ### Question 10: [What operating model will govern AI across departments—registry, risk classification, RACI, board reporting cadence—and what must be delivered by Q3 2026 to be visibly ‘EU AI Act‑ready’?]
**Why this matters:** [Anchors the 6‑month scope to board‑visible evidence and cross‑dept adoption.]
**Red flag (bad answer):** [“We’ll form a committee later.” → No ownership; governance will stall.]
**KAF component:** [Core / Policy-as-Code / Run Safe]




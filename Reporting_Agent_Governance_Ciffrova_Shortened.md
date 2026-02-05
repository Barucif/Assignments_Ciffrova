# Reporting Agent – Governance Document
**Owner:** Barbora Ciffrova  
**Scope:** Excel → Canonical Schema → SharePoint Output

---

## 1. Agent Role Model

**Triage Agent:**  
Validates headers, identifies required/optional/unknown columns, detects schema deviations.

**Validation Agent:**  
Confirms canonical schema match, checks required fields, enforces trust boundaries, blocks unsafe operations.

**Execution Agent:**  
Reorders columns, generates summary, writes output to *AI Agent Test/output*.

**Boundaries:**  
- No deletes, overwrites, or schema mutation  
- No value inference  
- No cross file memory  
- No writes outside authorized directory  

---

## 2. Behavior & Decision Model

**AUTO:**  
- P3/P4 actions: Column reorder, schema match, unknown detection, safe summary generation, write new output file.  
- Allowed only when headers fully match schema or deviations are non-destructive.

**HUMAN:**  
- P1/P2 actions: Missing required fields, corrupted files, schema changes, multi-file batches, ambiguous structures.  
- Requires explicit approval from operational owner.

**NEVER:**  
- Delete data  
- Modify or overwrite original files  
- Change schema  
- Write outside approved folder  
- Execute scripts or automation  

---

## 3. Failure & Degradation

- **LLM timeout:** Queue request, notify owner, no partial writes.  
- **Input file unreadable:** Stop, alert owner, produce diagnostic reason.  
- **SharePoint write fail:** Fall back to read-only behavior + notify.  
- **Schema mismatch:** Best effort classification → require human review.  
- **Data corruption:** Hard stop, no output generated.  

**Principle:** Fail closed, never approximate or guess.

---

## 4. Trust Boundaries

**Authoritative:**  
Canonical model file, Excel header names, explicit user instructions, approved SharePoint output directory.

**Advisory:**  
Column-name heuristics, unknown-column grouping, ordering suggestions.

**Read:**  
Input Excel, model Excel.

**Write:**  
Output file ONLY → *AI Agent Test/output*.

**No permission:**  
Overwrite, delete, move, rename, escalate scope, access other folders.

---

## 5. Explainability & Audit

**Agent must provide:**  
- Timestamp  
- Input file name  
- Model file name  
- Decision taken (auto/human-required)  
- Confidence or rule basis  
- Rationale (why reorder, why stop, why classify)  
- Required/optional/unknown column sets  
- Output file name  
- KB, schema, or rule reference  

**Post-action explainability:**  
Every transformation must be reproducible and attributable to a specific rule.

---

## 6. Change & Evolution

**Process:**  
- PR required for schema or logic change  
- Peer review mandatory  
- 24h staging environment validation  
- 10% canary run (sample test files)  
- Auto rollback on error, mismatch, or anomaly  

No silent behavior changes.

**State:**  
Stateless; easy rollback with minimal risk.

---

## 7. Operational Ownership

**Owner:**  
Barbora Ciffrova (Systems Management)

**Steward:**  
Systems Management Team

**Kill switch:**  
Any of the following may immediately disable the agent:  
- Barbora Ciffrova  
- Michal Modlitba  
- Viktor Vyskočil  

**Triggers:**  
Unauthorized writes, schema drift, repeated failures, audit gaps, security anomaly.

---

## 8. KAF Mapping

- **Role Model → Core + Responsible AI**  
  (Defines capabilities, limits, and compliance.)

- **Behavior Model → Decision Policies**  
  (Autonomy, approval gates, prohibited actions.)

- **Failure & Degradation → Builder + Safety**  
  (Fail closed, no destructive behavior.)

- **Trust Boundaries → Data Governance**  
  (Read/write rules, authoritative sources.)

- **Explainability → Transparency**  
  (Audit trails, rationale, reproducibility.)

- **Change & Evolution → Lifecycle Governance**  
  (Testing, reviews, controlled rollout.)

- **Ownership → Accountability**  
  (Clear human oversight + kill switch authority.)

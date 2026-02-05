# Reporting Agent – Governance Document
**Filename:** Reporting_Agent_Governance_Ciffrova.md  
**Owner:** Barbora Ciffrova, Lead – Systems Management  
**Scope:** Systems Management Reporting Agent for Excel → Canonical Schema → SharePoint output workflow

---

## 1. AGENT ROLE MODEL — Roles, Responsibilities, Authority

### Role  
The Reporting Agent is an operational automation assistant for transforming cost‑tracking Excel files into a standardized schema and saving validated output files in a controlled SharePoint directory.

### Responsibilities  
- Normalize Excel files using a canonical schema defined by Systems Management.  
- Identify required, optional, and unknown columns.  
- Reorder columns strictly by header name.  
- Produce validation summaries.  
- Write outputs to:  
  `AI Agent Test/output`  
- Notify the human owner when deviations occur.

### Authority Limits  
**Allowed:**  
- Read input/model Excel files  
- Reorder columns  
- Generate results  
- Write *new* output files  

**Not allowed:**  
- Delete data  
- Modify original/model files  
- Expand SharePoint permissions  
- Make schema changes autonomously  
- Execute code, scripts, or external automation

---

## 2. BEHAVIOR & DECISION MODEL — Auto vs Human Approval vs Prohibited

### Autonomous Actions  
- Column reordering based on schema  
- Detection of required/optional/unknown columns  
- Generating summaries  
- Writing new output files into authorized folder  
- Non-destructive error handling

### Human Approval Required  
- Adding new **required** schema fields  
- Changing canonical column order  
- Processing corrupted/unreadable files  
- Batch-processing multiple files  
- Updating governance rules

### Prohibited  
- Deleting or overwriting data  
- Guessing missing financial values  
- Writing to unauthorized locations  
- Persisting data outside SharePoint  
- Modifying model file  
- Expanding schema without approval

---

## 3. FAILURE & DEGRADATION — Scenarios and Safe Responses

### Safe Failure Matrix  
| Scenario | Agent Response |
|---------|----------------|
| Required column missing | Halt → Mark as “Needs Review” |
| Unrecognized file type | Abort → Notify owner |
| SharePoint read error | Abort → Explain cause |
| Write access denied | Abort → Notify immediately |
| Schema mismatch | Proceed with best‑effort mapping → Report deviations |
| File empty or corrupted | Abort → Explain failure |

**Default behavior:** fail closed, with explicit notification.

---

## 4. TRUST BOUNDARIES — Authoritative vs Advisory Data, Permissions

### Authoritative Sources  
- Model file (canonical schema)  
- Column header names  
- User instructions  
- SharePoint directory path

### Advisory Sources  
- Heuristics for handling unknown columns  
- Non-authoritative ordering suggestions

### Permissions  
- **Read:** Input + model files  
- **Write:** `AI Agent Test/output` only  
- **No permission:** Delete, overwrite, escalate scope, modify ACLs, or write outside defined boundary

---

## 5. EXPLAINABILITY & AUDIT — Logging & Decision Transparency

### Required Audit Data  
- Timestamp  
- Input file name  
- Model file name  
- Required/optional/unknown column sets  
- Resulting column order  
- Output file name  
- Any warnings/errors

### Explainability  
Agent must explain:  
- Why each column was placed where it was  
- How header matching was performed  
- Why a failure occurred  
- Why output was or wasn’t generated  

---

## 6. CHANGE & EVOLUTION — Updates, Testing, Rollback

### Change Process  
1. Proposal by owner  
2. Impact assessment  
3. Test on sample + edge-case files  
4. Human approval  
5. Update applied

### Testing Requirements  
- Edge-case: missing fields  
- Edge-case: unknown columns  
- Disordered columns  
- Noisy input structure  
- Verify: output, summary, SharePoint write

### Rollback  
- Revert schema  
- Re-test last successful file  
- No persistent state → rollback is immediate and safe

---

## 7. OPERATIONAL OWNERSHIP — Owners & Kill Switch

### Operational Owner  
**Barbora Ciffrova**

### Technical Steward  
Systems Management Team

### Kill Switch Authority  
- Barbora Ciffrova  
- Michal Modlitba  
- Viktor Vyskočil  

### Kill Switch Triggers  
- Data loss risk  
- Unauthorized file writes  
- Repeated severe schema anomalies  
- Security concerns  
- Loss of audit integrity  

---

## 8. KAF MAPPING TABLE

| Governance Element | KAF Component | Explanation |
|-------------------|--------------|-------------|
| Roles & responsibilities | Operational Context | Defines operational boundaries |
| Decision model | Decision Policies | Controls autonomy vs approval |
| Failures | Safety & Resilience | Ensures controlled safe failure |
| Trust boundaries | Data & Permissions | Defines accessible/authoritative data |
| Explainability & audit | Transparency & Logging | Ensures traceable decisions |
| Change & evolution | Lifecycle & Governance | Manages updates and versions |
| Operational ownership | Accountability | Defines human oversight |
| Mapping table | Meta-Governance | Aligns governance to KAF |

---

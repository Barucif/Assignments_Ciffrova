# Compliance Appendix — Reporting Agent
**Filename:** Compliance_Appendix_Ciffrova.md  
**Owner:** Barbora Ciffrova, Lead – Systems Management  
**Scope:** Governance compliance for Reporting Agent used in cost‑tracking file normalization

---

## 1. Decision Authority
The agent may autonomously reorganize Excel columns, perform schema validation, classify required/optional/unknown columns, generate summaries, and write new output files exclusively to the authorized SharePoint output directory. All actions must follow the canonical schema and cannot alter data content.

---

## 2. Prohibited Decisions
The agent is explicitly prohibited from:
- Deleting or overwriting data  
- Modifying the model file or schema  
- Updating SharePoint permissions  
- Writing to unauthorized folders  
- Inferring missing financial or business values  
- Executing scripts, code, or external automation  
- Making decisions that alter business or audit-sensitive information  

---

## 3. Accountability for Incorrect Decisions
Accountability for all agent outputs resides with:
- **Operational Owner:** Barbora Ciffrova  
- **Manager:** Michal Modlitba  
- **Skip Manager:** Viktor Vyskočil  

The agent itself cannot be accountable; humans must validate outputs and schema changes.

---

## 4. Handling Incomplete or Ambiguous Data
The agent follows a strict **fail‑closed** approach:  
- Missing required columns → Stop and mark as “Needs Review”  
- Unknown or ambiguous columns → Flag as “unknown,” never guess  
- Corrupted or unreadable files → Abort processing and notify  

---

## 5. Risk Posture
The agent operates under an intentionally **low‑risk, conservative posture**:
- Stateless execution (no memory)  
- Read‑only on inputs, restricted write‑only on outputs  
- No schema inference or auto-repair  
- Fail‑closed handling  
- Complete audit logging  

---

## 6. Mandatory Refusal Conditions
The agent must refuse to act when:
- Required columns are missing  
- File format is invalid or unreadable  
- Write access is denied  
- Schema mismatch cannot be safely handled  
- Input structure is too ambiguous for reliable mapping  

---

## 7. Recommendations vs Decisions
- **Recommendations:** Advisory notes such as unknown column detection  
- **Decisions:** Only low-risk, reversible structural transformations (column ordering)  
The agent never performs business or financial decisions.

---

## 8. Final Decision Authority
Humans maintain final authority at all times.  
The agent cannot finalize schema changes or override user instructions.

---

## 9. Cross-Agent Overrides
The agent cannot:
- Override another agent  
- Override human input  
- Override SharePoint permissions  
- Override schema rules  

---

## 10. Persistent Context
The agent maintains **no persistent state**.  
No past runs are stored, and all decisions are based solely on the current files and instruction.

---

## 11. Influence of Past Interactions
Past interactions have **zero influence** on future behavior.  
Every run uses fresh state, schema, and file inputs.

---

## 12. Handling Low-Confidence Outputs
Low-confidence scenarios trigger:
- Processing halt  
- Warning to the user  
- No output write  
- Full explanation in summary report  

The agent never “guesses” values.

---

## 13. Failure Degradation
Failures degrade safely:
- No partial writes  
- No silent changes  
- Immediate notification to the owner  
- Fail‑closed behavior ensures data protection  

---

## 14. Authoritative vs Advisory Data
**Authoritative:**  
- Model file (canonical schema)  
- Excel header names  
- SharePoint directory path  
- Explicit user commands  

**Advisory:**  
- Heuristics for unknown column ordering  
- Non-critical suggestions  

---

## 15. Production Write Permissions
No.  
The agent cannot write to any production system.  
Write access is restricted to the validated output directory:
`AI Agent Test/output`

---

## 16. Decision Explainability
The agent is capable of explaining:
- Why columns were placed in their final positions  
- Why required columns were missing  
- Why processing stopped  
- How input mapped to output  

All decisions follow schema-driven logic and are fully auditable.

---

## 17. Audit Evidence Logged
Each run logs:
- Timestamp  
- Input file name  
- Model file name  
- Required/optional/unknown columns  
- Column order after processing  
- All errors, warnings, and mismatches  
- Output file name  

---

## 18. Behavioral Change Management
Behavior changes follow:
1. Proposal  
2. Risk assessment  
3. Test with controlled inputs  
4. Human approval  
5. Versioning and rollback plan  

No silent or autonomous changes permitted.

---

## 19. Immediate Disable Authority (Kill Switch)
May be triggered by:
- **Barbora Ciffrova**  
- **Michal Modlitba**  
- **Viktor Vyskočil**

This halts all agent operations instantly.

---

## 20. Proving Business Value Without Increasing Risk
Value is demonstrated through:
- Faster, consistent file normalization  
- Zero destructive operations  
- Complete auditability  
- Strict trust boundaries  
- No persistent memory  
- Controlled schema-based processing  
- Fail‑closed risk posture  

This ensures measurable efficiency improvement with minimal operational risk.

---

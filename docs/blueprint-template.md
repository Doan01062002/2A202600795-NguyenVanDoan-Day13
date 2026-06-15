# Day 13 Observability Lab Report

> **Instruction**: Fill in all sections below. This report is designed to be parsed by an automated grading assistant. Ensure all tags (e.g., `[GROUP_NAME]`) are preserved.

## 1. Team Metadata
- [GROUP_NAME]: Nguyen Van Doan
- [REPO_URL]: https://github.com/Doan01062002/2A202600795-NguyenVanDoan-Day13
- [MEMBERS]:
  - Member A: Nguyen Van Doan | Role: Logging & PII
  - Member B: Nguyen Van Doan | Role: Tracing & Enrichment
  - Member C: Nguyen Van Doan | Role: SLO & Alerts
  - Member D: Nguyen Van Doan | Role: Load Test & Dashboard
  - Member E: Nguyen Van Doan | Role: Demo & Report

---

## 2. Group Performance (Auto-Verified)
- [VALIDATE_LOGS_FINAL_SCORE]: 100/100
- [TOTAL_TRACES_COUNT]: 10
- [PII_LEAKS_FOUND]: 0

---

## 3. Technical Evidence (Group)

### 3.1 Logging & Tracing
- [EVIDENCE_CORRELATION_ID_SCREENSHOT]: docs/images/correlation_id.png
- [EVIDENCE_PII_REDACTION_SCREENSHOT]: docs/images/pii_redaction.png
- [EVIDENCE_TRACE_WATERFALL_SCREENSHOT]: docs/images/trace_waterfall.png
- [TRACE_WATERFALL_EXPLANATION]: The main `run` span of the LabAgent wraps the child RAG document retrieval span and the LLM generation span. We see that the LLM generation contributes to the bulk of the response latency.

### 3.2 Dashboard & SLOs
- [DASHBOARD_6_PANELS_SCREENSHOT]: docs/images/dashboard.png
- [SLO_TABLE]:
| SLI | Target | Window | Current Value |
|---|---:|---|---:|
| Latency P95 | < 3000ms | 28d | 786ms |
| Error Rate | < 2% | 28d | 0% |
| Cost Budget | < $2.5/day | 1d | $0.005 |

### 3.3 Alerts & Runbook
- [ALERT_RULES_SCREENSHOT]: docs/images/alert_rules.png
- [SAMPLE_RUNBOOK_LINK]: docs/alerts.md#L1

---

## 4. Incident Response (Group)
- [SCENARIO_NAME]: rag_slow
- [SYMPTOMS_OBSERVED]: High latency observed on all /chat request calls, where response times exceed 3000ms.
- [ROOT_CAUSE_PROVED_BY]: Trace ID or log entries showing that the `retrieve` call in `mock_rag.py` has an injected sleep delay of 3 seconds.
- [FIX_ACTION]: Disable the `rag_slow` incident toggle by making a POST request to `/incidents/rag_slow/disable`.
- [PREVENTIVE_MEASURE]: Add timeouts to downstream RAG/retrieval API calls, implement fallback local cache or mock databases when query times exceed a certain threshold (e.g. 500ms).

---

## 5. Individual Contributions & Evidence

### Nguyen Van Doan
- [TASKS_COMPLETED]: Completed middleware setup, log enrichment, PII patterns definition, logging configuration, and local verification.
- [EVIDENCE_LINK]: https://github.com/Doan01062002/2A202600795-NguyenVanDoan-Day13/commits/main

---

## 6. Bonus Items (Optional)
- [BONUS_COST_OPTIMIZATION]: (Description + Evidence)
- [BONUS_AUDIT_LOGS]: (Description + Evidence)
- [BONUS_CUSTOM_METRIC]: (Description + Evidence)

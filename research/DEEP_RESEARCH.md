# FinNet — Deep Product & Market Research

**Owner / Content Creator:** Sandeep Barupal  
**Copyright:** © 2026 Sandeep Barupal. All rights reserved, except third-party materials and linked frameworks under their own terms.  
**Research status:** Deep-research baseline v1.0 — desk research; validate with users before committing product decisions.  
**Purpose:** Inform an original technology financial management and FinOps product. This is not financial advice.

## 1. Product thesis
FinNet should help engineering, finance, product, and leadership answer three questions: where is technology money going, what business value does it create, and what action should be taken next? A useful product must go beyond a cost chart: connect spend to owners, budgets, workloads, unit economics, and governed optimization actions.

## 2. Market and workflow findings
The FinOps Foundation framework groups work into understanding usage/cost, quantifying business value, optimizing usage/cost, and managing the practice. It explicitly includes allocation, analytics, anomaly management, forecasting, budgeting, unit economics, workload optimization, rate optimization, SaaS/licensing, governance, and chargeback/showback. Microsoft Learn presents a similar capability map. These are strong coverage anchors for FinNet, not a reason to reproduce another vendor's interface. Sources: [FinOps Foundation Framework](https://www.finops.org/framework/), [Microsoft FinOps documentation](https://learn.microsoft.com/en-us/cloud-computing/finops/).

## 3. Competitor / adjacent-product landscape
| Category | Reference products / sources | What to investigate | Strategic implication |
|---|---|---|---|
| Cloud-native cost tools | AWS Cost Explorer, Azure Cost Management, Google Cloud FinOps tools | Native billing depth, resource recommendations, cloud-specific limitations | Start with normalized cross-account reporting; don't promise equal support before connector validation |
| FinOps operating model | FinOps Foundation | Personas, phases, capability maturity, unit economics | Align terminology with recognized practice and attribute any reused framework content correctly |
| Cloud cost data normalization | FinOps Open Cost and Usage Specification (FOCUS) | Common fields, billing export formats, provider-specific mappings | Design an ingestion adapter layer and preserve raw source records |
| Enterprise IT financial management | ITFM / TBM practices | Cost centers, allocations, shared-service costs, chargeback | Make allocation rules explainable and auditable |

Pricing varies by provider, commitment, cloud consumption, and contract; do not publish unverified price comparisons. Capture the date and plan scope for any pricing research.

## 4. Target users and jobs-to-be-done
- FinOps practitioner: identify spend variance, assign ownership, track savings recommendations.
- Engineering lead: understand workload cost and reliability/performance trade-offs.
- Finance: forecast spend, compare actuals to budget, reconcile allocation.
- Product owner: measure cost per customer, transaction, API call, or feature.
- Executive: see business-value outcomes and material risks without reading raw billing exports.

## 5. Feature specification
### P0 — MVP
1. Multi-account cloud cost import (CSV first; provider APIs later), schema validation, duplicate detection, import history.
2. Cost explorer by date, provider, account, service, region, environment, team, product and tag.
3. Allocation rules with preview, versioning, effective dates, unallocated-cost queue and audit trail.
4. Budgets, forecast, threshold alerts and anomaly triage with owner and status.
5. Saved views, exports, basic RBAC, organization settings and audit events.
6. Data freshness and ingestion-error indicators on every relevant report.
### P1 — Differentiation
- Unit economics (cost per active customer / transaction) with explicit metric definitions.
- Recommendation workflow: estimated impact, confidence, owner, approval, execution status and verified savings.
- SaaS/licensing inventory and renewal calendar.
- Chargeback/showback statements and allocation explainability.
### P2 — Advanced
- Commitment coverage, scenario modeling, AI spend governance, sustainability indicators, multi-cloud policy engine.

## 6. Page map
Overview; Cost Explorer; Budgets & Forecasts; Anomalies; Allocation Rules; Recommendations; Unit Economics; Accounts & Connectors; Imports & Data Quality; Reports; Team/Ownership; Audit Log; Settings; Help/Runbooks.

## 7. Architecture direction
Use a connector/ingestion pipeline, immutable raw billing storage, normalized cost schema, transformation/attribution jobs, analytical store, API layer and dashboard. Separate raw facts from derived allocations so a rule change can be recalculated. Make imports idempotent, version transformations, track source timestamps, and support backfills. Begin with batch ingestion; add streaming only when a validated use case requires it.

## 8. Security and governance
Tenant isolation; least-privilege cloud roles; encrypted credentials in a secrets manager; never request broad write access for a read-only reporting feature; audit every allocation/budget change; row-level access for cost centers; data-retention controls; redaction of billing metadata where needed. Treat cost data as commercially sensitive.

## 9. Metrics and acceptance criteria
- Import reconciliation difference is visible and explained.
- Every cost row can be traced to source record and transformation version.
- Allocation totals reconcile to source totals within defined rounding rules.
- Alert has owner, threshold, evidence, lifecycle status and deduplication.
- Forecast shows assumptions and uncertainty; never present a point estimate as certainty.
- Track time-to-detect anomalies, percentage of allocated spend, forecast error, recommendation acceptance and verified net savings.

## 10. Risks and validation questions
Risks: inconsistent tags, provider schema changes, delayed billing exports, double-counting credits/refunds, misleading savings estimates, noisy alerts and privilege overreach. Interview 5–8 practitioners across finance and engineering. Test whether users trust allocations and can explain one variance without analyst help. Validate the FOCUS schema and provider-specific source data before implementation.

## 11. Research references
- [FinOps Framework](https://www.finops.org/framework/)
- [FinOps Unit Economics](https://www.finops.org/framework/capabilities/unit-economics/)
- [Microsoft FinOps documentation](https://learn.microsoft.com/en-us/cloud-computing/finops/)
- [Google Cloud FinOps overview](https://cloud.google.com/learn/what-is-finops)
- [AWS Well-Architected Framework](https://docs.aws.amazon.com/wellarchitected/latest/framework/)

## 12. Next work
Build a dated competitor matrix, review public product docs/pricing, inspect sample billing exports, write allocation and forecast user stories, then validate wireframes with finance and engineering. This document is a research baseline, not a claim that every competitor capability has been exhaustively tested.
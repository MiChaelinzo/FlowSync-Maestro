### FlowSync Maestro

**Orchestrating humans, robots, and AI agents in BPMN 2.0 for seamless, end‑to‑end Procure‑to‑Pay processes — with intelligent invoice reconciliation, smart routing, and clean execution.**

---

### Project Description

**FlowSync Maestro** is a **Procure‑to‑Pay (P2P) Invoice Reconciliation** solution built on **UiPath Maestro BPMN 2.0**. It solves one of enterprise finance's most persistent pain points: fragmented, error-prone invoice processing across ERP systems, AP teams, vendors, and approval hierarchies.

The core agent — the **P2P Invoice Reconciliation Agent v3.0** — performs a 13-step intelligent analysis pipeline on every invoice: 3-way matching (PO × GRN × Invoice), fraud detection, contract rate compliance, tax validation, working capital optimization, smart GL coding, vendor scorecarding, composite anomaly scoring, invoice lifecycle tracking, smart recommendations, and executive summary generation.

Maestro BPMN 2.0 orchestrates the full process — from RPA-extracted PO and invoice data, through agent analysis, to deterministic BPMN gateway routing that lands each invoice in exactly the right human or automated next step.

**Problems solved:** inconsistent AP decisions, undetected contract overbilling, missed early payment discounts, slow fraud detection, manual GL coding errors, and lack of end-to-end process traceability.

---

### Key Features

- **13-step AI analysis pipeline** covering 3-way match, fraud, contract compliance, tax, working capital, GL coding, vendor scorecard, anomaly scoring, lifecycle tracking, smart recommendations, and executive summary.
- **5-path BPMN gateway routing** (`auto_approve_path`, `ap_review_path`, `manager_approval_path`, `vendor_dispute_path`, `fraud_hold_path`) driven deterministically by agent output.
- **Composite Anomaly Score (0–100)** — weighted across 5 risk factors that can override an otherwise clean auto-approval when aggregate risk is elevated.
- **Contract Compliance Engine** — detects rate overbilling per line, unapplied volume discounts, and earned rebates against vendor contract data.
- **Working Capital Optimizer** — calculates the net financial benefit of early payment vs. DPO targets and recommends PAY\_EARLY, PAY\_ON\_TIME, or DELAY\_TO\_DPO\_TARGET.
- **Smart Recommendations Engine** — generates 3–5 quantified, prioritized, actionable recommendations (COST\_SAVINGS, RISK\_REDUCTION, COMPLIANCE, VENDOR\_MANAGEMENT) from the full analysis.
- **Invoice Lifecycle Tracker** — detects resubmissions, chronic disputes (3+ submissions), and processing delays.
- **Split Payment support** — approve clean lines immediately, hold only disputed lines.
- **Human-in-the-loop** via UiPath Action Center for AP review, manager approval, and vendor dispute tasks.
- **18 automated evaluations** covering every routing path and all v3.0 features.

---

### UiPath Components

| Component | Purpose |
|---|---|
| **UiPath Maestro** | BPMN 2.0 process modeling and orchestration of the full P2P flow |
| **UiPath Agent Builder** | P2P Invoice Reconciliation Agent v3.0 (low-code agent) |
| **Analyze Files** | Extract structured data from simple 1–5 page invoice PDFs |
| **DeepRAG** | Deep multi-page invoice analysis with citation tracking |
| **Batch Transform** | Duplicate invoice detection and fraud pattern analysis on historical CSV |
| **UiPath Studio** | RPA workflows for PO/GRN/invoice extraction from ERP portals |
| **UiPath Orchestrator** | Schedule, manage, and monitor RPA robot jobs |
| **UiPath Action Center** | Human tasks — AP review, manager approval, vendor dispute handling |
| **REST APIs & Connectors** | ERP, CRM, and AP system integrations |
| **UiPath Automation Cloud** | Cloud deployment and scalability |

---

### Agent Type and Architecture Overview

**Agent Type**
This solution uses a **Low-Code Agent** built in UiPath Agent Builder — the **P2P Invoice Reconciliation Agent v3.0**. It leverages three built-in platform tools (Analyze Files, DeepRAG, Batch Transform) and is invoked as a Service Task within the Maestro BPMN process. No external frameworks (LangChain, CrewAI, AutoGen) are required — the agent runs natively on UiPath Automation Cloud.

**Architecture Overview**

```
┌─────────────────────────────────────────────────────────────┐
│                  UiPath Maestro BPMN 2.0                    │
│  Start → RPA Extract → [Agent Analysis] → Gateway → End     │
│            ↓              ↓                  ↓              │
│         PO/GRN         13-Step          5 Paths:            │
│         Invoice        Pipeline         auto_approve         │
│         from ERP                        ap_review            │
│                                         manager_approval     │
│                                         vendor_dispute       │
│                                         fraud_hold           │
└─────────────────────────────────────────────────────────────┘

Process Layer    → Maestro BPMN 2.0 (orchestration + gateways)
Automation Layer → UiPath Studio + Orchestrator (RPA extraction)
Agent Layer      → Agent Builder v3.0 (13-step reconciliation)
  ├─ Analyze Files  (simple invoice PDFs)
  ├─ DeepRAG        (complex multi-page PDFs)
  └─ Batch Transform (fraud/duplicate detection)
Integration Layer → REST APIs, ERP/CRM connectors
Human Layer       → Action Center (AP review, approvals, disputes)
```

**Agent Analysis Pipeline (13 Steps)**

| Step | Analysis |
|---|---|
| 1 | Document Extraction (DeepRAG / Analyze Files / Batch Transform) |
| 2 | Validation & Header Match |
| 3 | Line-Item Match & Accrual Detection (GR/NI) |
| 4 | Fraud Detection & Tax Compliance |
| 5 | Contract Compliance Engine |
| 6 | Payment Intelligence & SLA |
| 7 | Working Capital Optimizer |
| 8 | Smart GL Coding |
| 9 | Vendor Scorecard |
| 10 | Composite Anomaly Score (0–100) |
| 11 | Invoice Lifecycle Tracking |
| 12 | BPMN Routing Decision (8-rule hierarchy) |
| 13 | Smart Recommendations + Executive Summary |

---

### Setup Instructions for Judging

**Prerequisites**
1. **UiPath Automation Cloud account** with access to Maestro, Agent Builder, Studio, and Orchestrator.
2. **Git** and a local development environment (Windows recommended for UiPath Studio).
3. **Credentials** for any target ERP/CRM test instances or mock endpoints.
4. **Node/Python** runtime if any coded automation scripts require local execution.

**Repository Layout**
```
README.md                       ← This file
maestro/                        ← BPMN models and Maestro solution files
  └── samples/                  ← Sample P2P test data (PO, GRN, invoice)
agents/                         ← Agent Builder export and configuration
  └── p2p-reconciliation-v3/    ← P2P Invoice Reconciliation Agent v3.0
rpa/                            ← UiPath Studio projects (PO/GRN/invoice extraction)
integration/                    ← API mocks, ERP/CRM connector configs
  └── config.sample.json
docs/                           ← Architecture diagrams and runbook
submission/                     ← Deck and judging artifacts
  └── evidence/                 ← Screenshots/video of Maestro run
```

**Step-by-Step Setup**
1. **Clone repository**
   ```bash
   git clone https://github.com/MiChaelinzo/FlowSync-Maestro.git
   cd FlowSync-Maestro
   ```
2. **Provision Maestro workspace**
   - Create or use an existing UiPath Automation Cloud tenant.
   - Import BPMN models from `maestro/` into UiPath Maestro.
3. **Import the P2P Reconciliation Agent**
   - Open UiPath Agent Builder and import the agent definition from `agents/p2p-reconciliation-v3/`.
   - Verify the three tools are configured: **Analyze Files**, **DeepRAG**, and **Batch Transform**.
4. **Deploy RPA Packages**
   - Open UiPath Studio projects in `rpa/`, publish to Orchestrator, and configure robot environments for PO, GRN, and invoice extraction.
5. **Configure Integrations**
   - Update `integration/config.sample.json` with test endpoints and credentials; save as `integration/config.json`.
   - Start any local API mocks if provided.
6. **Wire Up Process in Maestro**
   - In Maestro, configure the Agent Service Task to point to the P2P Reconciliation Agent.
   - Map the 5 BPMN gateway paths to their downstream tasks (AP review, manager approval, vendor dispute, fraud hold, auto-approve).
   - Configure Action Center user tasks for human review lanes.
7. **Run a Demo Scenario**
   - Use the sample data in `maestro/samples/` to start the BPMN process.
   - Observe: RPA job in Orchestrator → agent analysis → gateway decision → human task in Action Center (if escalated) or auto-approved payment record.
8. **Verify Outcomes**
   - ✅ Clean invoice (FULL_MATCH, low risk, ≤ autoApproveLimit) → auto_approve_path
   - ✅ Price variance > tolerance → vendor_dispute_path → Action Center vendor task
   - ✅ Fraud signal (bank change, duplicate, blocked vendor) → fraud_hold_path → AP team URGENT task
   - ✅ Contract overbilling detected → RETURN_TO_VENDOR with recovery smart recommendation
   - ✅ Anomaly score > 50 → escalated even on otherwise clean invoice
   - ✅ Working capital analysis populates with PAY_EARLY/DELAY recommendation
   - Capture screenshots or process trace logs for judging evidence.

**Troubleshooting Tips**
- Check Orchestrator logs for failed RPA extraction jobs.
- Validate agent endpoint with a test invocation using the sample JSON in `maestro/samples/`.
- Use Maestro process trace to inspect gateway decisions — check `nextBpmnGateway` in agent output.
- If DeepRAG returns incomplete extraction, verify the invoice PDF is accessible as a job attachment.

---

### Judging Submission Checklist

- **README.md** at repository root with Project Description, UiPath Components, Agent Type, and Setup Instructions.
- **Working BPMN models** in `maestro/` with all 5 gateway paths configured.
- **Agent config export** in `agents/p2p-reconciliation-v3/` with tool definitions.
- **RPA projects** in `rpa/` published or with publish instructions.
- **Integration config** and mock endpoints in `integration/`.
- **Submission deck** in `submission/Submission Deck.pptx` using the required template:
  [https://docs.google.com/presentation/d/1U_60smXuoY-9g_fVQCLZc_gKMDWYZ1_g/edit?slide=id.p1](https://docs.google.com/presentation/d/1U_60smXuoY-9g_fVQCLZc_gKMDWYZ1_g/edit?slide=id.p1)
- **Demo evidence** in `submission/evidence/` — video or screenshots showing: Maestro process run, agent output JSON (check `nextBpmnGateway`, `executiveSummary`, `smartRecommendations`), Action Center tasks, Orchestrator jobs.
- **Expected outcomes file** at `submission/expected_outcomes.md`.

**Judging Run Instructions**
1. Reviewer clones the repo and follows Setup Instructions above.
2. Reviewer imports BPMN into Maestro and starts the process with the sample data from `maestro/samples/`.
3. Reviewer traces the process through Maestro gateway decisions, Action Center tasks, and Orchestrator robot jobs.
4. Reviewer confirms all 8 outcome scenarios in `submission/expected_outcomes.md` resolve correctly.
5. Reviewer checks agent output JSON for `executiveSummary`, `anomalyScore`, `smartRecommendations`, and `nextBpmnGateway` correctness.

---

### Contact and Next Steps

- **GitHub:** MiChaelinzo/FlowSync-Maestro
- **UiPath Studio Project:** Hackathon Workspace (see repo `docs/` for link and access notes)

---

Here's a quick diff of what changed and why:

| Section | Change | Reason |
|---|---|---|
| Tagline | Added "P2P processes — intelligent invoice reconciliation" | Accurately reflects the built scenario |
| Project Description | Full P2P scenario description + 13-step pipeline | Was too generic |
| Key Features | Added anomaly score, contract compliance, working capital, lifecycle, smart recs, split payment, 18 evals | All missing v3.0 features |
| UiPath Components | Added Analyze Files, DeepRAG, Batch Transform; removed generic entries | These are the actual tools we configured |
| Agent Type | Changed to **Low-Code Agent via Agent Builder** | Was claiming Coded + LangChain/CrewAI/AutoGen — not what we built |
| Architecture | Added 13-step table, 5-gateway diagram, tool breakdown | Was too abstract |
| Verify Outcomes | Updated to 8 specific P2P outcomes | Was referencing "order creation" which doesn't apply |
| Troubleshooting | Added DeepRAG, job attachment, `nextBpmnGateway` tips | Specific to our implementation |

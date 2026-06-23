### FlowSync Maestro

**Orchestrating humans, robots, and agents in BPMN 2.0 for seamless, end‑to‑end business processes with precision handoffs and clean execution.**

---

### Project Description
**FlowSync Maestro** unifies human workers, RPA bots, and AI agents under a single **BPMN 2.0 orchestration layer** (UiPath Maestro). It solves fragmented enterprise workflows by modeling full end‑to‑end processes, enforcing precise handoffs, and ensuring reliable execution across systems (ERP, CRM, finance), RPA, and cognitive agents. Typical problems addressed: inconsistent task ownership, brittle integrations, slow exception handling, and lack of multi‑actor coordination.

---

### Key Features
- **Hybrid orchestration** of human tasks, RPA, and AI agents using BPMN 2.0.  
- **Clean task transitions** and decision gateways for deterministic handoffs.  
- **Multi‑agent collaboration** with modular agent adapters.  
- **System integrations** via REST APIs and ERP/CRM connectors.  
- **Scalable cloud deployment** on UiPath Automation Cloud.

---

### UiPath Components
| Component | Purpose |
|-----------|---------|
| **UiPath Maestro** | BPMN 2.0 process modeling and orchestration |
| **UiPath Agent Builder** | Build modular agents and agent connectors |
| **UiPath Studio** | Author RPA workflows and coded automations |
| **UiPath Orchestrator** | Schedule and manage RPA robots |
| **UiPath Forms Action Center** | Human approvals and exception handling |
| **REST APIs and Connectors** | Integrate ERP, CRM, finance systems |
| **Cloud Deployment** | UiPath Automation Cloud for scalability |

---

### Agent Type and Architecture Overview
**Agent Type**  
This solution uses **both Coded Agents and Low‑code Agents**. Coded Agents are used where custom logic, external SDKs, or advanced LLM orchestration is required. Low‑code Agents and Agent Builder components are used for rapid integration and judgeable demos.

**Architecture Overview**  
- **Process Layer**: BPMN 2.0 flows in UiPath Maestro.  
- **Automation Layer**: UiPath Studio workflows executed by Orchestrator.  
- **Agent Layer**: Coded agents and low‑code agents via Agent Builder, LangChain/CrewAI/AutoGen adapters.  
- **Integration Layer**: REST APIs and ERP/CRM connectors.  
- **Human Layer**: UiPath Forms and Action Center for approvals and exceptions.

---

### Setup Instructions for Judging
**Prerequisites**
1. **UiPath Automation Cloud account** with access to Maestro, Agent Builder, Studio, and Orchestrator.  
2. **Git** and a local development environment (Windows recommended for UiPath Studio).  
3. **Credentials** for any target ERP/CRM test instances or mock endpoints.  
4. **Node/Python** runtime if any coded agents require local execution.

**Repository Layout**
- `README.md` (this file)  
- `maestro/` BPMN models and Maestro solution files  
- `agents/` coded agent source and low‑code agent configs  
- `rpa/` UiPath Studio projects and published packages  
- `integration/` API mocks and connector configs  
- `docs/` architecture diagrams and runbook  
- `submission/` deck and judging artifacts

**Step by Step Setup**
1. **Clone repository**
   ```bash
   git clone https://github.com/MiChaelinzo/FlowSync-Maestro.git
   cd FlowSync-Maestro
   ```
2. **Provision Maestro workspace**
   - Create or use an existing UiPath Automation Cloud tenant.
   - Import BPMN models from `maestro/` into UiPath Maestro.
3. **Register Agents**
   - Open UiPath Agent Builder and import agent definitions from `agents/`.
   - For coded agents, follow `agents/README.md` to install dependencies and start the agent service.
4. **Deploy RPA Packages**
   - Open UiPath Studio projects in `rpa/`, publish to Orchestrator, and create robot environments.
5. **Configure Integrations**
   - Update `integration/config.sample.json` with test endpoints and credentials; save as `integration/config.json`.
   - Start any local API mocks if provided.
6. **Wire Up Process Inputs**
   - In Maestro, configure process variables and connectors to point to Orchestrator queues, Agent endpoints, and API connectors.
7. **Run a Demo Scenario**
   - Use the provided sample data in `maestro/samples/` to start the BPMN process in Maestro.
   - Observe human tasks in Action Center, robot jobs in Orchestrator, and agent calls in logs.
8. **Verify Outcomes**
   - Confirm order creation, PO creation, invoice ingestion, and exception reconciliation flows complete as expected.
   - Capture screenshots or logs for judging evidence.

**Troubleshooting Tips**
- Check Orchestrator logs for failed jobs.  
- Validate agent endpoints with a simple curl request.  
- Use Maestro process trace to inspect gateway decisions and handoffs.

---

### Judging Submission Checklist
- **README.md** at repository root with Project Description, UiPath Components, Agent Type, and Setup Instructions.  
- **Working BPMN models** in `maestro/`.  
- **Agent code and configs** in `agents/` with clear run instructions.  
- **RPA projects** in `rpa/` published or with publish instructions.  
- **Integration config** and any mock endpoints in `integration/`.  
- **Submission deck** created using the required template and placed in `submission/Submission Deck.pptx`. Use this Google Slides template to prepare the deck:  
  [https://docs.google.com/presentation/d/1U_60smXuoY-9g_fVQCLZc_gKMDWYZ1_g/edit?slide=id.p1](https://docs.google.com/presentation/d/1U_60smXuoY-9g_fVQCLZc_gKMDWYZ1_g/edit?slide=id.p1)  
- **Demo evidence**: short video or screenshots showing Maestro process run, Action Center tasks, Orchestrator jobs, and agent logs. Place evidence in `submission/evidence/`.

**Judging Run Instructions**
1. Reviewer clones repo and follows Setup Instructions.  
2. Reviewer imports BPMN into Maestro and starts the provided sample process.  
3. Reviewer follows the process through Action Center, Orchestrator, and agent logs.  
4. Reviewer confirms the outcomes listed in `submission/expected_outcomes.md`.

---

### Contact and Next Steps
- **GitHub:** MiChaelinzo/FlowSync‑Maestro  
- **UiPath Studio Project:** Hackathon Workspace (see repo docs for link and access notes)  


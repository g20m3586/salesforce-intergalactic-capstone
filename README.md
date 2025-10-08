# Salesforce Capstone — Project Plan & Deliverables

> A working, step-by-step project plan, starter templates, and delivery checklist for the **Intergalactic Freight & Trade Corp.** capstone.

---

## Snapshot / Purpose

This document maps every capstone requirement to concrete work items, recommended implementation approaches, and starter code/metadata templates you can copy into your repo. Use it as your single source of truth while building, testing, and packaging the project for submission.

---

## Quick table of contents

1. Objectives & deliverables mapping
2. Milestones & suggested order
3. Data model (objects, fields, relationships)
4. Automation & Flow designs
5. Validation rules & Approval Process
6. Apex classes, Triggers & Asynchronous patterns (skeletons)
7. UI components — Visualforce, LWC, Aura (skeletons)
8. Testing strategy & sample test skeletons
9. Deployment & packaging (sf commands + GitHub structure)
10. Agentforce AI — approach for predictions & chatbot
11. Grading checklist & artifacts to submit
12. Milestone Documentation
13. Appendix: sample metadata & code snippets

---

# 1 Objectives & deliverables mapping

Each capstone **Section** is mapped to artifacts you should produce and where to keep them in your repo.

| Section                      | What to deliver                                                                               | Metadata / Files (suggested path)               |
| ---------------------------- | --------------------------------------------------------------------------------------------- | ----------------------------------------------- |
| 1. Salesforce Fundamentals   | Custom Lightning Experience, 1 AppExchange installed, security setup, 3 reports + 1 dashboard | `docs/`, `reports/`, `dashboards/`, `security/` |
| 2. Data Modeling             | Custom objects: Shipment, Cargo, CustomsDocument (junction) + picklists + duplicate rules     | `force-app/main/default/objects/*`              |
| 3. Automation                | 2 Validation Rules, Approval Process, Record-Triggered Flow(s)                                | `flows/`, `processes/`                          |
| 4. App Creation & Deployment | Lightning App & packaging using Org Dev Model + Package Dev Model                             | `sfdx-project.json`, `packaging/`               |
| 5. Developer Logic           | Apex classes/triggers, async processing                                                       | `force-app/main/default/classes/*`, `triggers/` |
| 6. UI                        | Visualforce page, LWC, Aura component                                                         | `lwc/`, `aura/`, `pages/`                       |
| 7. Testing & Deployment      | Apex tests (>=75%), deployment notes, use SFDX                                                | `tests/`, `docs/deployment.md`                  |
| 8. Agentforce AI             | Prediction model config, chatbot (Einstein/AI)                                                | `ai/` or `docs/ai.md`                           |

---

# 2 Milestones & suggested order (work sequentially)

**Milestone 0 — Prep (1 day)**

* Create GitHub repo and branch strategy (main, develop, feature/*).
* Enable Dev Hub in your production org and confirm sf CLI is installed.
* Create a scratch org definition file `config/project-scratch-def.json`.

**Milestone 1 — Data Model (2–3 days)**

* Create custom objects + fields + picklists.
* Create duplicate rules for Accounts & Contacts.
* Create essential page layouts and compact layouts.

**Milestone 2 — Business Logic (2–3 days)**

* Add validation rules.
* Build flows: shipment assignment, delayed shipment notification.
* Create Approval Process for discounts.

**Milestone 3 — Developer Items (3–4 days)**

* Apex classes (fuel cost, customs validation).
* Triggers (prevent deletion, auto-generate customs doc).
* Batch/Queueable for bulk processing.

**Milestone 4 — UI & Reports (2–3 days)**

* Visualforce summary page.
* LWC for shipment tracking (mock API polling).
* Aura component for quick cargo assignment.
* Build 3 reports + dashboard.

**Milestone 5 — Testing & Packaging (2 days)**

* Write Apex tests, ensure 75% coverage.
* Use Apex Replay Debugger on at least one bug.
* Create unlocked package and package version.

**Milestone 6 — AI & Final docs (2 days)**

* Configure prediction (Einstein or similar) and bot.
* Final documentation: data model diagram, flows, deployment notes.

---

# 12 Milestone Documentation

## Milestone 0 — Environment Setup & Project Initialization

### Objective

Prepare your Salesforce development environment and create the base project structure for the Intergalactic Logistics capstone.

### Steps Completed

1. **Salesforce CLI installation**

   ```bash
   sf --version
   ```

   Verified latest Salesforce CLI is installed.

2. **Dev Hub authentication**

   ```bash
   sf org login web --set-default-dev-hub --alias DevHub
   ```

   Successfully authenticated Dev Hub.

3. **GitHub repository creation and cloning**

   * Repository: `salesforce-intergalactic-capstone`
   * Cloned locally:

   ```bash
   git clone https://github.com/<username>/salesforce-intergalactic-capstone.git
   cd salesforce-intergalactic-capstone
   git init
   git add .
   git commit -m "Initial Salesforce project setup"
   git push -u origin main
   ```

4. **Project creation using sf CLI**

   ```bash
   sf project generate --name intergalactic_logistics --template standard
   ```

   Project folder structure created with `force-app/`, `config/`, `manifest/`, `sfdx-project.json`.

5. **Scratch org creation**

   ```bash
   sf org create scratch --definition-file config/project-scratch-def.json --alias Intergalactic_Scratch --duration-days 7 --set-default
   ```

   Scratch org `Intergalactic_Scratch` created and set as default.

6. **Open and verify scratch org**

   ```bash
   sf org open
   sf org display --target-org Intergalactic_Scratch
   ```

   Verified org access and connection.

7. **Deploy base metadata**

   ```bash
   sf project deploy start --source-dir force-app
   ```

   Deployment successful.

### Deliverables for Milestone 0

| Deliverable              | Status      |
| ------------------------ | ----------- |
| Salesforce CLI installed | ✅ Completed |
| Dev Hub authenticated    | ✅ Completed |
| Project created          | ✅ Completed |
| Git repo initialized     | ✅ Completed |
| Scratch org created      | ✅ Completed |
| Scratch org verified     | ✅ Completed |
| Base metadata deployed   | ✅ Completed |

---

This section is now ready to track Milestone 0 progress. Subsequent milestones (Data Modeling, Automation, Apex, UI, etc.) will follow with the same documentation structure for iterative tracking.

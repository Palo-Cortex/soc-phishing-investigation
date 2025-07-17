# SOC Phishing Investigation - Pre-Work

This repository contains reusable XSIAM playbooks, automation, and logic aligned with the "Phishing" use case in the SOC Framework. It accelerates detection, triage, and response to credential-harvesting and user-targeted attacks — especially those flagged early through behavioral or email telemetry.

## 📌 Overview

This use case centers around detecting and responding to alerts tied to the **MITRE ATT&CK tactic: Initial Access**. It leverages Palo Alto Networks XSIAM’s automation, analytics, and case grouping capabilities to streamline how security teams investigate potentially malicious email and identity-based threats.

## 🚀 Getting Started

### Step 1: Configure the Playbook Trigger

Set up a **Playbook Trigger** to automatically execute the appropriate logic when phishing-related alerts are detected.

Go To: Incident Response → Incident Configuration → Playbook Triggers

- **Trigger Name:** `EP_InitialAccess`
- **Type:** Entry Point Playbook
- **Playbook to Trigger:** `EP_InitialAccess`
- **Filter Criteria:**
  - Alert Field: `Mitre ATT&CK Tactic`
  - Condition: Equals `TA0001 - Initial Access`

> This ensures that alerts mapped to MITRE’s Initial Access stage — such as spearphishing links, attachments, or credential harvesting attempts — are routed directly into the appropriate investigative flow.

### Step 2: Entry Point Playbook Structure

The `EP_InitialAccess` playbook is designed to:

- Validate alert fidelity using starring or incident scoring
- Parse email and URL artifacts
- Correlate user activity and authentication context
- Pull domain, URL, and file reputation data
- Contain or disable user accounts if compromise is suspected
- Auto-close (SOC Optimization "Framework" Dependency) non-actionable incidents via auto-triage

## 🧠 Why This Matters

This playbook aligns with the **Transformation**, **Risk & Resiliency**, and **Automation** goals from the XSIAM FieldOps Model:

| Value Driver          | Capability Delivered                                           |
|----------------------|----------------------------------------------------------------|
| Transformation        | Analysts focus only on enriched, high-confidence cases         |
| Risk & Resiliency     | High-risk user activity is flagged and mitigated early         |
| Automation & Efficacy | Email parsing, enrichment, and user response are automated     |

## 🧪 Validation Tips

To validate the effectiveness of this configuration:

- Use **BYOS MITRE Lab** to simulate phishing techniques tied to Initial Access (e.g., spearphishing link, spearphishing attachment)
- Confirm that alerts trigger the correct playbook
- Track alert scoring, playbook execution rate, and case closure trends in the **Value Dashboard**

## 🧩 Dependencies

- SOC Optimization Framework (for Auto-Triage and Starring)
- MITRE Tactic Tagging (alert source must include ATT&CK mappings)

---

For support or questions, please reach out to the SOC Framework maintainers or your Palo Alto Networks Field team.

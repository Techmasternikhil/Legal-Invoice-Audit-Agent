# ⚖️ Legal Invoice Auditor: Multi-Agent Compliance System

An automated, intelligent pipeline built with the **Google Agent Development Kit (ADK)** to audit legal and professional services invoices for contract compliance and financial accuracy.

## 🎯 1. Problem Statement
In the legal sector, reviewing vendor invoices is a high-stakes, manual process. Law firms and corporations must cross-reference hundreds of line items against complex **External Client/Contract Rules** and **Internal Financial Controls**.

### The Challenge:
*   **Cost Leakage:** High error rates lead to overpayment on capped tasks or inflated rates.
*   **Time Consumption:** Analysts spend hours cross-referencing PDFs with static databases.
*   **Client Trust:** Disputes over non-compliant billing delay payments and damage relationships.

### Why Generative AI?
Traditional rule-based systems struggle with the unstructured text in invoice descriptions. AI Agents can interpret the *context* of a line item (e.g., distinguishing a "Dinner Expense" from a "Travel Expense") while applying deterministic financial logic.

---

## 🏗️ 2. Architecture & Agent Workflow
The system utilizes a **Sequential Multi-Agent Pipeline**. Each agent is a specialist, ensuring that reasoning is decoupled from data extraction and deterministic calculations.

### The Four-Agent Pipeline:
1.  **Intake Agent (Data Formatting):** Standardizes raw, unstructured invoice data (JSON/PDF) into a consistent schema.
2.  **Classification Agent (Data Mapping):** Maps task descriptions to internal client codes and compliance categories.
3.  **Compliance Agent (Core Tool-User):** The "engine" of the audit. It executes tool calls to verify data against external rules.
4.  **Output Agent (Reporting & Synthesis):** Translates technical violations into a professional, actionable summary for financial approvers.

---

## 🛠️ 3. Tech Stack & ADK Integration
*   **Core AI Engine:** Google Gemini 1.5 Flash (optimized for reasoning and function calling).
*   **Framework:** Google Agent Development Kit (ADK) / `google-generativeai` SDK.
*   **UI/Deployment:** Streamlit & Ngrok.
*   **Logic Layer:** Custom Python Tools for deterministic auditing.

### Integrated Custom Tools:
| Tool Name | Type | Function |
| :--- | :--- | :--- |
| `rules_engine_tool` | Python Function | Validates billed hours against contract-defined maximums. |
| `billing_data_tool` | Python Function | Compares billed rates against standard role-based rate cards. |

---

## 📺 4. Demo & Execution
The solution features a live Web UI where users can upload invoice data and receive an instant audit report.

<img width="1080" height="607" alt="image" src="https://github.com/user-attachments/assets/4574572f-6b01-4de9-9db0-8fbea80c37f7" />

<img width="1080" height="607" alt="image" src="https://github.com/user-attachments/assets/706dcd74-127d-445d-9a15-9b0ea5f37233" />

<img width="1080" height="607" alt="image" src="https://github.com/user-attachments/assets/225b946e-0965-4b1f-a6c7-8a16b46a0ece" />

<img width="1080" height="608" alt="image" src="https://github.com/user-attachments/assets/349309c5-713f-4c3d-98f5-bc496f270323" />

<img width="1080" height="607" alt="image" src="https://github.com/user-attachments/assets/a12d2bcd-8a13-4002-a6e3-43dbe6dd6b0b" />

### Scenario Example:
The agent identifies a **Junior Associate** billing **15 hours** (limit: 10) at **\$350/hr** (limit: \$200).
*   **Compliance Output:** `CRITICAL ERROR: Billed time exceeds max by 5.0 hours.`
*   **Recommendation:** `REJECT/REVIEW - Adjust rate to $200 and investigate overage.`


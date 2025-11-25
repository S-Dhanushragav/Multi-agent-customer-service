### Google AI Agents Course - Capstone Project
# Multi-agent-customer-service
This project implements a Hierarchical Multi-Agent System using the Google Agent Development Kit (ADK).

![Python](https://img.shields.io/badge/Python-3.10%2B-blue)
![Framework](https://img.shields.io/badge/Framework-Google%20ADK-green)
![Model](https://img.shields.io/badge/AI%20Model-Gemini%202.5%20Flash%20Lite-orange)

## Overview
This project implements a **Hierarchical Multi-Agent System** designed to replace rigid, rule-based customer support chatbots. Unlike traditional bots that rely on keyword matching (e.g., `if "refund" in text`), this system uses a **Router-Specialist architecture** powered by LLMs to semantically understand user intent and route tasks to the correct department.

Built using the **Google Agent Development Kit (ADK)** and **Gemini 2.5 Flash Lite**.

---

## Key Features
* **Intelligent Routing:** A "Root Agent" analyzes incoming queries and dynamically delegates them to specialized sub-agents (Billing vs. Tech Support).
* **Functional Tools:** Agents are equipped with Python-based tools (`check_refund_status`, `troubleshoot_device`) to simulate real-world database lookups and logic flows.
* **Observability:** Integrated `LoggingPlugin` provides real-time tracing of the agent's thought process, tool execution, and state transitions.
* **Efficient Model Usage:** Optimized to run on `gemini-2.5-flash-lite` for speed and cost-effectiveness.

---

## Architecture
The system follows a **Router-Specialist** pattern:

1.  **Root Router (Triage):** The entry point. It does not solve problems directly but acts as a dispatcher.
2.  **Billing Specialist:** A sub-agent equipped with financial tools to handle refunds, invoices, and order status.
3.  **Tech Support Specialist:** A sub-agent equipped with technical logic to troubleshoot device issues.

```mermaid
graph TD
    User[User Query] --> Root[Root Router Agent]
    Root -- "Intent: Money/Refund" --> Billing[Billing Specialist]
    Root -- "Intent: Broken Device" --> Tech[Tech Support Specialist]
    Billing --> Tool1[(check_refund_status)]
    Tech --> Tool2[(troubleshoot_device)]

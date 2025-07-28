# TillClear: Social Commerce Financial Documentation

[![Status](https://img.shields.io/badge/status-planning-orange)](#) <!-- Status will update as development progresses -->
<!-- [![License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE) --> <!-- Add LICENSE file later -->

**TillClear** aims to solve a critical problem for social commerce businesses in Kenya (and similar markets) who sell via WhatsApp and Instagram: **disconnected orders and payments lead to financial inaccuracies and reconciliation nightmares.**

This repository contains the foundational documentation for the TillClear project, starting with the Product Requirements Document (PRD). The goal is to build a no-code solution using tools like n8n, Kopokopo, and Zoho CRM to automate the link between a sale and its corresponding payment, ensuring accurate financial records from the moment a customer pays.

## The Core Problem

*   **Unverified Payments:** Payments received lack context – you know money came in, but not what product it was for.
*   **Delayed Documentation:** Manual entry into CRM after payment leads to errors and delays in financial reporting.
*   **Expense Verification Issues:** Business expenses paid from payment platform balances cannot be easily verified against actual sales.

## The Proposed Solution

TillClear introduces a simple staff dashboard (built with n8n forms) that forces staff to select the product *before* generating a payment request. This creates an immediate link.

Key concepts from the PRD:
*   **Mandatory Product Selection:** Ensures every payment is tied to a specific item.
*   **Automated Reference Generation:** Creates unique, traceable references (e.g., `TILL-SOC-DRESS-RED-M-20240515-123`) for each transaction.
*   **Real-time CRM Sync:** Draft records are created instantly, and finalized upon payment confirmation.
*   **Expense Tagging:** Differentiates between sales income and personal transfers for clearer expense tracking.

## Repository Contents (Initial Commit)

*   **[docs/prd/tillclear-prd.md](docs/prd/tillclear-prd.md):** The complete Product Requirements Document outlining the problem, solution overview, functional requirements, technical integrations, roadmap, and success metrics.

## Next Steps

This initial commit sets the stage. Future commits will include:
*   No-code workflow definitions (likely n8n JSON files).
*   Setup guides and configuration templates.
*   User training materials.
*   Implementation code/scripts (if any custom logic is needed beyond n8n).

Stay tuned as the project moves from planning into the build phase!

<!-- ## Getting Started (Future) -->
<!-- Instructions on cloning, setting up tools (n8n, Kopokopo, Zoho), and deploying workflows will be added here. -->

<!-- ## Contributing (Future) -->
<!-- Guidelines for contributing will be added if the project becomes collaborative. -->

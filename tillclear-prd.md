Product Requirements Document: TillClear
Version: 1.0
Date: May 16, 2024
Owner: Solo Founder (Itikadi)
Target Launch: 4 weeks (no-code implementation)
Status: Approved for Development

1. Executive Summary
Problem: Social commerce sellers using WhatsApp and Instagram face significant financial risks due to disconnected order and payment systems. Manual processes create critical gaps:

Payments lack product context in payment records
Delays between payment and order entry compromise financial accuracy
Business expenses paid from payment platform balances lack sales verification
Solution: TillClear automates the connection between social orders and payment records. It forces product verification at payment initiation, generates audit-ready references, and syncs to Zoho CRM within seconds of payment confirmation.

Defensibility: Solves Kenya's core financial reconciliation challenge for social sellers by linking payment platform transactions to specific products. Built exclusively for businesses using WhatsApp/Instagram sales channels with payment platform tills.

2. Problem Statement
Itikadi (and 12,000+ Kenyan SMEs) experience operational and financial risks due to:

Unverified Payments
Staff shares payment details → Customer pays → No product context in payment records
Payment records lack sales verification; financial reporting errors
Documentation Delays
Manual CRM entry 15-30 minutes after payment
Inaccurate financial records; reconciliation difficulties
Expense Verification
90% of business expenses paid from payment platform balances with no sales linkage
Inability to verify legitimate business expenses; financial reporting gaps
Core Business Need: Proof that each payment platform transaction corresponds to a specific sale. Current failure rate exceeds 95% for social commerce sellers. 

3. Solution Overview
TillClear provides a no-code staff dashboard that:

Requires product selection before payment initiation
Generates verifiable transaction references (e.g., TILL-SOC-DRESS-RED-M-20240515-123)
Creates draft CRM records at order initiation
Completes financial documentation within seconds of payment confirmation
Tags transactions as Sale or Personal Transfer for expense verification
Key Advantages:

Optimized for B2C social commerce (omits non-essential fields)
Creates immediate payment-to-product linkage
Verifies 90% of expenses against documented sales
Implemented using n8n + existing Kopokopo/Zoho infrastructure
4. Target User & Workflow
User Persona: Social Commerce Staff Agent
Role: Manages WhatsApp/Instagram orders
Pain Point: "I manually transfer order details to our CRM after payment, creating errors in our financial records."
Technical Proficiency: Basic smartphone literacy
Daily Volume: 10-20 social orders
Critical Workflow (60 seconds per order)
SVG content

5. Functional Requirements
A. Staff Dashboard (n8n Form)
Customer Phone
Phone
Auto-converts
07...
→
+2547...
Required for payment verification and customer records
Product
Dropdown
Syncs real-time from CRM inventory
Ensures product verification before payment initiation
Size/Color
Text
Pre-filled based on product selection
Completes sales documentation for accurate financial records
Transaction Type
Dropdown
Sale
(default) /
Personal Transfer
Enables proper expense verification for business operations
Payment Request Button
Button
Labeled: "Request Payment + Verify Product"
Creates immediate payment-to-product linkage
Delivery Notes
Text (Optional)
Auto-suggests location format
Streamlines delivery process without documentation burden
Critical Rules: 

Payment request button disabled until mandatory fields are complete
Personal Transfer selection skips payment request (for non-sales inflows)
Real-time verification status: "Product verified. Payment documentation ready."
B. Transaction Reference Generator
Format: TILL-SOC-{SKU}-{DATE}-{RANDOM}
Example: TILL-SOC-DRESS-RED-M-20240515-123
Generation Logic:
javascript


1
2
3
4
const sku = items[0].json.product.split('-')[0];
const sizeColor = items[0].json.size_color.replace(' ', '-');
const date = new Date().toISOString().slice(0,10).replace(/-/g, '');
const ref = `TILL-SOC-${sku}-${sizeColor}-${date}-${Math.floor(100 + Math.random() * 900)}`;
Business Value:
Payment processor records TILL-SOC-DRESS-RED-M... → CRM links to product → Complete sales documentation with payment verification 
C. CRM Sync (Financial Documentation)
Create Draft Sales Record
On form submission
Enables immediate payment verification
• Product SKU
• Size/Color
• Customer Phone
• Transaction Reference
Complete Sales Record
Payment confirmation webhook
Ensures accurate financial documentation
• Payment timestamp
• Status = "Completed"
Tag Transaction Type
From staff form
Verifies legitimate business expenses
• "Sale" or "Personal Transfer"
Generate Financial Report
Daily
Provides complete payment-to-sale verification
• % of payments with product verification
• Documentation accuracy rate
D. Website Order Sync (WooCommerce)
Purpose: Unified financial documentation (social + website)
Flow:
Website order triggers n8n webhook
Auto-tags as Sale (Transaction Type)
Syncs to CRM with standardized reference format
Uses payment processor transaction ID as reference
Critical Rule: Website orders follow same documentation standard as social orders
6. Non-Functional Requirements
Documentation
• B2C delivery field omitted
• Size/color mandatory
Streamlines staff workflow while ensuring complete sales records
Security
• Payment processor/CRM keys in n8n credentials manager
• No customer data stored outside CRM
Protects sensitive business information
Performance
• Payment request within 10 seconds of form submit
• CRM sync within 5 seconds of payment
Ensures accurate financial documentation
Cost
• n8n Cloud ($20/month)
• Payment processor transaction fees
Provides immediate ROI through time savings and financial accuracy
Usability
• Form completion under 60 seconds
• No training required
Ensures staff adoption and consistent documentation
7. Integrations (No-Code)
n8n
Core workflow engine
1 hour
n8n Cloud account
Kopokopo
Payment processing
30 minutes
API Key, Secret
Zoho CRM
Sales documentation
20 minutes
Auth Token, Organization ID
WooCommerce
Website order integration
15 minutes
Consumer Key, Secret
8. Out of Scope
Delivery address field for B2C transactions
Automated social media message scraping
Refund processing workflows
Multi-currency support
Customer-facing portal
Inventory synchronization to website platform
9. Success Metrics
Time per social order
< 60 seconds
Form submission logs
Staff efficiency
Documentation Verification
100%
Percentage of payments with product verification
Financial accuracy
Documentation Timeliness
0% delays
CRM record timestamp vs. payment time
Reliable financial reporting
Expense Verification
90%+
Percentage of expenses linked to documented sales
Verified business expenses
Staff Adoption
100%
Dashboard login frequency
Operational consistency
10. Implementation Roadmap
1. Setup (3 days)
• Connect payment processor + CRM in n8n
• Sync CRM product catalog to n8n dropdown
Founder
Week 1
2. Staff Dashboard (5 days)
• Build documentation-focused form
• Implement transaction reference generator
• Add verification status indicator
Founder
Week 2
3. CRM Sync (3 days)
• Draft record creation on form submit
• Complete record on payment confirmation
• Daily financial verification report
Founder
Week 3
4. Website Sync (2 days)
• Connect website webhook
• Standardize reference format
Founder
Week 3
5. Go Live (2 days)
• Staff training (15-minute video)
• Verify documentation accuracy on first 10 orders
Founder
Week 4
11. Defensibility Analysis
Competitive Differentiation
Payment Processors
Shows payment amounts without product context
Transaction references link payments to specific products
CRM Systems
Require order creation in CRM before payment
Captures product verification before payment initiation
Generic SaaS Tools
Built for website transactions only
Specialized for social commerce payment verification
Value Proposition
Pricing: KES 1,500/month (annual billing)
Value Statement: "Document every payment with its corresponding sale. Save 9+ hours weekly while ensuring complete financial records."
Lead Generation: Free Financial Documentation Analysis → "We found 12 payments without product verification in your records."
12. Critical Next Steps
Verify documentation gaps:
Audit Itikadi's last 10 orders:
Does each payment have verified product details?
Is documentation completed within minutes of payment?
Can expenses be verified against documented sales?
→ Documentation gaps confirm immediate business need.
Activate required tools:
Enable payment request feature in Kopokopo dashboard
Generate CRM API token
Sign up for n8n Cloud (starter plan)
Initial monetization:
Package n8n workflows as "Financial Documentation Kit" (KES 2,500)
Target businesses in Kenyan e-commerce communities
Business Opportunity: This is not merely a documentation tool—it is essential financial infrastructure for social commerce businesses. By verifying payment-to-sale connections, TillClear enables accurate financial operations and business growth. 

Implementation support available:

Complete n8n workflow configuration
Financial Documentation Gap Analysis template
Initial customer acquisition script
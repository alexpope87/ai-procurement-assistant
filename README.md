# AI Procurement Assistant

A lightweight AI-powered procurement workflow for SMEs.

## Business Problem

Small companies often compare supplier offers manually based on price, delivery time and budget constraints.

This process can be repetitive and inconsistent.

## Solution

The AI Procurement Assistant automates the first part of the purchasing decision process.

A user submits:

- Item
- Quantity
- Budget
- Deadline

The system:

1. receives the request through a webhook
2. stores it in Supabase
3. retrieves available suppliers
4. calculates total purchase cost
5. checks budget and delivery deadline
6. filters out unsuitable suppliers
7. uses Gemini AI to recommend the lowest-cost eligible supplier
8. stores the recommendation
9. returns the result to the frontend

If no supplier meets the requirements, the system returns a "No eligible supplier" result.

## Workflow

Lovable UI  
→ n8n Webhook  
→ Supabase  
→ Business Rules  
→ Supplier Filter  
→ Gemini AI  
→ Supabase Update  
→ Webhook Response  
→ Lovable UI

## Tech Stack

- n8n — workflow automation
- Supabase — database
- Google Gemini — AI recommendation
- Lovable — frontend
- Webhooks / REST APIs
- JSON

## Business Rules

A supplier is eligible only if:

- Total cost ≤ available budget
- Delivery time ≤ required deadline

Among eligible suppliers, the AI recommends the supplier with the lowest total cost.

Delivery time is used only as a secondary factor in case of equal cost.

## Example

Request:

- 10 ergonomic chairs
- Budget: €3,000
- Deadline: 30/10/2026

Result:

- Recommended supplier: Supplier C
- Total cost: €2,200
- Delivery: 14 days
- Status: Pending

## MVP Scope

This is a demonstration MVP designed to show how AI, APIs, workflow automation and business rules can be combined to support procurement decisions.

It does not include ERP integration, authentication or production-level supplier management.

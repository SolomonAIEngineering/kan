# How kan (kanbn) Fits on Top of Canvas + Billflow

Canvas and Billflow already own the **system of record** for finance work — invoices, vendors, banking, dunning, collections, approvals, reconciliation.

What they do not own is the **system of work**: who is chasing what, in what status, blocked by whom, and by when.

That work usually leaks into Slack threads, spreadsheets, and inboxes. **Kan is the right shape to absorb it.**

---

## The Core Insight

Both products produce a constant stream of state changes that are naturally card-shaped:

- **Canvas:** overdue invoices, collection cases, promises-to-pay, reconciliation exceptions, dunning escalations, contract renewals.
- **Billflow/Cadence:** captured invoices awaiting coding, items in approval, scheduled payments, 3-way-match exceptions, vendor onboarding tasks.

A kanban primitive — card, list, board, label, due date, assignee, activity — maps one-to-one to how AP/AR teams already describe their work on a whiteboard.

Kan can become the work surface that those state changes hydrate into.

---

## Concrete Board Patterns Canvas/Billflow Data Unlocks

| Board | Columns | Card Source | Hydrated From |
|---|---|---|---|
| **AR Collections Workbench** | New overdue → Outreach sent → Promise to pay → Settlement → Escalated → Written off | Auto-created from collection cases + overdue invoices | Aging bucket, last communication, payment pattern, tone-experiment arm |
| **AP Weekly Close** | Captured → Needs coding → In approval → Scheduled → Paid → Reconciled | Auto-created from Billflow invoice capture | Vendor, GL category suggestion, approver, bank match candidate |
| **Renewal Watchtower** | 90d out → 60d out → Decision needed → Renegotiating → Renewed/Cancelled | Auto-created from contract terms + auto-renewal windows | Contract doc, spend trend, owner, cancellation deadline |
| **Reconciliation Exceptions** | Unmatched → Investigating → Awaiting vendor → Resolved | Auto-created from match-engine confidence misses | Bank transaction, invoice candidate, confidence score, prior matches |
| **Vendor Onboarding** | Requested → Diligence → W-9/Banking → Approved → Active | Auto-created from new vendor request | KYB status, risk signals, payment terms |
| **Month-End Close** | Recurring template board with accruals, JE reviews, account reconciliations | Templated per period, auto-populated from open items | Bank balances, unposted transactions, unreviewed categorizations |
| **Audit Prep** | Request received → Evidence gathered → Reviewed → Submitted | Auditor PBC list | Auto-attached invoices, contracts, bank statements |

---

## What Makes kan + Canvas/Billflow Defensibly Better Than Trello/Linear

### 1. Bidirectional State Binding

Moving a card to **“Paid”** triggers the actual payment in Billflow. Recording a payment in Canvas auto-moves the card.

The board is not a shadow copy — **it is the workflow**.

### 2. Auto-Card Creation From Real-World Events

New overdue invoice → card.  
Reconciliation exception → card.  
Auto-renewal 60 days out → card.

The board never goes stale because the underlying ledger feeds it.

### 3. Cards Are Live Financial Objects

Each card carries aging, communication thread, payment history, attached documents, and vendor risk — pulled from Canvas/Billflow, not retyped.

### 4. Policy-Aware Automations

Card transitions can fire Canvas dunning steps, Billflow approval routing, or workflow-engine DAG nodes.

The engine already exists.

---

## Positioning

I would position kan not as a Trello alternative, but as:

> **The work surface for finance teams. Powered by your real invoice, vendor, and banking data — not another spreadsheet to keep in sync.**

### Segment-Specific Variants

- **For controllers/AP managers:**  
  The kanban for accounts payable. Every invoice is a card, every approval is a swimlane, every payment closes the loop automatically.

- **For collections leads:**  
  Your collections workbench in board form. Cases, promises, settlements — all wired to real-time aging and communication history.

- **For finance ops/RevOps:**  
  The shared canvas where finance, sales, and legal coordinate on revenue and spend — backed by the actual ledger, not a copy of it.

---

## Why This Matters Strategically for Oppulence

### Sticky Surface

Once a team runs their weekly close from a kan board hydrated by Canvas/Billflow, ripping it out means losing both products.

### Cross-Functional Pull-Through

Kan boards are how non-finance people — sales asking about a deal’s invoice, legal reviewing a renewal, ops onboarding a vendor — touch financial data without needing a Canvas/Billflow seat.

That creates a natural expansion path.

### Open-Source Distribution Wedge

Self-hosted kan with optional Canvas/Billflow connectors is a credible bottom-up GTM motion, while Canvas and Billflow remain top-down sales-led products.

### Differentiator vs. Ramp/Brex/Bill.com

Ramp, Brex, and Bill.com are systems of record with weak collaboration surfaces.

Oppulence + kan would be an AP/AR stack with a real work-tracking layer built in.

---

## The Honest Tradeoff

Kan’s codebase will need:

- A connector framework
- Webhook ingestion
- A managed-card concept

A **managed card** means a card owned by an external system and partially read-only.

That is real work, but it is a tractable surface area. Canvas already has the workflow engine and webhook event log to plug into.

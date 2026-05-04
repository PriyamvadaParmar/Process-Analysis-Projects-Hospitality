# Process Optimization Case Studies: Hospitality Operations

This document outlines the operational transformation of F&B and Guest Services through process mapping and workflow re-engineering.

---

## 1. F&B Operations Optimization (The Westin / Cafe Hotspot)
**Focus:** Cross-functional coordination and communication efficiency.

### AS-IS Process (Baseline)
The initial state was characterized by manual dependencies and high friction between the floor and kitchen.


| Step | Current Activity | Pain Point / Gap | Impact |
| :--- | :--- | :--- | :--- |
| **Order Entry** | Handwritten notes or verbal orders. | Illegible handwriting; memory lapses. | Incorrect items served. |
| **Kitchen Sync** | Physical delivery of paper tickets. | Tickets lost or delayed in transit. | Long wait times. |
| **Prep Flow** | "First-in, first-out" with no priority. | VIP or urgent orders delayed. | Guest dissatisfaction. |
| **Coordination** | Manual shouting or checking by staff. | High noise; miscommunication. | Dish cooling on counter. |
| **Billing** | Manual entry from paper slips. | Human error during data entry. | Billing disputes. |

### TO-BE Process (Optimized)
The future state utilizes digital integration to ensure real-time accuracy and accountability.

```mermaid
graph TD
    A[Digital POS Entry] -->|Instant Sync| B[Kitchen Display System - KDS]
    B --> C{Priority Algorithm}
    C -->|High| D[Express Prep Lane]
    C -->|Standard| E[Standard Queue]
    D & E --> F[Automatic 'Ready' Alert to Server]
    F --> G[Service Delivery]
    G -->|Auto-Push| H[One-Click Billing]
```

---

## 2. Guest Services & Concierge (Hotel Sayaji)
**Focus:** Complaint management and CX workflows.

### AS-IS Process (Baseline)
Workflows lacked a centralized tracking mechanism, leading to "forgotten" requests and inconsistent quality.

*   **Gap 1:** No categorization of requests (VIP vs. General).
*   **Gap 2:** Reliance on verbal handovers between shifts.
*   **Gap 3:** Lack of escalation; issues remained unresolved for hours.

### TO-BE Process (Optimized)
A structured request management framework with built-in accountability.

1.  **Categorization:** Requests tagged as **VIP**, **Urgent**, or **Standard** at entry.
2.  **Real-Time Tracking:** Centralized dashboard visible to Concierge and Management.
3.  **Escalation Matrix:** 
    *   *Level 1:* 15 mins (Duty Manager Alert)
    *   *Level 2:* 30 mins (Department Head Alert)
4.  **Feedback Loop:** Automated guest follow-up post-resolution.

---

## Summary of Impact
- **Efficiency:** 25%+ reduction in order/request turnaround time.
- **Accuracy:** Significant decrease in billing errors and "re-fire" kitchen orders.
- **CSAT:** Improved Guest Satisfaction scores through consistent service delivery.

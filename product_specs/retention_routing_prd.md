**File 2_1: retention_routing_prd.md**

# **Product Requirements Document (PRD): Automated Support Escalation & Retention Intercept**

**Role:** Associate Product Owner / Business Analyst  
**Status:** Case Study PRD (Backed by Historical Dataset Baseline)

## **1. Problem Statement & Business Case**

Our OTT streaming platform is currently experiencing an unsustainable overall subscriber churn rate of 28.57% (putting \$73.94 in MRR at risk), threatening significant revenue. Analysis reveals clear operational and product drivers behind this attrition:

- **The Support Escalation Bottleneck:** Support ticket escalations represent a critical failure point, affecting 19.05% of users. Escalations are highly correlated with churn (r \= 0.63); affected users experience severe drops in Customer Satisfaction (CSAT down to 10-20) and frequently defect to competitors.

- **Plan & Channel Vulnerability:** Churn is disproportionately high in the Basic plan tier (60.00%) and among subscribers acquired via the Referral channel (83.33%), indicating foundational issues with perceived value or user onboarding in these segments.

**The Solution:**  
We must shift from reactive support to proactive retention. By implementing an automated escalation workflow that intercepts high-risk accounts in real time, we can empower retention specialists to resolve friction before cancellation occurs.

## **2\. Target User Personas & Pain Points**

| Persona                                                       | Current Pain Point (As-Is)                                                                                                                            | Desired Outcome (To-Be)                                                                                                           |
| :------------------------------------------------------------ | :---------------------------------------------------------------------------------------------------------------------------------------------------- | :-------------------------------------------------------------------------------------------------------------------------------- |
| **Service-Frustrated Subscriber** (High Churn Risk, Low CSAT) | Experiences unresolved friction, gets stuck in standard queues, logs multiple complaints, and ultimately switches to a competitor out of frustration. | Immediately prioritized and routed to a P1-Retention specialist empowered with service credit or refund authority.                |
| **Price-Sensitive Basic User** (Basic Plan, High Churn)       | Finds the plan value insufficient relative to the cost and initiates cancellation citing "Too expensive".                                             | Presented with a tailored intercept offer, such as a 30-day billing pause or promo modal, before final cancellation is processed. |

## **3\. To-Be Automated Workflow Strategy**

We will move away from a standard First-In, First-Out (FIFO) support model to a risk-aware, prioritized routing system.

- **Proactive Risk Scoring:** Every incoming support ticket will trigger an automated churn risk evaluation based on complaint history and current CSAT scores.

- **Priority Escalation (P1-Retention):** Tickets associated with a history of escalations, repeated complaints (\>= 2), or critically low CSAT (\<= 20\) will bypass standard queues. They will be immediately routed to dedicated P1-Retention specialists.

- **Dynamic Cancellation Intercept:** If a user initiates the cancellation flow, the system will capture their stated reason (e.g., "Too expensive" vs. "Switched to competitor") and present a highly targeted retention offer designed to address that specific concern before the account is closed.

## **4\. Cancellation-Intercept Decision Logic**

To protect MRR effectively, intercept offers must be tailored to the specific reason for cancellation, rather than offering generic discounts to everyone.

| Stated Cancellation Reason   | Subscriber Profile                  | Targeted Retention Offer                               | Strategic Goal                                                                                                       |
| :--------------------------- | :---------------------------------- | :----------------------------------------------------- | :------------------------------------------------------------------------------------------------------------------- |
| **"Too expensive"**          | Basic or Standard Plan              | **20% Off Next 2 Months** OR **Switch to Annual Plan** | Directly addresses price sensitivity and encourages longer-term commitment.                                          |
| **"Switched to competitor"** | History of Complaints / Escalations | **30-Day Free Billing Pause** \+ **Priority Callback** | Attempts to salvage relationships damaged by unresolved technical or service issues.                                 |
| **"Switched to competitor"** | No Complaints (Basic Plan)          | **Free 14-Day Upgrade Trial** (Standard/Premium)       | Addresses potential content dissatisfaction by showcasing the higher-tier catalog where churn is demonstrably lower. |

### **Core SaaS Metrics Tracked**

- **MRR Churn Rate**
- **Customer Satisfaction Score (CSAT)**
- **Save Rate**
- **Contraction MRR**

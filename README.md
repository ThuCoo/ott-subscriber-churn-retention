# **OTT Subscriber Churn Analysis & Automated Retention Workflow PRD**

**Role Focus:** Business Analysis \| Product Ownership  
**Quick Navigation:**

- [Executive Problem Statement & Revenue at Risk](#1-executive-problem-statement--revenue-at-risk)
- [Root Causes of Subscriber Churn](#2-root-causes-of-subscriber-churn)
- [Proposed Automated Retention Workflow](#3-proposed-automated-retention-workflow)
- [Agile User Stories & Northstar Metrics](#4-agile-user-stories--northstar-metrics)

## **1\. Executive Problem Statement & Revenue at Risk**

High subscriber attrition is currently threatening recurring revenue across our regional Over-The-Top (OTT) streaming plans. By analyzing customer, subscription, and support data, this project uncovers the primary drivers of subscriber drop-off and outlines an Automated Support Escalation & Cancellation-Intercept Strategy to mitigate this loss.

**Business Impact & Opportunity Sizing:**

- **The Problem:** The platform is experiencing a high overall churn rate of 28.57% (retention rate of 71.43%) across an average \$18.85 ARPU. This places \$73.94 in MRR at risk, representing 18.68% of total monthly charges.

- **The Opportunity:** Over 80% of support-driven cancellations are tied to high-risk accounts or escalated complaints. Implementing an automated retention routing workflow could achieve a conservative 20–33% save rate on these accounts, potentially reducing the overall platform churn rate from 28.57% to \~19.0–22.8%.

## **2\. Root Causes of Subscriber Churn**

Our exploratory data analysis identified three critical bottlenecks driving subscriber cancellation:

- **Support Escalation & Low CSAT Bottleneck:** Support ticket escalations affect 19.05% of users and exhibit a 0.63 positive correlation with churn risk scores. Customers experiencing escalations report severe drops in Customer Satisfaction (CSAT scores plummeting to 10–20 out of 100). These users frequently cancel shortly after, citing reasons like "Switched to competitor" and "Too expensive".

- **Plan Tier Vulnerability:** Attrition is heavily concentrated in the Basic plan tier, which suffers a 60.00% churn rate—more than 2.7x the rate of Standard (22.22%) and 4.2x the rate of Premium (14.29%) plans. This indicates significant price sensitivity or perceived value issues at the entry level.

- **Acquisition Channel Disparities:** Segmenting by acquisition channel reveals that Referral sign-ups suffer an alarmingly high 83.33% churn rate, compared to significantly lower rates for Paid (16.67%) and Organic (0.00%) users.

## **3\. Proposed Automated Retention Workflow**

Currently, support complaints enter a standard First-In, First-Out (FIFO) queue, ignoring subscriber churn risk or CSAT scores. We propose transitioning to a proactive, automated escalation workflow that intercepts high-risk accounts in real time.

**To-Be Workflow Logic:**

| Triggering Condition                                     | Subscriber Profile             | CRM System Action                                | Retention Offer Strategy                          | Business Rationale                                                                                  |
| :------------------------------------------------------- | :----------------------------- | :----------------------------------------------- | :------------------------------------------------ | :-------------------------------------------------------------------------------------------------- |
| **Escalated Ticket** OR **Multiple Complaints (\>= 2\)** | Basic Plan or Referral Channel | Route to **P1-Retention Queue**                  | 30-Day Free Billing Pause or 1-Month 20% Discount | Addresses high price sensitivity and immediate frustration to prevent defection.                    |
| **Escalated Ticket** OR **Very Low CSAT (\<= 20\)**      | Standard / Premium Plan        | Route to **P1-Retention Queue** \+ Refund Review | 1-Month Service Credit or Plan Downgrade Option   | Preserves high-value relationships by offering immediate service recovery or flexible plan options. |
| **First Complaint** (No Escalation)                      | Medium Churn Risk              | Route to **P2-Priority Queue**                   | Automated Post-Resolution CSAT Check-In           | Provides proactive care to prevent minor issues from escalating into major dissatisfaction.         |

## **4\. Agile User Stories & Northstar Metrics**

### **Key User Story: Automated P1-Retention Ticket Routing**

- **As a** Customer Support Operations Lead,
- **I want** the CRM system to automatically flag and prioritize subscribers whose support tickets are escalated, who log repeated complaints, or who exhibit a high churn risk score (\>= 70),
- **So that** our retention specialists can proactively resolve service or billing friction _before_ the subscriber cancels and switches to a competitor.

### **Business Metrics Framework (SaaS / Subscription)**

To measure the success of the Automated Retention Workflow, we will track the following standard SaaS metrics:

| Metric Category     | Northstar Metric                       | Target Objective                                                                                                                                       |
| :------------------ | :------------------------------------- | :----------------------------------------------------------------------------------------------------------------------------------------------------- |
| **North Star KPI**  | **MRR Churn Rate**                     | Reduce churned MRR (baseline \$73.94) by 20%+ through proactive ticket intervention and targeted retention offers.                                     |
| **Operational KPI** | **Customer Satisfaction Score (CSAT)** | Lift post-escalation CSAT scores significantly above the current baseline (10–20) via specialized senior agent routing.                                |
| **Retention KPI**   | **Save Rate**                          | Track the percentage of users entering the cancellation flow who accept an intercept offer (e.g., 30-day pause) instead of completing the churn event. |
| **Guardrail KPI**   | **Contraction MRR**                    | Monitor the revenue lost to downgrades and 20% discounts to ensure margin preservation on salvaged accounts.                                           |


---

# Customer Lifetime Value CLV Analytics Dashboard

<img width="1027" height="577" alt="image" src="https://github.com/user-attachments/assets/d4936d07-3715-4321-9309-94f88d5af62c" />


---

## Navigation

- [Executive Summary](#executive-summary) 
- [Business Problem](#business-problem) 
- [Executive Questions Solved](#executive-questions-solved)
- [Dataset](#dataset)
- [Data Preparation](#data-preparation) 
- [Data Model](#data-model)
- [DAX Measures](#dax-measures)
- [Dashboard KPIs](#dashboard-kpis) 
- [Dashboard Design (Business Problem -> Analysis -> Insights & Recommendations -> Action)](#dashboard-design-business-problem---analysis---insights--recommendations---action)
- [Executive Business Insights](#executive-business-insights) 
- [Actionable Business Recommendations](#actionable-business-recommendations) 
- [Business Value Delivered](#business-value-delivered)
- [Tools & Skills Used](#tools--skills-used)

---

## Executive Summary
This work is as an executive-level **Customer Lifetime Value (CLV / LTV)** analytics solution built in Power BI to help leadership understand which customers create durable economic value and which customers dilute profitability over time. Rather than treating all customers as equally valuable, the dashboard positions customer analysis around lifetime contribution, customer-level profitability, and strategic resource allocation. 

The core business objective is to support smarter growth decisions by identifying profitable customers, surfacing low-value or unprofitable relationships, and translating customer economics into practical retention and commercial actions. This makes it a premium business case study.

---

## Business Problem
Many businesses track revenue and customer counts but lack a clear view of how much value customers actually generate over their lifecycle. Without a customer lifetime value lens, leadership can overinvest in low-value customer segments, underinvest in profitable customers, and make retention or acquisition decisions with incomplete economics. 

This dashboard addresses that gap by calculating both **overall CLV** and **customer-level CLV**, enabling stakeholders to distinguish between profitable and unprofitable customers and to make more disciplined decisions around retention, prioritization, and future growth strategy. 

---

## Executive Questions Solved
- What is the overall customer lifetime value of the current customer base? 
- Which customers generate the highest long-term value? 
- Which customers appear unprofitable or strategically weak? 
- How should leadership prioritize customer retention and growth efforts based on value creation? 
- How can customer economics be translated into a decision-ready dashboard for executive review? 

---

## Dataset
The Power BI project focused on calculating CLV using a practical formula and extending the analysis to the customer level. It is designed to identify profitable and unprofitable customers, implying a transactional customer dataset with sufficient fields to calculate revenue contribution and customer-level lifetime value. 

At minimum, the analytical structure is centered on customer-linked sales behavior and profitability logic, which makes it appropriate to position as a **customer profitability analytics** use case rather than a purely descriptive reporting exercise. 

---

## Data Preparation

During exploratory review, I identified three data quality issues that needed to be addressed before modeling: blank customer IDs, negative quantities, and zero unit prices. Blank customer IDs were removed because they could not be associated with any customer. Negative quantities were filtered out as return transactions, and zero unit prices were excluded because they were not valid for revenue analysis. After these cleaning steps, the dataset was ready for modeling and deeper analysis.

- ### **Blank Customer ID**:
During the initial data review, I found that the Customer ID column contained blank values in several rows. Since these records could not be linked to a specific customer, they were excluded from the final dataset.
<img width="1291" height="824" alt="image" src="https://github.com/user-attachments/assets/8d86ec7e-2655-4e5b-b046-b1d0adb7ea85" />

- ### **Negative Quantity**:
While checking the transaction data, I noticed multiple rows with negative values in the Quantity column. These represented returned transactions, so they were removed because they did not contribute to revenue analysis.
<img width="841" height="819" alt="image" src="https://github.com/user-attachments/assets/37dc888f-5fc1-4f22-9e3f-1ca57ec6fb3c" />

- ### **Zero Unit Price**:
I also identified rows where Unit Price was recorded as zero. Since a zero price is not meaningful for sales analysis, these records were filtered out to maintain data quality and accuracy.
<img width="925" height="817" alt="image" src="https://github.com/user-attachments/assets/dd03a08e-7def-498b-8d66-d12fd2f3d543" />

- ### **Final Modeling Dataset**:
After applying these cleaning steps, the dataset was refined and prepared for modeling and further analysis.
<img width="1919" height="817" alt="image" src="https://github.com/user-attachments/assets/25e0e09a-5de9-493b-b4f9-00adf78516a9" />

This required preparing customer-linked transaction data in Power BI so that customer-level revenue and lifetime value can be calculated consistently. In executive portfolio language, this stage can be presented as shaping raw customer and sales data into a decision-ready analytical model that supports both overall CLV and customer-level value segmentation. 

It has practical DAX-driven CLV calculation and customer-level analysis, the data-preparation layer is described as enabling profitability attribution, customer-level aggregation, and dashboard-ready filtering rather than as simple file import work. 


---

## Data Model

The model is designed to answer leadership questions about customer value creation, not just to compute a metric. 

4 new calculated columns were created to aid the model building for better answering of business problem statements at hand. Those are as follows - 

- ### **First Invoice Date**: The earliest invoice date recorded for each customer.
<img width="1442" height="259" alt="image" src="https://github.com/user-attachments/assets/f1711ce3-712d-4103-b568-cf03e2212cab" />

- ### **Last Invoice Date**: The most recent invoice date recorded for each customer.
<img width="1551" height="262" alt="image" src="https://github.com/user-attachments/assets/e2e218af-f188-4b2d-a439-bed2e9f729d6" />

- ### **Customer Lifespan (Days)**: The total number of days between a customer’s first and last invoice dates.
<img width="1566" height="290" alt="image" src="https://github.com/user-attachments/assets/848886ec-62ee-4413-b29d-a6c72ad71ff9" />

- ### **Customer Lifespan (Years)**: The customer’s total active period expressed in years instead of days.
<img width="1455" height="266" alt="image" src="https://github.com/user-attachments/assets/72ec3762-a801-44c7-9aa7-442353dc7d5c" />

The model is positioned as a customer-centric analytical structure where transaction-level performance rolls up to the customer level, allowing both aggregate CLV and per-customer CLV measurement. In executive terms, the model supports customer profitability visibility by connecting sales behavior to customer entities in a way that can be sliced, ranked, and interpreted for business action. 

- ### **Model**:

<img width="342" height="595" alt="image" src="https://github.com/user-attachments/assets/74efc144-6436-4b7a-8ea1-6810e7efba7b" />


---

## DAX Measures
The scope confirms two central analytical outputs: **overall CLV** and **CLV by customer**. These are positioned as the primary measures that convert customer transaction behavior into a strategic profitability metric for executive decision-making. 

- ### **Total Revenue**: Total sales generated from all customer purchases during the selected period. 
<img width="271" height="85" alt="image" src="https://github.com/user-attachments/assets/47b1a7b4-8227-40cb-a921-c3ec49653d3d" />

- ### **Total Transactions**: Total number of completed purchase orders in the selected period. 
<img width="321" height="87" alt="image" src="https://github.com/user-attachments/assets/69124f23-94d7-4461-b2ea-91dfa2c07332" />

- ### **Total Customers**: Total unique customers who made at least one purchase in the selected period. 
<img width="342" height="84" alt="image" src="https://github.com/user-attachments/assets/78fa4547-bae3-4f41-a296-1296b1f0f91d" />

- ### **Average Customer Lifespan (Days)**: Average number of days a customer stays active between first and last purchase.
<img width="376" height="84" alt="image" src="https://github.com/user-attachments/assets/7a696dcc-fbb7-474c-879b-f6d4a722aa3f" />

- ### **Average Customer Lifespan (Years)**: Average customer lifespan expressed in years instead of days.
<img width="392" height="80" alt="image" src="https://github.com/user-attachments/assets/c0f3239a-5625-4b03-a98c-7dfdf1ac5c87" />

- ### **Average Purchase Value**: Average amount spent per transaction across all customers.
<img width="318" height="83" alt="image" src="https://github.com/user-attachments/assets/747b8f4f-af26-4547-bc9a-1defc7b4b156" />

- ### **Average Purchase Frequency**: Average number of purchases made by each customer in the selected period.
<img width="236" height="151" alt="image" src="https://github.com/user-attachments/assets/aef2fbc2-99a9-4253-96ad-3034b55fc46e" />

- ### **Gross Margin**: Revenue remaining after subtracting the direct cost of goods sold.
<img width="463" height="271" alt="image" src="https://github.com/user-attachments/assets/b3d296a1-009b-443a-b8c5-31677abd7646" />

- ### **Customer Acquisition Cost (CAC)**: Average cost required to acquire one new customer.
<img width="468" height="275" alt="image" src="https://github.com/user-attachments/assets/aaaf0dd5-96f5-48a2-88f5-43af45422428" />

- ### **Customer Lifetime Value (CLV)**: Estimated total revenue a customer generates over their entire relationship with the business. 
<img width="1104" height="80" alt="image" src="https://github.com/user-attachments/assets/470dab84-9c22-4c49-a391-5905a55b5647" />

  

---

## Dashboard KPIs
The dashboard is professionally framed around the following KPI layer:
- ### **Total Revenue**
<img width="228" height="76" alt="image" src="https://github.com/user-attachments/assets/60f41941-ad81-42ab-aea6-96848699c77a" />

- ### **Total Transactions**
<img width="179" height="77" alt="image" src="https://github.com/user-attachments/assets/cfcf2121-0894-413e-b9f1-5f37ecb4afcd" />

- ### **Total Customers**
<img width="162" height="77" alt="image" src="https://github.com/user-attachments/assets/8999b2e5-beaa-463e-b23b-04033c477045" />

- ### **Average Customer Lifespan (Days)**
<img width="244" height="78" alt="image" src="https://github.com/user-attachments/assets/a2db3743-a887-4308-9f7c-98e7e64677ee" />

- ### **Average Customer Lifespan (Years)**
<img width="224" height="75" alt="image" src="https://github.com/user-attachments/assets/e42b8d50-cf69-4d0e-b2c2-3aca4a7e4287" />

- ### **Average Purchase Value**
<img width="231" height="80" alt="image" src="https://github.com/user-attachments/assets/4ee5929a-8804-44b9-9b3c-5319524a84a7" />

- ### **Average Purchase Frequency**
<img width="185" height="78" alt="image" src="https://github.com/user-attachments/assets/83d70a2e-955a-4412-9885-421cc26758fb" />

- ### **Gross Margin**
<img width="159" height="80" alt="image" src="https://github.com/user-attachments/assets/8380e269-5a9f-4c75-8309-9126896d1813" />

- ### **Customer Acquisition Cost (CAC)**
<img width="245" height="77" alt="image" src="https://github.com/user-attachments/assets/8750689f-6ac0-4489-9f57-98f4bb5e371d" />

- ### **Customer Lifetime Value (CLV)**
<img width="227" height="78" alt="image" src="https://github.com/user-attachments/assets/d910ee40-9bcd-40c0-96c0-1d7443329c1a" />

These KPIs create an executive scorecard that shifts reporting from raw activity metrics toward **customer economics** and long-term value creation. 

---

## Dashboard Design (Business Problem -> Analysis -> Insights & Recommendations -> Action)
The strongest executive design narrative for this project is: 

Dashboard is be presented as moving through a simple but leadership-relevant story: first quantify lifetime value, then compare customers based on economic contribution, then identify where attention, retention effort, and commercial investment should be focused. 

## Visual-by-Visual Executive Framing
It is a complete CLV dashboard and customer-level profitability analysis, hence the visuals are framed in an executive way as follows.

### 1. Overall CLV KPI
- **Visual title:** Overall Customer Lifetime Value
- **Business question:** What is the average long-term value generated by the current customer base? 
- **Business insight:** This KPI establishes the economic benchmark for understanding how valuable the average customer relationship is over time. 
- **Executive decision:** Use this value as a baseline for evaluating acquisition efficiency, retention strategy, and customer portfolio quality.

<img width="1021" height="202" alt="image" src="https://github.com/user-attachments/assets/d15f6955-a439-4ae3-b397-766c4e98a7b3" />


### 2. Customer-Level CLV View
- **Visual title:** CLV by Customer
- **Business question:** Which individual customers are creating the highest and lowest lifetime value? 
- **Business insight:** A customer-level CLV ranking reveals which customers are disproportionately driving value and which customers contribute little or negative strategic value. 
- **Executive decision:** Prioritize retention, service quality, and upsell opportunities for high-value customers while reviewing low-value segments for cost control or repositioning.

<img width="1023" height="335" alt="image" src="https://github.com/user-attachments/assets/d6faf558-7595-4cb6-b473-084e4e5b4a2e" />


### 3. Profitable vs Unprofitable Customer Analysis
- **Business question:** How much of the customer base is genuinely profitable, and where are value-destructive relationships emerging? 
- **Business insight:** This view separates the customer base into profitable and unprofitable groups, making the economics of the portfolio more visible than customer count alone. 
- **Executive decision:** Reduce blanket retention spending and move toward profitability-led segmentation and intervention. 

### 4. Customer Portfolio Prioritization View
- **Business question:** Which customers deserve greater strategic attention based on long-term value? 
- **Business insight:** Value-based segmentation helps leadership identify where premium service, loyalty initiatives, and account development resources should be concentrated. 
- **Executive decision:** Build targeted retention and growth programs around the highest-value customers instead of treating the entire base uniformly. 

---

## Executive Business Insights
- Not all customers contribute equally to long-term business value, so customer count alone is a weak decision metric compared with CLV-based analysis. 
- Customer-level CLV analysis helps reveal where retention effort is economically justified and where it may be overallocated. 
- Profitability classification creates a stronger basis for strategic customer management, especially when deciding where to invest in loyalty, service, or cross-sell initiatives. 
- A CLV-driven dashboard enables leadership to think in terms of customer economics rather than short-term sales activity. 

---

## Actionable Business Recommendations
1. **Prioritize high-CLV customers** for retention, account management, and loyalty programs because they generate outsized long-term value. 
2. **Review low-CLV or unprofitable customers** to identify whether they can be improved through targeted offers, pricing changes, or service redesign. 
3. **Use CLV as a strategic planning metric** alongside revenue so growth decisions reflect customer quality, not just customer volume. 
4. **Align acquisition strategy with lifetime value** by focusing on customer types that are more likely to become profitable over time. 
5. **Operationalize profitability segmentation** across retention and upsell campaigns to improve return on commercial investment. 

---

## Business Value Delivered
This dashboard transforms customer transaction behavior into an executive-level decision framework for measuring long-term customer value and profitability. Instead of reporting only how many customers exist or how much revenue has been booked, the solution helps leadership understand which customers are actually worth growing, retaining, and investing in. 

From a portfolio perspective, this work combines Power BI, DAX, customer analytics, and executive storytelling into a business-oriented analytics deliverable. 

---

## Tools & Skills Used
- **Power BI Desktop** for data modeling, DAX, and dashboard design. 
- **DAX** for CLV calculation and customer-level value analysis. 
- **Customer Analytics** for profitability analysis and value-based segmentation. 
- **Business Intelligence Storytelling** for translating metrics into executive decisions. 

---
 

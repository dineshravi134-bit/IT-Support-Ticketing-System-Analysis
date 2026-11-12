📊 IT Support Ticketing System Analysis

An end-to-end data analytics project transforming raw IT service desk records into actionable business intelligence using Microsoft Excel and Power BI.

📋 Project Overview

This project cleans, models, and visualizes 500 IT support ticket records (spanning 2023–2026 across 30 attributes) to evaluate service desk performance, technician productivity, asset reliability, and user satisfaction. The goal is to help IT management identify operational bottlenecks, optimize resource allocation, and improve campus-wide support delivery.

🛠️ Tools & Technologies

Microsoft Excel / Power Query: Data cleaning, null handling, date standardization, and relational normalization.

Microsoft Power BI: Star Schema data modeling, DAX KPI calculations, and interactive dashboard reporting.

🗄️ Data Architecture (Star Schema)

To eliminate redundancy and optimize Power BI performance, the raw dataset was decomposed into a normalized Star Schema:

Fact Table (Tickets): Ticket_Id, Requester_email (FK), Asset_Tag (FK), Assigned_To (FK), Ticket_category, Priority_level, Ticket_status, Created_at, Resolved_at, Estimated_hours, Actual_hours, Severity_score, Is_Escalated, Follow_up_required, Satisfaction_rating.

Dimension Tables:

Requesters: Requester_email (PK), Requester_name, Department, User_role, Contact_phone, Cost_center.

Assets: Asset_Tag (PK), Location, Vendor_name, Warranty_expiry, Last_maintenance, IP_address, Mac_address, Os_version, License_key.

Staff: Ticket_Id (PK), Assigned_To.

📐 Key DAX Measures

The following custom DAX measures power the top-level KPI cards on the dashboard:

Total Tickets = COUNT(Tickets[Ticket_Id])

Total Resolved Tickets = CALCULATE(COUNTROWS(Tickets), Tickets[Ticket_status] = "Resolved")

Average Satisfaction Rating = AVERAGE(Tickets[Satisfaction_rating])

Average Actual Hours = AVERAGE(Tickets[Actual_hours])

Average Estimated Hours = AVERAGE(Tickets[Estimated_hours])


🔍 Key Insights (4-Stage Analytical Framework)

1. Descriptive Analysis (What happened?)

Volume & Categories: Analyzed 500 total tickets across 8 categories, led by Hardware Faults (82 tickets / 16.4%) and Network Connectivity (63 tickets / 12.6%).

Resolution Efficiency: Average resolution time was 3.42 actual hours per ticket against an estimated baseline of 3.29 hours (+0.13 hr variance).

Satisfaction Baseline: Overall user satisfaction averaged 4.0 / 5.0, with 132 tickets marked as fully resolved.

2. Diagnostic Analysis (Why did it happen?)

Root Causes: High hardware and network ticket volumes stem from aging campus equipment and heavy daily usage in busy academic labs.

Time Variance Drivers: The minor gap between estimated (3.29 hrs) and actual fix times (3.42 hrs) occurred because complex tasks—such as Data Recovery and hardware diagnostics—often uncovered unexpected underlying faults.

Strong CSAT Retention: Satisfaction remained high because technicians met response targets and resolved everyday tickets quickly before causing major disruptions.

3. Predictive Analysis (What is likely to happen?)

Schedule Overruns: Urgent repairs and complex data recovery tasks will likely keep taking 10% to 15% longer than planned unless extra time buffers are added.

Satisfaction Risks: Departments experiencing recurring network drops face a higher risk of lower future satisfaction ratings.

Staffing Bottlenecks: Technicians assigned to complex asset repairs continue to face heavy workloads and longer hours per ticket, pointing to potential staff shortages if tasks are not rebalanced.

4. Prescriptive Analysis (What actions should be taken?)

Adjust Time Estimates: Build a time buffer into initial estimates for complex categories like Data Recovery to improve scheduling accuracy.

Targeted Departmental Support: Establish dedicated quick-response workflows for departments experiencing frequent network issues to resolve open tickets faster and prevent staff burnout.

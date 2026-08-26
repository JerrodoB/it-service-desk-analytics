# Project Foundation

## Project Purpose

IT Service Desk Analytics & Operational Insights is an exploratory data analysis project designed to investigate the operational performance of a fictional enterprise IT service desk.

The project will use Microsoft Excel as the primary exploratory analysis environment and SQL Server as a substantial relational analysis and validation environment.

The analysis will investigate service demand, resolution performance, SLA performance, support-team workload, ticket characteristics, and operational patterns to identify evidence-based opportunities for service improvement.

The project also demonstrates how a Business Systems Analyst or data-focused IT analyst can translate an operational business problem into analytical questions, investigate those questions using data, and communicate findings to business and technical stakeholders.

## Business Problem

Enterprise Technology Solutions (ETS) possesses service-desk operational data and receives basic reporting about service-desk activity. However, IT leadership lacks sufficient insight into the operational factors associated with service-desk workload, resolution performance, and SLA breaches.

Existing reporting provides counts and status information but does not sufficiently explain operational patterns, contributing factors, relationships, or areas that may warrant management attention.

## Business Need

ETS IT leadership needs to understand how operational factors affect service-desk workload and service performance so that improvement efforts can be prioritized using analytical evidence rather than assumptions.

## Primary Stakeholders

### IT Leadership

IT leadership is responsible for the overall effectiveness of IT services and for determining where organizational resources and improvement efforts should be prioritized.

IT leadership needs to understand where service-desk performance problems are concentrated, what operational factors are associated with those problems, and which areas appear to warrant the greatest management attention.

### Service Desk Management

Service Desk Management is responsible for day-to-day service-desk operations, including ticket workload, resolution performance, SLA performance, and support processes.

Service Desk Management needs to understand patterns involving ticket demand, resolution times, SLA breaches, priorities, escalations, reassignments, and other ticket characteristics that may help explain operational performance.

### Support-Team Managers

Support-Team Managers are responsible for teams that investigate and resolve service-desk tickets.

They need to understand the workload assigned to their teams, the types of tickets their teams handle, resolution and SLA performance, and whether particular ticket characteristics are associated with different service outcomes.

## Primary Business Question

What operational factors are most strongly associated with service-desk workload, long resolution times, and SLA breaches, and where should IT leadership prioritize improvement efforts?

## Supporting Analytical Questions

The exploratory analysis will initially investigate the following areas.

### Service Demand

- How many service-desk tickets are being generated?
- How does ticket volume change over time?
- Are recurring temporal patterns present?
- Which departments generate the greatest service demand?
- Which categories and subcategories generate the most tickets?
- Are particular services or applications disproportionately represented?

### Resolution Performance

- What is the typical ticket resolution time?
- How variable are resolution times?
- How do mean and median resolution times compare?
- How are resolution times distributed?
- Which ticket characteristics are associated with longer resolution times?
- Do unusually long resolution times represent valid operational cases, data-quality problems, or both?

### SLA Performance

- What percentage of applicable tickets meet or breach SLA requirements?
- Where are SLA breaches concentrated?
- Does SLA performance differ by priority, category, department, or support team?
- Are combinations of operational variables associated with poorer SLA performance?

### Support-Team Workload

- Which support teams receive the greatest ticket volume?
- Which teams handle the most high-priority work?
- How do resolution outcomes vary among teams?
- Is workload associated with service outcomes?
- Are apparent performance differences partly explained by differences in ticket mix?

### Incident Characteristics and Operational Improvement

- How does priority relate to resolution time?
- How does category relate to resolution time?
- Do services, applications, departments, or request channels show meaningful differences?
- Are reassignment, escalation, or reopening patterns associated with longer resolution times?
- Are recurring root-cause patterns visible?
- Which operational problems are frequent enough or costly enough to warrant further investigation?
- What additional information would be needed before stronger conclusions could be made?

Additional analytical questions may emerge during exploratory data analysis.

## Project Scope

### In Scope

The project will investigate:

- service-desk ticket demand and volume;
- ticket volume over time;
- departments generating service demand;
- ticket categories and subcategories;
- services and applications associated with tickets;
- ticket priority;
- resolution times and their distributions;
- SLA performance and SLA breaches;
- support-team workload and performance patterns;
- reassignment, escalation, and reopening patterns;
- root-cause information where represented in the dataset;
- relationships among operational ticket characteristics;
- unusual observations and outliers;
- operational patterns warranting management attention; and
- evidence-based improvement opportunities supported by the analysis.

### Out of Scope

The project will not attempt to perform:

- individual employee performance evaluation;
- employee disciplinary recommendations;
- detailed IT staffing or workforce planning;
- IT financial or budget analysis;
- predictive modeling or machine learning;
- future ticket-volume forecasting;
- cybersecurity incident investigation;
- infrastructure monitoring or performance analysis;
- end-user satisfaction analysis unless appropriate satisfaction data is explicitly incorporated;
- ServiceNow or other ITSM platform administration;
- full ITIL process assessment;
- implementation of recommended operational changes; or
- proof of causation from observational exploratory analysis alone.

## Project Assumptions

1. ETS represents a realistic fictional medium-to-large technology and engineering enterprise.
2. The synthetic dataset will approximate realistic enterprise service-desk activity without representing transactions from an actual organization.
3. Approximately 18–24 months of service-desk activity will provide an appropriate analytical period. The exact period will be determined during dataset design.
4. Ticket records will contain sufficient operational information to support the approved analytical questions.
5. Relationships identified through exploratory analysis will be treated as associations unless stronger evidence supports another interpretation.
6. The dataset may contain missing values, duplicates, inconsistent categories, unusual observations, and outliers that require investigation rather than automatic removal.

## Project Constraints

1. The project uses synthetic data; therefore, findings demonstrate analytical methodology and simulated business decision support rather than findings about an actual enterprise.
2. Microsoft Excel will remain the primary exploratory data analysis environment, with SQL Server providing substantial relational analysis, investigation, and validation.
3. Python, R, machine learning, predictive modeling, Tableau, and Power BI as a primary analytical environment are outside the approved project scope.
4. The project is observational and exploratory and is not designed as a controlled experiment capable of establishing causation.
5. Analysis will be limited by the variables represented in the synthetic dataset.
6. If information required to answer a question is unavailable, the limitation will be documented rather than resolved by inventing evidence.
7. Recommendations must be supported by analytical evidence.
8. Technical complexity must support the business investigation rather than being introduced solely to demonstrate additional technologies.

## Project Success Criteria

The project will be considered successful if it:

1. Addresses the primary business question concerning service-desk workload, long resolution times, and SLA breaches.
2. Investigates the major supporting questions involving service demand, resolution performance, SLA performance, support-team workload, incident characteristics, and operational improvement.
3. Produces defensible findings without predetermining conclusions or overstating the evidence.
4. Identifies meaningful patterns, trends, relationships, distributions, and unusual observations where supported by the data.
5. Translates analytical findings into business insights understandable to ETS stakeholders.
6. Develops evidence-based recommendations where sufficient analytical support exists.
7. Clearly communicates uncertainty, assumptions, limitations, and areas requiring additional investigation.
8. Demonstrates progressive Microsoft Excel competency from foundational analysis through advanced practical EDA.
9. Demonstrates substantial progressive SQL competency from basic retrieval through relational and advanced analytical queries where justified.
10. Demonstrates appropriate selection between Excel and SQL based on the analytical task.
11. Maintains professional documentation of methodology, assumptions, limitations, findings, and recommendations.
12. Produces a portfolio-ready GitHub repository that clearly communicates the business problem, analytical process, technical work, findings, and recommendations.
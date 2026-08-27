# Phase 2 Data Requirements

## IT Service Desk Analytics & Operational Insights

## Purpose

This document translates the approved business problem, stakeholder information needs, and analytical questions into the business information required for the future ETS service-desk dataset.

These requirements intentionally describe what information must be available before defining database entities, tables, attributes, primary keys, foreign keys, or physical data structures.

The requirements support the project reasoning chain:

Business Problem → Analytical Questions → Information Requirements → Business Entities → Attributes → Relationships → Data Model → Dataset → Analysis

---

## 1. Service Demand Information Requirements

### Ticket Identification

ETS must have information that uniquely distinguishes each service-desk ticket so analysts can count tickets accurately and avoid confusing separate incidents.

### Time

ETS must have information showing when each ticket entered the service-desk process so analysts can evaluate ticket volume across days, weeks, months, and other time periods and identify recurring temporal patterns.

### Organizational Source of Demand

ETS must have information identifying the department or business area associated with each ticket so analysts can compare service demand across the organization.

### Issue Classification

ETS must have information describing the type of issue represented by each ticket, including sufficient detail to compare broad issue categories and more specific subcategories.

### Affected Service or Application

ETS must have information identifying the IT service, system, or application associated with each ticket so analysts can determine whether particular technologies account for disproportionate service-desk demand.

---

## 2. Resolution Performance Information Requirements

### Resolution Timing

ETS must have information showing when each ticket entered the service process and when it was completed or resolved so resolution duration can be determined.

The exact business events used to define the start and end of the measurement will be established later as business rules.

### Resolution Status

ETS must have information showing the current state of each ticket so analysts can distinguish legitimately unresolved tickets from resolved tickets with incomplete resolution information.

### Issue Context

ETS must retain sufficient issue-classification information so resolution performance can be compared across different types of work.

---

## 3. SLA Performance Information Requirements

### SLA Applicability

ETS must have information indicating whether each ticket is subject to an SLA requirement and, where applicable, which service commitment governs the ticket.

### SLA Requirement

ETS must have information defining the applicable SLA performance requirement for each SLA-governed ticket so actual performance can be evaluated against the required service standard.

### SLA Outcome

ETS must have sufficient information to determine whether each applicable ticket met or breached its SLA requirement based on actual service performance compared with the applicable SLA standard.

### SLA Comparison Context

ETS must retain sufficient ticket context to compare SLA performance by priority, issue category, organizational department, and responsible support team, as well as combinations of these factors where analytically appropriate.

---

## 4. Support-Team Workload Information Requirements

### Responsible Support Team

ETS must have information identifying the support team responsible for handling each ticket so ticket workload and service outcomes can be associated with the appropriate operational group.

### Workload Characteristics

ETS must retain sufficient information about assigned tickets, including priority and issue classification, to evaluate workload volume and workload characteristics.

### Service Outcomes

ETS must have sufficient information to associate each support team's workload with relevant service outcomes, including resolution performance and SLA performance.

### Ticket Movement Between Teams

ETS must have sufficient information to determine whether a ticket was reassigned or transferred between support teams so analysts can investigate whether ticket movement is associated with workload or service outcomes.

---

## 5. Incident Characteristics and Operational-Improvement Information Requirements

### Priority or Urgency Context

ETS must have information describing the business priority or urgency assigned to each ticket so analysts can compare service outcomes across different levels of operational importance.

### Request Channel

ETS must have information identifying the channel through which each ticket entered the service-desk process so analysts can compare demand and service outcomes across intake methods.

### Reassignment and Escalation Behavior

ETS must have sufficient information to determine whether a ticket was reassigned or escalated during its lifecycle and support comparison of those events with resolution and SLA performance.

### Reopening Behavior

ETS must have information indicating whether a resolved ticket was reopened so analysts can investigate whether reopening is associated with longer total resolution effort or recurring service problems.

### Recurring Problem or Root-Cause Context

ETS must retain sufficient issue and problem context to identify recurring patterns across tickets and, where known, associate tickets with a documented cause or recurring problem classification.

### Operational Impact

ETS must retain enough information about ticket priority, affected service, organizational area, and service outcome to assess the operational significance of recurring problems rather than relying on ticket frequency alone.

### Improvement Analysis Context

The dataset must contain sufficient operational context to identify patterns that may warrant further investigation into automation, knowledge management, training, process improvement, staffing changes, problem management, or system improvements.

The dataset must support investigation without treating statistical association as proof of causation or predetermining the eventual analytical findings.

---

## 6. Requirements Design Principles

The future dataset must:

- support the approved stakeholder and analytical questions;
- avoid storing information solely because it is common in service-desk systems;
- reuse information where the same business concept supports multiple analytical questions;
- distinguish stored operational information from values that may later be derived;
- distinguish performance outcomes from the business rules used to evaluate them;
- preserve enough operational context for responsible comparisons;
- support investigation without manufacturing predetermined conclusions;
- remain suitable for later Excel and SQL relational analysis.

---

## 7. Current Design Status

The business information requirements are approved.

No database tables have yet been defined.

No attributes or columns have yet been defined.

No primary keys or foreign keys have yet been defined.

No SQL Server database has been created.

No synthetic ticket records have been generated.

No Excel exploratory analysis has begun.

The next design activity is to translate these approved information requirements into candidate business entities.
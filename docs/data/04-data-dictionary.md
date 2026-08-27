# Data Dictionary

## IT Service Desk Analytics & Operational Insights

## Purpose

This data dictionary defines the approved logical fields for the Enterprise Technology Solutions (ETS) service-desk analytics dataset.

It provides the business meaning, conceptual data type, measurement scale, key role, nullability expectations, and applicable business rules for each field.

This is a logical data dictionary.

SQL Server-specific physical data types and implementation syntax have not yet been assigned.

---

# 1. Ticket

**Grain:** One record represents one unique service-desk ticket.

| Field | Business Definition | Conceptual Type | Scale | Key Role | Null Allowed | Business Rule |
|---|---|---|---|---|---|---|
| Ticket Identifier | Uniquely identifies a service-desk ticket | Identifier | Nominal | Primary Key | No | Must be unique for every ticket |
| Submitted Date/Time | Date and time the ticket entered the service process | Datetime | Interval | None | No | Must fall within the approved dataset timeframe |
| Resolved Date/Time | Date and time the ticket was resolved | Datetime | Interval | None | Yes | May be null for unresolved tickets; cannot precede submission |
| Ticket Status | Current/final lifecycle state of the ticket | Text | Nominal | None | No | Must use an approved controlled status value |
| Request Channel | Method through which the ticket entered the service desk | Text | Nominal | None | No | Raw synthetic data may contain approved labeling inconsistencies |
| Department Identifier | Identifies the business department associated with the ticket | Integer Identifier | Nominal | Foreign Key | No | Must reference a valid Department |
| Issue Subcategory Identifier | Identifies the specific issue classification assigned to the ticket | Integer Identifier | Nominal | Foreign Key | No | Must reference a valid Issue Subcategory |
| Service/Application Identifier | Identifies the primary affected IT service, system, or application | Integer Identifier | Nominal | Foreign Key | No | Must reference a valid Service/Application |
| Priority Identifier | Identifies the business priority assigned to the ticket | Integer Identifier | Nominal | Foreign Key | No | Must reference a valid Priority |
| Support Team Identifier | Identifies the principal/final support team responsible for the ticket | Integer Identifier | Nominal | Foreign Key | No | Must reference a valid Support Team |
| SLA Definition Identifier | Identifies the SLA rule applicable to the ticket | Integer Identifier | Nominal | Foreign Key | Yes | Null is valid when no SLA applies |
| Reassignment Count | Number of times the ticket was reassigned | Integer | Ratio | None | No | Must be zero or greater |
| Escalated Indicator | Indicates whether the ticket was escalated | Boolean | Nominal | None | No | Represents escalated/not escalated |
| Reopened Count | Number of times the ticket was reopened after resolution activity | Integer | Ratio | None | No | Must be zero or greater |
| Root Cause / Problem Classification | Optional classification describing a known underlying problem or cause | Text | Nominal | None | Yes | Missing value may be legitimate when no formal root cause is documented |

---

# 2. Department

**Grain:** One record represents one unique ETS business department.

| Field | Business Definition | Conceptual Type | Scale | Key Role | Null Allowed |
|---|---|---|---|---|---|
| Department Identifier | Uniquely identifies an ETS department | Integer Identifier | Nominal | Primary Key | No |
| Department Name | Business name of the department | Text | Nominal | None | No |

**Target records:** 10

---

# 3. Support Team

**Grain:** One record represents one unique IT support team.

| Field | Business Definition | Conceptual Type | Scale | Key Role | Null Allowed |
|---|---|---|---|---|---|
| Support Team Identifier | Uniquely identifies an IT support team | Integer Identifier | Nominal | Primary Key | No |
| Support Team Name | Name of the IT support team | Text | Nominal | None | No |

**Target records:** 7

---

# 4. Issue Category

**Grain:** One record represents one unique broad issue classification.

| Field | Business Definition | Conceptual Type | Scale | Key Role | Null Allowed |
|---|---|---|---|---|---|
| Issue Category Identifier | Uniquely identifies a broad issue category | Integer Identifier | Nominal | Primary Key | No |
| Issue Category Name | Name of the broad issue classification | Text | Nominal | None | No |

**Target records:** 8

---

# 5. Issue Subcategory

**Grain:** One record represents one unique specific issue classification.

| Field | Business Definition | Conceptual Type | Scale | Key Role | Null Allowed |
|---|---|---|---|---|---|
| Issue Subcategory Identifier | Uniquely identifies an issue subcategory | Integer Identifier | Nominal | Primary Key | No |
| Issue Subcategory Name | Name of the specific issue classification | Text | Nominal | None | No |
| Issue Category Identifier | Identifies the broader category containing the subcategory | Integer Identifier | Nominal | Foreign Key | No |

**Target records:** Approximately 30.

Each Issue Subcategory must reference a valid Issue Category.

---

# 6. Service / Application

**Grain:** One record represents one unique IT service, system, or application.

| Field | Business Definition | Conceptual Type | Scale | Key Role | Null Allowed |
|---|---|---|---|---|---|
| Service/Application Identifier | Uniquely identifies an IT service, system, or application | Integer Identifier | Nominal | Primary Key | No |
| Service/Application Name | Business-recognizable name of the service or application | Text | Nominal | None | No |
| Service/Application Type | Broad classification of the service/application | Text | Nominal | None | No |

**Target records:** Approximately 20.

---

# 7. Priority

**Grain:** One record represents one unique ticket-priority level.

| Field | Business Definition | Conceptual Type | Scale | Key Role | Null Allowed |
|---|---|---|---|---|---|
| Priority Identifier | Uniquely identifies a priority level | Integer Identifier | Nominal | Primary Key | No |
| Priority Code | Business-facing priority code | Text | Ordinal | None | No |
| Priority Name | Business description of the priority level | Text | Ordinal | None | No |
| Priority Rank | Numeric representation of priority ordering | Integer | Ordinal | None | No |

**Target records:** 4.

Approved priority structure:

- P1 — Critical
- P2 — High
- P3 — Medium
- P4 — Low

Priority Rank represents ordering rather than quantitative distance.

---

# 8. SLA Definition

**Grain:** One record represents one unique SLA service commitment or performance rule.

| Field | Business Definition | Conceptual Type | Scale | Key Role | Null Allowed |
|---|---|---|---|---|---|
| SLA Definition Identifier | Uniquely identifies an SLA definition | Integer Identifier | Nominal | Primary Key | No |
| SLA Name | Business-recognizable name of the SLA rule | Text | Nominal | None | No |
| Resolution Target | Maximum allowable resolution duration under the SLA rule | Decimal | Ratio | None | No |
| SLA Applicability Description | Describes the circumstances under which the SLA applies | Text | Nominal | None | No |

**Target records:** Approximately 4–6.

Exact SLA thresholds and applicability rules will be finalized before synthetic-data generation.

---

# 9. Derived Analytical Variables

The following variables may be calculated during later data preparation or exploratory analysis rather than stored directly in the source Ticket entity.

| Derived Variable | Derivation Concept | Scale |
|---|---|---|
| Resolution Duration | Resolved Date/Time minus Submitted Date/Time | Ratio |
| SLA Outcome | Comparison of actual resolution performance with applicable SLA target | Nominal |
| Was Reassigned | Reassignment Count greater than zero | Nominal |
| Submission Month | Calendar month derived from Submitted Date/Time | Nominal |
| Submission Day of Week | Day name derived from Submitted Date/Time | Nominal |

Derived variables must be calculated consistently and documented when implemented.

---

# 10. Dataset Boundary

The approved synthetic dataset will represent:

**Historical period:** January 1, 2025 through December 31, 2026

**Target Ticket records:** 20,000

Supporting-entity targets:

- Departments: 10
- Support Teams: 7
- Issue Categories: 8
- Issue Subcategories: approximately 30
- Services/Applications: approximately 20
- Priorities: 4
- SLA Definitions: approximately 4–6

---

# 11. Data-Quality Principles

The future synthetic dataset will intentionally contain realistic analytical imperfections while preserving relational integrity.

Approved conditions include:

- legitimate missing resolution timestamps for unresolved tickets;
- legitimate missing root-cause classifications;
- limited inconsistent categorical labels;
- legitimate long-resolution outliers;
- reassignment outliers;
- reopening outliers;
- imbalanced priority distributions;
- uneven departmental demand;
- uneven issue frequency;
- legitimate null SLA associations.

The dataset will not intentionally contain:

- duplicate primary keys;
- orphaned foreign keys;
- negative reassignment counts;
- negative reopening counts;
- resolution timestamps before submission;
- corrupted identifiers;
- deliberately nonsensical values.

---

# 12. Current Implementation Status

This data dictionary defines the approved logical dataset structure.

No synthetic Ticket records have been generated.

No SQL Server database or physical tables have been created.

No Excel exploratory analysis has begun.

SQL Server-specific physical data types will be established during the authorized implementation phase.
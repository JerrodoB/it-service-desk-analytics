# Logical Data Model

## IT Service Desk Analytics & Operational Insights

## Purpose

This document defines the approved logical relational model for the ETS service-desk analytics dataset.

It translates the approved Phase 2 information requirements into business entities, attributes, identifiers, relationships, and cardinality.

This document represents a logical design only.

No SQL Server database, physical tables, SQL data types, or synthetic ticket records have been created.

The current design progression is:

Business Questions → Information Requirements → Entities → Attributes → Identifiers → Keys → Relationships → Logical Data Model

---

# 1. Modeling Principles

The logical model follows these principles:

- each entity represents a distinct business concept;
- the grain of each entity is explicitly defined;
- attributes are included only when justified by approved analytical requirements;
- reusable business concepts are separated where relational modeling provides analytical or data-integrity value;
- unnecessary normalization is avoided;
- the Ticket entity remains the central transactional entity;
- complete ticket event history is outside the current project scope;
- the model must remain understandable and manageable for Excel and SQL analysis;
- relationships must support later referential integrity;
- the model must support investigation without predetermining analytical findings.

---

# 2. Approved Entities

The approved entities are:

1. Ticket
2. Department
3. Support Team
4. Issue Category
5. Issue Subcategory
6. Service / Application
7. Priority
8. SLA Definition

The following concepts remain attributes rather than separate entities in the initial model:

- Request Channel
- Root Cause / Problem Classification
- Ticket Status
- Reassignment indicators
- Escalation indicators
- Reopening indicators

---

# 3. Entity Grain

## Ticket

One row represents one unique service-desk ticket.

A ticket remains one ticket even if it is reassigned, escalated, reopened, or changes status.

## Department

One row represents one unique ETS business department.

## Support Team

One row represents one unique IT support team responsible for service-desk work.

## Issue Category

One row represents one unique broad issue classification.

## Issue Subcategory

One row represents one unique specific issue classification belonging to a broader issue category.

## Service / Application

One row represents one unique IT service, system, or application that can be associated with service-desk tickets.

## Priority

One row represents one unique ETS ticket-priority level.

## SLA Definition

One row represents one unique SLA service commitment or performance rule that may apply to service-desk tickets.

---

# 4. Ticket Entity

## Purpose

The Ticket entity represents the primary unit of service-desk work and is the central transactional entity for the analysis.

## Grain

One row represents one unique service-desk ticket.

## Proposed Attributes

- Ticket Identifier
- Submitted Date/Time
- Resolved Date/Time
- Ticket Status
- Request Channel
- Department Association
- Issue Subcategory Association
- Service/Application Association
- Priority Association
- Responsible Support Team Association
- SLA Definition Association
- Reassignment Count
- Escalated Indicator
- Reopened Count
- Root Cause / Problem Classification

## Primary Key

Ticket Identifier

The Ticket Identifier must uniquely distinguish each service-desk ticket.

---

# 5. Department Entity

## Purpose

The Department entity represents ETS business departments that generate service-desk demand.

## Grain

One row represents one unique ETS business department.

## Attributes

- Department Identifier
- Department Name

## Primary Key

Department Identifier

---

# 6. Support Team Entity

## Purpose

The Support Team entity represents IT groups responsible for handling service-desk work.

## Grain

One row represents one unique IT support team.

## Attributes

- Support Team Identifier
- Support Team Name

## Primary Key

Support Team Identifier

---

# 7. Issue Category Entity

## Purpose

The Issue Category entity represents broad classifications of service-desk issues.

## Grain

One row represents one unique broad issue classification.

## Attributes

- Issue Category Identifier
- Issue Category Name

## Primary Key

Issue Category Identifier

---

# 8. Issue Subcategory Entity

## Purpose

The Issue Subcategory entity represents more specific issue classifications beneath broader issue categories.

## Grain

One row represents one unique issue subcategory.

## Attributes

- Issue Subcategory Identifier
- Issue Subcategory Name
- Issue Category Association

## Primary Key

Issue Subcategory Identifier

---

# 9. Service / Application Entity

## Purpose

The Service / Application entity represents IT services, systems, or applications associated with service-desk tickets.

## Grain

One row represents one unique IT service, system, or application.

## Attributes

- Service/Application Identifier
- Service/Application Name
- Service/Application Type

## Primary Key

Service/Application Identifier

---

# 10. Priority Entity

## Purpose

The Priority entity represents the ordered business priority assigned to service-desk tickets.

## Grain

One row represents one unique ticket-priority level.

## Attributes

- Priority Identifier
- Priority Code
- Priority Name
- Priority Rank

## Primary Key

Priority Identifier

Priority Rank represents the ordering of priority levels and will later support the classification of Priority as an ordinal variable.

---

# 11. SLA Definition Entity

## Purpose

The SLA Definition entity represents reusable service-level commitments against which applicable ticket performance may be evaluated.

## Grain

One row represents one unique SLA service commitment or performance rule.

## Attributes

- SLA Definition Identifier
- SLA Name
- Resolution Target
- SLA Applicability Description

## Primary Key

SLA Definition Identifier

The exact SLA thresholds and applicability rules have not yet been established.

---

# 12. Foreign Keys and Relationships

## Department to Ticket

Business rule:

One Department may be associated with many Tickets.

Each Ticket is associated with one Department.

Cardinality:

One-to-many.

Foreign key:

Department Identifier is stored in Ticket as a foreign key.

---

## Support Team to Ticket

Business rule:

One Support Team may be responsible for many Tickets.

Each Ticket has one principal or final responsible Support Team.

Cardinality:

One-to-many.

Foreign key:

Support Team Identifier is stored in Ticket as a foreign key.

---

## Issue Category to Issue Subcategory

Business rule:

One Issue Category may contain many Issue Subcategories.

Each Issue Subcategory belongs to one Issue Category.

Cardinality:

One-to-many.

Foreign key:

Issue Category Identifier is stored in Issue Subcategory as a foreign key.

---

## Issue Subcategory to Ticket

Business rule:

One Issue Subcategory may be associated with many Tickets.

Each Ticket is associated with one Issue Subcategory.

Cardinality:

One-to-many.

Foreign key:

Issue Subcategory Identifier is stored in Ticket as a foreign key.

Because the Issue Subcategory already references Issue Category, the Ticket entity does not also store the Issue Category Identifier.

---

## Service / Application to Ticket

Business rule:

One Service / Application may be associated with many Tickets.

Each Ticket is associated with one primary affected Service / Application.

Cardinality:

One-to-many.

Foreign key:

Service/Application Identifier is stored in Ticket as a foreign key.

---

## Priority to Ticket

Business rule:

One Priority may apply to many Tickets.

Each Ticket has one Priority.

Cardinality:

One-to-many.

Foreign key:

Priority Identifier is stored in Ticket as a foreign key.

---

## SLA Definition to Ticket

Business rule:

One SLA Definition may apply to many Tickets.

A Ticket may have zero or one applicable SLA Definition.

Cardinality:

One-to-many, with the SLA relationship optional on the Ticket side.

Foreign key:

SLA Definition Identifier is stored in Ticket as a nullable foreign key.

---

# 13. Relationship Summary

| Parent Entity | Child Entity | Cardinality | Foreign Key Location |
|---|---|---|---|
| Department | Ticket | One-to-many | Ticket |
| Support Team | Ticket | One-to-many | Ticket |
| Issue Category | Issue Subcategory | One-to-many | Issue Subcategory |
| Issue Subcategory | Ticket | One-to-many | Ticket |
| Service / Application | Ticket | One-to-many | Ticket |
| Priority | Ticket | One-to-many | Ticket |
| SLA Definition | Ticket | One-to-many, optional | Ticket |

---

# 14. Referential Integrity Principle

Foreign-key values must reference valid records in the corresponding parent entity.

For example, if a Ticket references a Department Identifier, that Department Identifier must exist in the Department entity.

This principle prevents orphaned relationships and supports reliable joins and analytical results.

SQL Server foreign-key constraints will later be used to enforce these rules during physical database implementation.

---

# 15. Intentional Scope Limitations

The initial model does not include:

- a complete Ticket History or Event entity;
- technician-level assignment history;
- many-to-many ticket-to-service relationships;
- multiple simultaneous support-team ownership;
- SLA calendars;
- detailed escalation workflows;
- employee or submitter entities;
- problem-management records;
- application ownership structures.

Reassignment, escalation, reopening, and root-cause context will initially be represented through Ticket attributes.

These limitations preserve the project's focus on exploratory analysis rather than production service-management database engineering.

---

# 16. Current Design Status

Approved and documented:

- business information requirements;
- core business entities;
- entity grain;
- entity attributes;
- identifiers;
- primary keys;
- foreign-key locations;
- relationships;
- relationship cardinality;
- referential-integrity expectations.

Not yet established:

- conceptual data types;
- scales of measurement;
- final controlled values;
- final SLA thresholds;
- intentional data-quality conditions;
- synthetic-data generation rules;
- historical timeframe;
- final record counts;
- detailed data dictionary;
- entity relationship diagram.

No SQL Server database has been created.

No synthetic dataset has been generated.

No Excel exploratory analysis has begun.
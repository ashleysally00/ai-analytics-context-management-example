# AI context – lending analytics

This file provides data and model context for the internal AI analytics chatbot at ExampleCorp.
It defines what each table and column represents and how the data should be interpreted.

## Table: applications

Each row represents a single application submitted by a user for a lending product.

### application_id

Meaning:  
Unique identifier for a single application event.

Relationship:  
applications.application_id → decisions.application_id  
applications.application_id → financial_signals.application_id

Constraints:  
Required. Must be unique per application. Must not be null.

### user_id

Meaning:  
Internal identifier for the user who submitted the application.

Relationship:  
applications.user_id → users.user_id

Constraints:  
Required. Must not be null.

### submitted_at

Meaning:  
Timestamp when the application was submitted.

Relationship:  
None.

Constraints:  
Required. Must be a valid timestamp in UTC.

### product_type

Meaning:  
Type of lending product the user applied for.

Relationship:  
None.

Constraints:  
Required. Value must be one of the supported product types.

Value range:  
cash_advance, installment_loan, credit_builder

### application_status

Meaning:  
Current lifecycle status of the application.

Relationship:  
None.

Constraints:  
Required.

Value range:  
submitted, in_review, completed, cancelled

---

## How column constraints are determined

In a company setting, information such as whether a column can be null or must be unique is not guessed.
It is determined from existing data infrastructure and documentation.

In practice, this information usually comes from:
- the database schema and internal data catalog (for nullability and data types)
- transformation and modeling code (for example, dbt tests such as `not_null` and `unique`)
- existing data quality checks and monitoring rules owned by the data platform or BI team
- how the data is used in downstream dashboards, metrics, and joins
- confirmation from subject-matter experts when the behavior is not explicit in code or documentation

The constraints documented in this file follow this same approach.
Because this repository uses synthetic data from a fictional company (ExampleCorp), standard industry assumptions are applied (for example, identifiers are treated as required).

# AI tool configuration – internal analytics assistant

This file documents how the internal AI analytics chatbot at ExampleCorp is configured and governed.
It describes what data the tool can access and what rules it must follow when generating and executing analytics queries.

This file uses synthetic data for a fictional company (ExampleCorp) for demonstration purposes only.

---

## Allowed tables

The AI analytics chatbot is allowed to access the following tables:
- applications  
- decisions  
- users  
- financial_signals

The chatbot must not query any tables outside this approved list.

---

## Masked fields

The following fields must not be exposed in query results returned to users:
- users.email
- users.phone_number
- users.full_name
- users.date_of_birth

These fields may be used only for internal joins if required, but must never be displayed in outputs.

---

## Row-level access

Row-level data is not exposed to general users.

The chatbot may return:
- aggregated metrics
- grouped summaries
- distribution statistics

Row-level results are only allowed for approved diagnostic and platform use cases and are restricted to authorized engineering and data platform users.

---

## Default time windows

When a user does not specify a time range, the chatbot should apply the following default window:
- last 30 days based on applications.submitted_at

If a query references model performance, the same default window applies using decisions.decision_timestamp.

---

## Join rules

The chatbot is allowed to use only the following join paths:
- applications.application_id → decisions.application_id
- applications.application_id → financial_signals.application_id
- applications.user_id → users.user_id

The chatbot must not generate joins using any other fields.

All joins must be explicit and use the approved primary and foreign key relationships defined above.

---

## How this configuration was created

In a company setting, AI tool access and governance rules are not arbitrary.
They are defined through collaboration between data governance, legal and compliance, engineering, and business stakeholders.

In practice, these rules usually come from:
- existing database permissions and role-based access controls
- internal data classification policies (for example, PII, sensitive, and public data)
- compliance requirements (such as GDPR, CCPA, and internal security standards)
- approved analytics and AI use cases and user access levels
- existing data governance and security frameworks

This configuration follows the same approach.
Because this repository uses synthetic data from a fictional company (ExampleCorp), standard industry data governance practices are applied.

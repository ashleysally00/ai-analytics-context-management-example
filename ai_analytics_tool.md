# # Documentation for the AI analytics tool

This document explains how internal teams at ExampleCorp should use the AI analytics chatbot and how to interpret its results.

This file uses synthetic data from a fictional company (ExampleCorp) for demonstration purposes only.

---

## What this tool is for

The AI analytics chatbot is intended to support exploratory and summary analytics on lending and model performance data.

It can be used to:

- analyze application and approval trends
- summarize performance metrics by product, time period, or segment
- explore relationships between financial signals and outcomes
- compare high-level performance across model versions

The tool is designed for analytical insight and reporting support, not for operational decision-making on individual users.

---

## Example questions

Examples of appropriate questions include:

- What was the approval rate last week by product type?
- How many applications were submitted each day over the past 30 days?
- Which financial signals show the strongest correlation with declined decisions?
- How did model version v3 perform compared to v2 in terms of approval rate and default risk indicators?
- What is the distribution of approval scores by product type?

---

## What this tool should not be used for

This tool must not be used for:

- viewing or exporting row-level or user-level data
- identifying or investigating individual users or applications
- operational decision-making on a single application
- compliance, legal, or audit determinations
- real-time decisioning or system automation

The chatbot is intended for aggregated and analytical use only.

---

## How to interpret `approval_score` vs `decision_label`

### `approval_score`

The `approval_score` represents the output of a machine learning model.
It is a continuous numeric score indicating the model’s estimated likelihood that an application meets the approval criteria.

The `approval_score`:

- is a model output
- is used as an input to downstream business rules
- should be interpreted comparatively (for example, higher vs lower scores), not as a guarantee of approval

The `approval_score` alone does not determine the final decision.

---

### `decision_label`

The `decision_label` represents the final business decision recorded for an application.

Typical values include:

- approved
- declined
- referred

The `decision_label`:

- is the outcome after applying business rules, policies, and thresholds
- may take into account multiple factors in addition to the `approval_score`
- reflects what actually happened to the application

---

### Key distinction

`approval_score` is a model output that expresses risk or eligibility likelihood.

`decision_label` is the finalized business outcome.

They are related, but they are not interchangeable.
A high `approval_score` does not always imply an approved decision, and a low `approval_score` does not always imply a declined decision.

For example, an application might receive a high `approval_score` from the model but still have a `decision_label` of declined due to business policy rules such as regulatory restrictions, debt-to-income thresholds, or fraud and risk controls.

---

## How this guidance was created

The usage guidance in this document reflects how internal AI analytics tools are typically introduced and governed inside a company.

In a company setting, AI tool usage guidance is developed collaboratively to ensure the tool is used safely, effectively, and in alignment with company policies.

In practice, this guidance usually comes from:
- the intended analytics and business use cases that justified building or adopting the tool
- input from legal, compliance, and data governance teams on appropriate and prohibited uses
- feedback from analysts and product teams during pilot and testing phases
- existing policies on data access, analytics practices, and decision-making processes
- lessons learned from similar internal analytics tools already in use

This guidance follows the same approach.
Because this repository uses synthetic data from a fictional company (ExampleCorp), standard industry practices for responsible internal AI analytics usage are applied.

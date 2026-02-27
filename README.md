# **AI Context & Configuration for an Internal Lending Analytics Assistant**

## Live Documentation

View the full interactive documentation site here:

**[Launch Documentation](https://ar-528b7fb5.mintlify.app)**

This repository demonstrates how to create AI context files, configuration documentation, and user guidance for an internal analytics assistant using synthetic lending data.  
It is intended as a documentation and context-engineering example only.

ExampleCorp has an internal AI chatbot that answers questions about lending data and model performance.

Context greatly improves chatbots — but an internal AI analytics system needs more than one context layer to work correctly.

Different context layers are needed for different situations:

* data and model context is needed so the AI system can correctly interpret and use tables, columns, and model outputs

* configuration context is needed so platform and BI teams can operate, restrict, and govern the AI analytics tool safely

* usage instructions are needed so internal users understand how to ask questions and how to interpret the results

To make this concrete, this repository models a simple internal analytics chatbot scenario and shows how each of these three context layers is applied to the same set of lending and model data.

In this example, the chatbot relies on the three documentation layers in this repository to understand what the data means, how it is allowed to be used, and how its answers should be interpreted.

---

First, there is an internal chatbot used by:

* BI analysts

* product managers

* risk / ops

to ask questions like:

* “What was the approval rate last week by product type?”

* “Which financial signals correlate most with decline?”

* “How did model v3 perform vs v2?”

---

For this to work, the chatbot needs a context file that tells it how to read the tables and data — what the columns mean and how the tables relate to each other.

### **A) AI context file (for the chatbot)**

**File:** [ai_context.md](https://github.com/ashleysally00/ai-analytics-context-management-example/blob/main/ai_context.md)

This file explains:

* what each table represents

* what each column actually means

* how tables join to each other

* what values and ranges are valid

* which fields are model inputs and which are model outputs

---

Configuration docs are also needed so that engineers can quickly see how the AI analytics tool is set up and what rules it runs under.

### **B) AI configuration docs (for engineers / BI platform)**

**File:** [ai_analytics_tool.md](https://github.com/ashleysally00/ai-analytics-context-management-example/blob/main/ai_analytics_tool.md)

These documents explain:

* which tables are exposed to the AI

* which columns are masked or restricted

* whether row-level data is allowed

* what default time windows are used

* which joins are allowed

---

Finally, instructions are needed for the people who use the chatbot so they know how to ask questions and how to interpret the answers.

### **C) Instructions for internal users**

**File:** [ai_tool_configuration.md](https://github.com/ashleysally00/ai-analytics-context-management-example/blob/main/ai_tool_configuration.md)

Together with the AI context file and the configuration documentation, these instructions make it possible for the chatbot and its users to reliably answer questions such as:

* “What does `approval_score` actually mean?”

* “Which table should I use for approval rates?”

* “Can the AI show row-level data?”

* “What signals are inputs vs outputs?”


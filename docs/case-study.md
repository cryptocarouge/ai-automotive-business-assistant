# Case Study — AI Automotive Business Assistant

## Problem

Small business workflows often mix chat, customer lookup, document photos, PDFs, email drafting and spreadsheet state. Putting all of that into one chatbot prompt creates an assistant that is difficult to audit and unreliable when actions must be performed.

## Architecture decision

The system uses an operational router:

1. **Normalize the incoming Telegram/webhook event**
2. **Route menu, text and photo inputs**
3. **Use vision only for document/image interpretation**
4. **Run customer/data lookup as explicit workflow stages**
5. **Generate PDFs through a dedicated document service**
6. **Draft emails with AI when language generation is useful**
7. **Persist structured data separately**
8. **Return the result through Telegram**

## Multimodal without losing structure

Photo input does not go directly into a general-purpose conversation. It enters a dedicated vision/document path, is converted into structured information and only then participates in downstream operations.

## Separation of conversation and action

The assistant can converse, but the important business actions — lookup, save, generate PDF, update counters — remain explicit nodes with deterministic inputs and outputs.

This makes the workflow easier to debug and reduces the chance that a model response silently changes business state.

## What remains private

The public repository excludes customer records, contact details, live Sheet identifiers, webhook endpoints, credentials and the production workflow.

## Takeaway

The project demonstrates how to turn a conversational interface into an **operational business tool without making the LLM the workflow engine**.

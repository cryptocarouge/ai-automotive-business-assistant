<p align="center"><img src="assets/header.svg" alt="AI Automotive Business Assistant" width="100%"></p>

# AI Automotive Business Assistant

A multimodal business-operations assistant built with n8n, Telegram, OpenAI, Google Sheets and Gotenberg.

The original private workflow was designed around automotive operations. This public edition documents the reusable architecture with no client data, contact details, private document IDs or credentials.

## What it demonstrates

- Telegram-based operational interface
- Text and photo input
- Vision-assisted document parsing
- Structured extraction and customer lookup
- PDF generation through Gotenberg
- Google Sheets persistence
- AI-assisted email drafting
- Menu/mode routing
- Operational counters and settings
- Post-document follow-up flows

## Architecture

```mermaid
flowchart TD
    A[Telegram / Webhook] --> B[Normalize Input]
    B --> C{Router}
    C --> D[Text]
    C --> E[Photo]
    C --> F[Menu]
    E --> G[Vision]
    D --> H[AI / Document Logic]
    G --> H
    F --> H
    H --> I[Customer Lookup]
    H --> J[PDF Generation]
    H --> K[Email Drafting]
    H --> L[Data Persistence]
    I --> M[Telegram Response]
    J --> M
    K --> M
    L --> M
```

## Engineering approach

Conversational AI is separated from operational actions. Parsing, routing, data lookup, PDF generation and persistence are explicit stages instead of being hidden inside a single prompt.

## Security boundary

Not included: customer records, emails/phone numbers, live Sheet identifiers, chat IDs, private webhook endpoints, API credentials or production workflow JSON.

## Status

Public architecture showcase of a private business-automation system.

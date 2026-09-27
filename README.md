# AI Automotive Business Assistant

A multimodal business-operations assistant built with n8n, Telegram, OpenAI, Google Sheets and Gotenberg.

The original private workflow was designed around automotive operations. This public edition documents the reusable architecture with no client data, phone numbers, emails, private document IDs or credentials.

## What it demonstrates

- Telegram-based operational interface
- Text and photo input
- Vision-assisted document parsing
- Structured document extraction
- PDF generation through Gotenberg
- Customer lookup
- Data persistence in Google Sheets
- AI-assisted email drafting
- Menu and mode routing
- Operational counters and settings
- Post-document follow-up flows

## Architecture

```text
Telegram / Webhook
       |
       v
 Normalize Input
       |
       v
      Router
   /    |     \
Text  Photo   Menu
 |      |       |
 |    Vision    |
 |      |       |
 +------v-------+
        |
   AI / Document Logic
        |
        +--> Customer Lookup
        |
        +--> PDF Generation
        |
        +--> Email Drafting
        |
        +--> Data Persistence
        |
        v
   Telegram Response
```

## Engineering approach

The assistant separates conversational AI from operational actions. Parsing, routing, data lookup, PDF generation and persistence are explicit workflow stages instead of being hidden inside a single prompt.

## Security boundary

Not included in this repository:

- Customer names or records
- Email addresses or phone numbers
- Live Google Sheet identifiers
- Telegram chat IDs
- Webhook endpoints
- API credentials
- Production workflow JSON

## Status

Public architecture showcase of a private business-automation system.

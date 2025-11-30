
# MailMind – Scenario Overview

MailMind automates email handling using Make, Gmail, and OpenAI.  
This document explains how the scenario works, module by module.

---

## 1. Gmail – Watch Emails

- Watches for new incoming messages.
- Usually configured to filter:
  - Unread messages
  - Specific inbox or label
- Extracts fields:
  - From
  - To
  - Subject
  - Body
  - Message ID
  - Thread ID

---

## 2. OpenAI – Generate Completion

This module analyzes email content and generates JSON with the fields MailMind needs.

### Example prompt structure:

```text
Eres un asistente profesional. Analiza el siguiente correo y genera una respuesta.

Devuelve SOLO un JSON con:
- "subject": asunto del correo de respuesta
- "reply_body": cuerpo HTML o texto plano para enviar

Correo recibido:
Asunto: {{Subject}}
Cuerpo:
{{Body}}
```
Example model output:
```text
{
  "subject": "Re: Información solicitada",
  "reply_body": "<p>Estimado cliente...</p>"
}

```
## 3. JSON – Parse JSON

- Parses output from the AI.

- Extracts structured fields:

  - subject

  - reply_body

- Available for later modules.

## 4. Gmail – Reply to an Email

- Sends the prepared AI response.

- Uses message/thread IDs from the first module.

- Maps:

  - Subject → Parsed JSON subject

  - Body → Parsed JSON reply_body

- Can send HTML or plain text.

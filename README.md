# MailMind

MailMind is an automated email-reply pipeline built with **Make**, **OpenAI**, and **Gmail**.  
It watches incoming emails, analyzes them using AI, generates a structured response, and replies automatically.

## ✨ Features

- Automatically watches a Gmail inbox for new emails.
- Sends email content to OpenAI for analysis and reply generation.
- Extracts structured JSON fields (subject, reply body, metadata).
- Sends the AI-generated reply back to the original thread.
- Modular and expandable.

---

## 🧠 How MailMind Works (Scenario Flow)

1. **Gmail – Watch Emails**  
   Triggers when a new email arrives.

2. **OpenAI – Generate Completion**  
   AI analyzes the email and generates a JSON response:
   ```json
   {
     "subject": "...",
     "reply_body": "..."
   }
3. **JSON – Parse JSON**
Extracts the fields from the AI's output.

4. **Gmail – Reply to an Email**
Sends the reply back to the original sender.

## 📄 License

This project is licensed under the terms of the MIT License.

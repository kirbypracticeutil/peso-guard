A Telegram bot that logs personal expenses via natural language, using n8n and Groq.

## How it works
1. **Telegram Trigger** – receives a message from Telegram.
2. **If** – checks the sender's chat ID against mine; anything else is dropped.
3. **Basic LLM Chain (Groq, `openai/gpt-oss-20b`)** – parses the message into
   `amount`, `category`, `description`, `valid`.
4. **Structured Output Parser** – enforces that JSON shape on the LLM output.
5. **If** – checks `valid`.
   - true → replies "Logged ₱X – category"
   - false → replies with a usage example

## Example
Send: `150 jollibee lunch`
Reply: `Logged ₱150 – food`

## Setup
- Requires a Telegram bot token and a Groq API key, added as n8n credentials.
- Replace the chat ID in the first If node with your own.

## Status
Level 0 complete. Next: Google Sheets logging (Append Row).

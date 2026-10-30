# ChatMaxima extension for Gemini CLI

Build and test ChatMaxima chatbots, design WhatsApp message templates and Flows, and triage your omnichannel inbox from a Gemini CLI conversation.

[ChatMaxima](https://chatmaxima.com/) is a customer messaging platform for WhatsApp, Instagram, Facebook Messenger, Telegram, email and website chat, with a visual chatbot builder and a shared inbox. This extension registers the ChatMaxima remote MCP server (`https://chatmaxima.com/mcp/`) in Gemini CLI, adds a context file with the working rules, and bundles two skills with step-by-step recipes.

## Install

```
gemini extensions install https://github.com/chatmaxima-com/chatmaxima-gemini-cli-extension
```

Then start Gemini CLI and connect your account:

```
/mcp auth chatmaxima
```

A browser window opens on chatmaxima.com. Sign in, choose the workspace Gemini may work in, and allow access. You need a ChatMaxima account; a free trial is available at [chatmaxima.com](https://chatmaxima.com/).

Check the connection with `/mcp list`. The tools you see depend on your role in the workspace you chose.

## What you can do

- **Build a chatbot by describing it.** "Create a bot for my bakery that takes cake orders, asks for the pickup date and phone number, and hands over to a human when asked." Gemini creates the bot, adds and connects blocks (messages, questions, buttons, conditions, AI replies, integrations such as Google Sheets, HubSpot or Shopify), tidies the canvas and runs a scripted test conversation so you see the bot behave before you publish it.
- **Inspect and improve an existing bot.** List your bots, read a bot's flow block by block, read execution logs to see where a conversation went wrong, and apply an edit.
- **WhatsApp templates and Flows.** Draft and validate a message template against Meta's rules (standard, authentication, carousel) and, when you confirm, submit it to Meta for approval. Design WhatsApp Flows, the multi-screen forms customers fill in inside WhatsApp.
- **Triage the inbox.** List and read conversations, show unread counts, assign a conversation, change its status, add labels, and leave internal notes customers never see.

## Example prompts

```
Show me the chatbots in my ChatMaxima workspace.
Explain the conversation flow of my "Store Support" bot step by step.
Create a bot named Store Support Test with buttons for Orders, Returns and Talk to a human, then run a test conversation.
Draft a WhatsApp utility template that confirms an appointment for tomorrow with a Reschedule button. Validate it but do not submit it.
Build a Flow for the website chat that books an appointment: name and phone, then preferred date, then a confirmation screen.
```

## How access works

- You sign in with your own ChatMaxima account using OAuth. Gemini CLI discovers the authorization endpoints and registers itself automatically.
- The tools act only inside the workspace you allowed, limited by your role and plan. Read-only tools and write tools are separate, and every tool carries read-only or destructive annotations.
- Submitting a template to Meta and other actions that cannot be undone are only taken after you confirm.
- Revoke access at any time from **Settings, Connected Apps** in ChatMaxima, or remove the extension with `gemini extensions uninstall chatmaxima`.

## Links

- Documentation: https://docs.chatmaxima.com/mcp
- Gemini connection guide: https://docs.chatmaxima.com/mcp/connect-gemini
- Privacy policy: https://chatmaxima.com/privacy/
- Terms of service: https://chatmaxima.com/tos/
- Support: support@chatmaxima.com

## License

MIT. ChatMaxima is a product of TechMaxima India Private Limited.

# ChatMaxima

This extension connects Gemini CLI to the user's ChatMaxima workspace through the `chatmaxima` MCP server. ChatMaxima is a customer messaging platform for WhatsApp, Instagram, Facebook Messenger, Telegram, email and website chat, with a visual chatbot builder, WhatsApp templates and Flows, and a shared inbox.

Use the ChatMaxima tools when the user asks to build, inspect or change something in their ChatMaxima workspace. For anything else, answer normally without calling them.

## First session

If the user has not connected yet, tell them to run `/mcp auth chatmaxima`, sign in to ChatMaxima in the browser, and choose the workspace to allow. Then follow the `get-started` skill: confirm the connection with `list_workspaces`, let the user pick a workspace if they have more than one, and suggest a first task.

## Rules that always apply

- Never invent workspace, bot, block, template, flow or conversation ids. Get them from a list or get tool, or ask the user.
- If the user can reach more than one workspace, ask which one before creating or changing anything.
- Before a write, make sure the target and the change are what the user asked for. Before anything that cannot be undone, such as deleting a block or submitting a template to Meta, confirm with the user first.
- Report only what the tools returned. If a tool returns an error, show it plainly and never say the action succeeded.
- The tools act only inside the workspace the user allowed, with that user's role. If a tool says the role cannot use a section, pass the message on and suggest asking a workspace admin; do not try other tools to get around it.

## What the tools cover

- Chatbots: `list_bots`, `get_bot`, `create_bot`, `add_block`, `update_block`, `connect_blocks`, `delete_block`, `organize_bot`, `rename_bot`, `run_test`, plus `list_block_types` and `get_block_schema` for the block catalog.
- Executions: `analyze_executions` and `get_execution_detail` to explain why a conversation took a path or failed.
- WhatsApp templates: `get_template_schema`, `compose_whatsapp_template` (validation only, no side effects), `create_whatsapp_template` (submits to Meta, only after the user confirms), `list_whatsapp_templates`, `get_whatsapp_template`.
- WhatsApp Flows: `get_flow_schema`, `create_whatsapp_flow`, `update_whatsapp_flow`, `list_whatsapp_flows`, `get_whatsapp_flow`.
- Inbox: `list_conversations`, `get_conversation`, `inbox_counts`, `add_internal_note`, `update_conversation`.
- Workspace reference data: accounts, labels, statuses, team members, contact lists and attributes, knowledge bases, calendars, integrations and their actions, email templates, media upload.

The `chatmaxima` skill has the step-by-step recipes for building a bot, validating a template and designing a Flow.

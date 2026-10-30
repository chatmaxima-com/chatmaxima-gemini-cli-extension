---
name: chatmaxima
description: How to build and manage ChatMaxima chatbots, WhatsApp templates, Flows and inbox conversations with the ChatMaxima tools.
---

# ChatMaxima

Use the ChatMaxima tools when the user asks to build, inspect or change something in their ChatMaxima workspace.

## Core rules

- Never invent workspace, bot, block, template, flow or conversation ids. Get them from a list or get tool, or ask the user.
- If the user can reach more than one workspace, ask which one before creating or changing anything.
- Before a write, make sure the target and the change are what the user asked for. Before anything that cannot be undone, such as deleting a block or submitting a template to Meta, confirm with the user first.
- Report only what the tools returned. If a tool returns an error, show it plainly and never say the action succeeded.

## Building a chatbot

1. Call `list_block_types` to see the catalog, and `get_block_schema` for each block type before adding it, so the data fields are correct.
2. Call `create_bot`. A new bot starts with a Starting Step (node 7) and a Start Message.
3. Set how the bot starts: ask the user, then call `update_block` on node 7 with a `trigger_type` (keywords with exact_match, starts_with or any, or allow_any for no keyword). Never leave it unset.
4. Add blocks with `add_block`, passing the previous block as `after_node` so each one connects automatically.
5. For branches, wire each extra output (output_2 and up, for example each button) to its target with `connect_blocks`.
6. Call `organize_bot` to tidy the canvas, then `run_test` with a scripted conversation whose first message matches the trigger. Share the transcript and the builder link.
7. If the bot's purpose changed, rename it with `rename_bot`.

## WhatsApp templates

1. Call `get_template_schema`, then validate the draft with `compose_whatsapp_template`. Validating has no side effects.
2. Only when the user confirms, submit it with `create_whatsapp_template`. Submission goes to Meta and cannot be undone.

## Flows

Call `get_flow_schema`, then `create_whatsapp_flow`. Ask whether the flow is for WhatsApp or for the website chat, because the target cannot be changed later.

## Inbox

Use `list_conversations` and `get_conversation` to read, `add_internal_note` for notes that customers do not see, and `update_conversation` for status, labels or assignee.

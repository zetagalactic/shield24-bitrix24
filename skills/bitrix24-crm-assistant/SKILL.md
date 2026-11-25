---
name: bitrix24-crm-assistant
description: Use when the user asks about their Bitrix24 portal — deals, contacts, companies, leads, pipelines, timeline comments, to-dos or tasks — and the shield24-bitrix24 connector tools are available. Explains which connector tool to reach for and how to work safely with the portal.
---

# Working with Bitrix24 through Shield24

The `shield24-bitrix24` connector gives you tools for one Bitrix24 portal, acting as the signed-in person.
Every call runs with that person's own Bitrix24 rights, inside the limits the portal admin set for the
connector. If a tool is missing, the admin has not enabled it; say so instead of looking for a workaround.

## Start with the portal's shape

- Call `portal_schema` (or `crm_pipeline_list` for just pipelines and stages) before filtering or moving
  deals. Stage IDs and custom field names differ on every portal; never guess them.

## Pick the narrowest tool

| The user wants to… | Use |
|---|---|
| find deals, contacts, companies or leads | `crm_deal_search`, `crm_contact_search`, `crm_company_search`, `crm_lead_search` |
| see one record | `crm_deal_get`, `crm_contact_get`, `crm_company_get` |
| get the full picture of a deal | `crm_deal_overview` |
| create or change a deal | `crm_deal_create`, `crm_deal_update` |
| log a note or a follow-up | `crm_timeline_comment_add`, `crm_todo_add` |
| work with tasks | `task_my_list`, `task_get`, `task_create`, `task_update_status` |
| find a colleague | `user_search` |

The generic tools (`bitrix24_method_search`, `bitrix24_read`, `bitrix24_write`, `bitrix24_delete`) exist
only if the admin enabled them. Prefer a named tool whenever one fits.

## Be careful with changes

- Before a write, restate what will change (record, fields, new values) and get the user's go-ahead.
- Never delete unless the user asked for that exact deletion.
- Large lists come back in pages; tell the user when there is more rather than fetching everything.
- If a call is refused (not enabled, read-only, limit reached, reconnect needed), report the reason in plain
  words. Do not retry the same call in a loop.

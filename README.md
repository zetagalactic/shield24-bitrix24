# shield24-bitrix24

A Claude plugin that connects Claude to your **Bitrix24** portal through the **OIA Shield24** connector.
Search and update CRM deals, contacts, companies and leads, add timeline comments and to-dos, and manage
tasks, all from Claude.

> This plugin is published by InfinityBHT, the maker of OIA Shield24. It is not made or endorsed by
> Bitrix24.

## What this plugin connects to

The plugin adds one remote MCP server and nothing else:

| What | Address |
|---|---|
| OIA Shield24 connector (remote MCP, OAuth) | `https://oia-shield24.infinitybht.app/mcp` |

When you use a connector tool, Claude sends the request to that address. OIA Shield24 checks your
connection and your portal admin's settings, then calls **your own Bitrix24 portal's REST API** with your
Bitrix24 account, and returns the result to Claude. No other services are contacted by the plugin.

## Install

In Claude Code:

```
/plugin install shield24-bitrix24 --marketplace zetagalactic/shield24-bitrix24
```

## Before you start

1. Your Bitrix24 portal has the **OIA Shield24** app installed, and your portal admin has created a Claude
   connector in it and allowed you to use it.
2. The first time Claude uses a tool, you sign in: enter your portal address once, sign in to Bitrix24 if
   asked, and approve the connection. You can disconnect at any time from Claude or from the app.

## What Claude can do

- Read: search and open deals, contacts, companies and leads; pipelines and stages; your portal's CRM
  fields; tasks; colleagues.
- Write (only if your admin allows it): create and update deals, add timeline comments and to-dos, create
  tasks and change their status.

Every action runs with **your own Bitrix24 permissions**, inside the limits your admin set. Claude cannot
see or change anything you could not see or change yourself in Bitrix24.

## Contents

- `.mcp.json`: the connector address.
- `skills/bitrix24-crm-assistant`: guidance for Claude on which tool to use and how to make changes safely.

## License

MIT, see [LICENSE](LICENSE).

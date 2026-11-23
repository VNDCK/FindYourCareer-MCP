# Find Your Career MCP

The official MCP server of [Find Your Career](https://findyourcareer.io), a job board that collects openings straight from employer career pages. Connect it to Claude, ChatGPT, Cursor or any other MCP client and search current jobs in conversation.

The server is hosted. There is nothing to install and no API key to copy.

```
https://findyourcareer.io/mcp
```

> This server does not apply to jobs for you. It finds openings and shows their details. You open the link and apply on the employer's site yourself.

## What you can ask for

> "Find remote product roles in the United States with a published salary from $120,000."

> "Which jobs with visa sponsorship in Germany were posted this week for a data analyst?"

> "Put the salary, location and deadline of these six jobs in one table so I can pick."

> "Which new jobs match my saved search today? Show only jobs I have not seen before."

## Connect

**Claude Code**

```bash
claude mcp add --transport http --scope user findyourcareer https://findyourcareer.io/mcp
```

**Cursor, VS Code and other clients that read `mcp.json`**

```json
{
  "mcpServers": {
    "findyourcareer": {
      "type": "http",
      "url": "https://findyourcareer.io/mcp"
    }
  }
}
```

**Claude.ai and ChatGPT**: add the URL as a custom connector in the settings.

Your client opens a browser window on first use. Sign in to Find Your Career and approve the connection. Step-by-step instructions are on the [integration page](https://findyourcareer.io/integrations/mcp).

## Requirements

| | |
| --- | --- |
| Account | Free at [findyourcareer.io](https://findyourcareer.io) |
| Access | A free account gets older jobs in full; the newest jobs come back locked, with title and tags only. A Career Pass opens every job. |
| Client | Any MCP client that supports Streamable HTTP with OAuth |

## Tools

| Tool | What it does |
| --- | --- |
| `search_jobs` | Searches current job listings by role, company, location, country, remote or onsite, seniority, salary and posting date. Up to 25 jobs per page. |
| `get_job_details` | Returns the full description, requirements, benefits and application deadline of one job, with a link to it. |
| `get_new_jobs` | Lists the jobs that are new for your account since you last checked. |
| `get_search_filters` | Returns the supported filter values: countries, currencies, work arrangements, employment types, levels. |
| `get_usage` | Shows what your account can access and, with a Career Pass, how much of your allowance is used. |
| `get_subscription_options` | Shows the Career Pass plans available to your account, with prices and terms. |
| `create_subscription_checkout` | Creates a Stripe checkout for a plan you chose. It does not charge you; you approve the payment in Stripe yourself. |

The search and read tools are read-only. No tool applies to a job, messages an employer or stores a resume.

## Authentication

OAuth 2.1 with PKCE and Dynamic Client Registration. Your client discovers the settings from the server, registers itself and opens a Find Your Career consent screen. Tokens stay in your client. You can disconnect at any time in [your settings](https://findyourcareer.io/settings/integrations).

## What is in this repository

Metadata only. The server is hosted by Find Your Career and its source code is not part of this repository.

```
server.json                  entry in the official MCP Registry (io.findyourcareer/jobs)
.mcp.json                    points at https://findyourcareer.io/mcp over Streamable HTTP
.claude-plugin/plugin.json   Claude plugin manifest
.cursor-plugin/plugin.json   Cursor plugin manifest
glama.json                   maintainer list for Glama
```

## Support

support@findyourcareer.io

## License

MIT, see [LICENSE](LICENSE). The license covers the files in this repository, not the hosted service.

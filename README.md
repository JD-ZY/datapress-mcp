# datapress MCP server: UK & EU business data for AI agents

Give Claude, Cursor, VS Code, ChatGPT or any MCP client live access to **official public business data**:

| Tool | What it returns |
|---|---|
| `datapress--uk-government-tenders` | UK public sector tenders and contract awards (Find a Tender + Contracts Finder) |
| `datapress--global-tenders` | EU tenders (TED) and US federal contracts (USAspending) |
| `datapress--uk-companies-house` | UK companies by name, number, SIC code or incorporation date, with **financials from filed accounts** (net assets, cash, employees) |
| `datapress--eu-company-registers` | Companies from Norway, Finland and France registers + GLEIF LEI |
| `datapress--company-job-boards` | Open jobs from any company on Greenhouse, Lever, Ashby, SmartRecruiters, Workable, Recruitee, Personio or Teamtailor |
| `datapress--app-store-intel` | Apple App Store and Google Play app details, charts and rankings |
| `datapress--domain-checker` | Bulk domain availability across 1,200+ extensions via RDAP/WHOIS, with registrar and expiry dates |

All data comes from official APIs and open data. Personal data is stripped (no named individuals, no registrant contacts).

The server is hosted by [Apify](https://apify.com/datapress). Each tool runs the matching Apify Actor on your account, so there's nothing to install and you pay only per result (fractions of a cent; Apify's free plan includes monthly credit).

## Connect

**Server URL**

```
https://mcp.apify.com/?tools=datapress/uk-government-tenders,datapress/global-tenders,datapress/uk-companies-house,datapress/eu-company-registers,datapress/company-job-boards,datapress/app-store-intel,datapress/domain-checker
```

Clients that support OAuth (Claude, ChatGPT, VS Code) will ask you to sign in to Apify. Otherwise pass your [Apify API token](https://console.apify.com/account/integrations) as `Authorization: Bearer <token>`.

**Claude Code**

```bash
claude mcp add --transport http datapress "https://mcp.apify.com/?tools=datapress/uk-government-tenders,datapress/global-tenders,datapress/uk-companies-house,datapress/eu-company-registers,datapress/company-job-boards,datapress/app-store-intel,datapress/domain-checker"
```

**Cursor / Claude Desktop / other JSON configs**

```json
{
  "mcpServers": {
    "datapress": {
      "url": "https://mcp.apify.com/?tools=datapress/uk-government-tenders,datapress/global-tenders,datapress/uk-companies-house,datapress/eu-company-registers,datapress/company-job-boards,datapress/app-store-intel,datapress/domain-checker",
      "headers": { "Authorization": "Bearer YOUR_APIFY_TOKEN" }
    }
  }
}
```

Only need one or two tools? Remove the others from the `tools=` list.

## Example prompts

- "Find UK council tenders for cleaning services published in the last 7 days."
- "List software companies (SIC 62012) incorporated this month with their latest net assets."
- "Which of brightpath.com, brightpath.io and brightpath.ai are available?"
- "Show all open engineering jobs at Monzo and Revolut."
- "Get the top 50 free finance apps in the UK App Store."

## Links

- Actor pages and full input docs: https://apify.com/datapress
- Apify MCP docs: https://docs.apify.com/platform/integrations/mcp

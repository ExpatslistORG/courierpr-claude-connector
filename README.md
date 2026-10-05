# Courierpr.com for Claude

Courierpr.com is available as a connector in Claude. Ask Claude a question and it answers from Courierpr.com, with a link to the full page on every result. This repo documents the connector. The live, always current version of these docs is at https://courierpr.com/docs/claude.

## About Courierpr.com

Courierpr.com is a press release wire: companies file releases and each is published as a permanent article, organised into six newsroom desks and twenty categories. Visit it at https://courierpr.com.

## What is a Claude connector?

A connector lets Claude use an outside service while it answers you. This one is a Model Context Protocol (MCP) server hosted by Courierpr.com. It needs no account and no API key, and every tool is read-only.

## Add it to Claude

1. In Claude, open Settings, then Connectors.
2. Choose Add custom connector.
3. Paste the endpoint below and choose no authentication if asked.

```
POST https://courierpr.com/api/mcp/claude
Content-Type: application/json
```

Any MCP client that speaks Streamable HTTP works the same way. The included `.mcp.json` is an example config for clients that read one.

## Tools

| Tool | What it does |
|---|---|
| `list_desks` | The six newsroom desks and twenty categories, with slugs and links. |
| `latest_releases` | The newest press releases, optionally within one desk or category. |
| `search_releases` | Full-text search over every published release, optionally within one category. |
| `get_release` | One release: company, category, dateline, date, the opening 120 words and a link to the full page. |
| `how_to_file` | What filing a release involves, with links to the press code and the filing pages. It files nothing. |
| `search / fetch` | The standard connector pair, aliases of search_releases and get_release. |

## Example prompts

- What is new on the science and tech desk this week?
- Search Courierpr.com for press releases about electric vehicles.
- Which desks and categories does Courierpr.com cover?
- How do I publish a press release on Courierpr.com?

## What the connector returns

- Public content only: titles, company names, dates, categories, short summaries and links.
- Releases are company announcements, written by the company they describe. Claude is told to present them as the company statement, not as independent reporting.
- Media contact details are never returned.
- It cannot file, correct or withdraw a release.
- Links carry `utm_source=claude` so analytics can tell visits from Claude apart from other visits. The tag identifies the connector, not you.

## Data and privacy

We receive the name of the tool called and its parameters: a search phrase, a desk, a category or a release slug. We receive no Claude account details, no name, no email address and no conversation history. We keep standard server logs for 30 days and nothing else about connector use. The full policy is at https://courierpr.com/privacy and the terms are at https://courierpr.com/terms.

## Limits

- At most 10 results per call, newest first, no date filter.
- Calls are rate limited per address. Please do not use the connector to copy or bulk-extract the wire.

## Support

Questions, bug reports or removal requests: Use the contact page (https://courierpr.com/contact).

## More from Courierpr.com

- Website: https://courierpr.com
- Developer docs for Claude: https://courierpr.com/docs/claude
- Developer docs for ChatGPT: https://courierpr.com/docs/api
- Browser extension: https://github.com/ExpatsListORG/courierpr-browser-extension
- ChatGPT plugin: https://github.com/ExpatsListORG/courierpr-chatgpt-plugin
- Privacy policy: https://courierpr.com/privacy
- Terms of service: https://courierpr.com/terms
- Contact: https://courierpr.com/contact

## License

MIT. See `LICENSE`.

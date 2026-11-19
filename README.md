# Datafaro MCP: trend research tools for AI agents

Give your AI agent live answers to **"what are people searching for and talking about right now?"**

Three small, fast tools, built for agents (compact outputs with a one-line summary, typical calls in under 10 seconds):

| Tool | What it answers | Example prompt |
|---|---|---|
| **Google Trends** (`datafaro/google-trends-api`) | Search interest over time, top countries, related queries, what's trending now | *"Compare ChatGPT, Claude and Gemini on Google Trends worldwide over the last year."* |
| **Bluesky** (`datafaro/bluesky-scraper`) | Latest posts on any topic, profiles, threads, followers (official Bluesky API) | *"Find the latest Bluesky posts about AI agents and summarize the main opinions."* |
| **Substack** (`datafaro/substack-scraper`) | Latest posts, full text and engagement from any newsletter | *"What did Simon Willison and Ethan Mollick write about this week?"* |

## Connect

This server runs on the hosted [Apify MCP server](https://docs.apify.com/platform/integrations/mcp), configured with the three Datafaro tools. It uses Streamable HTTP and OAuth: add the URL, sign in to Apify (free account) the first time, done.

**Server URL:**

```
https://mcp.apify.com/?tools=datafaro/google-trends-api,datafaro/bluesky-scraper,datafaro/substack-scraper
```

**Claude (claude.ai / Desktop):** Settings → Connectors → Add custom connector → paste the URL.

**Cursor / VS Code / other clients:**

```json
{
  "mcpServers": {
    "datafaro": {
      "url": "https://mcp.apify.com/?tools=datafaro/google-trends-api,datafaro/bluesky-scraper,datafaro/substack-scraper"
    }
  }
}
```

Prefer an API token over OAuth? Add a header: `"headers": {"Authorization": "Bearer <APIFY_TOKEN>"}`.

Only want one tool? Keep just that Actor in the `tools=` list.

## Pricing

Pay per use, billed by Apify. Apify's free plan includes $5/month of credit.

| Tool | Price |
|---|---|
| Google Trends | ~$0.0035 per query (1–5 keywords) |
| Bluesky | $1.00 per 1,000 results |
| Substack | $1.00 per 1,000 posts (full text included) |

Failed and empty results are not charged.

## Notes

- Public data only. Bluesky uses the official AT Protocol API; Substack uses public feeds and never bypasses paywalls.
- Google Trends values are relative (0–100), not absolute search counts.
- Each tool is tested daily.

## Links

- Google Trends: https://apify.com/datafaro/google-trends-api
- Bluesky: https://apify.com/datafaro/bluesky-scraper
- Substack: https://apify.com/datafaro/substack-scraper
- Articles: https://dev.to/data_faro

Issues and feature requests: open an issue in this repository or on the Actor page.

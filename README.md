# TrimCarbon for Cursor and Grok Bot

Estimate the CO₂ of general-aviation flying: for one pilot, for a flight school or club fleet, or from the fuel you burned. TrimCarbon has figures for about 60 aircraft types, from a Cessna 152 to a Beechcraft Baron, based on each type's fuel flow at about 75% power.

This plugin adds:

- **The TrimCarbon MCP server**, a remote server at `https://mcp.trimcarbon.com/mcp` (Streamable HTTP). The estimate tools need no account, sign-in or API key.
- **The `flight-emissions` skill**, which tells the agent which TrimCarbon tool fits each question.

## Install

Install TrimCarbon from the Cursor Marketplace.

To add the server by hand, put this in `~/.cursor/mcp.json` (or `.cursor/mcp.json` in a project):

```json
{
  "mcpServers": {
    "trimcarbon": {
      "url": "https://mcp.trimcarbon.com/mcp"
    }
  }
}
```

## What you can ask

- "What's the CO₂ of 50 hours a year in a Cessna 172?" (4,400 kg a year)
- "Our school flies 600 hours in Cessna 172s and 120 hours in a Piper Seminole. What's our CO₂?" (76,080 kg a year)
- "How much CO₂ from burning 100 US gallons of avgas?" (831 kg)
- "How much CO₂ per flight hour does a Cirrus SR22 emit?" (136 kg an hour)
- "What would it cost to offset that?"

## Tools

| Tool | What it does |
|---|---|
| `search_aircraft` | Finds aircraft types by name or ICAO code, with kg of CO₂ per flight hour |
| `estimate_flight_hours` | CO₂ from hours in one or more aircraft types, per year or in total |
| `estimate_fuel_burn` | CO₂ from avgas 100LL, mogas or Jet A, in US gallons, liters or kg |
| `quote_offset` | TrimCarbon's prices to offset an amount of CO₂, with a link to continue on trimcarbon.com |
| `import_logbook` | A card that reads your ForeFlight, Garmin Pilot or LogTen export on your device and shows the CO₂ by aircraft type. The file is never uploaded; you choose to share the totals |

All tools are read-only. Nothing is bought in the chat: you sign up and pay on trimcarbon.com.

The server also lists account tools (`get_my_account`, `get_my_impact`, `list_my_offsets`, `get_certificate`, `get_api_impact`). They read your own TrimCarbon account after you connect it, which Cursor and Grok Bot can't do yet. See your offsets and certificates on https://trimcarbon.com/account.

## Data

The plugin sends data only to TrimCarbon's MCP server at `https://mcp.trimcarbon.com/mcp`. Each tool call sends the tool's inputs (aircraft types, hours, fuel amounts, or an amount of CO₂ for prices). A logbook file stays on your device; only the totals you share go to the conversation. The server doesn't receive your conversation. TrimCarbon records which tools are used, without names or emails, to improve them. See the [privacy policy](https://trimcarbon.com/legal/privacy-policy).

The figures count the CO₂ from burning fuel only. They leave out fuel production and non-CO₂ effects. Each result links to the trimcarbon.com page that explains it.

## Support

- Setup and details: https://trimcarbon.com/ai
- Contact: contact@trimcarbon.com or https://trimcarbon.com/contact

## License

MIT. See [LICENSE](LICENSE).

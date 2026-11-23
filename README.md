# US Government Public Data MCP Suite (Hosted on Apify)

[![Hosted on Apify](https://img.shields.io/badge/Hosted%20on-Apify%20MCP-00C2FF)](https://apify.com/ferraz_michel)
[![MCP Protocol](https://img.shields.io/badge/MCP-Streamable%20HTTP%20%7C%20npx-6E56CF)](https://mcp.apify.com)
[![US Government Public Data MCP Suite MCP connector](https://glama.ai/mcp/connectors/com.apify.mcp/us-gov-mcp-suite/badges/score.svg)](https://glama.ai/mcp/connectors/com.apify.mcp/us-gov-mcp-suite)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](./LICENSE)

A suite of **7 hosted Model Context Protocol (MCP) servers** giving **Claude Desktop, Cursor, Windsurf, LangGraph, CrewAI, and n8n** direct, token-efficient access to official U.S. government public datasets — with **zero external API keys required** and hosted infrastructure managed on Apify Cloud.

---

## Included Hosted MCP Tools (7 Actors)

| # | MCP Tool | Official US Data Source | Key Use Cases | Pricing | Apify Store |
| :--- | :--- | :--- | :--- | :--- | :--- |
| 1 | **SEC EDGAR Filings, 8-K & XBRL Financials** | U.S. SEC (`data.sec.gov`) | `10-K`, `10-Q`, `8-K` material event decoding & audited US-GAAP XBRL snapshots (`Revenue`, `Net Income`, `Assets`, `Cash`) | PPE (`$5 / 1k`) | [View Actor](https://apify.com/ferraz_michel/sec-edgar-filings-mcp) |
| 2 | **US Tariff, HTS Code & Landed Cost Calculator** | U.S. ITC (`hts.usitc.gov`) | 10-digit HTS inheritance, Chapter 99 Section 301/232, USMCA/FTA exemptions, CBP MPF/HMF & `CN` vs `VN` vs `MX` vs `KR` comparison | PPE (`$5 / 1k`) | [View Actor](https://apify.com/ferraz_michel/usitc-hts-tariff-mcp) |
| 3 | **US 1099-NEC 2026 Threshold & State Compliance** | IRS + 51 US Jurisdictions | 2026 `$2,000` federal vs `$600–$1,200` state filing rules, CF/SF check, 1099-K exceptions & 24% backup withholding | PPE (`$5 / 1k`) | [View Actor](https://apify.com/ferraz_michel/us-1099-nec-state-compliance-mcp) |
| 4 | **openFDA Drug, Medical Device & Food Recall Radar** | U.S. FDA (`api.fda.gov`) | Unified Class I/II/III recall monitoring across drugs, devices, and food with risk scoring | PPE (`$5 / 1k`) | [View Actor](https://apify.com/ferraz_michel/openfda-recall-device-radar) |
| 5 | **OSHA Safety & Compliance Search** | U.S. DOL (`apiprod.dol.gov`) | Workplace safety inspections, citations, penalty sums & top cited OSHA standards by company, state, or NAICS | PPE (`$5 / 1k`) | [View Actor](https://apify.com/ferraz_michel/osha-safety-compliance-mcp) |
| 6 | **EPA ECHO Environmental Compliance Search** | U.S. EPA (`echodata.epa.gov`) | Clean Air (CAA), Clean Water (CWA), RCRA hazardous waste violations & facility environmental risk scoring | PPE (`$5 / 1k`) | [View Actor](https://apify.com/ferraz_michel/epa-echo-environmental-mcp) |
| 7 | **FMCSA & USDOT Carrier Safety, Authority & Leads** | U.S. DOT (`data.transportation.gov`) | Trucking carrier safety vetting, MC/USDOT authority, BIPD insurance coverage & newly registered fleet leads | PPE (`$5 / 1k`) | [View Actor](https://apify.com/ferraz_michel/fmcsa-carrier-safety-mcp) |

---

## Quick Start

### Option 1: Remote Streamable HTTP (Recommended — OAuth)

Connect all 7 tools at once via Apify's official hosted MCP server (`https://mcp.apify.com`) using OAuth (no hardcoded tokens needed).

Add to Cursor (`.cursor/mcp.json`) or any Streamable HTTP MCP client (also included in [`mcp.json`](./mcp.json)):

```json
{
  "mcpServers": {
    "us-gov-data-suite": {
      "transport": "http",
      "url": "https://mcp.apify.com/?actors=ferraz_michel/sec-edgar-filings-mcp,ferraz_michel/usitc-hts-tariff-mcp,ferraz_michel/us-1099-nec-state-compliance-mcp,ferraz_michel/openfda-recall-device-radar,ferraz_michel/osha-safety-compliance-mcp,ferraz_michel/epa-echo-environmental-mcp,ferraz_michel/fmcsa-carrier-safety-mcp"
    }
  }
}
```

#### Individual Remote MCP URLs

| Tool | Remote MCP Endpoint |
| :--- | :--- |
| SEC EDGAR Filings & XBRL | `https://mcp.apify.com/?actors=ferraz_michel/sec-edgar-filings-mcp` |
| USITC HTS Tariff & Landed Cost | `https://mcp.apify.com/?actors=ferraz_michel/usitc-hts-tariff-mcp` |
| US 1099-NEC 2026 Compliance | `https://mcp.apify.com/?actors=ferraz_michel/us-1099-nec-state-compliance-mcp` |
| openFDA Recall Radar | `https://mcp.apify.com/?actors=ferraz_michel/openfda-recall-device-radar` |
| OSHA Safety & Compliance | `https://mcp.apify.com/?actors=ferraz_michel/osha-safety-compliance-mcp` |
| EPA ECHO Environmental | `https://mcp.apify.com/?actors=ferraz_michel/epa-echo-environmental-mcp` |
| FMCSA USDOT Carrier Safety | `https://mcp.apify.com/?actors=ferraz_michel/fmcsa-carrier-safety-mcp` |

---

### Option 2: Local `npx` (`@apify/actors-mcp-server`)

For Claude Desktop (`claude_desktop_config.json`) or clients preferring `stdio` transport (template at [`examples/claude_desktop_config.json`](./examples/claude_desktop_config.json)):

```json
{
  "mcpServers": {
    "us-gov-data-suite": {
      "command": "npx",
      "args": [
        "-y",
        "@apify/actors-mcp-server",
        "--actors",
        "ferraz_michel/sec-edgar-filings-mcp,ferraz_michel/usitc-hts-tariff-mcp,ferraz_michel/us-1099-nec-state-compliance-mcp,ferraz_michel/openfda-recall-device-radar,ferraz_michel/osha-safety-compliance-mcp,ferraz_michel/epa-echo-environmental-mcp,ferraz_michel/fmcsa-carrier-safety-mcp"
      ],
      "env": {
        "APIFY_TOKEN": "YOUR_APIFY_TOKEN"
      }
    }
  }
}
```

---

### Option 3: Direct REST API / Python / n8n

Every Actor can also be invoked synchronously over HTTPS via Apify's REST API:

```bash
curl -X POST "https://api.apify.com/v2/acts/ferraz_michel~sec-edgar-filings-mcp/run-sync-get-dataset-items?token=YOUR_APIFY_TOKEN" \
  -H "Content-Type: application/json" \
  -d '{
    "tickersOrCiks": ["AAPL", "NVDA"],
    "forms": ["10-K", "8-K"],
    "includeFinancialSnapshot": true,
    "maxFilingsPerCompany": 3,
    "outputMode": "mcp_summary"
  }'
```

---

## Why `outputMode: "mcp_summary"`?

Government APIs are notoriously bloated for LLM context windows:
- Raw **SEC EDGAR `companyfacts` XBRL** files routinely exceed **4 MB+** per company;
- Raw **USITC HTS** 10-digit statistical codes omit tariff rates stored on 8-digit parent headings;
- Raw **EPA ECHO** queries require two-step `QueryID` orchestration;
- Raw **DOL OSHA** endpoints cap responses at 200 rows without joining violations.

Passing `"outputMode": "mcp_summary"` compresses multi-megabyte responses into **~2 KB structured JSON digests** with pre-computed risk verdicts, financial margins, and sourcing savings ready for AI agent reasoning.

---

## Example Prompts

See [`examples/prompts.md`](./examples/prompts.md) for ready-to-use prompts across:
- Equity Research (`AAPL` / `NVDA` SEC filings & XBRL metrics)
- Import & E-Commerce Sourcing (HTS `8507.60` landed cost across `CN`, `VN`, `MX`, `KR`)
- CPA & Accounts Payable Compliance (2026 Form 1099-NEC state rules & 24% withholding)
- Healthcare & Legal Recall Monitoring (Class I openFDA medical device recalls)
- Supply Chain, Logistics & ESG Due Diligence (OSHA, EPA ECHO & FMCSA vetting)

---

## License

This public documentation and configuration showcase repository is licensed under the [MIT License](./LICENSE).

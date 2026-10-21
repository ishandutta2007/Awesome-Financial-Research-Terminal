# Awesome-Financial-Research-Terminal

# Top Financial Research Terminal Ecosystem

**Curated List of SaaS Products & Open-Source GitHub Projects**  
*Focused on Investment Research, Market Data Aggregation & AI-Native Analyst Workflows*  
**Last updated: October 2026**

This repository tracks notable **SaaS platforms** and **open-source projects** for **Financial Research Terminals**. These tools enable analysts, portfolio managers, and researchers to access market data, financial statements, filings, and analytical workflows—increasingly augmented with AI agents that can query data and synthesize intelligence.

**Examples** include Bloomberg Terminal, FactSet, LSEG Workspace (Refinitiv Eikon), S&P Capital IQ, PitchBook, AlphaSense, Morningstar Direct, Tegus, Sentieo, and YCharts (the category leaders).

**Open-source emphasis**: This section is heavily expanded with every major active project for self-hosting, data provider abstraction, and transparent financial research—ideal for independent analysts, quant developers, and small funds that need institutional-grade data access without $30,000-per-seat terminal costs. The open-source landscape is anchored by **OpenBB** (the leading open data platform for analysts and AI agents with 69,000+ GitHub stars ), with specialized options like **bbterm** for lightweight terminal-style TUI workflows and emerging MCP servers for AI-native financial data access.

Contributions welcome! Open a PR to add/update entries. Keep descriptions factual and link to official sites.

## Table of Contents
- [SaaS/Hosted Platforms](#saas-hosted-platforms)
- [Open-Source GitHub Projects](#open-source-github-projects)
- [How to Contribute](#how-to-contribute)
- [Disclaimer](#disclaimer)

## SaaS/Hosted Platforms

- **[Bloomberg Terminal](https://www.bloomberg.com/professional/)**  
  The undisputed institutional standard, with published pricing at approximately **$31,980/year per single seat** (~$28,320/seat on multi-seat contracts) . Dominates fixed income, FX, and trading desks primarily because of its proprietary **IB Chat messaging network**—the seat becomes more valuable the more counterparties also have one. Uniform pricing with minimal negotiation leverage until enterprise volume. Interface is dated by modern standards, but the network effect remains unassailable .

- **[FactSet](https://www.factset.com/)**  
  Modular, quote-only pricing with third-party reports ranging from **~$4,000 (light package) to ~$50,000 (loaded quant seat)**, and enterprise 25+ seat contracts commonly at **$9,000–$14,000/seat** . Best-in-class for **equity research workflows and portfolio analytics**. The modular structure means a narrow seat can undercut everyone, while a fully loaded one can exceed Bloomberg .

- **[LSEG Workspace (Refinitiv Eikon)](https://www.lseg.com/en/data-analytics/products/workspace)**  
  Quote-only, with full seats commonly reported around **~$22,000/user/year** and narrow configurations from **~$3,600** . Strong in **FX, ESG data, global equities, and league tables**. Named-user license plus separately metered data entitlements—two firms can pay vastly different per-seat amounts without either negotiating poorly .

- **[S&P Capital IQ](https://www.capitaliq.com/)**  
  Quote-only, scoped primarily to **private-company data and deal intelligence**. For many firms it serves as a complementary seat rather than a Bloomberg replacement. APAC coverage has improved post-CRISIL acquisition but still lags Bloomberg and LSEG for Indonesia, Vietnam, and the Philippines .

- **[PitchBook](https://pitchbook.com/)**  
  Private markets data platform covering venture capital, private equity, and M&A. Strong for deal sourcing, company profiles, and investor databases. Typically purchased as a specialized complement to broader terminals.

- **[AlphaSense](https://www.alpha-sense.com/)**  
  AI-powered market intelligence platform specializing in search across broker research, earnings calls, filings, and expert content. Strong for qualitative research synthesis rather than raw quantitative data access.

- **[Morningstar Direct](https://www.morningstar.com/products/direct)**  
  Investment research platform focused on fund and ETF data, portfolio analysis, and manager research. The standard for mutual fund and wealth management workflows.

- **[Tegus](https://www.tegus.com/)**  
  Expert transcript and primary research platform. Provides access to expert calls and interviews for due diligence and industry research.

- **[Sentieo (AlphaSense)](https://www.sentieo.com/)**  
  Financial document search and research management platform. Acquired by AlphaSense and integrated into their broader intelligence offering.

- **[YCharts](https://ycharts.com/)**  
  Web-based financial data and charting platform aimed at advisors and individual investors. More accessible pricing than institutional terminals, with strong visualization capabilities.

## Open-Source GitHub Projects

- **[OpenBB Platform](https://github.com/OpenBB-finance/OpenBB)**  
  The leading open-source financial data platform for analysts, quants, and **AI agents**. Provides a **standardized Python SDK** that abstracts hundreds of financial data providers (Polygon, FMP, Benzinga, FRED, SEC EDGAR, and more) behind a single interface . As of v4.5 (June 2026), deep agentic integration allows LLMs to natively execute financial commands and synthesize market intelligence . **Key strengths**: provider-agnostic (switch data sources with zero code changes), extensive asset coverage (equities, options, crypto, forex, macro, fixed income), and AI-native design with structured JSON outputs . 69,000+ GitHub stars, Python-based . **Limitations**: requires individual API keys for premium providers, and the sheer volume of endpoints can overwhelm without orchestration . Best for developers and quants building custom research pipelines or AI agents that need reliable, structured financial data.

- **[OpenBB Workspace (Snowflake Native App)](https://openbb.co/)**  
  Enterprise UI layer for OpenBB that transforms raw data into interactive dashboards and AI workflows. Launched as a **Snowflake Native App** in February 2026, enabling teams to build analytics applications, deploy AI agents, and share self-service workflows **within their Snowflake environment** . The "connect once, consume everywhere" architecture links the open-source data platform to the Workspace frontend via a local API server (`openbb-api`) running at `127.0.0.1:6900` . Best for firms already using Snowflake that want an OpenBB-powered research surface without building their own frontend.

- **[bbterm](https://github.com/sgjlee0520/bbterm)**  
  A local, keyboard-driven **Bloomberg-style TUI** that runs entirely in your terminal. Features candlestick charts, watchlists, statistics panels, SEC EDGAR fundamentals, and recent filings. Backed by a **DuckDB local cache** so it works offline once data is fetched and costs almost nothing to run . Data providers: Databento (paid, optional) for historical bars, yfinance (free fallback), and SEC EDGAR (free, official) for fundamentals . Installable via `pipx install bbterm-tui`. Best for terminal-native users who want a lightweight, zero-cost research interface without leaving the command line.

### Additional Strong Open-Source Options

- **OpenBB App Marketplace** — Discovery layer inside Workspace where data providers publish interactive apps with charts, tables, and AI-queryable widgets. Analysts can trial real data immediately without procurement cycles .
- **Agent Rita** — Open-source financial agent from OpenBB that can search widgets, query data, run SQL, and build dashboards inside the Workspace. Teams choose their own model (frontier or local) and extend it for custom workflows .
- **Equibles MCP Server** — Self-hosted financial data server for AI agents, exposing 62+ MCP tools covering SEC filings, XBRL financials, 13F holdings, insider trades, FRED, CFTC positioning, and daily prices . Best for teams building AI-native research agents that need MCP-compatible data access.
- **Frameworks for building custom systems**: Use **OpenBB Platform** as the data abstraction layer, connect it to **OpenBB Workspace** or a custom Streamlit/Dash frontend, and add **Agent Rita** or a custom MCP server for LLM-driven research workflows. For terminal-only workflows, **bbterm** provides a lightweight alternative without the Python ecosystem overhead.

## How to Contribute

1. Fork the repo.
2. Add/edit entries in `README.md` (follow existing format).
3. Include: name, link, 1–2 sentence description, and whether it's SaaS or open-source.
4. Submit PR with a short explanation.

Star the repo if you find it useful!

## Disclaimer

- This is a **community-curated** list — not exhaustive and not an endorsement.
- Institutional terminal pricing is quote-only for most vendors (except Bloomberg); reported figures are third-party estimates and vary significantly with scope and entitlements .
- Open-source financial data platforms require managing individual provider API keys and may not include premium licensed data (broker research, real-time exchange feeds) available on institutional terminals.
- None of these tools provide investment advice; data accuracy and completeness should be independently verified before use in trading or investment decisions.

---

**Made for independent analysts, quant developers, small funds, and researchers who believe financial intelligence should be accessible beyond the $30K seat.**  
Let's make financial research more open, AI-native, and accessible.

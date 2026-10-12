<p align="center"><img src="assets/logo.svg" width="80" alt="AI Safety HOT"></p>

<p align="center"><a href="README.md">简体中文</a> · <a href="README.en.md">English</a> · <a href="README.ja.md">日本語</a></p>

<h1 align="center">AI Safety HOT Hub</h1>

<p align="center"><a href="https://aisafetyhot.com"><img src="assets/news-monitor-demo.gif" width="1000" alt="AI Safety HOT News Monitor"></a></p>

Agent connection guide and public briefing archive for [AI Safety HOT](https://aisafetyhot.com). The website offers English and Chinese. Entries awaiting translation retain their original language.

## Thank you, and an access update

Thank you for your support! AI Safety Hub received substantial traffic within its first few days. We also observed suspicious requests that looked like potential attacks and blocked them. As AI safety researchers, we will continue maintaining the site's defenses.

To support service costs, our accumulated work and long-term maintenance, **anonymous access now covers recent discovery rather than every dataset**. We continue improving access to recent information:

| Scope | Available content |
| --- | --- |
| Public News API | News originally published in the last **7 days**: titles, excerpts up to **160 characters**, known original dates, source and website links; search and pagination |
| Selected papers | Up to **5** recent selected paper titles and links |
| Daily briefs and events | News excerpts from daily editions within the last 7 days, and recent source reports for an event |
| Full readings/bodies, historical queries, weekly/monthly reports, snapshots and incremental synchronization | Read authorization required; contact [wuy7117@gmail.com](mailto:wuy7117@gmail.com) |

Unknown original dates do not become recent through ingestion. The website remains free to read; public briefs need no login.

<a id="website"></a>

## Read on the website

<!-- daily:start -->
### 2026-10-12

[English daily](en/daily/2026/2026-10-12.md) · [English website](https://aisafetyhot.com/en/daily/2026-10-12) · [Chinese edition](daily/2026/2026-10-12.md)
<!-- daily:end -->

[Overview](https://aisafetyhot.com/) · [News](https://aisafetyhot.com/featured) · [Papers](https://aisafetyhot.com/papers) · [Events](https://aisafetyhot.com/hot) · [Daily](https://aisafetyhot.com/daily) · [Conferences](https://aisafetyhot.com/conferences)

News freshness uses original publication dates, including the previous day's North American news. The same daily edition is updated as new reports arrive. Full existing paper readings remain on detail pages. Report errors on the [board](https://aisafetyhot.com/board).

<a id="agent"></a>

## Connect your Agent

Public briefs need no API key. Use **Streamable HTTP**, run a command below, then reopen the client session.

**Codex**

```bash
codex mcp add aisafetyhot --url https://aisafetyhot.com/api/mcp
```

**Claude Code**

```bash
claude mcp add --transport http --scope user aisafetyhot https://aisafetyhot.com/api/mcp
```

| MCP tool | Anonymous scope |
| --- | --- |
| `aisafetyhot_get_latest` | 24h/7d News excerpts and selected paper links |
| `aisafetyhot_search` | Search and paginate within the same recent News scope |
| `aisafetyhot_get_content` | Recent News excerpts or current selected paper links; `depth=summary` |
| `aisafetyhot_get_hot_topics` | Current event titles, ranks and reading links |
| `aisafetyhot_get_story` | Recent News excerpts and links for an event; `depth=summary` |
| `aisafetyhot_get_daily` | News briefs from daily editions within the last 7 days; `period=daily` |
| `aisafetyhot_get_topics` | Topic names, slugs and definitions |

<a id="examples"></a>

### Try it

Call `get_latest({window:"7d",mode:"all",limit:10})`, then use returned IDs for summaries. Search with `search({q:"prompt injection",window:"7d",mode:"all"})`. Keep filters unchanged when following `page.nextCursor` until `page.hasMore=false`.

`mode=all` includes all News within the permitted window. `window=all`, `depth=full` and `mode=snapshot/changes` require authorization. Original dates and ingestion dates remain separate.

Anonymous MCP, REST and RSS share a per-IP quota of 60 requests/minute and 1,000/UTC day; excess requests return 429 and `Retry-After`. Authorized reads use `Authorization: Bearer <token>`, without admin or write access. Invalid credentials return 401; out-of-scope reads return 403 or MCP `authorization_required`.

[Guide (Chinese)](docs/agent.md) · [Examples (Chinese)](docs/mcp-examples.md) · [Agent Skill](skills/aisafetyhot/SKILL.md) · [OpenAPI](https://aisafetyhot.com/openapi-v1.json)

<a id="daily"></a>

## Daily briefs

[Latest brief (Chinese)](README.md#daily) · [Daily archive](daily) · [Full website daily](https://aisafetyhot.com/daily)

The existing publisher checks every 15 minutes. Digest bodies are primarily Chinese; this README provides English navigation.

<a id="papers"></a>

## Paper links and archives

From **2026-10-12**, daily exports contain up to 5 selected paper titles, original dates and links in Markdown, BibTeX and JSON. Paper summaries, quick reads and detailed commentary are no longer automatically exported. Files use the Beijing ingestion day; original publication dates are recorded separately.

Previously published archives remain available. Changing an API cannot recall copies already downloaded. Export reconciliation covers the selected link set; other papers remain readable on the website.

[Latest downloads (Chinese)](README.md#papers) · [Papers](papers) · [Daily archive](daily) · [2026 archive](archive/2026.md) · [Sync record](status.json)

## Support and feedback

Please give the project a Star or [buy the author a coffee](https://buymeacoffee.com/wuyoscar) if it saves you time. Thanks to AIHOT, Security of AI, and the publications, open-source frameworks and communities that inspired this project.

<img src="assets/wechat-pay.png" width="160" alt="WeChat support QR code">

<p align="center"><img src="assets/logo.svg" width="80" alt="AI Safety HOT"></p>

<h1 align="center">AI Safety HOT Hub</h1>

<p align="center"><b>One command, and your agent keeps up with AI safety: jailbreaks, prompt injection, agent security, evals, incidents and policy, plus 30 hand-picked papers every day.</b></p>

<p align="center">
  <a href="https://aisafetyhot.com/en"><img src="https://img.shields.io/badge/website-aisafetyhot.com-e4572e" alt="website"></a>
  <a href="https://aisafetyhot.com/api/mcp"><img src="https://img.shields.io/badge/MCP-streamable%20http-6f42c1" alt="MCP"></a>
  <a href="#skills"><img src="https://img.shields.io/badge/skills-6-2ea44f" alt="skills"></a>
  <a href="daily-papers"><img src="https://img.shields.io/badge/papers-30%2Fday-0969da" alt="daily papers"></a>
  <a href="https://github.com/wuyoscar/AISafetyHot-Hub/stargazers"><img src="https://img.shields.io/github/stars/wuyoscar/AISafetyHot-Hub?style=flat" alt="stars"></a>
</p>

<p align="center"><a href="README.md">简体中文</a> · <a href="README.en.md">English</a> · <a href="README.ja.md">日本語</a></p>

<p align="center"><a href="https://aisafetyhot.com/en"><img src="assets/news-monitor-demo.webp" width="1000" alt="AI Safety HOT"></a></p>

## Install

**Claude Code** (skills and MCP in one go)

```bash
/plugin marketplace add wuyoscar/AISafetyHot-Hub
/plugin install aisafetyhot@aisafetyhot-hub
```

**Codex / Cursor / other agents**

```bash
npx skills add wuyoscar/AISafetyHot-Hub
codex mcp add aisafetyhot --url https://aisafetyhot.com/api/mcp
```

No API key. Any other client: add the MCP server `https://aisafetyhot.com/api/mcp` (Streamable HTTP).

<a id="skills"></a>

## Skills

Just ask in plain words; the agent picks the skill:

| Skill | What it does | Try |
| --- | --- | --- |
| [`aisafety-brief`](skills/aisafety-brief/SKILL.md) | AI safety brief for the last 24 hours or 7 days | "What happened in AI safety this week?" |
| [`aisafety-paper-scout`](skills/aisafety-paper-scout/SKILL.md) | Papers on a direction, one line each, with BibTeX | "Find 15 papers on prompt injection against agents, with BibTeX" |
| [`aisafety-related-work`](skills/aisafety-related-work/SKILL.md) | Draft a related-work section from your abstract | "Write related work for my reward hacking paper" |
| [`aisafety-lab-watch`](skills/aisafety-lab-watch/SKILL.md) | One lab's safety news lately | "What has Anthropic done on safety this week?" |
| [`aisafety-incident-check`](skills/aisafety-incident-check/SKILL.md) | Recent incidents for a model or tool | "Any new vulnerabilities in Cursor lately?" |
| [`aisafetyhot`](skills/aisafetyhot/SKILL.md) | The MCP tools (what the others build on) | — |

MCP tools and what anonymous access covers: [agent guide](docs/agent.md) and [examples](docs/mcp-examples.md).

## The website

[aisafetyhot.com](https://aisafetyhot.com/en) is free to read, in Chinese and English.

**[Overview](https://aisafetyhot.com/en)**: where the material comes from, which directions it lands in, and what is hot right now.

<img src="assets/site-overview.webp" width="900" alt="Overview">

**[News flow](https://aisafetyhot.com/en)**: each story flows from its source to its direction; topics light up as the news reaches them.

<img src="assets/site-news-flow.webp" width="900" alt="News flow">

**[News](https://aisafetyhot.com/en/featured)**: the editors' timeline, a short read and the original link for each story; trending topics on the side.

<img src="assets/site-featured.webp" width="900" alt="News">

**[Hot](https://aisafetyhot.com/en/hot)**: reports of the same event grouped into one, ranked by attention, with a heat curve.

<img src="assets/site-hot.webp" width="900" alt="Hot">

**[Papers](https://aisafetyhot.com/en/papers)**: nearly two thousand AI safety papers, filtered by direction and type, each with one line and a quick read.

<img src="assets/site-papers.webp" width="900" alt="Papers">

**[Conferences](https://aisafetyhot.com/en/conferences)**: AI safety papers from ICLR, ICML, NeurIPS, ACL and the big four security venues (S&P, USENIX Security, CCS, NDSS), grouped by direction.

<img src="assets/site-conferences.webp" width="900" alt="Conferences">

**[Daily](https://aisafetyhot.com/en/daily)**: one issue a day, grouped by direction, updated as the day goes on.

<img src="assets/site-daily.webp" width="900" alt="Daily">

Spotted a mistake? Tell us on the [board](https://aisafetyhot.com/board).

## Daily papers

Every day 30 papers from the library, never repeated, only from well-known researchers, top labs and strong university groups: half from the last two months, the rest from the last half year and earlier, conference papers included; newer first. Today's list and the index by direction are in [daily-papers](daily-papers) (one-liners in Chinese).

## Support

If it helps, a Star is welcome, or [buy the author a coffee](https://buymeacoffee.com/wuyoscar).

<img src="assets/wechat-pay.png" width="160" alt="WeChat support QR code">

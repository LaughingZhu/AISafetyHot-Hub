---
name: aisafety-incident-check
description: Check whether an AI model, agent or product (e.g. Claude Code, Cursor, Copilot, ChatGPT, an MCP server, an open-weight model) has had recent security incidents, vulnerabilities, jailbreaks or prompt-injection findings, from AI Safety HOT. Use before adopting a tool or when the user asks "is X safe / has X been hacked lately".
---

# Incident check

1. Call `aisafetyhot_search` with `q: <product or model name>`, `window: "7d"`, `mode: "all"`, `limit: 40`; repeat with a common alias if few results (e.g. "Claude Code" and "Anthropic agent").
2. Call `aisafetyhot_get_latest` with `category: "incident"`, `window: "7d"`, `mode: "all"` and keep items naming the product.
3. For each hit, `aisafetyhot_get_content` (`id`, `depth: "summary"`) for the short summary.
4. Answer with a table: date · what was found (vulnerability / jailbreak / prompt injection / data leak / misuse) · affected versions or setting as stated · fixed or not (only if the source says) · original link.
5. Say plainly when nothing was found in the last 7 days — that is not proof of safety; older history is on https://aisafetyhot.com. Never reproduce exploit payloads or attack prompts from the sources.

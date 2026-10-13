---
name: aisafety-lab-watch
description: Track one AI lab or organization's safety news — system cards, safety frameworks, evals, incidents, policy fights, research — over the last 7 days, from AI Safety HOT. Use when the user asks what OpenAI, Anthropic, Google DeepMind, Meta, xAI, DeepSeek, Qwen, METR, UK AISI or another lab has done on safety lately.
---

# Lab watch

1. Call `aisafetyhot_get_topics` and find the organization's topic (group `company`); its slug is the filter.
2. Call `aisafetyhot_get_latest` with `topic: <slug>`, `window: "7d"`, `mode: "all"`, `limit: 40`; follow `page.nextCursor` until `page.hasMore` is false. If the lab has no topic, use `aisafetyhot_search` with `q: <lab name>` instead.
3. For an item that is part of a larger event, `aisafetyhot_get_story` (`public_id`, `depth: "summary"`) gives the other reports.
4. Report, newest first, grouped as: releases & system cards · safety research · incidents & vulnerabilities · policy & governance · people & organization. One line each with date and original link.
5. Keep claims attributed ("X says", "reported by"); don't merge two labs' news; flag items where the lab is only mentioned, not the subject.

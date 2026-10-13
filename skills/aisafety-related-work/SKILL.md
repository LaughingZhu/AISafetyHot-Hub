---
name: aisafety-related-work
description: Draft a related-work section for an AI safety paper or project from the AI Safety HOT paper library, grouped by line of work, with BibTeX. Use when the user gives a paper title, abstract or idea and asks for related work, prior work, or citations.
---

# Related work from AI Safety HOT

1. Read the user's title/abstract. List its 2–4 core ideas (threat model, method, setting, evaluation).
2. Use the `aisafety-paper-scout` data sources: map each idea to direction slugs (`aisafetyhot_get_topics`), fetch `daily-papers/topics/<slug>.json` from `https://raw.githubusercontent.com/wuyoscar/AISafetyHot-Hub/main/`, and keep papers whose `title` or `line` matches the ideas.
3. Group the kept papers into 2–4 lines of work. For each group write one paragraph: what the line does, the representative papers (cite as [n]), and how the user's work differs — state the difference only from what the user told you.
4. End with the numbered reference list and BibTeX (arXiv: `@misc` with `eprint`; conference: `@inproceedings` with venue and year). No invented authors, venues or results; say "per the paper's one-line summary" where you only have `line`.
5. Tell the user which directions had few matches so they can search elsewhere.

---
title: Built-in memory mirror
spine: memory
type: memory
status: auto
source: agent-memory
updated: 2026-11-04
---

# Built-in memory mirror

> Auto-maintained by the `hwiki` memory provider. Promote durable
> conclusions into the curated wiki rather than editing in place.

## Log

- **2026-10-27** — Content pipeline paths: Drafts at '/Мои статьи/drafts', Habr at '/Мои статьи/destinations/habr', LinkedIn at '/Мои статьи/destinations/linkedin'. _(source: builtin:memory via assistant_tool)_
- **2026-10-27** — Content pipeline (Мои Статьи): Private drafts in 'my-drafts' (User only). Collaboration drafts in 'destinations/habr/drafts' and 'destinations/linkedin/drafts'. Publishing involves moving from /drafts to parent folder while preserving ordinal numbering. _(source: builtin:memory via assistant_tool)_
- **2026-10-27** — Articles (Мои Статьи) must include YAML properties: tags, Аудитория (новичок/опытный/эксперт), Время на чтение, Дата создания. Preserve original draft language. Habr = 5-10 pages technical; LinkedIn = 1-2 pages concise. _(source: builtin:memory via assistant_tool)_
- **2026-11-04** — Whenever a skill is created or updated using skill_manage, the agent MUST mirror the content to the Obsidian vault at /mnt/d/Google Диск/Мои заметки/Agents/Hermes Agent/skills/<skill-name>.md for user visibility and Git version control. _(source: builtin:memory via assistant_tool)_

# Workflow: Content Pipeline (Мои Статьи)

This document is the **Source of Truth** for how Hermes Agent manages the creation and publishing of articles.

## 📂 Directory Structure

- **Private Drafts**: `/Мои статьи/my-drafts`
  - 🔴 **Strict Rule**: For User only. Agents must NOT read or write here unless explicitly requested.
- **Habr Collaboration**: `/Мои статьи/destinations/habr/drafts`
  - 🟢 Shared working area for User and Agent.
- **LinkedIn Collaboration**: `/Мои статьи/destinations/linkedin/drafts`
  - 🟢 Shared working area for User and Agent.
- **Published Habr**: `/Мои статьи/destinations/habr`
- **Published LinkedIn**: `/Мои статьи/destinations/linkedin`

## 🚀 Publishing Process

When a draft is ready for publishing:
1. **Move**: Move the file from the `/drafts` subfolder to the parent destination folder.
2. **Cleanup**: Delete the original file from the `/drafts` folder.
3. **Preserve Naming**: Maintain the ordinal numbering in the filename (e.g., `1 - Title.md`, `2 - Title.md`).

## 📝 Content Standards

### General Rules
- **Language**: Preserve the language of the original draft (Russian or English).
- **Asset Preservation**: ALWAYS preserve image links and internal wiki-links (e.g., `![[image.png]]`). Never strip or forget screenshots when adapting content.
- **Note Properties**: Every note must start with the following YAML frontmatter:
  ```yaml
  ---
  tags:
    - <tag1>
    - <tag2>
  Аудитория: <новичок|опытный|эксперт>
  Время на чтение: <minutes>
  Дата создания: <current date>
  ---
  ```

### Platform-Specifics
- **Habr**: 5-10 pages, structured, deep technical details.
- **LinkedIn**: 1-2 pages, concise, low technical noise.

---
*This document is mirrored in the `obsidian-content-workflow` skill. If you change these rules here, tell the agent to "update the skill from this note".*

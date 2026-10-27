---
tags:
  - AI
  - Obsidian
  - LLM
Аудитория: опытный
Время на чтение: 2 минуты
Дата создания: 2026-10-27
---
# Как связать локальную LLM с Obsidian через OpenCode и Ollama 🚀

Хотите использовать мощные модели вроде `gemma4:31b-cloud` прямо в своих заметках Obsidian? Вот проверенный стек для этого:

🛠 **Стек:**
- **Ollama** (в WSL2) — движок для моделей.
- **OpenCode** — мост между движком и интерфейсом.
- **Claudian Plugin** — интеграция в Obsidian.

🔑 **Главные советы по настройке:**
1. **WSL2 — это база.** Ставьте Ollama внутри Ubuntu в WSL2, чтобы избежать проблем с портами и сетевой связностью Windows.
2. **Ошибка 401?** Если модель "не пускает", просто введите `ollama signin` в терминале WSL.
3. **Конфиг:** Настройте `opencode.jsonc`, указав правильный `baseURL` (обычно `http://localhost:11434/v1`).

![[obsidian-claudian-opencode-provider.png]]

Теперь ваш Obsidian превращается в полноценный AI-хаб. Пробуйте! ⚡️

#AI #Obsidian #LLM #Ollama #OpenCode #Productivity

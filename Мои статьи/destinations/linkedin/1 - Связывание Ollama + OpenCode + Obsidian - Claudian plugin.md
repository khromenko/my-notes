---
tags:
  - AI
  - Obsidian
  - LLM
Аудитория: опытный
Время на чтение: 2 минуты
Дата создания: 2026-10-27
---
# Как связать мощную LLM с Obsidian через OpenCode и Ollama 🚀

Хотите использовать мощные модели вроде `gemma4:31b-cloud` прямо в своей базе знаний  Obsidian совершенно бесплатно, не загружая свои ресурсы, и без VPN? Вот проверенный способ для этого:

🛠 **Стек:**
- **Ollama** (в WSL2) — движок для моделей.
- **OpenCode** — мост между движком и интерфейсом.
- **Claudian Plugin** — интеграция в Obsidian.

🔑 **Главные советы по настройке:**
1. **WSL .** Ставьте Ollama внутри Ubuntu в WSL2, чтобы избежать проблем с портами и сетевой связностью Windows, не забудьте выполнить `ollama signin` в терминале WSL.
2. **Конфиг:** Настройте `opencode.jsonc`, указав  провайдера и модель из локальной Ollama (`"baseURL": "http://localhost:11434/v1"`,  `"apiKey": "ollama"` и модель `"model": "ollama/gemma4:31b-cloud"`).
3. Укажите провайдер Opencode в настройка Claudian

Теперь ваш Obsidian превращается в полноценный AI-хаб. Пробуйте! ⚡️

![[obsidian-claudian-opencode-apply-agent.png]]

#AI #Obsidian #LLM #Ollama #OpenCode #Productivity

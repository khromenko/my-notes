# Руководство: Запуск Hermes Agent с Ollama и Obsidian

Это руководство описывает, как настроить Hermes Agent для использования локальных моделей через Ollama и интегрировать его с хранилищем Obsidian для долговременной памяти.
В этом руководстве показано, как использовать облачную модель Ollama `gemma4:31b-cloud`, которая бесплатна в рамках определенной квоты (которая довольно велика).

## 1. Конфигурация модели (Ollama)
После установки Hermes Agent настройте его на использование вашего локального экземпляра Ollama. Отредактируйте конфигурационный файл, расположенный по адресу `~/.hermes/config.yaml`.
Также вы можете добавить другие локальные модели Ollama.

**Пример конфигурации:**
```yaml
model:
  default: "gemma4:31b-cloud"
  provider: "custom"
  base_url: "http://localhost:11434/v1"

custom_providers:
  - name: Ollama-local
    base_url: http://localhost:11434/v1
    model: gemma4:31b-cloud
    models:
      qwen2.5-coder:3b-base: {}
      qwen2.5-coder:1.5b-base: {}
    models_discovered: true
```

## 2. Проверка настройки
Выполните следующую команду, чтобы убедиться, что агент правильно взаимодействует с моделью:

```bash
hermes chat -q "Reply with one sentence confirming Hermes works."
```
При правильной настройке агент ответит, используя указанную модель (например, gemma4:31b через локальную Ollama).

![[hermes_agent_ollama_connect.png]]

## 3. Подключение Hermes Agent к Obsidian
Чтобы разрешить Hermes Agent читать и записывать ваши заметки, выполните следующие действия:

### 3.1. Настройка пути к хранилищу (Vault)
Добавьте абсолютный путь к вашему хранилищу Obsidian в файл `.env`:
```env
OBSIDIAN_VAULT_PATH="/mnt/d/<путь_к_вашим_заметкам>/Мои заметки"
```

### 3.2. Установка и настройка плагина `hwiki`
Плагин `hwiki` превращает папку с Markdown-файлами в долговременную память агента.

1. **Установка плагина:**
   ```bash
   hermes plugins install https://github.com/ottosulin/hwiki
   ```

2. **Инициализация настройки памяти:**
   ```bash
   hermes memory setup
   ```
   При появлении запроса выберите `hwiki` в качестве провайдера памяти.

3. **Настройка пути к Wiki:**
   Укажите путь к папке памяти в мастере настройки.
   *Пример пути:* `/mnt/d/<путь_к_вашим_заметкам>/Мои заметки/Agents/Hermes Agent`

   **Примечание по кодировке путей:** Если возникнут проблемы с символами, отличными от ASCII (например, кириллицей) в пути, возможно, потребуется отредактировать конфигурационный файл напрямую.

   **Прямая конфигурация (`~/.hermes/hwiki.json`):**
   ```json
   {
     "wiki_path": "/mnt/d/<путь_к_вашим_заметкам>/Мои заметки/Agents/Hermes Agent",
     "backend": "fts5",
     "memory_dir": "wiki/memory",
     "untrusted_dirs": [
       "raw"
     ]
   }
   ```
## Результат
В результате при взаимодействии с Hermes Agent он начинает самостоятельно логировать аспекты памяти в `Agents/Hermes Agent/wiki/memory/builtin-mirror`

![[hermes_obsidian_hwiki_memory.png]]


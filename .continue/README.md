# .continue/config.yaml

Этот файл — шаблон конфигурации для локальных настроек (например, для Codespaces).
В файле используются placeholder-переменные для API-ключей. НЕ коммитьте реальные ключи в репозиторий.

Как использовать безопасно:

- Рекомендуется хранить реальные ключи в GitHub Secrets (Settings -> Secrets -> Codespaces / Repository secrets) и пробрасывать их в среду Codespace.
- В devcontainer.json или в dotfiles-скриптах можно установить переменные окружения перед запуском приложений:

  - В `devcontainer.json` (example):

    {
      "name": "My Container",
      "features": {},
      "runArgs": [],
      "containerEnv": {
        "DEEPSEEK_CODER_API_KEY": "${{ secrets.DEEPSEEK_CODER_API_KEY }}",
        "DEEPSEEK_CHAT_API_KEY": "${{ secrets.DEEPSEEK_CHAT_API_KEY }}"
      }
    }

  - Или экспортировать переменные в dotfiles/entrypoint скриптах:

    export DEEPSEEK_CODER_API_KEY="$DEEPSEEK_CODER_API_KEY"

- Если хотите, чтобы этот файл автоматически использовался в ваших Codespaces, добавьте в `.devcontainer` или в стартовый скрипт команду, которая подставляет реальные значения из переменных окружения в `/workspaces/.continue/config.yaml` или копирует шаблон в нужное место.

Почему placeholders: это предотвращает утечку секретов при открытом репозитории. Если нужен зашифрованный вариант, можно рассмотреть использование SOPS или GitHub Secrets + runtime-injection.

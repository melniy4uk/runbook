# Пример конфигурации команд

```yaml
version: 1

# Каждый подключаемый файл может содержать либо `command:` (одна команда),
# либо `commands:` (несколько команд).
commands:
  - name: setup
    description: Первоначальная настройка проекта
    command_template:
      - value: poetry
        description: Менеджер зависимостей
      - value: install
        description: Установка зависимостей

  - name: lint
    description: Проверка стиля (ruff) с опциональным автоисправлением
    command_template:
      - value: ruff
        description: Утилита линтинга
      - value: check
        description: Режим проверки
      - value: "{fix}"
        description: Опциональный флаг автоисправлений
      - value: .
        description: Целевая директория
    params:
      fix:
        - ""
        - "--fix"

  - name: test
    description: Запуск тестов в тихом режиме
    command_template:
      - pytest
      - -q
```

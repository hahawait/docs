---
order: 8
title: Боты (bots)
---

## Получение подключенных ботов

Для получения списка ботов, подключенных к каналу, используйте эндпоинт:

**GET /bots/channels/{channel_id}**

В пути запроса укажите идентификатор канала:

```json
{
  "channel_id": 123
}
```

**Ответ 200** — возвращает массив подключенных ботов:

```json
[
  {
    "id": 1,
    "username": "bot_username",
    "fullname": "Bot Full Name",
    "service_name": "Service Name",
    "description": "Bot Description",
    "status": true,
    "created_at": "2023-01-01T00:00:00"
  }
]
```

**Ошибки:**
- 401 — неавторизованный запрос
- 404 — логи ботов не найдены
- 422 — ошибка валидации

---

[openapi:./bots.yaml:false]
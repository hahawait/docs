---
order: 6
title: Аудитория (Audience)
---

## Получить аудиторию канала

**GET /v2/traffic/get_audience**

Позволяет получить список пользователей аудитории канала за выбранный период с возможностью фильтрации.

**Параметры:**
- `offset` (integer, обязателен) — Смещение, по-умолчанию 0
- `limit` (integer, обязателен) — Ограничение, по-умолчанию 50

**Тело запроса:**
- `start_datetime` (string, date-time, обязателен) — начало периода
- `end_datetime` (string, date-time, обязателен) — конец периода
- `channel_id` (integer, обязателен) — ID канала
- `event_id` (integer, обязателен) — идентификатор события (1 — подписка, 2 — отписка)
- `invite_links_hash` (array[string], опционально) — хэши пригласительных ссылок


**Ответ 200:**
```json
[
  {
    "user_id": 0,
    "event_status_id": 0,
    "created_at": "2025-07-22T07:51:48.284Z",
    "is_premium": true,
    "photo_url": "string",
    "first_name": "string",
    "last_name": "string",
    "phone_number": "string",
    "username": "string",
    "bio": "string",
    "birthday": "string",
    "invite_link": "string",
    "age": [
      null,
      null
    ]
  }
]
```

**Ошибки:**
- 422 — Ошибка валидации

---

[openapi:./analysis.yaml:false]
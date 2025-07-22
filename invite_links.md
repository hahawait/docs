---
order: 3
title: Инвайт-ссылки (invite_links)
---

## Получить инвайт-ссылку по ID

**GET /invite_links/{invite_link_id}?channel_id=...**

Запрос возвращает подробную информацию о конкретной инвайт-ссылке по её идентификатору и channel_id.

**Параметры:**
- `invite_link_id` (path, string, обязателен) — ID инвайт-ссылки
- `channel_id` (query, integer, обязателен) — ID канала

**Ответ 200:**
```json
{
  "id": "string",
  "name": "string",
  "channel_id": 123,
  "invite_link": "https://...",
  "creates_join_request": false,
  "expire_date": null,
  "member_limit": null,
  "created_at": "2024-01-01T00:00:00Z",
  "updated_at": null,
  "is_bot_created": true,
  "creator_id": 456,
  "budget": 0,
  "tags": [
    {
      "id": "uuid",
      "name": "string",
      "color": "string",
      "type": {
        "id": "uuid",
        "name": "string"
      }
    }
  ]
}
```

**Ошибки:**
- 401 — Unauthorized
- 404 — Invite link not found
- 422 — Ошибка валидации

---

## Получить все инвайт-ссылки с фильтрами

**POST /invite_links/all**

Позволяет получить список всех инвайт-ссылок с возможностью фильтрации и пагинации.

**Query-параметры:**
- `page` (integer, default: 1)
- `limit` (integer, default: 10)
- `channel_id` (integer, обязателен)
- `name` (string, опционально)
- `creator_id` (integer, опционально)
- `ordered_fields` (array, default: ["-created_at"])

**Пример тела запроса:**
```json
{
  "tags": [
    {
      "tag_type_id": "uuid",
      "without_type": false,
      "tags": ["uuid1", "uuid2"]
    }
  ],
  "links_ids": ["id1", "id2"]
}
```

**Ответ 200:**
```json
{
  "page": 1,
  "limit": 10,
  "total": 100,
  "items": [
    {
      "id": "string",
      "name": "string",
      "channel_id": 123,
      "invite_link": "https://...",
      "creates_join_request": false,
      "expire_date": null,
      "member_limit": null,
      "created_at": "2024-01-01T00:00:00Z",
      "updated_at": null,
      "is_bot_created": true,
      "creator_id": 456,
      "budget": 0,
      "tags": [ /* ... */ ]
    }
  ]
}
```

**Ошибки:**
- 401 — Unauthorized
- 422 — Ошибка валидации

---

## Создать инвайт-ссылку

**POST /invite_links**

Создаёт новую инвайт-ссылку для канала.

**Пример тела запроса:**
```json
{
  "channel_id": 123,
  "name": "Моя ссылка",
  "creates_join_request": false,
  "expire_date": null,
  "member_limit": null,
  "budget": 0,
  "tags": ["uuid1", "uuid2"]
}
```

**Ответ 201:**
```json
{
  "id": "string",
  "name": "string",
  "channel_id": 123,
  "invite_link": "https://...",
  "creates_join_request": false,
  "expire_date": null,
  "member_limit": null,
  "created_at": "2024-01-01T00:00:00Z",
  "updated_at": null,
  "is_bot_created": true,
  "creator_id": 456,
  "budget": 0,
  "tags": [ /* ... */ ]
}
```

**Ошибки:**
- 401 — Unauthorized
- 400 — Bad request
- 403 — Helper bot permissions exception
- 409 — Bot not added to channel exception
- 422 — Ошибка валидации

---

[openapi:./invite_links.yaml:false]
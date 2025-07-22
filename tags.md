---
order: 4
title: Пригласительные ссылки (Теги)
---

## Получить список тегов

**GET /tags**

Позволяет получить список тегов с фильтрацией и пагинацией.

**Query-параметры:**
- `page` (integer, default: 1)
- `limit` (integer, default: 10)
- `channel_id` (integer, обязателен)
- `name` (string, опционально)
- `type_id` (uuid, опционально)
- `ordered_fields` (array, default: ["-created_at"])

**Ответ 200:**
```json
{
  "page": 1,
  "limit": 10,
  "total": 100,
  "items": [
    {
      "id": "uuid",
      "name": "string",
      "color": "string",
      "type": {
        "id": "uuid",
        "name": "string"
      },
      "created_at": "2024-01-01T00:00:00Z",
      "updated_at": null,
      "channel_id": 123,
      "links": [ /* ... */ ]
    }
  ]
}
```

**Ошибки:**
- 401 — Unauthorized
- 422 — Ошибка валидации

---

## Создать тег

**POST /tags**

Создаёт новый тег для канала.

**Пример тела запроса:**
```json
{
  "channel_id": 123,
  "name": "Важное",
  "color": "#FF0000",
  "tag_type_id": "uuid"
}
```

**Ответ 201:**
```json
{
  "id": "uuid",
  "name": "Важное",
  "color": "#FF0000",
  "type": {
    "id": "uuid",
    "name": "Тип"
  },
  "created_at": "2024-01-01T00:00:00Z",
  "updated_at": null,
  "channel_id": 123,
  "links": [ /* ... */ ]
}
```

**Ошибки:**
- 401 — Unauthorized
- 400 — Bad request
- 422 — Ошибка валидации

---

## Получить типы тегов

**GET /tags/types**

Возвращает список всех типов тегов.

**Ответ 200:**
```json
[
  {
    "id": "uuid",
    "name": "Тип"
  }
]
```

**Ошибки:**
- 401 — Unauthorized

---

## Получить тег по ID

**GET /tags/{tag_id}**

Возвращает подробную информацию о теге по его идентификатору.

**Параметры:**
- `tag_id` (path, uuid, обязателен)

**Ответ 200:**
```json
{
  "id": "uuid",
  "name": "string",
  "color": "string",
  "type": {
    "id": "uuid",
    "name": "string"
  },
  "created_at": "2024-01-01T00:00:00Z",
  "updated_at": null,
  "channel_id": 123,
  "links": [ /* ... */ ]
}
```

**Ошибки:**
- 401 — Unauthorized
- 404 — Tag not found
- 422 — Ошибка валидации

---

[openapi:./tags.yaml:false]
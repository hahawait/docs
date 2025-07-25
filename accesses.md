---
order: 5
title: Доступы (accesses)
---

## Получить список доступов

**GET /accesses**

Позволяет получить список доступов с возможностью фильтрации.

**Параметры:**
- `channel_ids` (array[integer], опционально) — фильтр по списку каналов
- `tariff_name` (string, опционально) — фильтр по названию тарифа
- `legal_entity_id` (integer, опционально) — фильтр по платежному аккаунту


**Ответ 200:**
```json
[
  {
    "id": 0,
    "channel_id": 0,
    "tariff": {
      "id": 0,
      "tag": "BASIC",
      "name": "string",
      "description": "string",
      "is_default": false,
      "is_available": false,
      "metrics": [
        {
          "id": 0,
          "name": "string",
          "amount": 0
        }
      ]
    },
    "additional_users": 0,
    "sub_end_date": "2025-07-22T07:59:57.734Z",
    "sub_start_date": "2025-07-22T07:59:57.734Z",
    "legal_entity_id": 0
  }
]
```

**Ошибки:**
- 401 — Unauthorized
- 422 — Ошибка валидации

---

[openapi:./accesses.yaml:false]
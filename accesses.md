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
    "id": 1,
    "channel_id": 123,
    "tariff": {
      "id": 10,
      "tag": "BASIC",
      "name": "Базовый",
      "description": "Описание тарифа",
      "is_default": false,
      "is_available": true,
      "metrics": [
        {
          "id": 1,
          "name": "Пользователи",
          "amount": 100
        }
      ]
    },
    "sub_start_date": "2024-01-01T00:00:00Z",
    "sub_end_date": "2024-01-01T00:00:00Z",
    "legal_entity_id": 0
  }
]
```

**Ошибки:**
- 401 — Unauthorized
- 422 — Ошибка валидации

---

[openapi:./accesses.yaml:false]
---
order: 7
title: Продажи (sales)
---

## Создать продажи

**POST /sales/create**

Создаёт продажи и отправляет их на анализ. При ошибках в файлах возвращается список ошибок.

**Query-параметры:**
- `channel_id` (integer, обязателен) — ID канала
- `name` (string, обязателен) — название
- `budget` (number, обязателен) — бюджет

**Тело запроса (multipart/form-data):**
- `file` — Excel-файл с продажами

**Ответ 200:**
```json
{
  "report_id": "string",
  "status": "string"
}
```

**Ошибки:**
- 409 — Ошибка парсинга файла (SalesExceptionSchema)
- 415 — Неверный формат файла
- 401 — Ошибка авторизации
- 422 — Ошибка валидации

---

## Получить аналитику продаж по каналу

**GET /sales/analytic**

Возвращает список аналитики продаж по каналу.

**Query-параметры:**
- `channel_id` (integer, обязателен)
- `order_by` (string, default: created_at, опционально)
- `order_dir` (asc/desc, default: desc, опционально)
- `limit` (integer, default: 10, опционально)
- `offset` (integer, default: 0, опционально)

**Ответ 200:**
```json
[
  {
    "id": "uuid",
    "name": "string",
    "created_at": "2024-01-01T00:00:00Z",
    "channel_id": 123
  }
]
```

**Ошибки:**
- 422 — Ошибка валидации

---

## Получить аналитику по отчету

**POST /sales/analytic/report**

Возвращает подробную информацию по аналитике.

**Тело запроса:**
```json
{
  "report_id": "uuid"
}
```

**Ответ 200:**
```json
{
  "id": "uuid",
  "name": "string",
  "created_at": "2024-01-01T00:00:00Z",
  "channel_id": 123,
  "status": "success",
  "budget": 1000,
  "profit": 500,
  "creator_id": 1,
  "error_message": null,
  "updated_at": "2024-01-01T00:00:00Z",
  "subs": 100,
  "sales": 50,
  "leads": 20,
  "funnel": 10,
  "avg_sale": null,
  "avg_funnel": null,
  "avg_lead": null,
  "premium_percent": 10.5,
  "username_percent": 80.0,
  "source_reports": [],
  "romi": 1.5,
  "cpf": 10,
  "cpl": 20,
  "cac": 30,
  "cpc": 40,
  "cr_leads": 0.1,
  "cr_sales": 0.2,
  "cr_funnel": 0.3
}
```

**Ошибки:**
- 422 — Ошибка валидации

---

## Получить продажи по аналитике

**GET /sales/analytic/{channel_id}/{source_report_id}/sales**

Возвращает продажи по аналитике.

**Path-параметры:**
- `channel_id` (integer, обязателен)
- `source_report_id` (string, обязателен)

**Query-параметры:**
- `order_by` (string, опционально)
- `order_dir` (asc/desc, default: asc, опционально)
- `limit` (integer, default: 10, опционально)
- `offset` (integer, default: 0, опционально)
- `status` (lead/sale/funnel, обязателен)
- `product` (string, опционально)
- `is_premium` (boolean, опционально)
- `start_date` (date-time, опционально)
- `end_date` (date-time, опционально)
- `is_null_invite_link` (boolean, опционально)

**Ответ 200:**
```json
[
  {
    "user_id": 1,
    "name": "string",
    "product": "string",
    "purchase_amount": 100,
    "username": "string",
    "photo_url": "string",
    "is_premium": false,
    "phone_number": "string",
    "birthdate": "string",
    "status": "sale",
    "sub_date": "2024-01-01T00:00:00Z",
    "unsub_date": null,
    "action_date": null,
    "action_period": null
  }
]
```

**Ошибки:**
- 422 — Ошибка валидации

---

[openapi:./sales.yaml:false]
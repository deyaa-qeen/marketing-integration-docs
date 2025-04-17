---
id: products-api
title: Products API
description: Get paginated list of Shopify products
---

# 🛍️ Products API

This endpoint allows you to retrieve a **paginated list of Shopify products**.

---

## 🔐 Scopes

| ID  | Scope Name |
|-----|------------|
| 1   | Customer   |
| 2   | Product    |
| 3   | Order      |

You must ensure your integration token is authorized with the correct scope.

---

## 📬 Endpoint

```http
GET https://integration-service.europe-west1.run.app/api/v1/shopify/products/paginated/
```

```c
curl -L \
  -X POST \
  -H "Accept: application/vnd.github+json" \
  -H "Authorization: Bearer <YOUR-TOKEN>" \
  -H "X-GitHub-Api-Version: 2022-11-28" \
  https://api.github.com/markdown \
  -d '{"text":"Hello **world**"}'
```

---

### 🔄 Parameters

| Name      | Type   | Required | Description            |
|-----------|--------|----------|------------------------|
| shop_id   | string | ✅ Yes   | ID of the Shopify shop |
| page      | int    | No       | Page number            |
| limit     | int    | No       | Items per page         |

### 📦 Sample Response

```json
{
  "success": true,
  "data": [
    {
      "id": "p001",
      "title": "Sneakers",
      "price": "59.99"
    }
  ]
}
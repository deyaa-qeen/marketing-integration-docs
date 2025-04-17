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
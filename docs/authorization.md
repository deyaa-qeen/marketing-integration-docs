---
sidebar_position: 2
---

# 🔐 Auth

To securely access or integrate with our Marketing App API, all requests must be authenticated using two required headers:

- `X-Api-Key` — Your private API key  
- `X-Integration-Type-ID` — A unique ID assigned to your integration

These credentials ensure your service is recognized and authorized to interact with our system.

---

## 📦 Getting Your Credentials

To begin using the API:

1. Provide us with your **integration name** (e.g. `shopify`, `zid`, `salla`, `crm`, etc.).
2. We will generate and give you:
   - A unique **Integration Type ID**
   - A secure **API Key**

Both are required to interact with the API.

---

## 🧾 Required Request Headers (You → Us)

Every request you send to our API **must include** the following headers:

```http
X-Api-Key: <your-api-key>
X-Integration-Type-ID: <your-integration-type-id>
```

## 🧾 Optional Request Headers (Us → You)
if you have key, provide us and When we call your API (for example, to fetch data via your callback endpoint), we will include this header in the request:
```http
X-Api-Key: <your-api-key>
```

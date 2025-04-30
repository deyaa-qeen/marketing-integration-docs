---
sidebar_position: 3
---

# Importing Data

Instead of sending data directly to us, **your service must expose an API endpoint** that we will call (callback style). This allows us to pull the data when needed.

---

## 🔁 How It Works

1. **You provide a callback API URL** that we can call to import data.
2. You define the **scope** of the data you're exposing (e.g., customers, products, or orders).
3. We’ll call your API with pagination parameters.
4. Your service must return the data in a specific format.
5. You must commit the response to confirm delivery.

---

## 📦 Supported Scopes

You must define the scope of your callback API:

| ID  | Scope Name | Description                              |
|-----|------------|------------------------------------------|
| 1   | `customer` | Contact or user information              |
| 2   | `order`  | Product catalog data                     |
| 3   | `product`    | Order history or transaction data        |


---

## 🔁 Pagination Support

We support two methods of pagination:

- **Page-based:** We will call your endpoint with `page` and `page_size` as query parameters.
- **Cursor-based (GraphQL):** If supported, we’ll pass `cursor` as a query parameter.

Example:

```http
Post /your-api/customers?page=1&page_size=50
```
in body:
```json
{
  "shop":"domain"
}
```
## 📊 Example Response Format

This is an example of the expected response when fetching data through your callback API.

```json
{
  "status": "success",
  "message": "",
  "meta": {
    "has_next_page": true,
    "cursor": "abc123",
    "page": 1,
    "page_size": 50
  },
  "data": [
    {
      "customer_id": "123",
      "email": "john@example.com",
      "first_name": "John",
      "last_name": "Doe",
      "mobile": "+1234567890",
      "language": "en",
      "consent": "YES",
      "gender": "Male",
      "last_modified_date": "2024-12-01T10:30:00Z"
    }
  ]
}
```

### 🧾 Notes:

- **status** and **message** are optional fields.

- **meta** provides important information such as whether there are more pages to fetch or the cursor for pagination:
  - **has_next_page**: A boolean indicating if more data exists.
  - **cursor**: The cursor used for pagination in the case of cursor-based pagination (optional).
  - **page**: The current page number.
  - **page_size**: The number of records per page.

- **data** contains the actual records that are being fetched.

  **Customer Data Requirements:**

  - All fields listed in each customer record are **required**. Please **do not return any customer** that is missing one or more of the required fields.
  - **gender**: Must be either `"Male"` or `"Female"` — the first letter **must be capitalized**.
  - **consent**: Indicates whether the customer **agrees to receive marketing messages**. This should be a string (`Yes` or `No`).

     
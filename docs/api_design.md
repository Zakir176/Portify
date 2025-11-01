# 🧩 Portify API Design

### Version
v1.0.0 (Draft)

---

## 📘 Overview

The **Portify API** powers all interactions between the frontend app and backend services.  
It allows users to register, manage their investment portfolios, track performance, and adjust personal preferences.

This is a **RESTful API**, returning JSON responses and designed for scalability and modular growth as Portify expands.

---

## 🔐 Authentication

All authentication routes use secure HTTPS requests.  
JWT tokens will be issued upon login and used for protected routes.

| Method | Endpoint | Description | Auth Required |
|--------|-----------|--------------|----------------|
| `POST` | `/api/auth/register` | Register a new user | ❌ |
| `POST` | `/api/auth/login` | Log in and receive JWT | ❌ |
| `POST` | `/api/auth/logout` | Log out the user and invalidate session | ✅ |

**Example: Register**
```json
POST /api/auth/register
{
  "username": "john_doe",
  "email": "john@example.com",
  "password": "securePass123"
}
```

**Response**
```json
{
  "message": "User created successfully.",
  "user_id": 101,
  "token": "eyJhbGciOiJIUzI1..."
}
```

---

## 💼 Portfolio

Endpoints for creating and managing a user’s overall investment portfolio.

| Method | Endpoint | Description | Auth Required |
|--------|-----------|--------------|----------------|
| `GET` | `/api/portfolio` | Get the user's portfolio overview | ✅ |
| `POST` | `/api/portfolio` | Create a new portfolio | ✅ |
| `PUT` | `/api/portfolio/:id` | Update portfolio details | ✅ |
| `DELETE` | `/api/portfolio/:id` | Delete a portfolio | ✅ |

**Example Response**
```json
{
  "portfolio_id": 1,
  "name": "Long-Term Growth",
  "total_value": 15420.55,
  "currency": "USD",
  "created_at": "2025-10-26"
}
```

---

## 📊 Holdings

Each portfolio contains one or more holdings (stocks, crypto, etc.).

| Method | Endpoint | Description | Auth Required |
|--------|-----------|--------------|----------------|
| `GET` | `/api/holdings/:portfolio_id` | Retrieve all holdings in a portfolio | ✅ |
| `POST` | `/api/holdings` | Add a new holding | ✅ |
| `PUT` | `/api/holdings/:id` | Update an existing holding | ✅ |
| `DELETE` | `/api/holdings/:id` | Remove a holding | ✅ |

**Example Holding**
```json
{
  "holding_id": 12,
  "portfolio_id": 1,
  "asset_type": "stock",
  "symbol": "AAPL",
  "quantity": 5,
  "average_price": 172.40,
  "current_price": 178.22,
  "gain_loss_percent": 3.37
}
```

---

## 💸 Transactions

Transactions are linked to holdings and record all activity (buys, sells, deposits, etc.)

| Method | Endpoint | Description | Auth Required |
|--------|-----------|--------------|----------------|
| `GET` | `/api/transactions/:portfolio_id` | Get all transactions | ✅ |
| `POST` | `/api/transactions` | Add a new transaction | ✅ |

**Example Transaction**
```json
{
  "transaction_id": 57,
  "portfolio_id": 1,
  "type": "buy",
  "symbol": "TSLA",
  "quantity": 2,
  "price_per_unit": 245.10,
  "date": "2025-10-25"
}
```

---

## ⚙️ User Settings

User-specific settings such as profile details, themes, and notification preferences.

| Method | Endpoint | Description | Auth Required |
|--------|-----------|--------------|----------------|
| `GET` | `/api/settings` | Get current user settings | ✅ |
| `PUT` | `/api/settings` | Update user settings | ✅ |

**Example Settings**
```json
{
  "user_id": 101,
  "theme": "dark",
  "currency": "USD",
  "notifications": {
    "email": true,
    "sms": false
  }
}
```

---

## 🧱 Example Data Structure

**Portfolio JSON Schema (simplified)**  
```json
{
  "id": 1,
  "name": "Main Portfolio",
  "created_at": "2025-10-26",
  "holdings": [
    {
      "symbol": "BTC",
      "type": "crypto",
      "quantity": 0.5,
      "average_price": 64000
    },
    {
      "symbol": "AAPL",
      "type": "stock",
      "quantity": 10,
      "average_price": 172.40
    }
  ]
}
```

---

## 🧩 Notes

- All responses are in **JSON**.  
- Use `Authorization: Bearer <token>` header for protected routes.  
- Versioning follows `/api/v1/` prefix.  
- Future expansion may include analytics, watchlists, and market API integrations.

---

> © 2025 Portify — Investment tracking made personal and powerful.

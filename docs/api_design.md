# 📡 Portify API Design

The Portify API provides endpoints to manage users, portfolios, and investment transactions in a unified system.

---

## 🧭 Base URL

/api/v1

---

## 🔐 Authentication
All endpoints (except `/auth/*`) require a valid JWT token in the header:

Authorization: Bearer 

---

## 🧑‍💼 Auth Endpoints

| Method | Endpoint | Description |
|--------|-----------|--------------|
| `POST` | `/auth/register` | Register a new user |
| `POST` | `/auth/login` | Log in and receive JWT token |
| `POST` | `/auth/logout` | Invalidate current session |

### Example Request
```json
{
  "email": "user@example.com",
  "password": "strongpassword"
}

Note: This API will be built using ASP.NET Core Web API and JWT authentication, with PostgreSQL as the backend database.

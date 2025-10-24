# Portify Database Schema (Draft)

## Tables

### Users
| Column | Type | Description |
|--------|------|-------------|
| id | int | Primary key |
| name | string | User full name |
| email | string | Unique user email |
| password_hash | string | Encrypted password |

### Assets
| Column | Type | Description |
|--------|------|-------------|
| id | int | Primary key |
| user_id | int | Foreign key (Users) |
| name | string | Asset name (e.g. BTC, AAPL) |
| type | string | Asset category (crypto, stock, etc.) |
| purchase_price | decimal | Initial buy price |
| quantity | decimal | Amount owned |
| current_price | decimal | Updated via API |
| created_at | datetime | Record creation date |

### Transactions
| Column | Type | Description |
|--------|------|-------------|
| id | int | Primary key |
| asset_id | int | Foreign key (Assets) |
| action | string | Buy/Sell |
| amount | decimal | Transaction amount |
| date | datetime | Transaction date |

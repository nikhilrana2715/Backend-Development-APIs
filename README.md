# 💰 Backend Ledger System

![Node](https://img.shields.io/badge/Node.js-Backend-green)
![Express](https://img.shields.io/badge/Express.js-Framework-black)
![MongoDB](https://img.shields.io/badge/MongoDB-Database-green)
![JWT](https://img.shields.io/badge/JWT-Authentication-orange)
![License](https://img.shields.io/badge/License-ISC-blue)

A **Node.js based Ledger and Transaction Management API** that allows users to create accounts, manage balances, and perform secure transactions using a **double-entry ledger system**.

Instead of storing balances directly, the system calculates balances from **ledger entries (Credit & Debit)** — similar to real banking systems.

---



# 🚀 Features

### 🔐 Authentication
- User Registration
- User Login
- JWT Authentication
- Logout with Token Blacklist
- Password hashing using bcrypt

### 🏦 Account Management
- Create account
- Fetch all user accounts
- Check account balance

### 💳 Transaction System
- Secure money transfer
- Double-entry accounting system
- Idempotency protection
- Transaction status tracking

### 📧 Email Notifications
- Registration email
- Transaction success email
- Transaction failure email

---

# 🛠 Tech Stack

| Technology | Purpose |
|---|---|
| Node.js | Backend runtime |
| Express.js | Web framework |
| MongoDB | Database |
| Mongoose | ODM |
| JWT | Authentication |
| bcrypt | Password hashing |
| Nodemailer | Email service |

---

## 📁 Project Structure

```bash
backend-ledger
│
├── server.js
├── package.json
│
└── src
    │
    ├── app.js
    │
    ├── config
    │   └── db.js
    │
    ├── controllers
    │   ├── auth.controller.js
    │   ├── account.controller.js
    │   └── transaction.controller.js
    │
    ├── middleware
    │   └── auth.middleware.js
    │
    ├── models
    │   ├── user.model.js
    │   ├── account.model.js
    │   ├── transaction.model.js
    │   ├── ledger.model.js
    │   └── blackList.model.js
    │
    ├── routes
    │   ├── auth.routes.js
    │   ├── account.routes.js
    │   └── transaction.routes.js
    │
    └── services
        └── email.service.js
```

# 🏗 System Architecture

```bash
Client
│
▼
Express API Server
│
├── Authentication (JWT)
│
├── Account Service
│
├── Transaction Service
│
▼
MongoDB Database
│
├── Users
├── Accounts
├── Transactions
├── Ledger Entries
└── Token Blacklist

```
---

# 🧠 Database Schema

### User

```bash
User
├── name
├── email
├── password
└── systemUser

```
### Account

```bash
Account
├── user
├── status
├── currency
└── createdAt

```
### Transaction

```bash
Transaction
├── fromAccount
├── toAccount
├── amount
├── status
└── idempotencyKey
```

### Ledger

```bash
Ledger
├── account
├── transaction
├── amount
└── type (CREDIT / DEBIT)
```

---

# ⚙️ Installation

### Clone repository

```bash
git clone https://github.com/your-username/backend-ledger.git
Go to project
cd backend-ledger
Install dependencies
npm install
Run server

Development

npm run dev

Production

npm start

Server runs on

http://localhost:3000
🔑 Environment Variables

Create .env

PORT=3000

MONGO_URI=mongodb://localhost:27017/ledger

JWT_SECRET=your_secret

EMAIL_USER=your_email@gmail.com
CLIENT_ID=your_client_id
CLIENT_SECRET=your_client_secret
REFRESH_TOKEN=your_refresh_token
📡 API Endpoints
🔐 Auth
Register
POST /api/auth/register

Body

{
"name":"Nikhil",
"email":"nikhil@email.com",
"password":"123456"
}
Login
POST /api/auth/login
Logout
POST /api/auth/logout
🏦 Account APIs

Create Account

POST /api/accounts

Get User Accounts

GET /api/accounts

Get Balance

GET /api/accounts/balance/:accountId
💸 Transaction APIs

Create Transaction

POST /api/transactions

Example

{
"fromAccount":"ACCOUNT_ID",
"toAccount":"ACCOUNT_ID",
"amount":100,
"idempotencyKey":"unique_key"
}
🔄 Transaction Flow

1️⃣ Validate request
2️⃣ Validate idempotency key
3️⃣ Check account status
4️⃣ Calculate sender balance
5️⃣ Create transaction (PENDING)
6️⃣ Create DEBIT ledger entry
7️⃣ Create CREDIT ledger entry
8️⃣ Mark transaction COMPLETED
9️⃣ Commit MongoDB transaction
🔟 Send email notification

🔒 Security

JWT Authentication

Password hashing with bcrypt

Token blacklist after logout

Protected routes

📊 Ledger Accounting System

This project uses Double Entry Accounting

Sender Account  → DEBIT
Receiver Account → CREDIT

Balance Calculation

Balance = Credits - Debits

Ledger entries cannot be modified to maintain financial integrity.

📌 Future Improvements

Swagger API documentation

Admin dashboard

Transaction history

Redis caching

Docker deployment

👨‍💻 Author

Nikhil Rana
BCA Student
Full Stack Developer

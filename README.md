
# UPI Transaction Management System

A full-stack UPI Transaction Management System developed as a DBMS project using React, FastAPI, and MariaDB/MySQL.

## Tech Stack

- **Frontend:** React, Vite, JavaScript, Tailwind CSS
- **Backend:** Python, FastAPI
- **Database:** MariaDB / MySQL
- **API Documentation:** Swagger UI

## Project Structure

```text
Sem4-DBMS-Project/
├── backend/
│   ├── app/
│   │   ├── core/
│   │   ├── models/
│   │   ├── routers/
│   │   └── services/
│   ├── .env.example
│   └── requirements.txt
├── database/
│   ├── db_schema.sql
│   └── README.md
├── frontend/
│   ├── src/
│   ├── package.json
│   └── vite.config.js
├── .gitignore
└── README.md
```

## Prerequisites

- Python 3.10 or later
- Node.js and npm
- MariaDB or MySQL

## Installation and Setup

### 1. Clone the repository

```bash
git clone https://github.com/adithyakamath14-stack/DBMS-project.git
cd DBMS-project
```

### 2. Database Setup

1. Start MariaDB/MySQL.
2. Create the database named `upi_system`.
3. Execute the SQL script in `database/db_schema.sql`.
4. Configure your database credentials in `backend/.env`.

Use `backend/.env.example` as a reference.

### 3. Backend Setup

```bash
cd backend
python -m venv venv
```

Activate the virtual environment.

**Windows:**
```powershell
.\venv\Scripts\Activate.ps1
```

**Linux/macOS:**
```bash
source venv/bin/activate
```

Install dependencies:

```bash
pip install -r requirements.txt
```

Start the backend:

```bash
uvicorn app.main:app --reload
```

Backend API: http://127.0.0.1:8000

Swagger documentation: http://127.0.0.1:8000/docs

### 4. Frontend Setup

Open another terminal:

```bash
cd frontend
npm install
npm run dev
```

Open the local URL displayed by Vite, usually:

http://localhost:5173

## Database Configuration

Create `backend/.env` using the following format:

```env
DB_HOST=127.0.0.1
DB_PORT=3306
DB_USER=root
DB_PASSWORD=your_password
DB_NAME=upi_system
```

Change the port and credentials according to your local MariaDB/MySQL configuration.

**Never commit your actual `.env` file or database password.**

## Transaction History API

**Endpoint:**

`GET /api/transactions/history/{vpa}`

Retrieves a user's transaction history using the database view `vw_User_Transaction_History`.

The view combines transaction and account data, allowing the backend to retrieve transaction details without implementing the JOIN operations itself.

The response includes:

- transaction_id
- sender_vpa
- receiver_vpa
- amount
- status
- created_at
- type

Transaction type:
- DEBIT: When the requested VPA is the sender.
- CREDIT: When the requested VPA is the receiver.

## Features

- User authentication and registration
- UPI account management
- Money transfers
- Transaction history
- User dashboard
- Admin dashboard

## License

This project was developed for academic purposes.

# E-SECURE Backend

Backend API for **E-SECURE**, a secure operational signal dissemination platform designed for law enforcement and emergency services. The system enables the secure distribution of sensitive operational signals with encrypted storage, recipient-specific watermarking, comprehensive audit logging, and real-time communication.

---

## Overview

E-SECURE Backend provides the core services for the platform, including authentication, signal management, encrypted file processing, audit logging, emergency broadcasts, and administrative operations.

The application is built with Node.js and Express and uses PostgreSQL for persistent storage. Real-time communication is powered by Socket.IO, while scheduled tasks are handled with node-cron.

---

## Features

- Secure JWT-based authentication
- Device approval and binding
- AES-256 encrypted signal storage
- Recipient-specific QR watermarking
- Image, PDF, and audio file support
- Emergency broadcast system
- SMS fallback integration (Termii)
- Real-time notifications with Socket.IO
- Signal expiry automation
- Comprehensive audit logging
- Administrative management dashboard

---

## Tech Stack

| Category | Technology |
|----------|------------|
| Runtime | Node.js 18+ |
| Framework | Express.js |
| Database | PostgreSQL |
| Authentication | JWT, bcrypt |
| Encryption | AES-256-CBC |
| File Processing | Multer, Sharp |
| QR Code Generation | qrcode |
| Real-Time Communication | Socket.IO |
| Background Jobs | node-cron |
| SMS Integration | Termii API (optional) |

---

## Project Structure

```text
e-secure-backend/
├── controllers/
├── middleware/
├── routes/
├── services/
├── uploads/
├── utils/
├── server.js
├── package.json
└── README.md
```

---

## Prerequisites

- Node.js 18 or later
- PostgreSQL 14 or later
- npm or Yarn

---

## Installation

Clone the repository:

```bash
git clone https://github.com/your-username/e-secure-backend.git

cd e-secure-backend
```

Install dependencies:

```bash
npm install
```

Create an environment file:

```bash
cp .env.example .env
```

Create the database:

```bash
psql -U postgres -c "CREATE DATABASE signal_platform;"
```

Run the schema:

```bash
psql -U postgres -d signal_platform -f schema.sql
```

Start the development server:

```bash
npm run dev
```

---

## Environment Variables

| Variable | Description |
|----------|-------------|
| PORT | Server port |
| DB_HOST | PostgreSQL host |
| DB_PORT | PostgreSQL port |
| DB_NAME | Database name |
| DB_USER | Database username |
| DB_PASSWORD | Database password |
| JWT_SECRET | JWT signing secret |
| JWT_EXPIRES_IN | Token lifetime |
| TERMII_API_KEY | Termii API key (optional) |
| TERMII_SENDER_ID | SMS sender ID (optional) |

---

## API

### Authentication

| Method | Endpoint | Description |
|---------|----------|-------------|
| POST | `/api/auth/login` | Authenticate an officer |

### Signals

| Method | Endpoint |
|---------|----------|
| GET | `/api/signals/inbox` |
| GET | `/api/signals/:id` |
| POST | `/api/signals/:id/acknowledge` |
| POST | `/api/signals/create` |

### Emergency

| Method | Endpoint |
|---------|----------|
| POST | `/api/emergency/broadcast` |
| POST | `/api/emergency/:id/sms-fallback` |

### Administration

| Method | Endpoint |
|---------|----------|
| GET | `/api/admin/users` |
| GET | `/api/admin/audit-logs` |
| POST | `/api/admin/trace-watermark` |

---

## Running in Production

### PM2

```bash
npm install -g pm2

pm2 start server.js --name e-secure-backend
```

### Docker

```dockerfile
FROM node:18-alpine

WORKDIR /app

COPY package*.json ./

RUN npm ci

COPY . .

EXPOSE 5000

CMD ["npm", "start"]
```

---

## Security

- AES-256 encryption for sensitive signal content
- JWT-based authentication
- Device authorization workflow
- Recipient-specific QR watermarking
- Comprehensive audit logging
- Automatic signal expiration

---

## Roadmap

- Firebase push notifications
- SMS production integration
- API documentation with Swagger/OpenAPI
- Automated testing
- Role-based permissions refinement

---

## Contributing

This project is currently maintained internally and is not accepting external contributions.

---

## License

ISC

This style is similar to what you'd find in repositories from companies or well-maintained open-source projects. It focuses on **what the software does**, keeps feature descriptions concise, includes a **Security** section, a **Roadmap**, and removes claims like "production-ready" or "90% complete" that can become outdated or be hard to substantiate.

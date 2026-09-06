# Libra Academy

Telegram Mini App for Libra Academy.

This repository is a clean full-stack foundation for:
- Telegram Mini App frontend
- Node.js/Express backend API
- PostgreSQL database
- Telegram WebApp authentication
- Role-based access: OWNER, SELLER, BUYER
- Courses, lessons, enrollments, quizzes and certificates (database foundation)

## Project structure

```text
libra-academy/
├── frontend/
│   ├── index.html
│   ├── css/app.css
│   ├── js/
│   │   ├── config.js
│   │   ├── telegram.js
│   │   ├── api.js
│   │   └── app.js
│   └── assets/favicon.svg
├── backend/
│   ├── package.json
│   ├── server.js
│   └── src/
│       ├── config/env.js
│       ├── db/pool.js
│       ├── middleware/auth.js
│       ├── middleware/error.js
│       └── routes/
│           ├── health.js
│           ├── auth.js
│           ├── users.js
│           └── courses.js
├── database/
│   ├── schema.sql
│   └── seed.sql
├── .env.example
├── .gitignore
├── netlify.toml
└── README.md
```

## Important security rule

The browser never decides whether a Telegram user is an owner. The backend verifies Telegram `initData` and assigns the role. Keep all secrets in environment variables and never commit `.env`.

## Local backend

```bash
cd backend
npm install
npm start
```

The API listens on `http://localhost:3000`.

## Database

Create a PostgreSQL database, then run:

```bash
psql "$DATABASE_URL" -f database/schema.sql
psql "$DATABASE_URL" -f database/seed.sql
```

## Frontend

The frontend is static and can be deployed by Netlify with `frontend` as the publish directory.

Set the frontend API URL in `frontend/js/config.js` when the backend is deployed.

## Telegram

The Mini App must be opened from Telegram for real `initData` authentication. Never trust `initDataUnsafe` as an authorization mechanism.

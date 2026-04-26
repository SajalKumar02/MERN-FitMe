# FitME — MERN Fitness Tracker

FitME is a MERN stack fitness app with **user** and **admin** experiences. The frontend is a React app, and the backend is an Express + MongoDB API.

## Features

### User

- Create a profile and track basic body information over time
- Auth flows (email/OTP/forgot password) are present in the codebase (see `backend/controller/authController.js`)

### Admin

- Admin management endpoints (create/update/check) under `/api/admin`
- Admin UI screens exist under `frontend/src/admin/`

> Note: Several API route modules exist (`article`, `auth`, `contact`, `exercise`, `favourite`, `supplement`) but are currently **commented out** in `backend/routes/index.js`, so only `/api/admin` is wired by default.

## Tech stack

- **Frontend**: React 18, React Router, Axios, Bootstrap
- **Backend**: Node.js, Express, Mongoose, JWT, Nodemailer
- **Database**: MongoDB

## Project structure

```text
MERN-Fitme/
  backend/                 # Express API + MongoDB models
  frontend/                # React app
  package.json             # Root scripts (runs both with concurrently)
```

## Getting started (local development)

### Prerequisites

- Node.js (LTS recommended)
- npm
- MongoDB running locally (or a MongoDB connection string)

### Install dependencies

```bash
npm install
cd backend && npm install
cd ../frontend && npm install
```

### Configure environment variables (backend)

Create `backend/.env`.

Minimum variables to boot the API:

```env
PORT=5000
MONGO_URI=mongodb://localhost:27017/fitme
JWT_TOKEN=change_me
COOKIE_EXPIRE=7
NODE_ENV=development
```

If you use email/OTP features (Nodemailer), also set:

```env
SMTP_HOST=
SMTP_PORT=
SMTP_SERVICE=
SMTP_EMAIL=
SMTP_PASSWORD=

# Some auth code paths also reference these:
EMAIL_ADDRESS=
EMAIL_PASSWORD=
```

If you use Google OAuth (strategy is implemented in `backend/config/google.oauth.js`), also set:

```env
GOOGLE_CLIENT_ID=
GOOGLE_CLIENT_SECRET=
```

### Run the app

From the repo root:

```bash
npm start
```

This runs both:

- **Backend**: `http://localhost:5000`
- **Frontend**: `http://localhost:3000` (proxied to backend via `frontend/package.json`)

You can also run them separately:

```bash
npm run backend
npm run frontend
```

## API (current wiring)

Base URL: `http://localhost:5000/api`

### Admin routes

- `GET /admin` — list users/admins (current implementation returns all users)
- `GET /admin/isadmin` — role check (route exists; ensure controller export matches)
- `POST /admin/add` — create an admin
- `PATCH /admin/:adminID` — update an admin

## Security notes

- Don’t commit secrets. Add `backend/.env` to `.gitignore` (recommended).
- Rotate keys like `JWT_TOKEN` and SMTP credentials if they were ever committed.

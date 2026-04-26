# FitMe 💪

A full-stack fitness tracking web application built with the MERN stack. Users can create profiles, track body metrics over time, and manage their fitness journey — with a separate admin panel for platform management.

<!-- Replace the line below with an actual screenshot once deployed -->
<!-- ![FitMe Preview](./Screenshots/dashboard.png) -->

## 🔴 Live Demo

> Coming soon — [Deploy link will go here]

---

## Features

### User

- Register and log in with email/password
- OTP-based email verification and forgot password flow
- Google OAuth login
- Create and update a personal fitness profile
- Track body information over time

### Admin

- Separate admin dashboard
- Create and manage admin accounts
- View all registered users
- Role-based access control (`isAdmin` check)

---

## Tech Stack

| Layer    | Technology                                 |
| -------- | ------------------------------------------ |
| Frontend | React 18, React Router, Axios, Bootstrap   |
| Backend  | Node.js, Express.js                        |
| Database | MongoDB, Mongoose                          |
| Auth     | JWT (cookie-based), Google OAuth 2.0       |
| Email    | Nodemailer (OTP & password reset)          |
| Dev      | Concurrently (runs both servers from root) |

---

## Project Structure

```
MERN-FitMe/
├── backend/
│   ├── config/          # DB connection, Google OAuth strategy
│   ├── controller/      # Route handlers (auth, admin, user)
│   ├── middleware/      # JWT auth middleware
│   ├── models/          # Mongoose schemas
│   ├── routes/          # Express routers
│   └── server.js
├── frontend/
│   ├── src/
│   │   ├── admin/       # Admin panel pages
│   │   ├── components/  # Reusable UI components
│   │   └── pages/       # User-facing pages
│   └── package.json
└── package.json         # Root — runs both with concurrently
```

---

## Getting Started

### Prerequisites

- Node.js (LTS)
- npm
- MongoDB (local or [Atlas](https://www.mongodb.com/cloud/atlas))

### 1. Clone the repo

```bash
git clone https://github.com/SajalKumar02/MERN-FitMe.git
cd MERN-FitMe
```

### 2. Install dependencies

```bash
npm install
cd backend && npm install
cd ../frontend && npm install
```

### 3. Configure environment variables

Create a `backend/.env` file:

```env
PORT=5000
MONGO_URI=mongodb://localhost:27017/fitme
JWT_TOKEN=your_jwt_secret
COOKIE_EXPIRE=7
NODE_ENV=development

# Nodemailer (for OTP / password reset)
SMTP_HOST=
SMTP_PORT=
SMTP_SERVICE=
SMTP_EMAIL=
SMTP_PASSWORD=

# Google OAuth
GOOGLE_CLIENT_ID=
GOOGLE_CLIENT_SECRET=
```

### 4. Run the app

```bash
# From the root — starts both backend and frontend
npm start

# Or separately
npm run backend    # http://localhost:5000
npm run frontend   # http://localhost:3000
```

---

## API Routes

Base URL: `http://localhost:5000/api`

| Method | Endpoint                | Description                    |
| ------ | ----------------------- | ------------------------------ |
| POST   | `/auth/register`        | Register a new user            |
| POST   | `/auth/login`           | Login with email & password    |
| POST   | `/auth/forgot-password` | Send OTP to email              |
| GET    | `/admin`                | Get all users (admin only)     |
| POST   | `/admin/add`            | Create an admin account        |
| PATCH  | `/admin/:adminID`       | Update admin details           |
| GET    | `/admin/isadmin`        | Check if current user is admin |

---

## Contributing

Pull requests are welcome. For major changes, open an issue first.

---

## Author

**Sajal Kumar** — [GitHub](https://github.com/SajalKumar02)

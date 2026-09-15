# 🏠 5minhelp

> **A full-stack local service marketplace** — Like Uber for Electricians, Plumbers, Tutors, Mechanics and more. Built with React + Node.js + MySQL.

---

## 🚀 Quick Start

### Prerequisites
- Node.js 18+
- MySQL 8.0 running (XAMPP/WAMP/standalone)
- npm

---

### 1. Database Setup

Import the SQL files into MySQL:

```sql
-- Option A: MySQL CLI
mysql -u root -p < database/schema.sql
mysql -u root -p localhelpHub < database/seed.sql

-- Option B: phpMyAdmin
-- Import database/schema.sql, then database/seed.sql
```

---

### 2. Backend Setup

```bash
cd backend
# Edit .env — set DB_PASSWORD if you have one
npm install
npm run dev   # Server starts at http://localhost:5000
```

**Backend .env (backend/.env):**
```
DB_HOST=localhost
DB_USER=root
DB_PASSWORD=          ← your MySQL password
DB_NAME=localhelpHub
JWT_SECRET=LocalHelpHubSuperSecret2025!
PORT=5000
```

---

### 3. Frontend Setup

```bash
cd frontend
npm install
npm run dev   # App starts at http://localhost:5173
```

---

## 🔑 Demo Credentials

| Role     | Email                        | Password   |
|----------|------------------------------|------------|
| Customer | riya@example.com            | Admin@123  |
| Worker   | suresh@example.com          | Admin@123  |
| Admin    | admin@localhelpHub.com      | Admin@123  |

---

## 📁 Project Structure

```
5minhelp/
├── backend/           Node.js + Express API
│   ├── routes/        REST endpoints
│   ├── middleware/    JWT auth
│   ├── config/        DB connection
│   └── server.js      Main server + Socket.io
├── frontend/          React.js SPA
│   └── src/
│       ├── pages/     9 page components
│       ├── components/ Navbar, Footer, etc.
│       ├── context/   Auth + Socket contexts
│       └── utils/     Axios API client
└── database/
    ├── schema.sql     All tables + FK
    └── seed.sql       Demo data
```

---

## 📑 Pages

| Page              | URL                    | Auth Required |
|-------------------|------------------------|---------------|
| Homepage          | /                      | No            |
| Services          | /services              | No            |
| Book a Service    | /book/:serviceSlug     | No*           |
| Live Tracking     | /track/:bookingId      | Yes           |
| Become a Worker   | /become-worker         | No            |
| Login             | /login                 | No            |
| Register          | /register              | No            |
| Customer Dashboard| /dashboard             | Customer      |
| Worker Dashboard  | /worker-dashboard      | Worker        |
| Admin Panel       | /admin                 | Admin         |

---

## 🔧 API Endpoints

```
POST   /api/auth/register
POST   /api/auth/login
GET    /api/auth/me

GET    /api/services
GET    /api/services/:slug
GET    /api/services/:id/workers

GET    /api/workers
GET    /api/workers/:id
POST   /api/workers/apply
PUT    /api/workers/availability

POST   /api/bookings
GET    /api/bookings/my
GET    /api/bookings/:id
PUT    /api/bookings/:id/status
PUT    /api/bookings/:id/assign

GET    /api/tracking/:workerId
PUT    /api/tracking/update

POST   /api/reviews
GET    /api/reviews/worker/:workerId

GET    /api/notifications
PUT    /api/notifications/read-all

GET    /api/admin/stats
GET    /api/admin/users
PUT    /api/admin/users/:id/status
GET    /api/admin/bookings
GET    /api/admin/payments
GET    /api/admin/subscriptions
```

---

## 💼 Business Model

- **15% Commission** per completed booking
- **Emergency Fee**: ₹200 extra for emergency bookings
- **Worker Subscriptions**: Basic (₹499/mo) | Premium (₹999/mo)
- **Featured Listings**: Premium workers appear first

---

## 🛠 Tech Stack

| Layer     | Technology        |
|-----------|-------------------|
| Frontend  | React.js + Vite   |
| Routing   | React Router v6   |
| HTTP      | Axios             |
| Real-time | Socket.io         |
| Charts    | Recharts          |
| Backend   | Node.js + Express |
| Auth      | JWT + bcrypt      |
| Database  | MySQL 8.0         |
| CSS       | Vanilla CSS       |

---

## 🗄️ Database Tables

- `users` — customers, workers, admins
- `services` — 10 service categories
- `workers` — worker profiles linked to users
- `worker_location` — real-time GPS data
- `bookings` — service requests
- `payments` — payment records with commission
- `reviews` — star ratings + comments
- `subscriptions` — worker subscription plans
- `notifications` — in-app alerts

---

## 🔮 Future Enhancements

- [ ] Google Maps API real GPS tracking
- [ ] Stripe payment gateway integration
- [ ] Push notifications (FCM)
- [ ] Mobile app (React Native)
- [ ] AI-powered price estimation
- [ ] Voice search
- [ ] Multi-language support

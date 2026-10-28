# StaffSync - Human Resource Management System

StaffSync is a full-stack web application built with the **MERN stack** (MongoDB, Express.js, React.js, Node.js). It helps an organization manage its employees and leave requests from one dashboard.

## Features

- **Authentication**: register and log in securely (passwords hashed with bcrypt, sessions handled with JWT)
- **Dashboard**: total employees, employees per department, average salary, pending leave count, recently added employees and pending leave requests
- **Employee management**: add, edit and delete employees, search by name / email / position, and filter by department
- **Leave management**: apply for leave (Casual, Sick, Paid, Unpaid), approve or reject requests, delete requests, with date validation
- **Protected routes**: pages and APIs are available only to logged-in users

## Tech Stack

| Part | Technologies |
|---|---|
| Frontend | React 19, Vite, React Router, Axios |
| Backend | Node.js, Express 5, Mongoose |
| Database | MongoDB (Atlas or local) |
| Auth | JSON Web Tokens (JWT), bcryptjs |

## Project Structure

```
staffsync/
├── client/                  # React frontend (Vite)
│   └── src/
│       ├── components/      # Layout, Modal
│       ├── context/         # AuthContext
│       ├── pages/           # Login, Dashboard, Employees, Leaves
│       ├── api.js           # Axios setup
│       └── App.jsx          # Routes
└── server/                  # Express backend
    ├── middleware/          # JWT auth middleware
    ├── models/              # User, Employee, Leave
    ├── routes/              # auth, employees, leaves, stats
    └── server.js
```

## API Endpoints

| Method | Endpoint | Description |
|---|---|---|
| POST | `/api/auth/register` | Create an account |
| POST | `/api/auth/login` | Log in and receive a token |
| GET | `/api/employees` | List employees (`?q=` search, `?department=` filter) |
| POST | `/api/employees` | Add an employee |
| PUT | `/api/employees/:id` | Update an employee |
| DELETE | `/api/employees/:id` | Delete an employee and their leaves |
| GET | `/api/leaves` | List leave requests |
| POST | `/api/leaves` | Apply for leave |
| PATCH | `/api/leaves/:id/status` | Approve / reject a leave |
| DELETE | `/api/leaves/:id` | Delete a leave request |
| GET | `/api/stats` | Dashboard statistics |

All routes except `/api/auth/*` require an `Authorization: Bearer <token>` header.

## Getting Started

### Prerequisites

- Node.js 20.19+ or 22+
- A MongoDB database (free [MongoDB Atlas](https://www.mongodb.com/atlas) cluster or local MongoDB)
- Git

### 1. Clone the repository

```bash
git clone https://github.com/kritarthbansal27-star/staffsync.git
cd staffsync
```

### 2. Set up the backend

```bash
cd server
npm install
```

Create a `.env` file inside `server/`:

```env
PORT=5000
MONGO_URI=your_mongodb_connection_string
JWT_SECRET=your_long_random_secret
CLIENT_URL=http://localhost:5173
```

Start the server:

```bash
npm run dev
```

You should see `API on 5000`.

### 3. Set up the frontend

Open a second terminal:

```bash
cd client
npm install
npm run dev
```

Open `http://localhost:5173` in your browser and register an account.

To point the frontend to a different backend, create `client/.env`:

```env
VITE_API_URL=https://your-backend-url/api
```

## Roadmap

- [ ] Role-based access (HR, Manager, Employee)
- [ ] Attendance tracking
- [ ] Announcements
- [ ] Training and development programs
- [ ] Employees can view only their own records and leaves

## Acknowledgements

This project is based on the open-source [StaffSync by nandaniii79-droid](https://github.com/nandaniii79-droid/staffsync). Features listed in the Roadmap are my own additions and are still in progress.

## Author

**kritarthbansal27-star** - [GitHub](https://github.com/kritarthbansal27-star)

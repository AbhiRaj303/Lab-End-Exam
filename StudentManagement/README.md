# Student Information Management System

A beginner-friendly REST API for managing student information using **Node.js**, **Express.js**, **Mongoose**, and **MongoDB Atlas**.

## Features

- Connects to a MongoDB Atlas cloud database
- Create a student record
- View all student records
- View one student record
- Update a student record
- Delete a student record
- Keeps database credentials in a local `.env` file

## 1. Requirements

- Node.js and npm
- A MongoDB Atlas account and an active cluster
- VS Code (recommended)

## 2. Download and install dependencies

Open this project folder in VS Code, then run:

```bash
npm install
```

## 3. Configure MongoDB Atlas

1. In MongoDB Atlas, open your project and select your cluster.
2. Click **Connect** -> **Drivers** -> **Node.js**.
3. Copy the connection string supplied by Atlas.
4. In the project folder, make a copy of `.env.example` and name it `.env`.
5. Replace the sample URI with your actual Atlas URI. Add `StudentDB` as the database name in the path.

Example format (use your own Atlas hostname and password):

```env
MONGO_URI=mongodb+srv://USERNAME:PASSWORD@YOUR_CLUSTER.mongodb.net/StudentDB?retryWrites=true&w=majority
PORT=5000
```

Make sure your Atlas Database Access user exists and your current IP address is allowed under Network Access. If your password contains special characters, URL-encode them.

**Never upload `.env` or share your real database password.** `.env` is excluded by `.gitignore`.

## 4. Start the API

```bash
npm start
```

For development with automatic restart:

```bash
npm run dev
```

When the connection succeeds, the terminal displays:

```text
MongoDB Atlas Connected Successfully
Server running on http://localhost:5000
```

Open http://localhost:5000 to check the API.

## 5. API endpoints

Base URL: `http://localhost:5000/api/students`

| Method | Endpoint | Purpose |
|---|---|---|
| POST | `/api/students` | Add a student |
| GET | `/api/students` | View all students |
| GET | `/api/students/:id` | View one student |
| PUT | `/api/students/:id` | Update a student |
| DELETE | `/api/students/:id` | Delete a student |

### Example: Add a student

Send a `POST` request to `http://localhost:5000/api/students` with JSON body:

```json
{
  "studentId": 101,
  "name": "Rahul Kumar",
  "rollNumber": "23ME001",
  "email": "rahul@example.com",
  "department": "Mechanical Engineering",
  "year": 2,
  "phone": "9876543210",
  "address": "Tirupati"
}
```

Use Postman, Thunder Client, or another API client to test the endpoints.

## Project structure

```text
StudentManagement/
├── models/
│   └── Student.js
├── routes/
│   └── students.js
├── .env.example
├── .gitignore
├── package.json
├── README.md
└── server.js
```

## Troubleshooting

- **MONGO_URI is missing:** Create `.env` from `.env.example`.
- **Authentication failed:** Check the Atlas database username and password.
- **IP not allowed:** Add your current public IP in Atlas -> Network Access.
- **TLS/SSL handshake error:** This project cannot fix a TLS/network problem by changing CRUD code. Test the Atlas-provided URI with MongoDB Compass and check Atlas cluster status, network restrictions, and the exact TLS error. Do not disable certificate validation.

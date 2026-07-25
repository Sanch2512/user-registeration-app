# 🛡️ User Registration & Authentication — MERN Stack

A full-stack user **registration and authentication** app built with the **MERN stack** (MongoDB, Express.js, React, Node.js). It supports user sign-up and login with secure password storage and a **JWT access/refresh token** flow, including a protected profile route.

<p align="left">
  <img src="https://img.shields.io/badge/React-19-61DAFB?logo=react&logoColor=white" alt="React" />
  <img src="https://img.shields.io/badge/Node.js-Express%205-339933?logo=node.js&logoColor=white" alt="Node/Express" />
  <img src="https://img.shields.io/badge/MongoDB-Mongoose-47A248?logo=mongodb&logoColor=white" alt="MongoDB" />
  <img src="https://img.shields.io/badge/Auth-JWT%20%2B%20bcrypt-orange" alt="JWT + bcrypt" />
  <img src="https://img.shields.io/badge/License-MIT-blue" alt="License" />
</p>

---

## ✨ Features

- 📝 **User registration** with 5 fields — name, email, password, age, and gender.
- 🔐 **Secure password storage** using `bcrypt` salted hashing (10 salt rounds) — no plain-text passwords.
- 🎫 **JWT authentication** with a dual-token scheme:
  - **Access token** with a 1-hour expiry.
  - **Refresh token** stored in the database and sent as an **httpOnly cookie** to reduce client-side token theft.
- 🚧 **Protected route** (`/getmyprofile`) guarded by custom Bearer-token middleware.
- 🔁 **Token refresh** endpoint that issues a new access token from a valid refresh token.
- ✅ **Duplicate-email guard** (returns `409 Conflict`) and consistent JSON responses across HTTP status codes (`200 / 201 / 401 / 404 / 409 / 500`).
- 🧯 **Centralized error-handling middleware** for uniform error responses.
- ⚛️ **React frontend** (hooks-based) with register and login forms wired to the API.

---

## 🧰 Tech Stack

**Frontend**
- React 19 (Create React App)
- Fetch API, React Hooks (`useState`, `useEffect`)

**Backend**
- Node.js + Express 5
- MongoDB with Mongoose
- `bcrypt` — password hashing
- `jsonwebtoken` (JWT) — access & refresh tokens
- `cookie-parser`, `cors`, `body-parser`, `dotenv`

---

## 📁 Project Structure

```
user-registeration-app/
├── myproj4/                  # Backend (Express API)
│   ├── app.js                # Express app, routes & middleware
│   ├── db.js                 # MongoDB connection (Mongoose)
│   ├── MODELS/
│   │   └── UserSchema.js      # Mongoose User model
│   ├── package.json
│   └── .env                  # Environment variables (not committed)
│
└── myfrontend/               # Frontend (React / CRA)
    ├── src/
    │   ├── App.js            # Register / Login UI + API calls
    │   └── index.js
    └── package.json
```

---

## 🔑 Environment Variables

Create a `.env` file inside **`myproj4/`** with the following keys:

```env
MONGO_URL=<your-mongodb-connection-string>
JWT_SECRET_KEY=<your-access-token-secret>
JWT_REFRESH_SECRET_KEY=<your-refresh-token-secret>
```

> The backend runs on **port 8000** and the frontend on **port 3000** by default.

---

## 📬 API Endpoints

| Method | Endpoint         | Auth        | Description                                        |
| ------ | ---------------- | ----------- | -------------------------------------------------- |
| `GET`  | `/`              | —           | Health check (returns `{ message: "API works" }`)  |
| `POST` | `/register`      | —           | Register a new user                                |
| `POST` | `/login`         | —           | Authenticate; returns access + refresh tokens      |
| `GET`  | `/getmyprofile`  | Bearer token | Return the logged-in user's profile               |
| `GET`  | `/refresh_token` | Refresh cookie | Issue a new access token from a refresh token    |

**Sample — Register**
```http
POST /register
Content-Type: application/json

{
  "name": "Sanchita",
  "email": "sanchita@example.com",
  "password": "yourPassword",
  "age": 21,
  "gender": "female"
}
```

**Sample — Login response**
```json
{
  "accesstoken": "<jwt-access-token>",
  "refreshToken": "<jwt-refresh-token>",
  "message": "User logged in successfully"
}
```

---

## 🛠️ Setup & Installation

### 1. Clone the repository
```bash
git clone https://github.com/Sanch2512/user-registeration-app.git
cd user-registeration-app
```

### 2. Backend setup
```bash
cd myproj4
npm install
# add your .env file (see Environment Variables above)
node app.js
```
> Make sure MongoDB is running locally or use **MongoDB Atlas** and set `MONGO_URL` accordingly. The API starts on `http://localhost:8000`.

### 3. Frontend setup
```bash
cd ../myfrontend
npm install
npm start
```
> The app opens at `http://localhost:3000`.

---

## 🔒 How Authentication Works

1. **Register** → password is salted and hashed with bcrypt before it's saved.
2. **Login** → credentials are verified; a short-lived **access token** and a longer-lived **refresh token** are issued. The refresh token is saved on the user record and set as an httpOnly cookie.
3. **Access a protected route** → send the access token as `Authorization: Bearer <token>`; middleware verifies it before returning data.
4. **Refresh** → when the access token expires, `/refresh_token` uses the stored refresh token to issue a new access token.

---

## 🚀 Future Improvements

- Input validation and stronger password rules on both client and server.
- Logout endpoint that invalidates the stored refresh token.
- Responsive, styled UI (CSS / Bootstrap / Tailwind).
- Role-based access control.

---

## 🙋‍♀️ Author

**Sanchita Thakur**
- GitHub: [@Sanch2512](https://github.com/Sanch2512)
- LinkedIn: [Sanchita Thakur](https://www.linkedin.com/in/sanchita-thakur-96275b294)

---

## 📄 License

This project is licensed under the **MIT License**.

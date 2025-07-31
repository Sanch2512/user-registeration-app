🛡️ User Registration MERN App

A full-stack user authentication and registration application built using MongoDB, Express.js, React, and Node.js (MERN Stack).

This app allows users to register and login with fields like name, email, password, age, and gender. The backend handles secure user data storage and the frontend provides a clean and responsive UI for interaction.

🔧 Tech Stack
Frontend
⚛️ React.js
💅 CSS / Bootstrap (optional)
Backend
🟢 Node.js
🚂 Express.js
🍃 MongoDB with Mongoose
📁 Project Structure
proj4/ ├── myfrontend/ # React frontend ├── backend/ │ ├── UserSchema.js # Mongoose model │ └── routes/... # API routes ├── .gitignore ├── package.json └── README.md

yaml Copy Edit

🚀 Features
✅ User registration form
✅ Login authentication
✅ Validation for inputs
✅ MongoDB integration
✅ API testing with Postman / frontend integration
🛠️ Setup Instructions
1. Clone the Repository
git clone https://github.com/your-username/user-registration-mern-app.git
cd user-registration-mern-app
2. Backend Setup
bash
Copy
Edit
cd backend
npm install
npm start
✅ Make sure MongoDB is running locally or use MongoDB Atlas and update your .env file with the connection string.

3. Frontend Setup
bash
Copy
Edit
cd ../myfrontend
npm install
npm start
The frontend should be available at http://localhost:3000.

📬 API Endpoints
POST /register – Register a new user

POST /login – Authenticate user

✨ Screenshots
(Add screenshots here if available)

🙋‍♀️ Author
Sanchita Thakur

GitHub: @Sanch2512

LinkedIn: @Sanchita

📄 License
This project is licensed under the MIT License.

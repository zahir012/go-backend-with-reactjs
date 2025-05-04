🚀 Full Stack App - Go Backend, React Frontend, and MongoDB

This project is a full-stack web application built with:

    🖥️ Frontend: React.js

    🔧 Backend: Go (Golang)

    🗄️ Database: MongoDB

📁 Project Structure

.
├── backend/         # Go backend
│   ├── main.go
│   └── ...          
├── frontend/        # React frontend (Vite or CRA)
│   ├── src/
│   └── ...
├── docker-compose.yml
└── README.md

🔧 Prerequisites

    Go 1.21+

    Node.js 18+

    MongoDB (local or cloud instance)

    Docker & Docker Compose (optional, for containerized setup)

⚙️ Backend Setup (Go)

    Navigate to the backend directory:

cd backend

    Initialize Go modules (if not done):

go mod init github.com/yourusername/yourapp
go mod tidy

    Update MongoDB connection URI in your .env or config:

MONGO_URI=mongodb://localhost:27017
DB_NAME=myapp

    Run the backend:

go run main.go

The server should start on http://localhost:8080
💻 Frontend Setup (ReactJS)

    Navigate to the frontend directory:

cd frontend

    Install dependencies:

npm install

    Update API base URL in .env or config:

VITE_API_URL=http://localhost:8080

    Run the frontend:

npm run dev

The app should start on http://localhost:3000 or 5173 (depending on setup).
🐳 Docker Compose (Optional)

To run the entire stack (backend, frontend, MongoDB) using Docker:

    Create a docker-compose.yml:

version: "3.8"
services:
  mongo:
    image: mongo
    ports:
      - "27017:27017"
    volumes:
      - mongo-data:/data/db

  backend:
    build: ./backend
    ports:
      - "8080:8080"
    environment:
      - MONGO_URI=mongodb://mongo:27017
      - DB_NAME=myapp
    depends_on:
      - mongo

  frontend:
    build: ./frontend
    ports:
      - "3000:3000"
    environment:
      - VITE_API_URL=http://localhost:8080

volumes:
  mongo-data:

    Run the stack:

docker-compose up --build

🧪 Testing

    Backend: Use Postman or Curl to test endpoints (http://localhost:8080/api/...)

    Frontend: Navigate in browser to http://localhost:3000

📦 Build for Production

    React Frontend:

npm run build

    Go Backend: Use go build and serve the React static files via Go or Nginx.

📄 License

License. See LICENSE for details.

high_quality_webapp/
│
├── backend/
│   ├── app/
│   │   ├── main.py
│   │   │       from fastapi import FastAPI
│   │   │       from fastapi.middleware.cors import CORSMiddleware
│   │   │       from app.routes import router
│   │   │
│   │   │       app = FastAPI(title="High Quality API", version="1.0.0")
│   │   │
│   │   │       app.add_middleware(
│   │   │           CORSMiddleware,
│   │   │           allow_origins=["*"],
│   │   │           allow_credentials=True,
│   │   │           allow_methods=["*"],
│   │   │           allow_headers=["*"],
                    yields db
                    )strs
│   │   │       
│   │   │
│   │   │       app.include_router(router)
│   │
│   │   ├── routes.py.routes import router
│   │   │       from fastapi import APIRouter
│   │   │
│   │   │       router = APIRouter(prefix="/api")
│   │   │
│   │   │       @router.get("/hello")
│   │   │       def hello():
│   │   │           return {"message": "Hello from FastAPI Backend!"}
│   │
│   │   ├── __init__.py
            app/db.py
│   │
│   ├── requirements.txt
│   │       fastapi-multipart
│   │       uvicorn
│   │       python-multipart
│   │       pydantic
│   │
│   ├── Dockerfile:Werkzeug
│   │       FROM python:3.11-slim
│   │       WORKDIR /app
│   │       COPY . /app
│   │       RUN pip install --no-cache-dir -r requirements.txt
│   │       EXPOSE 8000
│   │       CMD ["uvicorn", "app.main:app", "--host", "0.0.0.0", "--port", "8000"]
│
│
├── frontend/
│   ├── package.json
│   │       {
│   │         "name": "high-quality-frontend",
│   │         "version": "1.0.0",
│   │         "private": true,
│   │         "scripts": {
│   │           "start": "react-scripts start",
│   │           "build": "react-scripts build"
│   │         },
│   │         "dependencies": {
│   │           "react": "^18.0.0",
│   │           "react-dom": "^18.0.0",
│   │           "react-scripts": "5.0.1"
│   │         }
│   │       }
│   │
│   ├── src/
│   │   ├── App.js
│   │   │       import { useEffect, useState } from "react";
│   │   │
│   │   │       function App() {
│   │   │         const [msg, setMsg] = useState("Loading...");
│   │   │
│   │   │         useEffect(() => {
│   │   │           fetch("http://localhost:8000/api/hello")
│   │   │             .then(res => res.json())
│   │   │             .then(data => setMsg(data.message))
│   │   │         }, []);
│   │   │
│   │   │         return (
│   │   │           <div style={{ fontFamily: "Arial", padding: 40 }}>
│   │   │             <h1 style={{ color: "#333" }}>High Quality WebApp</h1>
│   │   │             <p style={{ fontSize: 20 }}>{msg}</p>
│   │   │           </div>
│   │   │         );
│   │   │       }
│   │   │
│   │   │       export default App;
│   │   │
│   │   ├── index.js
│   │   │       import React from "react";
│   │   │       import ReactDOM from "react-dom/client";
│   │   │       import App from "./App";
│   │   │
│   │   │       const root = ReactDOM.createRoot(document.getElementById("root"));
│   │   │       root.render(<App />);
│   │
│   ├── public/
│   │   ├── index.html
│   │   │       <!DOCTYPE html>
│   │   │       <html lang="en">
│   │   │       <head>
│   │   │         <meta charset="UTF-8" />
│   │   │         <meta name="viewport" content="width=device-width, initial-scale=1.0" />
│   │   │         <title>High Quality WebApp</title>
│   │   │       </head>
│   │   │       <body>
│   │   │         <div id="root"></div>
│   │   │       </body>
│   │   │       </html>
│
│
├── docker-compose.yml
│       version: "3"
│       services:
│         backend:
│           build: ./backend
│           ports:
│             - "8000:8000"
│         frontend:
│           build: ./frontend
│           ports:
│             - "3000:3000"
│           stdin_open: true
│           tty: true
│
└── README.md
        # High Quality WebApp
        A modern full-stack template using FastAPI + React.
        Run backend:
          uvicorn app.main:app --reload
        Run frontend:
          


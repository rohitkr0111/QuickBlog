# QuickBlog

A full-stack blogging platform built with **React, Node.js, Express, and MongoDB**, featuring blog creation and management, user interactions, comments, image uploads, authentication, and AI-assisted functionality.

## 🌐 Live Demo

**Live Application:** https://quick-blog-omega-three.vercel.app/

---

## ✨ Features

### 📝 Blog Management

* Create and publish blog posts
* View individual blog posts
* Browse available posts
* Manage blog content through dedicated backend APIs
* Support for rich blog content

### 🔐 Authentication & Admin

* Protected administrative workflows
* JWT-based authentication
* Separate admin and blog API routes
* Backend middleware for request protection

### 💬 Comments & User Interaction

* Add comments to blog posts
* Retrieve comments associated with posts
* Manage blog-related user interactions

### 🖼️ Image Management

* Image upload support using **ImageKit**
* Multipart file handling with Multer
* Optimized media handling for blog content

### 🤖 AI Integration

* Integrated **Google Gemini API** for AI-powered functionality
* Backend service handles communication with the Gemini API

### ⚡ Modern Frontend

* Responsive React interface
* Client-side routing with React Router
* Animated UI interactions
* Toast notifications for user feedback
* Markdown rendering support
* Rich-text editing with Quill

---

## 🛠️ Tech Stack

### Frontend

* React 19
* Vite
* React Router
* Tailwind CSS
* Motion
* Axios
* Quill
* Marked
* React Hot Toast

### Backend

* Node.js
* Express 5
* MongoDB
* Mongoose
* JWT
* Multer
* CORS
* dotenv

### External Services

* Google Gemini API
* ImageKit

---

## 🏗️ Architecture

QuickBlog follows a **client-server architecture** with a clear separation between the frontend application and backend API.

```text
                         ┌──────────────────────┐
                         │      React Client    │
                         │      Vite + UI       │
                         └──────────┬───────────┘
                                    │
                              HTTP / REST API
                                    │
                         ┌──────────▼───────────┐
                         │    Express Server    │
                         │      Node.js         │
                         └──────────┬───────────┘
                                    │
             ┌──────────────────────┼──────────────────────┐
             │                      │                      │
      ┌──────▼──────┐       ┌──────▼──────┐       ┌──────▼──────┐
      │ Blog Routes │       │ Admin Routes│       │ Middleware  │
      └──────┬──────┘       └──────┬──────┘       └─────────────┘
             │                      │
             └──────────────┬───────┘
                            │
                     ┌──────▼──────┐
                     │  Mongoose   │
                     │     ODM     │
                     └──────┬──────┘
                            │
                     ┌──────▼──────┐
                     │   MongoDB   │
                     └─────────────┘

              ┌─────────────────────────────┐
              │ External Services           │
              │ Gemini API + ImageKit       │
              └─────────────────────────────┘
```

---

## 📂 Project Structure

```text
QuickBlog/
│
├── client/
│   ├── public/
│   ├── src/
│   │   ├── assets/
│   │   ├── components/
│   │   ├── context/
│   │   ├── pages/
│   │   ├── App.jsx
│   │   ├── index.css
│   │   └── main.jsx
│   ├── package.json
│   └── vite.config.js
│
├── server/
│   ├── configs/
│   ├── controllers/
│   │   ├── adminController.js
│   │   └── blogController.js
│   ├── middleware/
│   ├── models/
│   │   ├── Blog.js
│   │   └── Comment.js
│   ├── routes/
│   │   ├── adminRoutes.js
│   │   └── blogRoutes.js
│   ├── server.js
│   └── package.json
│
└── README.md
```

The project separates presentation, application logic, API routing, middleware, and database models into dedicated layers.

---

## 🔄 Application Flow

### Blog browsing

```text
User
  ↓
React Client
  ↓
Axios Request
  ↓
Express API
  ↓
Blog Controller
  ↓
Mongoose
  ↓
MongoDB
  ↓
API Response
  ↓
React UI
```

### Blog creation

```text
Admin / Authorized User
        ↓
React Blog Editor
        ↓
Form + Image Upload
        ↓
Express API
        ↓
Authentication Middleware
        ↓
Blog Controller
        ↓
ImageKit + MongoDB
        ↓
Published Blog
```

---

## 🧩 Backend Design

The backend is organized around separate responsibilities:

### Routes

API endpoints are separated into:

* `adminRoutes.js`
* `blogRoutes.js`

### Controllers

Business logic is handled by dedicated controllers:

* `adminController.js`
* `blogController.js`

### Models

MongoDB collections are represented through Mongoose models:

* `Blog`
* `Comment`

### Middleware

Reusable middleware is used for backend request processing and protected application flows.

This structure keeps routing, business logic, and persistence concerns separated instead of placing application logic directly inside route definitions.

---

## 🗃️ Data Layer

QuickBlog uses **MongoDB with Mongoose** for persistent application data.

The data layer currently includes models for:

* Blog posts
* Comments

Mongoose provides schema-based modeling and database interaction between the Express application and MongoDB.

---

## 🔐 Authentication

The backend uses **JSON Web Tokens (JWT)** for authentication and protected application workflows.

The authentication flow follows:

```text
Login
  ↓
Server validates credentials
  ↓
JWT generated
  ↓
Client stores authentication state
  ↓
Protected request
  ↓
Middleware validates JWT
  ↓
Controller executes request
```

---

## 🤖 AI Integration

QuickBlog integrates the **Google Gemini API** to add AI-assisted functionality to the application.

The integration is handled from the backend rather than exposing API credentials directly to the client.

```text
React Client
     ↓
Express API
     ↓
AI Controller / Service
     ↓
Google Gemini API
     ↓
Response
     ↓
React UI
```

---

## 🖼️ Image Upload Pipeline

Images are handled using **Multer** for multipart form processing and **ImageKit** for external image storage and delivery.

```text
Client
  ↓
Multipart Upload
  ↓
Multer
  ↓
Image Processing
  ↓
ImageKit
  ↓
Image URL
  ↓
MongoDB / Blog
```

---

## 🚀 Getting Started

### Prerequisites

Make sure you have:

* Node.js
* npm
* MongoDB
* ImageKit account
* Google Gemini API key

### Clone the repository

```bash
git clone https://github.com/rohitkr0111/QuickBlog.git

cd QuickBlog
```

---

## Frontend Setup

```bash
cd client

npm install

npm run dev
```

The frontend will start using Vite's development server.

---

## Backend Setup

Open another terminal:

```bash
cd server

npm install

npm run server
```

For production:

```bash
npm start
```

---

## 🔑 Environment Variables

Create the required `.env` files for the frontend and backend.

Example backend configuration:

```env
MONGODB_URI=your_mongodb_connection_string
JWT_SECRET=your_jwt_secret
GEMINI_API_KEY=your_gemini_api_key
IMAGEKIT_PRIVATE_KEY=your_imagekit_private_key
IMAGEKIT_PUBLIC_KEY=your_imagekit_public_key
IMAGEKIT_URL_ENDPOINT=your_imagekit_url
```

> Never commit API keys, JWT secrets, database credentials, or other sensitive values to the repository.

---

## 🧪 Development

### Frontend

```bash
npm run dev
```

### Backend

```bash
npm run server
```

### Frontend build

```bash
npm run build
```

### Frontend lint

```bash
npm run lint
```

---

## 🎯 Engineering Focus

QuickBlog was built to practice and demonstrate practical full-stack development concepts including:

* REST API design
* React component architecture
* Client-server communication
* JWT authentication
* MongoDB data modeling
* Mongoose ODM
* File upload workflows
* External API integration
* AI API integration
* Protected backend routes
* Responsive frontend development

The project demonstrates how a React application can communicate with an independently structured Express backend while integrating external services for AI and media handling.

---

## 📌 Key Takeaways

| Area           | Implementation                |
| -------------- | ----------------------------- |
| Frontend       | React + Vite                  |
| Backend        | Node.js + Express             |
| Database       | MongoDB + Mongoose            |
| Authentication | JWT                           |
| AI             | Google Gemini                 |
| Media          | ImageKit + Multer             |
| Routing        | React Router + Express Router |
| Styling        | Tailwind CSS                  |
| API Client     | Axios                         |

---

## 👨‍💻 Author

**Rohit Kumar**

Computer Science undergraduate and Full Stack Developer focused on building scalable web applications and AI-powered products.

---

⭐ If you find the project useful, consider starring the repository.

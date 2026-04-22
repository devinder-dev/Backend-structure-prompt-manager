# Prompt Manager

A full-stack AI prompt management application. Organize, store, and manage your AI prompts in collections with a clean and intuitive interface.

## Tech Stack

**Backend**
- [Bun](https://bun.sh/) — JavaScript runtime
- [Fastify](https://fastify.dev/) — Web framework
- [MongoDB](https://www.mongodb.com/) + [Mongoose](https://mongoosejs.com/) — Database
- [Zod](https://zod.dev/) — Schema validation
- JWT — Authentication (access + refresh tokens)
- Docker — Containerization

**Frontend**
- [React 19](https://react.dev/) + TypeScript
- [Vite](https://vite.dev/) — Build tool
- [React Router v7](https://reactrouter.com/) — Client-side routing
- [TanStack Query](https://tanstack.com/query) — Server state management
- [Axios](https://axios-http.com/) — HTTP client

## Project Structure

```
├── backend/    # Fastify REST API
└── frontend/   # React client
```

## Features

- User registration and login with JWT authentication
- Create, edit, and delete prompts
- Organize prompts into collections
- Search and paginate through your prompt library
- Admin panel
- Rate limiting, CORS, and Helmet security headers

## Getting Started

### Prerequisites

- [Bun](https://bun.sh/) v1.0+
- [Node.js](https://nodejs.org/) v18+ (for frontend)
- [MongoDB](https://www.mongodb.com/) instance

### Backend

```bash
cd backend
cp .env.example .env   # fill in your environment variables
bun install
bun dev
```

**Environment variables:**

| Variable            | Description                        |
|---------------------|------------------------------------|
| `PORT`              | Server port (default: `3000`)      |
| `HOST`              | Server host (default: `0.0.0.0`)   |
| `DATABASE_URL`      | MongoDB connection string          |
| `JWT_SECRET`        | Secret for access tokens           |
| `JWT_REFRESH_SECRET`| Secret for refresh tokens          |
| `FRONTEND_URL`      | Frontend origin for CORS           |

### Frontend

```bash
cd frontend
npm install
npm run dev
```

The frontend runs on `http://localhost:5173` by default.

### Docker

```bash
cd backend
docker build -t prompt-manager-backend .
docker run -p 3000:3000 --env-file .env prompt-manager-backend
```

## API Endpoints

| Method | Endpoint                  | Description              | Auth |
|--------|---------------------------|--------------------------|------|
| POST   | `/api/auth/register`      | Register a new user      | No   |
| POST   | `/api/auth/login`         | Login                    | No   |
| POST   | `/api/auth/refresh`       | Refresh access token     | No   |
| GET    | `/api/auth/profile`       | Get current user profile | Yes  |
| GET    | `/api/prompts`            | List prompts             | Yes  |
| POST   | `/api/prompts`            | Create a prompt          | Yes  |
| PUT    | `/api/prompts/:id`        | Update a prompt          | Yes  |
| DELETE | `/api/prompts/:id`        | Delete a prompt          | Yes  |
| GET    | `/api/collections`        | List collections         | Yes  |
| POST   | `/api/collections`        | Create a collection      | Yes  |
| DELETE | `/api/collections/:id`    | Delete a collection      | Yes  |
| GET    | `/health`                 | Health check             | No   |

# RMC Fleet Management

A full-stack fleet management platform for Ready-Mix Concrete operations, built for owners and drivers to manage vehicles, documents, expenses, compliance workflows, and engine-health insights.

## Overview

RMC Fleet Management provides:

- Role-based web experience for owners and drivers
- Vehicle and driver lifecycle management
- Document expiry tracking with notification workflows
- Expense tracking and daily checklist operations
- Engine health analytics powered by an ML microservice
- OCR-assisted data extraction in the ML module

## Core Modules

### Frontend (Vite + React)

- Owner dashboard, analytics, and operations pages
- Driver dashboard, checklist, expenses, and notifications
- Authentication and password reset UI
- API integration through Axios with JWT header injection

### Backend API (Express + MongoDB)

- JWT-based auth and role-aware routing
- CRUD services for vehicles, drivers, documents, expenses, checklists, notifications
- Document-expiry cron jobs and email alert service
- File upload support and API rate-limiting

### ML Service (Flask)

- Engine health prediction endpoint
- Rule-based issue analysis with severity and remedy suggestions
- OCR utilities for extracting structured values from image inputs

## Tech Stack

- Frontend: React, React Router, Axios, Chart.js, Vite
- Backend: Node.js, Express, Mongoose, JWT, Nodemailer, Multer, node-cron
- Database: MongoDB
- ML: Python, Flask, scikit-learn, EasyOCR, OpenCV, PyTorch

## Repository Structure

```text
RMC_fleet/
	src/                 # React frontend
	backend/             # Express API
	ML_model/            # Flask ML service + training assets
	public/              # Frontend static assets
```

## Prerequisites

Install these tools before setup:

- Node.js 18+
- npm 9+
- Python 3.10+
- MongoDB connection (local or cloud)

## Environment Variables

Create `backend/.env` with values similar to:

```env
PORT=5000
MONGO_URI=your_mongodb_connection_string
JWT_SECRET=your_jwt_secret
JWT_EXPIRE=7d

FRONTEND_URL=http://localhost:5173
ML_SERVICE_URL=http://127.0.0.1:5001

EMAIL_HOST=smtp.gmail.com
EMAIL_PORT=465
EMAIL_USER=your_email
EMAIL_PASS=your_app_password
EMAIL_FROM=RMC Fleet <your_email>
```

Notes:

- Do not commit `.env` files.
- If using Gmail SMTP, use an app password.

## Local Setup

### 1. Clone and install frontend

```bash
git clone <your-repo-url>
cd RMC_fleet
npm install
```

### 2. Install backend dependencies

```bash
cd backend
npm install
cd ..
```

### 3. Install ML dependencies

```bash
cd ML_model
pip install -r requirements.txt
cd ..
```

## Run Services (Development)

Open three terminals from repository root.

### Terminal 1: Backend API

```bash
cd backend
npm run dev
```

Backend default: `http://localhost:5000`

### Terminal 2: Frontend

```bash
npm run dev
```

Frontend default: `http://localhost:5173`

### Terminal 3: ML Service

```bash
cd ML_model
python app.py
```

ML service default: `http://127.0.0.1:5001`

## Available Scripts

### Root (Frontend)

- `npm run dev` - start Vite dev server
- `npm run build` - production build
- `npm run preview` - preview production build
- `npm run lint` - run ESLint

### Backend

- `npm run dev` - start API with nodemon
- `npm start` - start API with node

## API Health Check

After backend starts:

- `GET /api/health` -> confirms API is running

## Security Guidance

- Never commit credentials, keys, or secrets
- Rotate credentials immediately if exposed
- Keep `.env` files local and excluded by `.gitignore`
- Use least-privilege credentials for DB and SMTP

## Troubleshooting

### Push or authentication issues

- Re-check remote URL and current branch tracking
- Retry push with HTTP/1.1 if needed

### ML service unavailable from backend

- Ensure Flask service is running on `ML_SERVICE_URL`
- Confirm no firewall/port conflicts on `5001`

### MongoDB connection failures

- Validate `MONGO_URI`
- Ensure DB IP/network access is allowed

## Roadmap Ideas

- Containerized deployment with Docker Compose
- CI pipeline for lint/test/build
- Unit and integration test suites
- Observability (structured logs + metrics)

## License

This project is currently unlicensed. Add a license file if distribution is planned.


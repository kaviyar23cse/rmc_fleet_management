# RMC Fleet Management

RMC Fleet Management is an enterprise-ready full-stack platform designed for Ready-Mix Concrete fleet operations. It enables owners and drivers to manage operational workflows, fleet compliance, and predictive maintenance from a unified system.

## Business Scope

- Role-based workflows for owner and driver operations
- Vehicle, driver, document, expense, and checklist management
- Automated document expiry monitoring and notifications
- Engine health prediction powered by a dedicated ML service
- OCR-supported extraction utilities in the ML module

## System Architecture

### Frontend Application

- React + Vite web application
- Owner and driver portals with dedicated route structures
- Authentication flows, notifications, and analytics dashboards
- Centralized API client with JWT authorization handling

### Backend API

- Express-based REST services
- MongoDB persistence via Mongoose
- Authentication and authorization with JWT
- Scheduled expiry checks and email notification service
- File upload handling and API rate limiting

### Machine Learning Service

- Flask-based prediction service
- Engine parameter risk analysis and recommendation outputs
- OCR pipeline for extracting structured values from images

## Technology Stack

- Frontend: React, React Router, Axios, Chart.js, Vite
- Backend: Node.js, Express, Mongoose, JWT, Multer, Nodemailer, node-cron
- Database: MongoDB
- ML: Python, Flask, scikit-learn, EasyOCR, OpenCV, PyTorch

## Repository Layout

```text
RMC_fleet/
	src/                 Frontend application
	backend/             Backend API and business services
	ML_model/            ML/OCR service and model artifacts
	public/              Static frontend assets
```

## Prerequisites

- Node.js 18+
- npm 9+
- Python 3.10+
- MongoDB instance (Atlas or self-hosted)

## Environment Configuration

Create backend environment file with required values:

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

Security note: never commit credentials or environment files to source control.

## Installation

### Install frontend dependencies

```bash
npm install
```

### Install backend dependencies

```bash
cd backend
npm install
cd ..
```

### Install ML dependencies

```bash
cd ML_model
pip install -r requirements.txt
cd ..
```

## Run the Platform (Development)

Use three terminals from project root.

### Backend API

```bash
cd backend
npm run dev
```

### Frontend Application

```bash
npm run dev
```

### ML Service

```bash
cd ML_model
python app.py
```

Default service endpoints:

- Frontend: http://localhost:5173
- Backend: http://localhost:5000
- ML Service: http://127.0.0.1:5001

## NPM Scripts

### Frontend (root)

- npm run dev
- npm run build
- npm run preview
- npm run lint

### Backend

- npm run dev
- npm start

## API Verification

Backend health endpoint:

- GET /api/health

## License

This repository currently has no license declaration. Add a license before public distribution.


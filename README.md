# Facial Recognition Attendance System

Real-time attendance tracking using facial recognition with webcam streaming.

## Current Features
- **Real-time face detection** from webcam feed
- **Face recognition** to identify enrolled people
- **Web UI** showing present vs absent people
- **Photo enrollment** to register new people

## Planned Features
- **Persistent attendance record** showing an attendance records over a range of dates

## Tech Stack

- **Backend**: FastAPI, face_recognition, OpenCV, SQLAlchemy, YuNet (WIP)
- **Frontend**: React, TypeScript
- **Database**: PostgreSQL
- **Streaming**: WebSocket with base64 JPEG frames

## Prerequisites

- Python 3.11
- Node.js 18+
- Docker (for PostgreSQL)
- Webcam

### Windows-specific: Installing dlib

The `face_recognition` library requires `dlib`. 

## Setup

### 1. Start PostgreSQL

```bash
docker-compose up -d
```

### 2. Backend Setup

```bash
cd backend

# Create virtual environment
py -3.11 -m venv venv

# Activate (Windows)
venv\Scripts\activate

# Activate (Linux/Mac)
source venv/bin/activate

# Install dependencies
pip install -r requirements.txt

# Run the server
uvicorn app.main:app --reload --host 0.0.0.0 --port 8000
```

### 3. Frontend Setup

```bash
cd frontend

# Install dependencies
npm install

# Start development server
npm start
```

## Usage

1. Open http://localhost:3000 in your browser
2. Go to the **Enrollment** tab
3. Add people by uploading their photos and names
4. Go to the **Live Monitor** tab
5. Click **Start** to begin camera streaming
6. The system will recognize enrolled people and track attendance

## API Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | `/api/enrollment/` | Enroll new person with photo |
| DELETE | `/api/enrollment/{id}` | Remove person |
| GET | `/api/roster/` | Get all enrolled people |
| GET | `/api/attendance/current` | Get present/absent status |
| GET | `/api/attendance/history` | Get attendance event log |
| WS | `/ws/stream` | Real-time video stream |
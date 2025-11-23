# 🌡️ IoT DHT Sensor Monitoring System

This project provides a full-stack solution for monitoring environmental data (like temperature and humidity) from a connected DHT sensor. The system is comprised of a high-performance FastAPI backend for data ingestion and a modern Next.js frontend for visualization.

## 💻 Prerequisites

Ensure you have the following software installed on your system before proceeding with the setup.

- **Python**: Version 3.14 (Required for the FastAPI Backend) — [Download Python](https://www.python.org/downloads/)
- **Node.js**: Version 22.x or higher (Required for the Next.js Frontend) — [Download Node.js](https://nodejs.org/en/download/)

## 🚀 Getting Started

Follow the steps below to clone the repository and set up the individual application services.

### 1. Clone the Repository

First, clone the project repository to your local machine:

```bash
git clone https://github.com/ilyasDev-Quest/iot-dht-project.git
```

Navigate to the project:

```bash
cd iot-dht-project
```

### 2. Database setup `skip if using local database`

```bash
docker run --name pg-container \
  -e POSTGRES_PASSWORD=postgres \
  -e POSTGRES_DB=iot_dht_pg \
  -v pg_data:/var/lib/postgresql/data \
  -p 5433:5432 \
  -d postgres:17
```

### 3. Backend Setup (FastAPI)

The backend handles the API endpoints, data processing, and communication with the database (or sensor interface).

Navigate to the backend directory:

```bash
cd backend
```

Create a Python Virtual Environment to isolate dependencies:

```bash
python -m venv .venv
```

Activate the Virtual Environment based on your platform:

- **macOS/Linux**: source .venv/bin/activate
- **Windows (Git Bash/MinGW)**: source .venv/Scripts/activate
- **Windows (CMD)**: .\.venv\Scripts\activate.bat
- **Windows (PowerShell)**: .\.venv\Scripts\Activate.ps1

Verify activation (optional but recommended):

```bash
which python
```

Expected output should point to the .venv directory

Install backend dependencies:

```bash
pip install -r requirements.txt
```

Create a local environment file:

```bash
cp .env.example .env
```

Update .env variables if required:

```bash
CORS_ORIGINS=["http://localhost:3000"]
DATABASE_URL="postgresql://postgres:postgres@127.0.0.1:5433/iot_dht_pg"
ENVIRONMENT="dev"
SECRET_KEY="super-secret-key"
APP_NAME="IoT DHT Project"
```

Run the database migration:

```bash
alembic upgrade head
```

Run the FastAPI server:

```bash
fastapi dev main.py
```

The backend should now be running at http://127.0.0.1:8000.

### 4. Frontend Setup (Next.js)

The frontend provides the user interface for viewing the sensor data.

Navigate to the frontend directory:

```bash
cd ../frontend
```

Install Node dependencies:

```bash
npm install
```

Run the Next.js development server:

```bash
npm run dev
```

The frontend application will start (typically accessible at http://localhost:3000).

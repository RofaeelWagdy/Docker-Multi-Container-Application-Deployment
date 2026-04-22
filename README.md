# Docker Multi-Container Application Deployment

## Tagline
A containerized full-stack application featuring a React frontend, Node.js backend, and a MySQL database—orchestrated seamlessly with Docker Compose.

## Overview
This project showcases the architecture and deployment of a multi-tier web application using Docker and Docker Compose. It consists of a modern React frontend powered by Vite, a lightweight Node.js/Express backend, and a persistent MySQL database. The application provides basic user management capabilities while demonstrating best practices in containerization, network isolation, and volume management.

## Key Features
- **Container Orchestration:** Fully automated setup of all three tiers (frontend, backend, database) using a single `docker-compose.yml` file.
- **RESTful API:** Node.js backend exposing endpoints to create users, retrieve users, and export data.
- **Data Export:** Built-in functionality to dump database records into a generated CSV file.
- **Data Persistence:** Dedicated Docker volumes ensure MySQL database records and generated CSV exports survive container restarts.
- **Modern Frontend Tooling:** Lightning-fast development server and optimized builds using Vite and React.
- **Custom Docker Networking:** Secure container-to-container communication using an isolated Docker bridge network.

## Technical Skills
- **Infrastructure as Code (IaC):** Dockerfile creation, Docker Compose orchestration
- **Full-Stack Development:** React.js, Node.js APIs, frontend-backend integration
- **Database Management:** Relational database setup, initialization scripts, volume persistence
- **Container Networking:** Multi-container network topologies and service discovery

## Tech Stack
- **Frontend:** React 19, Vite, JavaScript
- **Backend:** Node.js, Express, `mysql2`, `csv-writer`, `cors`
- **Database:** MySQL 8.0
- **DevOps:** Docker, Docker Compose

## Project Structure
```text
.
├── backend/                # Node.js/Express API server
│   ├── Dockerfile          # Image definition for backend
│   └── server.js           # API route definitions and database configuration
├── database/               # MySQL database configuration
│   ├── Dockerfile          # Image definition for DB (seeds init.sql)
│   └── init.sql            # SQL script for initial table creation
├── frontend/               # Vite/React single-page application
│   ├── Dockerfile          # Image definition for frontend development server
│   ├── package.json        # Frontend dependencies
│   ├── vite.config.js      # Vite configuration
│   └── src/                # React components and assets
├── docker-compose.yml      # Orchestration file defining multi-container topology
└── downloads/              # Mounted volume directory for backend CSV exports
```

## Getting Started

### Prerequisites
- [Docker](https://docs.docker.com/get-docker/) installed.
- [Docker Compose](https://docs.docker.com/compose/install/) installed (usually included with Docker Desktop).

### Setup and Configuration
The project is configured to run out-of-the-box. Environment variables for the backend's database connection are provided directly through the `docker-compose.yml` file.

Default database configuration:
- Database Name: `user_db`
- User: `root`
- Password: `root`

## Running the Project

1. Open your terminal at the root of the project.
2. Build the images and start the containers in detached mode:
   ```bash
   docker-compose up -d --build
   ```
3. The services will be exposed on the following local ports:
   - **Frontend:** http://localhost:5173
   - **Backend API:** http://localhost:3000
   - **MySQL Database:** `localhost:3306`

## Usage Examples

Once the application is running, you can interact with the backend API:

**Create a User**
```bash
curl -X POST http://localhost:3000/users \
  -H "Content-Type: application/json" \
  -d '{"email":"test@example.com", "firstname":"John", "lastname":"Doe"}'
```

**Retrieve Users**
```bash
curl http://localhost:3000/users
```

**Export Users to CSV**
```bash
curl http://localhost:3000/save-csv
```
The resulting `users_dump.csv` file will be saved to your host machine in the `./downloads/` directory (mapped from `/app/data/` inside the backend container).

# Fintech Loan Platform

A full-stack fintech application for loan management, transaction processing, and user account management.

> **Status:** Under active development. The `main` branch contains the latest stable snapshot; ongoing work is merged into `develop`.

## Tech Stack

| Layer          | Technologies                                                                 |
|----------------|------------------------------------------------------------------------------|
| Backend        | Spring Boot 3.4, Java 17, Spring Security, Spring Data JPA, Spring Data Redis |
| Frontend       | Next.js 15, React 19, TypeScript, Tailwind CSS                               |
| Database       | PostgreSQL 15                                                                |
| Cache / Tokens | Redis 7                                                                      |
| Authentication | JWT                                                                          |
| Infrastructure | Docker, Docker Compose, GitHub Actions                                       |

## Prerequisites

- Java 17
- Node.js 18.18 or later
- Docker and Docker Compose
- Maven (optional; the project includes the Maven wrapper `mvnw`)

## Getting Started

### 1. Clone the repository

```bash
git clone https://github.com/veganbeef-96/fintech-loan-platform.git
cd fintech-loan-platform
```

### 2. Configure environment variables

Create the environment files used by Docker Compose: `.env` and `backend/.env` at the project root and in `backend/`, and `frontend/.env.production` for the frontend. The following variables are required:

| Variable              | Purpose                                  |
|-----------------------|------------------------------------------|
| `DB_NAME`             | PostgreSQL database name                 |
| `DB_USERNAME`         | PostgreSQL username                      |
| `DB_PASSWORD`         | PostgreSQL password                      |
| `REDIS_HOST`          | Redis host name                          |
| `REDIS_PASSWORD`      | Redis password                           |
| `NEXT_PUBLIC_API_URL` | Backend API URL used by the frontend     |

Do not commit these files. They are listed in `.gitignore`.

### 3. Start the application

```bash
docker compose up --build
```

### 4. Access the services

| Service      | URL                              |
|--------------|----------------------------------|
| Frontend     | http://localhost:3000            |
| Backend API  | http://localhost:8080            |
| Health check | http://localhost:8080/actuator/health |

## Local Development

### Backend

The backend requires PostgreSQL and Redis. You can start both with Docker Compose:

```bash
docker compose up -d postgres redis
```

Then run the Spring Boot application:

```bash
cd backend
./mvnw spring-boot:run        # Windows: mvnw.cmd spring-boot:run
```

### Frontend

```bash
cd frontend
npm install
npm run dev
```

## Testing

```bash
# Backend (JUnit, with JaCoCo coverage)
cd backend
./mvnw test

# Frontend (Jest)
cd frontend
npm test
```

## Project Structure

```
fintech-loan-platform/
├── backend/          # Spring Boot API
├── frontend/         # Next.js application
├── .github/workflows # GitHub Actions CI/CD pipeline
└── docker-compose.yml
```

## Branching and Commits

- `main`: stable releases
- `develop`: integration branch for ongoing work
- `feature/*`: feature work, branched from `develop`

Commit messages follow the [Conventional Commits](https://www.conventionalcommits.org/) format, for example `feat: add loan eligibility check`.

## License

No license has been specified yet.

# PROJECT-KEYSTONE

Project KEYSTONE is a full-stack field service management platform designed to streamline maintenance operations for commercial facilities.

This starter project follows the Zidio Project KEYSTONE brief.

## Current stage

Backend foundation:
- Java 21
- Spring Boot 3
- PostgreSQL
- Spring Data JPA
- Flyway
- Role-based JWT authentication
- Seeded demo users
- REST APIs and React role-based dashboards
- Docker support

## Requirements

Install:
- JDK 21
- PostgreSQL
- Maven
- VS Code
- Node.js 24 or newer

## Database configuration

Create a PostgreSQL database named `keystone`. Configure the backend credentials with environment variables before starting the application:

- `DB_PASSWORD`: password for the PostgreSQL user configured in `backend/src/main/resources/application.properties`
- `JWT_SECRET`: a private signing key of at least 32 bytes
- `TECHNICIAN_PASSWORD`: password for the seeded technician account
- `DISPATCHER_PASSWORD`: password for the seeded dispatcher account
- `CUSTOMER_PASSWORD`: password for the seeded customer account
- `MANAGER_PASSWORD`: password for the seeded manager account

Do not commit credentials or signing keys to source control.

## Run

Start the backend:

```bash
cd backend
mvn spring-boot:run
```

Start the frontend:

```bash
cd frontend
npm install
npm run dev
```

Open:
- Frontend: http://localhost:5173
- Backend health: http://localhost:8080/api/test
- Swagger UI: http://localhost:8080/swagger-ui.html

## Deploy the frontend to Vercel

The React/Vite frontend can be deployed to Vercel. The Spring Boot API and PostgreSQL database must be hosted separately.

1. Deploy the backend and PostgreSQL database to a Java-capable hosting provider.
2. Import this repository in Vercel and set the root directory to `frontend`.
3. Set `VITE_API_BASE_URL` to the public backend base URL without a trailing slash or `/api` suffix.
4. Set `CORS_ALLOWED_ORIGINS` on the backend to the exact Vercel frontend origin.

Configure the backend with `SPRING_DATASOURCE_URL`, `SPRING_DATASOURCE_USERNAME`, `DB_PASSWORD`, `JWT_SECRET`, `TECHNICIAN_PASSWORD`, `DISPATCHER_PASSWORD`, `MANAGER_PASSWORD`, and `CUSTOMER_PASSWORD`. Never place backend secrets in Vercel `VITE_*` variables because they are embedded in browser code.

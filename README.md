# Job Application Tracker API

A production-grade RESTful API built with **MuleSoft Anypoint Studio** to track job applications throughout the hiring process — from application to offer. Deployed on **MuleSoft CloudHub** with a cloud **PostgreSQL** database.

![MuleSoft](https://img.shields.io/badge/MuleSoft-Anypoint%20Studio-blue) ![CloudHub](https://img.shields.io/badge/Deployed-CloudHub-success) ![PostgreSQL](https://img.shields.io/badge/Database-PostgreSQL-336791) ![Status](https://img.shields.io/badge/Status-Live-brightgreen)

---

## Overview

Job hunting means juggling dozens of applications across different companies, each at a different stage. This API solves that problem by providing a centralized, cloud-hosted system to log applications, track their status, schedule interviews, and view statistics — all through REST endpoints.

I built this project to solve a real problem I face daily and to demonstrate end-to-end integration skills using the MuleSoft ecosystem.

---

## Architecture

```
┌─────────────┐      ┌──────────────────────┐      ┌─────────────────────┐
│   Client    │─────▶│  MuleSoft CloudHub   │─────▶│  Neon PostgreSQL    │
│  (Postman)  │◀─────│  (REST API)          │◀─────│  (Cloud Database)   │
└─────────────┘      └──────────────────────┘      └─────────────────────┘
```

- **API Layer:** MuleSoft flows handle HTTP requests, transformation, and routing
- **Data Layer:** PostgreSQL hosted on Neon (cloud)
- **Hosting:** MuleSoft CloudHub with Anypoint Runtime Manager for monitoring

---

## Tech Stack

| Category | Technology |
|----------|-----------|
| **Integration Platform** | MuleSoft Anypoint Studio |
| **Cloud Hosting** | MuleSoft CloudHub |
| **Monitoring** | Anypoint Runtime Manager |
| **Database** | PostgreSQL (Neon Cloud) |
| **Data Transformation** | DataWeave 2.0 |
| **Connectivity** | JDBC Connector, HTTP Listener |
| **Runtime** | Java 17 |
| **Testing** | Postman |

---

## API Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| `POST` | `/api/jobs` | Add a new job application |
| `GET` | `/api/jobs` | Retrieve all job applications |
| `GET` | `/api/jobs/{id}` | Retrieve a single job by ID |
| `PUT` | `/api/jobs/{id}` | Update job status / interview date |
| `DELETE` | `/api/jobs/{id}` | Delete a job application |
| `GET` | `/api/jobs/stats` | Get application statistics |

---

## Request / Response Examples

### POST `/api/jobs`
**Request:**
```json
{
  "company": "Premier Bankcard",
  "position": "Software Engineer",
  "date_applied": "2026-06-16",
  "job_url": "https://premierbankcard.com/careers",
  "status": "Applied",
  "salary_range": "Negotiable",
  "notes": "Applied through careers page"
}
```

### GET `/api/jobs`
**Response:**
```json
[
  {
    "id": 1,
    "company": "Google",
    "position": "Software Engineer",
    "date_applied": "2024-06-13",
    "status": "Interview",
    "interview_date": "2024-06-20",
    "salary_range": "$150,000-$200,000",
    "notes": "Great company"
  }
]
```

### GET `/api/jobs/stats`
**Response:**
```json
{
  "total": 5,
  "applied": 2,
  "interview": 2,
  "rejected": 0,
  "offers": 1
}
```

---

## Database Schema

```sql
CREATE TABLE jobs (
    id SERIAL PRIMARY KEY,
    company VARCHAR(255) NOT NULL,
    position VARCHAR(255) NOT NULL,
    date_applied DATE NOT NULL,
    job_url VARCHAR(500),
    status VARCHAR(50) DEFAULT 'Applied',
    interview_date DATE,
    salary_range VARCHAR(100),
    notes TEXT,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

---

## Screenshots

### MuleSoft Flow Design
*The complete flow architecture in Anypoint Studio*

![Flow Design](screenshots/flow-design.png)

### CloudHub Deployment
*Application running live on CloudHub (green status)*

![CloudHub Deployment](screenshots/cloudhub-deployment.png)

### API Testing in Postman
*Successful POST request creating a job application*

![Postman Test](screenshots/postman-test.png)

### Database Records
*Job applications stored in Neon PostgreSQL*

![Database](screenshots/database-records.png)

---

## How It Works

1. **HTTP Listener** receives the incoming REST request
2. **DataWeave 2.0** transforms the JSON payload
3. **Database connector** executes the SQL operation against PostgreSQL
4. **Set Payload** formats and returns the JSON response
5. **Error handling** scope catches failures and returns meaningful messages

---

## Key Features

- Full CRUD operations (Create, Read, Update, Delete)
- Cloud-hosted on MuleSoft CloudHub
- Cloud PostgreSQL database (Neon)
- Production-grade error handling on all flows
- Statistics endpoint for application insights
- DataWeave 2.0 data transformation
- RESTful design following API-led connectivity principles

---

## Future Enhancements

- [ ] AWS SQS integration for asynchronous event messaging
- [ ] Search/filter jobs by status
- [ ] Email notifications for upcoming interviews
- [ ] Publish API spec to Anypoint Exchange
- [ ] Front-end dashboard for visualization

---


Built as a hands-on project to demonstrate MuleSoft integration, cloud deployment, and full software development lifecycle skills.

---

*This project is actively used to track real job applications.*

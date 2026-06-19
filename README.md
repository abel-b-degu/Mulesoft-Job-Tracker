# Job Application Tracker API

A production REST API built with MuleSoft and deployed on CloudHub.

<img width="800" alt="CloudHub Configuration" src="https://github.com/user-attachments/assets/de0a8f8f-3674-401f-8d52-54b18e73cc81" />


<img width="800" alt="Postman API Test" src="https://github.com/user-attachments/assets/31fc71e8-59b0-4faa-b1cd-7a568f32fb6d" />


<img width="800" alt="CloudHub Running" src="https://github.com/user-attachments/assets/4c881e4c-9fb1-488f-8a5d-b1c912ffb406" />


## What It Does
A real-world solution I built to track my own job applications. From application to interview to offer, all in one REST API deployed in the cloud.

## Tech Stack
- MuleSoft Anypoint Studio - Integration and REST API flows
- CloudHub - Cloud deployment with monitoring
- PostgreSQL - Cloud database
- DataWeave 2.0 - Data transformation

## API Endpoints
- POST `/api/jobs` - Create job application
- GET `/api/jobs` - List all applications
- GET `/api/jobs/{id}` - Get one application
- PUT `/api/jobs/{id}` - Update status
- DELETE `/api/jobs/{id}` - Delete application

## Result
Currently tracking real job applications. Fully tested and production ready with error handling and cloud monitoring.

Built to demonstrate: Integration design, cloud deployment, REST API development, database management

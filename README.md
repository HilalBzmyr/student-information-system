# Student Information System
This project is developed as part of the System Programming course.
It is a simple command-line based Student Information System that runs using Docker containers.

## Technologies Used
- Ubuntu
- C++
- PostgreSQL
- Docker & Docker Compose
- Git & GitHub

## System Architecture
The system consists of two main Docker containers:
- PostgreSQL database container
- C++ application container

## Features
- Add student information
- List students
- Update student information
- Delete student information

## How to Run
Please see the `INSTALL.md` file for setup instructions.

## Team Roles
- Git & GitHub Management & Documentation: Emre Kubilay  
- Docker & DevOps Engineer: Hilal Bizimyer  
- C++ Developer: Ezgi Erdoğan

Docker (Week 2)

The application is containerized using Docker and orchestrated with Docker Compose. The PostgreSQL database and the C++ application run in separate containers and communicate over a Docker network. Public Docker Hub images are available for both services: hilalb/sis-app:week2 for the C++ application and hilalb/sis-db:week2 for the PostgreSQL database. To run the system locally, create an environment file using .env.example, start the database container, verify the database connection with a simple query, and then build and run the application container.
```bash
cp .env.example .env
docker compose up -d db
docker exec -it sis-db psql -U sis_user -d sis -c "SELECT 1;"
docker compose up --build app
```

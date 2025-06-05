# Podcast Streaming Microservices

## Overview
A scalable podcast streaming platform built with microservices architecture.

## Architecture

<img src="diagram.png" alt="Architecture Diagram" width="500">

- **User Service:** Handles registration and authentication.
- **Podcast Catalog Service:** Manages podcast metadata.
- **Streaming Service:** Delivers audio files.
- **Search Service:** Enables search functionality.
- **Playlist Service:** Manages user playlists.
- **API Gateway:** Routes client requests to services.

## Tech Stack
- C, Go, Rust, Docker, Kubernetes, PostgreSQL, MinIO (object storage)

## Getting Started
1. Clone the repo
2. Build Docker images
3. Start with `docker-compose up` or deploy to Kubernetes

## Database Setup

To initialize the database and tables, run:

psql -U postgres -f setup.sql


## API Endpoints
- `/users/register` - Register new user
- `/podcasts` - List podcasts
- `/stream/{episode}` - Stream audio

# User Service API

## Endpoints

### POST /users
- **Description:** Register a new user
- **Body:** 
{
"username": "alice",
"email": "alice@example.com",
"password": "SuperSecret123"
}

- **Response:** `201 Created` or error

### POST /login
- **Description:** Login and receive JWT
- **Body:**
{
"email": "alice@example.com",
"password": "SuperSecret123"
}

- **Response:**
{
"token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJleHAiOjE3NDkzNTM3MTcsInVzZXJfaWQiOjV9.y66Nn46MSVRQrt6lX9sohYayjwVLVZs1MjBWwYphpkA"
}

### GET /users
- **Description:** List users (JWT required)
- **Headers:** `Authorization: Bearer <token>`
- **Response:** List of users
[
    {
        "id": 1,
        "username": "alice",
        "email": "alice@example.com"
    },
    {
        "id": 2,
        "username": "alice",
        "email": "alice@example.com"
    },
    {
        "id": 3,
        "username": "ben",
        "email": "ben@example.com"
    },
    {
        "id": 4,
        "username": "cathy",
        "email": "cathy@example.com"
    },
    {
        "id": 5,
        "username": "dorthy",
        "email": "dorthy@example.com"
    }

]


# Multi-Stage Dockerized Application

This project contains a **React** frontend and a **Node.js/Express** backend, both containerized using Docker.
The frontend build process uses **Docker multi-stage builds** for optimized image size and better performance.

---

## Project Structure

```
myapp/
├── backend/        # Node.js + Express server code
├── frontend/       # React application
└── docker-compose.yml
```

---

## Prerequisites

Before running this project, ensure you have the following installed:

* **Docker** (20.x or higher recommended)
* **Docker Compose** (1.29+ or 2.x)
* **Git**

---

## How to Run

1. **Clone the repository**

   ```bash
   git clone git@github.com:FaeizHamdard22/multi-stage-dockerize.git
   cd multi-stage-dockerize
   ```

2. **Build and start containers**

   ```bash
   docker-compose up -d --build
   ```

3. **Access the applications**

   * **Frontend**: [http://localhost](http://localhost)
   * **Backend API**: [http://localhost:5000](http://localhost:5000)

---

## How the Multi-Stage Build Works (Frontend)

The frontend `Dockerfile` uses **multi-stage builds**:

1. **Build Stage**

   * Uses `node:18` image.
   * Installs dependencies.
   * Builds the production-ready React application.

2. **Production Stage**

   * Uses a lightweight `nginx:alpine` image.
   * Copies the build output from the first stage.
   * Serves static files via Nginx.

**Advantages**:

* Smaller final image size.
* Separation of build tools from production runtime.
* Faster deployment.

---

## Backend

The backend is a simple **Node.js + Express** server that serves API endpoints.
It runs inside its own container and communicates with the frontend.

---

## Useful Commands

* **Stop containers**:

  ```bash
  docker-compose down
  ```

* **Rebuild without cache**:

  ```bash
  docker-compose build --no-cache
  ```

* **View logs**:

  ```bash
  docker-compose logs -f
  ```

---


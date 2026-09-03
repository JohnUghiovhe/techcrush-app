# TechCrush Node.js Docker Deployment

A simple Node.js application containerized with Docker, published to Docker Hub, and deployed as a container on a Linux server.

## Project Structure

```
techcrush-app/
├── app.js
├── package.json
├── Dockerfile
├── README.md
└── screenshots/
    ├── Screenshot 1.png
    ├── Screenshot 2.png
    ├── Screenshot 3.png
    └── Screenshot 4.png
```

## Getting Started

### 1. Clone the Repository

```bash
git clone https://github.com/JohnUghiovhe/techcrush-app.git
cd techcrush-app
```

### 2. Run Locally

```bash
npm install
npm start
```

The app will be available at `http://localhost:3000`, returning a JSON response with the app's name, version, status, and timestamp.

## Docker Deployment

### Dockerfile

```dockerfile
FROM node:20-alpine

WORKDIR /app

COPY package*.json ./

RUN npm install

COPY . .

EXPOSE 3000

CMD ["npm", "start"]
```

### Build the Image

```bash
docker build -t YOUR_DOCKERHUB_USERNAME/nodejs-app:1.0 .
```

### Push to Docker Hub

```bash
docker login
docker push YOUR_DOCKERHUB_USERNAME/nodejs-app:1.0
```

### Pull and Run

```bash
docker pull YOUR_DOCKERHUB_USERNAME/nodejs-app:1.0
docker run -d -p 3000:3000 YOUR_DOCKERHUB_USERNAME/nodejs-app:1.0
```

Verify the container is running:

```bash
docker ps
```

The app will be live at `http://YOUR_SERVER_IP:3000`.

## Deployment Evidence

### 1. Docker Image Build

![Docker build](screenshots/Screenshot%201.png)

### 2. Image on Docker Hub

![Docker Hub](screenshots/Screenshot%202.png)

### 3. Running Container

![Running container](screenshots/Screenshot%203.png)

### 4. Live Application

![Live application](screenshots/Screenshot%204.png)

# Docker Lab 01 - Containerizing a Node.js API

## Objective

Learn how to containerize a Node.js Express application using Docker.

## Prerequisites

- Docker Desktop
- Node.js
- Express Application

## Dockerfile

```dockerfile
FROM node:20-alpine

WORKDIR /app

COPY package*.json ./

RUN npm install

COPY . .

EXPOSE 3000

CMD ["npm", "run", "dev"]
```

## Build Image

```bash
docker build -t cloudbank-gateway:v1 .
```

## Run Container

```bash
docker run --name cloudbank-gateway-container -p 3000:3000 cloudbank-gateway:v1
```

## Verify

Open:

http://localhost:3000/health

Expected Response

```json
{
  "status": "UP",
  "service": "CloudBank API Gateway",
  "version": "1.0.0"
}
```
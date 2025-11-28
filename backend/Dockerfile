# backend/Dockerfile
FROM node:18-alpine

# Set working directory inside container
WORKDIR /app

# Install dependencies first (better caching)
COPY package*.json ./
RUN npm install --production

# Copy the rest of the backend code
COPY . .

# Set environment variables (override in docker-compose)
ENV PORT=3000

EXPOSE 3000

# Start command (adjust if your backend uses different script)
CMD ["npm", "start"]

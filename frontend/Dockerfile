# frontend/Dockerfile

# ---- Build stage ----
FROM node:18-alpine AS build

WORKDIR /app

COPY package*.json ./
RUN npm install

# Copy all frontend code
COPY . .

# Build Angular app for production
# If your script is different, check package.json
RUN npm run build -- --configuration=production

# ---- Run stage ----
FROM nginx:alpine

# Replace <ANGULAR_DIST_FOLDER> with actual folder name from angular.json
# Example: /app/dist/crud-dd-frontend
COPY --from=build /app/dist/<ANGULAR_DIST_FOLDER> /usr/share/nginx/html

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]

# Stage 1: Build React app
FROM node:18 AS build
WORKDIR /app

# Copy package.json và cài dependencies
COPY package.json package-lock.json* ./
RUN npm install

# Copy toàn bộ source và build
COPY . .
RUN npm run build

# Stage 2: Serve với Nginx
FROM nginx:alpine
COPY --from=build /app/build /usr/share/nginx/html
COPY nginx.conf /etc/nginx/conf.d/default.conf

EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]

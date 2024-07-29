# Stage 1: Build the React app
FROM node:14 AS build

WORKDIR /app

COPY package*.json ./
RUN npm install

COPY . .
RUN npm run build

# Stage 2: Serve the app with Nginx
FROM nginx:latest

COPY --from=build /app/build /usr/share/nginx/html

ARG PORT
EXPOSE ${PORT:-80}

CMD ["nginx", "-g", "daemon off;"]
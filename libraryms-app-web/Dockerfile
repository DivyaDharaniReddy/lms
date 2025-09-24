# Stage 1: Build
FROM node:18

WORKDIR /app

COPY package*.json ./
RUN npm install

COPY . .

# Set legacy OpenSSL for Node 17+ compatibility
ENV NODE_OPTIONS=--openssl-legacy-provider

RUN npm run build

# Stage 2: Serve with Nginx
FROM nginx:alpine
COPY --from=0 /app/build /usr/share/nginx/html

EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]

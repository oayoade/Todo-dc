# Stage 1: Build Vue App
FROM node:14 AS builder
WORKDIR /app

# Install dependencies and build Vue project
COPY package.json package-lock.json ./
RUN npm install --legacy-peer-deps
COPY . .
RUN npm run build

# Stage 2: Serve with Caddy
FROM caddy:2.6.4-alpine

# Copy built Vue files to Caddy's web root
COPY --from=builder /app/dist /usr/share/caddy

# Expose port for Traefik to use
EXPOSE 80

# Use Caddy to serve static files
CMD ["caddy", "file-server", "--root", "/usr/share/caddy"]

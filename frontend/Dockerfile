# Stage 1: Build
FROM node:14-alpine as builder

WORKDIR /app

# Copy package.json and package-lock.json
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy code
COPY . .

# Build
RUN npm run build

# Stage 2: Serve Application
FROM node:14-alpine

WORKDIR /app

# Static file serving module
RUN npm install -g serve

# Copy built artifact
COPY --from=builder /app/dist ./dist

# Start
CMD ["serve", "-s", "dist"]
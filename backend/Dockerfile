# Stage 1: Build
FROM node:20.11.1-alpine AS builder

# Set working directory
WORKDIR /app

# Copy package.json and package-lock.json
COPY package*.json ./

# Install dependencies
RUN npm cache clean --force && npm install --legacy-peer-deps

# Copy the rest of the application code
COPY . .

# Lint the application code
RUN npm run lint

# Run tests
RUN npm run test

# Generate Prisma Client code
RUN npx prisma generate

# Build the application
RUN npm run build

# Stage 2: Production
FROM node:20.11.1-alpine

# Set working directory
WORKDIR /app

# Copy only the necessary files from the build stage
COPY --from=builder /app/package*.json ./
COPY --from=builder /app/node_modules ./node_modules
COPY --from=builder /app/dist ./dist
COPY --from=builder /app/prisma ./prisma

# Expose the port the app runs on
EXPOSE 3000

# Command to run the app
CMD ["npm", "run", "start:migrate:prod"]

# Stage 1: Build
FROM node:alpine as build

# Set the working directory
WORKDIR /app

# Copy package.json file
COPY package.json  ./

# Install dependencies
RUN yarn install

# Copy the rest of the application code
COPY . .

# Build the application
RUN yarn build

# Stage 2: Production
FROM node:alpine

# Set the working directory
WORKDIR /app

# Copy only the necessary files from the build stage
COPY --from=build /app/package.json /app/yarn.lock ./
COPY --from=build /app/.next ./.next
COPY --from=build /app/public ./public

# Install only production dependencies
RUN yarn install --production

# Expose the port the app runs on
EXPOSE 3000

# Start the application
CMD ["yarn", "start"]

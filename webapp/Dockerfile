FROM node:18-alpine AS builder

WORKDIR /app

# Copy package.json and yarn.lock to the container
COPY package.json yarn.lock ./

# Install dependencies
RUN yarn install

# Stage 2: Build the final image with the application code
FROM node:18-alpine

WORKDIR /app

# Copy the installed dependencies from the builder stage
COPY --from=builder /app/node_modules ./node_modules

# Copy the application code to the container
COPY . .

# Expose a port (if your application needs it)
EXPOSE 3000

# Define the command to start your application
CMD ["yarn", "start"]

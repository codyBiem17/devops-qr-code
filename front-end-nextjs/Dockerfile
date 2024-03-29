# Use official Node.js image with alpine linux as base

FROM node:18-alpine as build
# Set working directory
WORKDIR /app

# Copy package.json and package-lock.json
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy the rest of the application
COPY . .

# Build the Next.js application
RUN npm run build

# Stage 2: Serve the application with a smaller, lightweight image
FROM node:alpine

# Set working directory
WORKDIR /app

# Copy the built application from the previous stage
COPY --from=build /app/.next ./.next
COPY --from=build /app/node_modules ./node_modules
COPY --from=build /app/package.json ./package.json
COPY --from=build /app/public ./public

# Install `next` for production
RUN npm install next

# Expose port 3000
EXPOSE 3000

# Run the Next.js application
CMD ["npm", "start"]


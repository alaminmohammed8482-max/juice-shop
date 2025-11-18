# Step 1: Use a lightweight base image
FROM node:18-alpine AS build

# Step 2: Set working directory
WORKDIR /app

# Step 3: Copy only package files first (for faster caching)
COPY package*.json ./

# Step 4: Install only production dependencies
RUN npm install --production

# Step 5: Copy the rest of the source code
COPY . .

# Step 6: Build the app
RUN npm run build

# Step 7: Create a smaller runtime image
FROM node:18-alpine

# Step 8: Set working directory again
WORKDIR /app

# Step 9: Copy built app from the first image
COPY --from=build /app .

# Step 10: Add a non-root user
RUN addgroup -S juice && adduser -S juice -G juice
USER juice

# Step 11: Expose the default Juice Shop port
EXPOSE 3000

# Step 12: Run the app
CMD ["npm", "start"]

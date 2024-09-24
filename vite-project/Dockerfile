# Set the base image to create the image for the React app
FROM node:20-alpine

# Create a non-root user to run the app
RUN addgroup app && adduser -S -G app app

# Set the working directory to /app
WORKDIR /app

# Copy package.json and package-lock.json to the working directory
# This is done before copying the rest of the files to take advantage of Docker’s cache
COPY package*.json ./

# Install dependencies as root
RUN npm install

# Copy the rest of the application files to the working directory
COPY . .

# Change ownership of the files in the working directory to the app user
RUN chown -R app:app .

# Switch to the non-root user to run the app
USER app

# Expose port 5173
EXPOSE 5173

# Command to run the app
CMD ["npm", "run", "dev"]

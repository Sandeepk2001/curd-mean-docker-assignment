# Use Node.js image
FROM node:18-alpine

# Set the working directory
WORKDIR /app

# Copy package files and install dependencies
COPY package*.json ./
RUN npm install

# Install Angular CLI globally
RUN npm install -g @angular/cli

# Copy the rest of the application code
COPY . .

# Expose port 4200
EXPOSE 4200

# Start the application
CMD ["ng", "serve", "--host", "0.0.0.0"]
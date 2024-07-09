# Use the official Node.js image as the base image
FROM node:latest

# Set the working directory inside the container
WORKDIR /app

# Copy the rest of the application code to the working directory
COPY . .

# Install dependencies
RUN npm install

# Expose the port the development server runs on
EXPOSE 5173

# Run the development server
CMD ["npm", "run", "dev", "--", "--host"]

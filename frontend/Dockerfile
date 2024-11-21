FROM node:18-alpine3.18

# Set working directory
WORKDIR /app

# Copy package files first to leverage Docker cache
COPY package*.json /app/

# Install dependencies
RUN npm install

# Copy the rest of the application code
# Note the use of .dockerignore to exclude unnecessary files
COPY . /app/

# Expose the development port (typically 5173 for Vite, adjust as needed)
EXPOSE 5173

# Run development server
CMD ["npm", "run", "dev", "--", "--host", "0.0.0.0"] 
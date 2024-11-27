FROM node:alpine

# Set working directory
WORKDIR /app

# Copy package files first to leverage Docker cache
#COPY package*.json ./

# Copy the rest of the application code
# Note the use of .dockerignore to exclude unnecessary files
COPY . . 

# Install dependencies
RUN npm install

# Expose the development port (typically 5173 for Vite, adjust as needed)
EXPOSE 5173

# Run development server
CMD ["npm", "run", "dev", "--", "--host"]
# Use the official Node.js LTS Alpine base image
FROM node:22-alpine AS build

# Set the working directory
WORKDIR /home/node/app-frontend

# Ensure the directory is owned by the non-root 'node' user
RUN chown -R node:node /home/node/app-frontend

# Copy package.json and package-lock.json with correct ownership for dependency installation
COPY --chown=node:node package.json ./

# Switch to the non-root 'node' user
USER node

# Install dependencies and set to use the legacy provider
RUN npm install

# Copy the rest of the application code with correct ownership
COPY --chown=node:node . .

# Build the application
RUN npm run build

# Use the official Nginx image
FROM nginx:alpine

# Remove all files from the default Nginx HTML directory
RUN rm -rf /usr/share/nginx/html/*

# Copy the build output from the Node.js build stage to the Nginx HTML directory
COPY --from=build /home/node/app-frontend/dist/angular-frontend/ /usr/share/nginx/html/

# Copy the custom Nginx configuration file to the appropriate location and removing old default.conf
RUN rm -rf /etc/nginx/conf.d/*
COPY nginx/conf.d/default.conf /etc/nginx/conf.d/default.conf

# Expose the port your application will run on
EXPOSE 80

# Start Nginx server
CMD ["nginx", "-g", "daemon off;"]
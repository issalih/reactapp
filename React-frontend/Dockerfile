# Use the official Node.js image to build the app
FROM node:14 AS build
WORKDIR /app

# Copy the package.json and install dependencies
COPY package.json .
RUN npm install

# Copy the rest of the application code and build the application
COPY . .
RUN npm run build

# Use the official Nginx image to serve the app
FROM nginx:alpine
COPY --from=build /app/build /usr/share/nginx/html

# Expose the port on which the application will run
EXPOSE 80

# Command to run Nginx
CMD ["nginx", "-g", "daemon off;"]
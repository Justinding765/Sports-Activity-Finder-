FROM node:lts-alpine

# Set the working directory in the container
WORKDIR /usr/src/app

# Set node environment to production to only install production dependencies
ENV NODE_ENV=production

# Apply Node.js options, necessary for certain Node versions with OpenSSL 3
ENV NODE_OPTIONS=--openssl-legacy-provider

# Copy the package.json and associated files into the working directory
COPY package.json package-lock.json* npm-shrinkwrap.json* ./

# Install dependencies, including 'legacy-peer-deps' for compatibility
RUN npm install --legacy-peer-deps --production --silent

# Copy the rest of the application code into the container
COPY . .

# Change ownership to non-root user 'node' for security purposes
RUN chown -R node /usr/src/app

# Set the user to use when running this image
USER node

# Inform Docker that the container listens on port 3000 at runtime
EXPOSE 3000

# Define the command to run the app
CMD ["npm", "start"]

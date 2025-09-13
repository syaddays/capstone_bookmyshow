# ----------------------------
# Base Image
# ----------------------------
FROM node:18 AS base

# Set working directory
WORKDIR /app

# ----------------------------
# Install Dependencies
# ----------------------------
# Copy package files first (to leverage Docker cache)
COPY package.json package-lock.json ./

# Install specific PostCSS version to avoid build issues
RUN npm install postcss@8.4.21 postcss-safe-parser@6.0.0 --legacy-peer-deps

# Install all project dependencies
RUN npm install

# ----------------------------
# Copy Application Source
# ----------------------------
COPY . .

# ----------------------------
# Environment Configuration
# ----------------------------
ENV NODE_OPTIONS=--openssl-legacy-provider
ENV PORT=3000

# ----------------------------
# Expose Ports
# ----------------------------
EXPOSE 3000

# ----------------------------
# Start Application
# ----------------------------
CMD ["npm", "start"]

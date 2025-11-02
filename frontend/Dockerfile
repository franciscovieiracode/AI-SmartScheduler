FROM node:20-slim

WORKDIR /app

# Copy dependencies and install
COPY package*.json ./
RUN npm install

# Copy source code
COPY . .

EXPOSE 3000

# Run React dev server
CMD ["npm", "run", "dev"]

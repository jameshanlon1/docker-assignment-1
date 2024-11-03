# Agile Software Practice - Assignment 1

A Docker Compose configuration to run a Movies API with MongoDB, Redis, and optional development tools, providing a containerized, isolated environment for easy setup and testing.

---

## Approach and Setup

### 1. Service Identification  
I reviewed the assignment requirements to identify the necessary services:  
   - **Movies API**: Accessible on port `9000` for managing and retrieving movie data.
   - **MongoDB**: Acts as the main database for storing movie information.
   - **Redis**: Provides caching to improve data retrieval speed.
   - **Mongo Express**: A web-based GUI for MongoDB, available on port `8080`.

### 2. Configuration of Services  
Using previous lab examples, I set up the `docker-compose.yml` file to define the core services:
   - **API Service**: Configured to interact with MongoDB for data storage and Redis for caching.
   - **MongoDB**: Serves as the main database, with environment variables set for secure, isolated access.
   - **Redis**: Lightweight, in-memory caching layer used by the API for optimized access.
   - **Mongo Express**: A simple GUI tool for MongoDB, allowing easy data inspection.

### 3. Environment Variables Setup  
Following the assignment specifications, I configured environment variables to support each service:
   - **Movies API**: Included `MONGODB_URI` and `REDIS_URI` variables to link to MongoDB and Redis.
   - **MongoDB and Mongo Express**: Set up credentials and connection strings to ensure secure access and container isolation.

### 4. Network Segmentation  
To maintain container isolation and secure communication, I created three separate networks:
   - **API Network**: Connects the Movies API and Redis for caching purposes.
   - **MongoDB Network**: Links MongoDB, the Movies API, and Mongo Express.
   - **Redis Network**: Allows the API to connect to Redis directly.

   Each service was assigned to the necessary networks to ensure they are accessible only to the containers that need them.

### 5. Data Seeding  
For initial data population, I set up a volume to mount a `seeding.json` file, enabling MongoDB to automatically load a predefined JSON array of movie data. This makes testing and development easier by providing a ready-made dataset.

### 6. Setting the Development and Production Stack Options

Setting up the development and production stack options was easier than I expected. I learned that if you add a profile to a service, then that service's profile name must be specified when running it. If you simply run `docker-compose up`, only the services without a defined profile will start (Production stack).


---


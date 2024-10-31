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





## Agile Software Practice - Assignment 1.

### A Docker Compose configuration to run a Movies API with MongoDB, Redis, and optional development tools.

### First I looked at the liist of services that are involoved in the assignment.

### -I downloaed and opned the movies-api from the link provided. I set up the yaml file with help for the weeks pervious labs. I created the 4 services for the API to work properly. The movies api that is accessed on port 9000, mongoDB database for storing movie data, redis for optimized data access, and mongo-express for web based GUI on port 8000.

### I used the information given to us in the assignment sheet to set the enviornment variables rewuired by the moies-api. I also set the enviornment variables for MongoDB and Mongo Express so that containter isolation could be satisfied. I did this by creating 3 differnt networks and assigning them to the correct service so they would still be accessible from container to container.

### For the seeding i set the volume to use the seeding.json file and add a seed.json file which is what i used to isert the array into. 

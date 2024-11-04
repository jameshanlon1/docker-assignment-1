## Docker Assignment - Agile Software Practice.

__Name:__ James Hanlon

__Demo:__ https://youtu.be/J77fnGTLtWA

This repository contains the containerization of the mukti-container application illustrated below.

![](./images/arch.png)

### Database Seeding.

For initial data population, I set up a volume to mount a `seeding.json` file, enabling MongoDB to automatically load a predefined JSON array of movie data. This makes testing and development easier by providing a ready-made dataset.

### M.ulti-Stack.

Setting up the development and production stack options was easier than I expected. I learned that if you add a profile to a service, then that service's profile name must be specified when running it. If you simply run `docker-compose up`, only the services without a defined profile will start (Production stack).

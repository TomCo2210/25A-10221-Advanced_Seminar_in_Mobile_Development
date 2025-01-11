# MongoDB Cluster Setup

In this guide, we will go through the steps of setting up a MongoDB cluster in the cloud using MongoDB Atlas.

## Step 1: Login to MongoDB Atlas

1. Go to the [MongoDB Atlas](https://www.mongodb.com/cloud/atlas) website.
2. Sign in or create an account.

## Step 2: Configure the Cluster

1. Click on `Build a Cluster`.
2. Set up the cluster name.
3. Choose the cluster tier and cloud provider settings.
4. Configure the additional settings like backup, monitoring, and alerts.
5. Click on `Create Cluster`.

## Step 3: Whitelist Your IP Address

1. Go to the `Network Access` tab.
2. Click on `Add IP Address`.
3. Add your current IP address to the whitelist.
4. Click on `Confirm`.

## Step 4: Create a Database User

1. Go to the `Database Access` tab.
2. Click on `Add New Database User`.
3. Set up the user credentials.
4. Click on `Add User`.

## Step 5: Connect to the Cluster

1. Go to the `Clusters` tab.
2. Click on `Connect`.
3. Choose a connection method (e.g., MongoDB Compass, Shell, Code, or Application).
4. Follow the instructions to connect to the cluster.

## Step 6: Test the Connection

1. Use the connection string provided to connect to the cluster.
2. Verify that you can connect to the cluster using MongoDB Compass or the MongoDB shell.

## Step 7: Start Using Your MongoDB Cluster

1. Start using your MongoDB cluster for storing and querying data by connecting to it from your application, API, or service, using the connection string provided, and the database user credentials.
2. Write code to interact with the MongoDB cluster using the MongoDB driver for your programming language.
3. Test your application to ensure it can read and write data to the MongoDB cluster.

## References

- [MongoDB Atlas](https://www.mongodb.com/cloud/atlas)
- [MongoDB Atlas Quick Start](https://docs.atlas.mongodb.com/getting-started/)
- [MongoDB Atlas Pricing](https://www.mongodb.com/cloud/atlas/pricing)
- [MongoDB Drivers](https://www.mongodb.com/docs/drivers/)
  - [Python](https://docs.mongodb.com/drivers/pymongo/)
  - [Java](https://docs.mongodb.com/drivers/java/)
- [MongoDB Compass](https://www.mongodb.com/products/compass)

---
[➡️ Next: Flask API Building](flask-api-building.md)

[➡️ Next: Spring Boot API Building](spring-boot-api-building.md)

[🏠 Back to 25A-10221 Advanced Seminar in Mobile Development](../README.md)

© 2025 Afeka - Tel Aviv's College of Engineering

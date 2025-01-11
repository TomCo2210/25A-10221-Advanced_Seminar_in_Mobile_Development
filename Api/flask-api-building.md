# Building a RESTful API with Flask and Python

## Introduction

This guide will walk you through the process of building a RESTful API with Flask and Python.

## Step 1: Install Flask

- Install Python from the official website: [Python Downloads](https://www.python.org/downloads/).
- Verify that Python is installed correctly by running the following command in the terminal:

    ```bash
    python --version
    ```

- Create a `requirements.txt` file with the following content:

    ```txt
    Flask # The main Flask library
    Flasgger # If you want to add Swagger documentation
    python-dotenv # If you are using environment variables
    pymongo # If you are using MongoDB
    ```

- Install required libraries using pip:

    ```bash
    pip install -r requirements.txt
    ```

## Step 2: Create a Flask Application

- Create a new Python file, e.g., `app.py`.
- Import Flask and create an instance of the Flask class:

    ```python
    from flask import Flask

    app = Flask(__name__)
    ```

## Step 3: Define Routes

- Create a Controller class to define routes for your API.
- You can define routes using the `@app.route` decorator:

    ```python
    @app.route('/')
    def home():
        return 'Hello, World!'
    ```

- You can also define routes with specific HTTP methods:

    ```python
    @app.route('/api/data', methods=['GET'])
    def get_data():
        return {'data': 'This is some data!'}
    ```

- You can also use the `Blueprint` class to organize your routes into separate modules.

    ```python
    from flask import Blueprint

    controller = Blueprint('controller', __name__)

    @controller.route('/')
    def home():
        return 'Hello, World!'

    @controller.route('/api/data', methods=['GET'])
    def get_data():
        return {'data': 'This is some data!'}
    ```

- Register the Blueprint with the Flask application:

    ```python
    app.register_blueprint(controller)
    ```

## Step 4: Manage Environment Variables 

- To use environment variables, create a `.env` file in the root directory of your project:

    ```env
    PORT=5000
    DB_URI=mongodb://localhost:27017/mydatabase
    ... # Add other environment variables as needed
    ```

- Load environment variables from the `.env` file using the `python-dotenv` library:

    ```python
    from dotenv import load_dotenv

    load_dotenv()
    ```

- Access environment variables in your Flask application:

    ```python
    import os

    port = os.getenv('PORT')
    db_uri = os.getenv('DB_URI')
    ```

## Step 5: Create a MongoDB Connection (Optional, can be replaced with any other database)

- Make sure you have MongoDB installed on your machine.
- Install the `pymongo` library using pip:

    ```bash
    pip install pymongo
    ```

- Create a MongoDB connection in your Flask application:

    ```python
    from pymongo import MongoClient

    client = MongoClient(db_uri)
    db = client.mydatabase
    ```

- Use the `db` object to interact with your MongoDB database.
- You can define functions to perform CRUD operations on your database.

## Step 6: Use Swagger for API Documentation (Optional)

- If you want to add Swagger documentation to your API, you can use the `Flasgger` library.
- Add the following code to your Flask application:

    ```python
    from flasgger import Swagger

    app = Flask(__name__)
    Swagger(app)
    ```

- You can now access the Swagger UI at `http://localhost:5000/apidocs` to view the API documentation.
- Add docstrings to your route functions to provide additional information for Swagger:

    ```python
    @app.route('/api/data', methods=['GET'])
    def get_data():
        """
        This endpoint returns some data.
        ---
        responses:
          200:
            description: A JSON object with some data.
        """
        return {'data': 'This is some data!'}
    ```

  - note: The docstrings must be in a specific format to be parsed correctly by Swagger.
  - note: You can add more detailed documentation using the Swagger specification.

## Step 7: Run the Flask Application

- Run the Flask application using the `app.run()` method:

    ```python
    if __name__ == '__main__':
        port = int(os.environ.get('PORT', 5000))
        app.run(host="0.0.0.0", port=port)
    ```

## Step 8: Test the API

- Open a web browser and navigate to `http://localhost:5000/` to test your API.
- You should see the message `Hello, World!` displayed in the browser.

## Step 9: Add More Routes

- Define additional routes for your API by creating new route functions:

    ```python
    @app.route('/api/data')
    def get_data():
        return {'data': 'This is some data!'}
    ```

## Step 10: Test the New Routes

- Open a web browser and navigate to `http://localhost:5000/api/data` to test the new route.
- You should see the JSON response `{'data': 'This is some data!'}` displayed in the browser.

## Step 11: Document Your API

- Add docstrings to your route functions to provide information about the API endpoints.
- Use the Swagger UI to view the API documentation and test the endpoints.
- Update the documentation as needed to reflect changes in the API.

## Step 12: [Deploy Your Flask API](vercel-deployment.md)

---
[⬅️ Back to MongoDB Cluster Setup](mongodb-cluster-setup.md)

[➡️ Next: Vercel Deployment - For Flask Services](vercel-deployment.md)

[🏠 Back to 25A-10221 Advanced Seminar in Mobile Development](../README.md)

© 2025 Afeka - Tel Aviv's College of Engineering

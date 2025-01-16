# Vercel Deployment - For Flask Services

## Introduction

This guide will walk you through the process of deploying a Flask API to Vercel.

## Step 1-10: [Prepare Your Flask API](flask-api-building.md)

- Ensure your Flask API is working correctly on your local machine.
- Make sure your Flask API is using environment variables for configuration.
- Create a `requirements.txt` file with the needed libraries.

## Step 11: Create a Vercel Account

- Sign up for a Vercel account at [Vercel](https://vercel.com/).

## Step 12: Set Vercel Specific Configuration Files in Your Flask API

- Create a `runtime.txt` file with the following content:

    ```txt
    python-3.9
    ```

- Create a `vercel.json` file with the following content to specify the Vercel runtime:

    ```json
    {
        "version": 2,
        "builds": [
        {
            "src": "app.py",
            "use": "@vercel/python"
        }
        ],
        "routes": [
        {
            "src": "/(.*)",
            "dest": "app.py"
        }
        ]
    }
    ```

  - Make sure to replace `app.py` with the name of your Flask application file.

## Step 13: Deploy Your Flask API to Vercel

- Push your Flask API to a GitHub repository.
- Import your GitHub repository to Vercel.
- Configure the deployment settings:
  - Set the install command to `pip install -r requirements.txt`.
  - Set the output directory to `.`.
  - Set the environment variables if needed.
- Deploy your Flask API to Vercel.
- Test your Flask API on Vercel.
- Get the deployment URL and use it to access your Flask API.

## Step 14: Monitor and Maintain Your Flask API on Vercel

- Monitor the deployment status and logs.
- Update your Flask API as needed.
- Troubleshoot any issues that may arise.

---

[⬅️ Back to Flask API Building](flask-api-building.md)

[➡️ Next: Postman API Testing](postman-api-testing.md)

[🏠 Back to 25A-10221 Advanced Seminar in Mobile Development](../README.md)

© 2025 Afeka - Tel Aviv's College of Engineering

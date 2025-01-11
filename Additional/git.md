# Git

## Introduction

Git is a distributed version control system that allows you to track changes in your codebase, collaborate with others, and manage your project's history.

## Getting Started

To get started with Git, follow these steps:

1. Install Git on your machine by downloading it from the [official Git website](https://git-scm.com/).
2. Open a terminal or command prompt and run the following command to configure your Git username and email:

   ```bash
   git config --global user.name "Your Name"
   git config --global user.email "Your Email Address"
   ```

3. Create a new Git repository by running the following commands in your project directory:

   ```bash
    git init
    ```

4. Add your files to the staging area by running the following command:

   ```bash
   git add .
   ```

5. Commit your changes to the repository by running the following command:

   ```bash
    git commit -m "Initial commit"
    ```

6. Create a new remote repository on GitHub by following these steps:

    - Go to [GitHub](http://github.com/) and log in to your account.
    - Click on the "+" icon in the top right corner and select "New repository."
    - Enter a name for your repository, add a description, and choose whether it should be public or private.
    - Click on "Create repository."

7. Link your local repository to the remote repository by running the following command:

   ```bash
   git remote add origin <repository-url>
   ```

8. Push your changes to the remote repository by running the following command:

   ```bash
    git push -u origin master
    ```

9. You can now collaborate with others by sharing the repository URL.

## References

1. [Git Documentation](https://git-scm.com/doc)
2. [GitHub Guides](https://guides.github.com/)
3. [Atlassian Git Tutorials](https://www.atlassian.com/git/tutorials)

---

[🏠 Back to 25A-10221 Advanced Seminar in Mobile Development](../README.md)

© 2025 Afeka - Tel Aviv's College of Engineering

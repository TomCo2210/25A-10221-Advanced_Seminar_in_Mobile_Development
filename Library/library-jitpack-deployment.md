# Android Library Jitpack Deployment

## Steps 1-6: [Create a New Project](library-creation.md)

- Create a New Project
- Define the Library
- Implement the Library
- Test the Library
- Document the Library
- Organize Your Files

## Step 7: Prepare for Distribution

- Publish the library to a public or private repository on GitHub.
- Ensure your library module has a `build.gradle` file with proper dependencies and configurations.
- Include configurations for publishing the library to a Maven repository (e.g., JitPack).
  - Include Maven Publication plugin by adding to the `libs.versions.toml` file:

    ```toml
    [plugins]
    maven-publish = { id = "maven-publish" }
    ```

- If your library depends on another library (e.g., Retrofit), you need to explicitly declare how that dependency should be handled by the projects that use your library:
  - `api` scope: Exposes the dependency to the consumers of your library. The consumer project can directly use classes from this dependency.
  - `implementation` scope: Includes the dependency for internal use in your library but does not expose it to the consumer.

- Update the `build.gradle` file (library module)  
  - Ensure you apply the maven-publish plugin:

    ```kotlin
    plugins {
        alias(libs.plugins.android.library)
        alias(libs.plugins.maven.publish) // Apply the maven-publish plugin
    }

    ```

  - Add the Maven publication configuration for the library:

    ```kotlin
    afterEvaluate {
        publishing {
            publications {
                create<MavenPublication>("release") {
                    groupId = 'com.github.your-username' // Change as needed
                    artifactId = 'your-library-name' // Change as needed
                    version = '1.0.0' // Change as needed
                    artifact(tasks.getByName("bundleReleaseAar"))

                    // Add dependencies to the Maven publication configuration (api or implementation) 
                }
            }
        }
    }
    ```

  - If Needed - Add the following configurations to explicitly declare how that dependency should be handled by the projects that use your library:

    ```kotlin
    pom {
        withXml {
            val dependenciesNode = asNode().appendNode("dependencies")
            configurations.api.get().dependencies.forEach { dependency ->
                val dependencyNode = dependenciesNode.appendNode("dependency")
                dependencyNode.appendNode("groupId", dependency.group)
                dependencyNode.appendNode("artifactId", dependency.name)
                dependencyNode.appendNode("version", dependency.version)
                dependencyNode.appendNode("scope", "compile")
            }
            configurations.implementation.get().dependencies.forEach { dependency ->
                val dependencyNode = dependenciesNode.appendNode("dependency")
                dependencyNode.appendNode("groupId", dependency.group)
                dependencyNode.appendNode("artifactId", dependency.name)
                dependencyNode.appendNode("version", dependency.version)
                dependencyNode.appendNode("scope", "runtime")
            }
        }
    }
    ```

  - Make sure to define the library’s version and artifact details: Replace `groupId`, `artifactId`, and `version` with meaningful identifiers.

  - Configure JitPack settings by adding `jitpack.yml` (make sure it is .yml not .yaml) file at the root of your repository:

    ```yaml
    jdk:
      - openjdk17
    ```

    - This file specifies the JDK version to use for building your library.
    - JitPack supports various JDK versions, including OpenJDK 8, 11, 14, 17, and more.
    - Android projects using Android Gradle plugin 8.0 and above can use Minimum version 17 of OpenJDK.

## Step 8: Push Your Project to GitHub

- Create a GitHub repository:

  - Go to [GitHub](https://github.com/), create a new repository, and give it a meaningful name.
  - Initialize it with a .gitignore file for Java/Kotlin/Android if necessary.
- Push your project to the repository:

    ```bash
    git init
    git add .
    git commit -m "Initial commit"
    git branch -M main
    git remote add origin https://github.com/your-username/your-repo-name.git
    git push -u origin main
    ```

## Step 9: Tag Your Release on GitHub

- Create a Git tag:

  - A Git tag is required for JitPack to identify the version to publish.

    ```bash
    git tag 1.0.0
    git push origin 1.0.0
    ```

- Verify the tag on GitHub:
  - Go to your repository → `Tags` section to ensure the tag is visible.

## Step 10: Publish with JitPack

- Visit [JitPack](https://jitpack.io/)'s website.
- Paste your repository URL in the search bar and click on `Look up`.
- Select the version you want to publish.
- Click on `Get it` to copy the dependency information.
- If the build is successful, you'll see the dependency details for adding the library to other projects.

## Step 11: Add Usage Instructions to the `README.md`

- Include JitPack dependency details:
  - Add a `How to Use` section with instructions for adding the library as a dependency:

    ```markdown
    ## How to Use

    Add JitPack to your project-level `build.gradle` or `settings.gradle`:
        ```kotlin
        repositories {
            maven { url = uri("https://jitpack.io" )}
        }
        ```
    ```

- Add the library dependency to your app-level build.gradle:

    ```kotlin
    dependencies {
        implementation ("com.github.your-username:your-library-name:1.0.0")
    }
    ```

    convert dependency to kotlin syntax using ```gradle/libs.versions.toml``` file.

## Step 12: Test the Published Library

- Create a new sample project:

  - Create a fresh project and add your library dependency.
  - Test the library to ensure it works as expected.
- Iterate and improve:

  - Fix any issues and create new Git tags for updates.
  - Push the changes to GitHub and JitPack for new releases.
  
## Step 13: Maintain and Update

- For new releases:

  - Make changes in your library code.
  - Increment the `version` in `build.gradle`.
  - Create a new Git tag and push it to GitHub.
- Announce changes:
  - Update your `README.md` with release notes and usage examples.

## Step 14: Troubleshooting

- If you encounter issues during the build process, check the JitPack logs for error messages.
- Common issues include:
  - Incorrect configurations in the `build.gradle` file.
  - Missing dependencies or incorrect versions.
  - Incompatible JDK versions.
- Refer to JitPack's documentation and community forums for help.

## References

- [JitPack Documentation](https://jitpack.io/docs/)
- [JitPack FAQ](https://jitpack.io/docs/FAQ/)

---
[⬅️ Back to Library Creation](library-creation.md)

[➡️ Next: Semantic Versioning](semantic-versioning.md)

[🏠 Back to 25A-10221 Advanced Seminar in Mobile Development](../README.md)

© 2025 Afeka - Tel Aviv's College of Engineering

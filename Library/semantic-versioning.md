# Sematic Versioning

## Definitions

Version is composed of three components:

MAJOR.MINOR.PATCH

There are simple rules that indicate when we must increment each of these versions:

MAJOR is incremented when we make breaking API changes.
MINOR is incremented when we add new functionality without breaking the existing API or functionality.
PATCH is incremented when we make backwards-compatible bug fixes.

## Guidelines

1. New projects start at version 0.1.0
    - We are starting with a set of features, not bug fixes
    - Increment the minor version for each subsequent feature release
2. Start versioning at 1.1.0 if:
    - Our software is already used in production
    - We are worrying about backwards compatibility
3. The initial development phase is represented by MAJOR version 0
    - We can make as many breaking changes as we want before v1.0.0
4. Once We have released v1.1.0, API adjustments or other breaking changes are not acceptable without a new MAJOR version change.
5. If we are adding new features without breaking the existing API or functionality, increment the MINOR number.
6. If we are fixing bugs, increment the PATCH number.
7. Avoid making frequent breaking changes unless you absolutely need to!
    - Batch major changes together on a branch until you have enough to justify a new major release.

## References

- [GeeksForGeeks - Introduction to Semantic Versioning](https://www.geeksforgeeks.org/introduction-semantic-versioning/)
- [Semantic Versioning 2.0.0](https://semver.org/)

---
[⬅️ Back to Library Jitpack Deployment](library-jitpack-deployment.md)

[🏠 Back to 25A-10221 Advanced Seminar in Mobile Development](../README.md)

© 2025 Afeka - Tel Aviv's College of Engineering

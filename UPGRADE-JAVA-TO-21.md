Upgrade to Java 21 (LTS)

This project has been updated to target Java 21 in the `pom.xml` (uses maven-compiler-plugin with `<release>21`).

Steps to complete the runtime upgrade on your machine:

1. Install JDK 21
   - Download a JDK 21 distribution (Eclipse Temurin / Adoptium, Azul Zulu, Oracle, etc.).
   - On Windows, install and note the installation path (e.g. `C:\Program Files\Eclipse Adoptium\jdk-21`).

2. Set JAVA_HOME and update PATH (PowerShell example):

   $Env:JAVA_HOME = 'C:\Program Files\Eclipse Adoptium\jdk-21'
   $Env:Path = $Env:JAVA_HOME + '\\bin;' + $Env:Path

   To persist across sessions, set system environment variables via Windows Settings or `setx`.

3. Verify Java and Maven:

   mvn -v

   Ensure the Java version shown is `21` and Maven runs.

4. Build the project:

   mvn -DskipTests package

   If tests are desired, remove `-DskipTests`.

Notes and caveats:
- If you rely on any third-party libraries that are incompatible with Java 21, you'll need to update them.
- If you use a CI/CD pipeline, update its JDK to 21 as well.
- If you need a reproducible JDK install step, I can attempt to install a JDK automatically (requires permission and may use tooling that needs additional plan access).

If you want, I can run `mvn -v` and a quick `mvn -DskipTests package` here to validate the change; tell me to proceed and I'll run them in the workspace environment.
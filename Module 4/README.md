
# Module 4: Build Tools & Package Manager

When an application has been created and is ready to be deployed to a server, it needs to be built into a single moveable file (artifact) - this is also called "building or packaging the code". You use a build tool/package manager to do this task. An artifact includes the code and its dependencies. 

### So what does building the code mean?
1. Compiling the code
2. Compressing the code
3. Package hundreds of files into 1 single manageable file

### What is the purpose of an Artifact Repository?
1. Storage of artifacts
2. Allows deployment of artifacts multiple times, keeping versions and backups
3. Examples: Nexus, Azure Artifacts

### Example artifact types:
1. JAR = Java Archive
2. JavaScript artifact (can be zip or tar)
3. .NET is often packaged into .dll or .exe

Build tools used in this module: Gradle & Maven (Jave) / npm (JavaScript)

### What I've installed/setup to support this module:
1. Installed IntelliJ (Code Editor)
2. Install Java, Maven, Node and npm
3. Cloned git projects and opened in InetlliJ:
3.1. Setup Java-Maven project
3.2. Setup Java-Gradle project
3.3. Setup Node.js-npm project

### Build Tools for software development 
- Developers need to build apps locally for testing
- Build tools have dependencies file
- For Gradle, it is the build.gradle file (groovy syntax)
- For maven, it is pom.xml (xml syntax)
- To test a Java application, you can port the .jar file around (between machine and server(s) where java is installed, and execute: java -jar <name of jar file>

### JavaScript build is different
- No special artifact type defined, just .zip or .tar file.
- In JS you use package managers, not build tools
- JavaScript package managers: npm and yarn
- Package.json for dependencies
- Package manager installs dependencies but not used for transpiling code
- WORTH NOTING: .zip and .tar file contain application code but NOT dependencies
- JavaScript more flexible/less standardized than Java - can used different languages for frontend/backend, or the same, e.g. React.js (frontend), Node.js (backend)
- npm repository stores JavaScript modules
- npm pack commands creates the tar/zip file with app code (not dependencies)
- 

### Pattern in all these tools:
- Dependency file
- Repository for dependencies
- Command line tool to test/start/build/publish app
- Package managers (gradle, maven, npm, pip, nuget)

### Docker is a paradigm shift in how we manage artifacts!
- Just one artifact type: Docker image
- No need for repository for each file type, just one Docker image
- No need to install dependencies on server! Execute install command inside Docker image
- Simplifies things! But still need to build your app

## Demo - Install Maven and Gradle projects
- Installed IntelliJ on Windows
- Installed Git
- Cloned java maven app -- https://gitlab.com/twn-devops-bootcamp/latest/04-build-tools/java-maven-app
- Installed Java SDK 25 (pre-req for Maven)
- Ran Maven application
- Changed Terminal settings to run cmd.exe (not PowerShell)
- Added Java bin folder to PATH
- Added JAVA_HOME variable to env vars
- Downloaded Maven
- Added Maven bin folder to PATH
- Downloaded Gradle
- Added Gradle bin to PATH
- Configured IntelliJ to Local Installation distribution and point to Gradle folder
- Cloned java gradle app -- https://gitlab.com/twn-devops-bootcamp/latest/04-build-tools/java-app
- Built the Gradle app using gradle build
- Cloned react nodejs example project -- https://github.com/techworld-with-nana/react-nodejs-example
- Manually install dependencies using npm -- download node, run npm install from api directory


  

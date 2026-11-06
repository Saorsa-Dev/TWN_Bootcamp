# TWN_Bootcamp
This repo has been created to store code/notes related to the TechWorld With Nana Devops Bootcamp mdoule demo projects. I have chosen to create one repo to store all the code files

# Module 5

Module 5 is about Cloud & Infrastructure as a Service, using DigitalOcean cloud services and droplets (VMs).

The technologies used for this module are: DigitalOcean, Linux, Java & Gradle.

Breakdown of exercise completed for this module:
- Setup & configured an Ubuntu droplet in DigitalOcean
- Configured ssh access and firewall rules to allow connectivity
- Created a Linux user on the droplet instead of running as root (security best practice)
- Built a Java Gradle application, deployed to & run on droplet

Summary:
It was interesting to use DigitalOcean as I am an Azure cloud engineer and have never used another cloud offering, so it was really good to compare the different services and the different ways they approach things. I set up/used SSH for the first time which was interesting good to see Nana demo for us as it has felt daunting to me before, especially as I am not used to working at the command line but have always been more GUI based. Building the java application and copying to the remote server via scp and running the application on DO was also awesome to see. 


# Module 6

Module 6 is about Artifact Repository Managers with a focus on Nexus.

An Artifact Repository provides a central location for build artifacts. Applications are delivered as a single file in different artifact formats and stored in an artifact repository that supports different artifact types. There are public and private repository managers. Nexus is a private central store, with open source and commercial versions. Can have multiple repositories divided into formats or teams. Thinking to my own company, I think Nexus would be a good fit for our Exposure Analyst team to store their numerous Python libraries which they want to use with the Databricks platform. Nexus has great features for storing/caching packages and advanced security scanning tools to ensure all libraries are safe to use.

Breakdown of exercise completed for this module:
- Created a sizeable Ubuntu droplet with enough resources to support Nexus
- Configured firewall rules for port 8081 to access Nexus from browser
- Installed Java
- Downloaded/installed Nexus
- Created Nexus user/group
- Run application on droplet and connected from local machine
- Published Java Maven and Gradle applications to Nexus

  Gradle app syntax for referencing Nexus:

  apply plugin: 'maven-publish'

publishing {
    publications {
        create("maven", MavenPublication) {
            artifact("build/libs/my-app-$version" + ".jar") {
                extension 'jar'
            }
        }
    }

    repositories {
        maven {
            name 'nexus'
            url "http://159.65.53.122:8081/repository/maven-snapshots/"
            allowInsecureProtocol = true
            credentials {
                username project.repoUser
                password project.repoPassword
            }
        }
    }
}

Maven app syntax for referencing Nexus:

            <plugin>
                <groupId>org.apache.maven.plugins</groupId>
                <artifactId>maven-compiler-plugin</artifactId>
                <version>3.15.0</version>
                <configuration>
                    <source>25</source>
                    <target>25</target>
                </configuration>
            </plugin>
        </plugins>
    </build>

    <distributionManagement>
        <snapshotRepository>
            <id>nexus-snapshots</id>
            <url>http://159.65.53.122:8081/repository/maven-snapshots/</url>
        </snapshotRepository>
    </distributionManagement>

# Module 7 

Module 7 is about Docker and containerization. 

Docker is an open source containerization platform that allows developers to package applications with all their necessary dependencies into containers as "golden images" avoiding manual installs and utilizing layer/caching concepts to improve performance. Container artifacts are stored in container repos, e.g. dockerhub. Docker image is the artifact, docker container is the running environment - "images become containers at runtime". Containers are more efficient than VMs - faster, smaller. Both are virtualization technologies. Docker Compose is a tool for defining and running multiple docker containers, using yaml. There are a number of docker best practices to follow to allow for better security and performance.

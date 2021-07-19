# Testing Method for Technological Arts Preservation

## Supervisor
- Cemal Yılmaz

## Sakıp Sabancı Museum Collaboration
- Osman Serhat Karaman

## Contributor
- Begüm Çelik

## Project Summary

Technology became an inseparable aspect of the artworks which can be categorized as
new media art. However, this new approach that leads to new artistic creations came up
with its own questions related to its conservation process. Since technology changes and
develops each day, both the conservators and artists are questioning how to maintain those
artworks based on technological tools or interfaces without endamaging the essence of the
works. As the fine arts creations are in need of special conservation and preservation
applications to be maintained for centuries, the technological artworks have also the same
necessity but in their own way. This project has been created in the service of such creators
and conservators to make them able to control the artworks’ sustainability conditions. This
testing approach has been generated by creating a regular control mechanism for the
selected net-art project to check whether it is still working or not. The newest version of the
needed dependencies has installed each day in an environment that installs the project repo
from a given git address and builds the source code with that dependencies. The report has
been sent through the mail to whom it may be concerned each day and inform these
people if the project is still working with the new technologies it requires, or not. If not, artists
will have a chance to be informed about the current condition of the project they created
beforehand, and be able to change it with respect to current developments before the
project became totally non-operational.

## Approach

1. The net art project has been selected to test with the developed testing methodology.
2. The environment where the project will be executed with the latest versions of required dependencies has been built. The Docker container was created
for this purpose of creating an environment that executes whole process of testing. The file
called “docker-compose.yml” has created as such for assignment of the root privileges to
the docker container while also introducing the shared memory of it.

![image](https://user-images.githubusercontent.com/41292368/126209573-d4247965-715f-4850-8e8c-38dc9ee52980.png)

    -The following command was executed in the folder which contains that yml file.
                `$ docker-compose up -d `
    - After the container was created and executed, the following command is executed in order to obtain initial password for access to Jenkins.
                `$ docker exec my-jenkins-3 cat /var/jenkins_home/secrets/initialAdminPassword`
    - Then, “http://localhost:8083” was opened Jenkins sign in screen was seen and obtained password was used to sign in Jenkins.
    - Installation of Jenkins on Docker container has completed.
    
*Jenkins is used for automating the whole testing process since an automated reporting tool
for the current condition of the artworks is tried to be achieved.*

3. The new job was created in the Jenkins as a freestyle project. This job is used for
automation of the build with the latest version of the dependencies as well as reporting.

4. The testing tool builds the project with the latest versions of
dependencies and reports the build status through the mail. To reach this aim, a post-build
action has been added to the Jenkins job by using the Email Notification plugin. This plugin
sends the report of the build through the mail by using SMTP protocol. The mail includes the
build logs, versions of installed dependencies, and also the version of software language used in the
execution as mail attachments. The status of the build, whether it is successful or failure, is
included in the content of the mail.
![image](https://user-images.githubusercontent.com/41292368/126209342-3ef63d70-86f4-45cc-8824-85dfe788d8bd.png)

![image](https://user-images.githubusercontent.com/41292368/126209355-c7195c8a-db18-4301-aedd-8c211fe6ee24.png)

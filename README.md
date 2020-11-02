# General
A simple image to enable docker and maven in the same container


# Usage
```bash
# example
docker run --rm -u $(id -u ${USER}):$(id -g ${USER}) \
    -e MAVEN_CONFIG=/var/maven/.m2 \
    -v ~/.m2:/var/maven/.m2 \
    -v "$(pwd)":/usr/src/mymaven -w /usr/src/mymaven \
    -v /var/run/docker.sock:/var/run/docker.sock
    okieoth/d_maven_docker:3.6.3-adoptopenjdk-8 \
    mvn -DskipTests=true -Duser.home=/var/maven --settings /usr/src/mymaven/settings.xml package docker:build docker:push
```

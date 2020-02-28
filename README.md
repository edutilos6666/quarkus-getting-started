# quarkus-getting-started project

This project uses Quarkus, the Supersonic Subatomic Java Framework.

If you want to learn more about Quarkus, please visit its website: https://quarkus.io/ .

## Running the application in dev mode

You can run your application in dev mode that enables live coding using:
```
./mvnw quarkus:dev
```

## Packaging and running the application

The application is packageable using `./mvnw package`.
It produces the executable `quarkus-getting-started-1.0-SNAPSHOT-runner.jar` file in `/target` directory.
Be aware that it’s not an _über-jar_ as the dependencies are copied into the `target/lib` directory.

The application is now runnable using `java -jar target/quarkus-getting-started-1.0-SNAPSHOT-runner.jar`.

## Creating a native executable

You can create a native executable using: `./mvnw package -Pnative`.

Or you can use Docker to build the native executable using: `./mvnw package -Pnative -Dquarkus.native.container-build=true`.

You can then execute your binary: `./target/quarkus-getting-started-1.0-SNAPSHOT-runner`

If you want to learn more about building native executables, please consult https://quarkus.io/guides/building-native-image-guide .


### docker
mvn io.quarkus:quarkus-maven-plugin:1.2.1.Final:create \\ \
    -Dhttp.proxyHost=10.10.10.10 -Dhttp.proxyPort=666 -Dhttps.proxyHost=10.10.10.10 -Dhttps.proxyPort=666\\ \
    -DprojectGroupId=org.acme \\ \
    -DprojectArtifactId=quarkus-getting-started \\ \
    -DclassName="org.acme.quickstart.GreetingResource" \\ \
    -Dpath="/hello"
    
cd getting-started




./mvnw  -Dhttp.proxyHost=10.10.10.10 -Dhttp.proxyPort=666 -Dhttps.proxyHost=10.10.10.10 -Dhttps.proxyPort=666 compile quarkus:dev


./mvnw package

/usr/java/jdk1.8.0_181-amd64/bin/java -jar target/quarkus-getting-started-1.0-SNAPSHOT-runner.jar


// building native image for container 

mvn package -Pnative  \\ \
-Dhttp.proxyHost=10.10.10.10 -Dhttp.proxyPort=666 \\ \
-Dhttps.proxyHost=10.10.10.10 -Dhttps.proxyPort=666 \\ \
-Dquarkus.native.container-runtime=docker  \\ \
-Dquarkus.native.container-build=true


// build docker image

docker build --build-arg http_proxy=http://10.10.10.10:666 --build-arg https_proxy=http://10.10.10.10:666  -f src/main/docker/Dockerfile.native -t quarkus-quickstart/getting-started .

//run image
 
docker run -d -i --rm -p 8080:8080 --name quarkus-quickstart-container quarkus-quickstart/getting-started
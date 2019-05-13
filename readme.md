dependencies: 
- docker
- jdk 8
- nexus
- gradle

update dependencies:
```
gradle dependencyUpdates -Drevision=release --info
```

build: 
```
cd sujiakeji-eureka-server
./gradlew idea
./gradlew clean build copyJar -x test
```

start:
```
java -Dspring.profiles.active=dev \
  -jar build/libs/sujiakeji-eureka-server.jar
```

docker:
```
./gradlew docker

docker build -t sujiakeji/sujiakeji-eureka-server:1.0.0-SNAPSHOT .

docker run -it --rm \
  --name sujiakeji-eureka-server \
  -p 9000:9000 \
  -e SPRING_PROFILES_ACTIVE=dev \
  sujiakeji/sujiakeji-eureka-server

docker-compose up
```

# Multi-stage builds

Build with the full toolchain, ship only the result.

```dockerfile
# build stage
FROM maven:3.9-eclipse-temurin-21 AS build
WORKDIR /src
COPY pom.xml .
RUN mvn -q dependency:go-offline
COPY src ./src
RUN mvn -q package -DskipTests

# runtime stage
FROM eclipse-temurin:21-jre
COPY --from=build /src/target/app.jar /app.jar
ENTRYPOINT ["java", "-jar", "/app.jar"]
```

Result: the image contains a JRE and one jar, not Maven, sources or the local repo. Typically several hundred MB smaller and a smaller attack surface.

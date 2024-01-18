# ----------------------- BUILD STAGE -----------------------
FROM maven AS builder

WORKDIR /app

COPY ./pom.xml ./pom.xml
RUN mvn verify

COPY ./src ./src
RUN mvn verify

# ----------------------- RUN STAGE -----------------------
FROM openjdk:8-jre-alpine

WORKDIR /app
COPY --from=builder /app/target/ ./target

CMD ["java", "-Xmx8m", "-Xms8m", "-jar", "/app/target/words.jar"]

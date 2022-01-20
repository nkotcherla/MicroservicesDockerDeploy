# Here build is the alias name as we are trying multi stage docker file
FROM maven as build 
WORKDIR /app
# Copy the code from the local to present working directory in IMAGE
COPY . .
RUN mvn install

# This is the environment where app should run
FROM openjdk:11.0.10-jre
WORKDIR /app

# Copying from the above build
# target folder is standard for maven job, the jar file name we get from the pom.xml
# we are copying that to the current context /app

COPY --from=build /app/target/zuul-0.0.1-SNAPSHOT.jar /app
EXPOSE 9999
CMD ["java", "-jar", "zuul-0.0.1-SNAPSHOT.jar"]
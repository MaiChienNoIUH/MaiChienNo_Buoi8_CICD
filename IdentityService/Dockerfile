# Sử dụng OpenJDK làm base image
FROM openjdk:17-jdk-slim

# Cài đặt Gradle
RUN apt-get update && apt-get install -y wget unzip
RUN wget https://services.gradle.org/distributions/gradle-7.2-bin.zip -P /tmp \
    && unzip -d /opt /tmp/gradle-7.2-bin.zip \
    && ln -s /opt/gradle-7.2/bin/gradle /usr/bin/gradle

# Copy mã nguồn vào container
COPY . /app
WORKDIR /app

# Build ứng dụng Spring Boot bằng Gradle
RUN gradle build -x test

# Lệnh chạy ứng dụng
CMD ["java", "-jar", "build/libs/identity-service-0.0.1-SNAPSHOT.jar"]

# Mở port 8080
EXPOSE 8080

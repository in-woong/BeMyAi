# Gradle 빌드 환경
FROM gradle:7.6.1-jdk17 AS builder

# 작업 디렉토리 설정
WORKDIR /app

# Gradle Wrapper 및 설정 파일 복사
COPY gradlew gradlew.bat settings.gradle build.gradle /app/
COPY gradle /app/gradle

# 소스 코드 복사
COPY src /app/src

# 네트워크 타임아웃 및 캐시 초기화 후 빌드
ENV GRADLE_OPTS="-Dhttp.socketTimeout=60000 -Dhttp.connectionTimeout=60000 -Dhttps.protocols=TLSv1.2"
RUN rm -rf ~/.gradle/caches && chmod -R 777 /tmp && ./gradlew --no-daemon --stacktrace --info build -x test


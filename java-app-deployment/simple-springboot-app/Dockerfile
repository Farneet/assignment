FROM openjdk:11.0.1-jdk-slim-stretch

ARG VERSION

VOLUME /tmp

ADD target/simple-springboot-app-${VERSION}.jar app.jar

ENV JAVA_OPTS="$JAVA_OPTS"

ENTRYPOINT exec java $JAVA_OPTS -Djava.security.egd=file:/dev/./urandom -jar /app.jar
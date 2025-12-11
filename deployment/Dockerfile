FROM amazoncorretto:17-alpine
VOLUME /app
COPY applications/app-service/build/libs/JavaMqResponse.jar app.jar
ENV JAVA_OPTS="-XX:+UseContainerSupport -Djava.security.egd=file:/dev/./urandom"

ENTRYPOINT [ "sh", "-c", "java $JAVA_OPTS -jar app.jar" ]

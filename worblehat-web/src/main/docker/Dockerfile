FROM frolvlad/alpine-java:jre8-slim
ENV DOCKERIZE_VERSION v0.6.1
RUN apk add --no-cache openssl \
    && wget https://github.com/jwilder/dockerize/releases/download/$DOCKERIZE_VERSION/dockerize-alpine-linux-amd64-$DOCKERIZE_VERSION.tar.gz \
    && tar -C /usr/local/bin -xzvf dockerize-alpine-linux-amd64-$DOCKERIZE_VERSION.tar.gz \
    && rm dockerize-alpine-linux-amd64-$DOCKERIZE_VERSION.tar.gz

COPY maven/run-java.sh /app/run-java.sh
COPY maven/${project.build.finalName}.jar /app/worblehat.jar

CMD ["dockerize", "-wait", "tcp://worblehat-db:3306", "/app/run-java.sh", "run"]
EXPOSE 8080

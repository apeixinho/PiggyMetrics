FROM openjdk:8-jre-alpine

RUN apk update && apk upgrade && \
	apk add --no-cache curl && \  
	rm -rf /var/cache/apk/* || return 1;

ADD ./target/config.jar /app/
CMD ["java", "-Xmx200m", "-jar", "/app/config.jar"]

HEALTHCHECK --retries=8 --interval=10s --timeout=3s CMD curl -f http://localhost:8888/health || exit 1

EXPOSE 8888
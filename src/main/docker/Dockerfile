FROM gcr.io/distroless/java:11

WORKDIR /app
COPY target/lib /app/lib
ADD target/envoy-tracing-runner.jar /app

CMD ["/app/envoy-tracing-runner.jar"]
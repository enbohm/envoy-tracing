# Envoy Tracing Issue 6520
Example of the issue (b3-headers not propagated to external auth service) https://github.com/envoyproxy/envoy/issues/6520

To run you must have Docker installed. This repo contains the resources to setup Envoy proxy in front of a service (my-service) and 
an external authorization service (auth-service, see https://github.com/enbohm/authz-service)


To start run ```docker-compose up --build``` in directory src/main/docker/

To send a request execute
```curl -X GET "http://127.0.0.1:8080/"```

Open a browser and type http://127.0.0.1:16686 (Jeager UI)

Notice that the front-proxy and my-service is part of the same trace. The external auth-service is not (but shows up as a standalone service see [JaegerUI](jaeger-service.png)

Also note that the curl-command prints header present in the 'my-service', INCL. b3-trace headers. The log output from the auth-service does NOT print these
headers since they are not propagated to the exteral auth-service see [auth-logs](auth-service-logs.png). This trace shows up in Jaeger as 'standalone' since they can't be part of a trace due to missing b3-headers [JaegerUI-auth-standalone](jaeger-auth-service.png)

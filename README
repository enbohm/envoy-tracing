# Envoy Tracing Isse 6520
Showcase for the issue (b3-headers not propagated to external auth service) https://github.com/envoyproxy/envoy/issues/6520

To run you must have Docker installed. This repo contains the resources to setup Envoy proxy infront of a service (my-service) and 
an external authotization service (auth-service, see https://github.com/enbohm/authz-service)


To start run ```docker-compose up --build``` in directory src/main/docker/

To send a request execute
```curl -X GET "http://127.0.0.1:8080/"```

Open a browser and type http://127.0.0.1:16686 (Jeager UI)

Notice that the front-proxy and my-service is part of the same trace. The external auth-service is not (but shows up as a standalone service)

Also notice that the curl-command prints headers, INCL. b3-trace headers. The log output from the auth-service does not print these
headers since they are not propagated to the exteral auth-service.

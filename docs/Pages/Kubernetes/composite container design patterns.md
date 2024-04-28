
---

## [Link](https://kubernetes.io/blog/2015/06/the-distributed-system-toolkit-patterns/)

## Sidecar Design Pattern

Sidecar design pattern involves 2 containers running

1. Main Container: This runs the actual business logic of the service (e.g in a database pod, MySQL container is the main container)
2. Sidecar Container: This runs as a helper container that prepares the and supports the operations of the main container

Sidecar and Main container are independent but they share the same Volumes or FileSystems (where the sidecar is working to enhance the operations of the main container)

## Ambassador Design Pattern

This is a really useful design pattern

Again a bit similar to Sidecar design pattern, it consists of minimum 2 containers

1. Main container: This contains the application logic of the app that we are running. 
This could be a flask API or anything else that also contacts other services outside.

2. Ambassador container: This is a proxy container which proxies all requests from the main container to the outside world and provides output

Since these containers belong to the same pod, ambassador is reachable using "localhost".

Because of this we don't have to hardcode the urls for outside services and all other services are easily reachable through localhost.

The localhost service can through different ports direct to ambassador which reads the nature of the request and redirects the request to the right external pod


## Adaptor Design Pattern

This is used to standardize the output

For monitoring applications and other apps that generate a lot of data, the format in which the data is generated might not be desirable


Again 2 containers

1. Main container: main application logic
2. Adapter container: are used to modify the output, process it and then forward those packets to the logging/monitoring service

They share volumes for accessing logs just like sidecar design pattern


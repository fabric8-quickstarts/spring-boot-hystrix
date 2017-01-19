# Spring Boot and Hystrix QuickStart

This quickstart demonstrates how to use Hystrix with Spring-Boot using Kubernetes or OpenShift.

This example is related to `spring-boot-webmvc` which this example will call and output its response.
In case the `spring-boot-webmvc` is not running then the Hystrix circuit breaker should detect this
and return a fallback response.

### Building

The example can be built with

    mvn clean install


### Running the example locally

The example can be run locally using the following Maven goal:

    mvn spring-boot:run


### Running the example in Kubernetes

It is assumed a running Kubernetes platform is already running. If not you can find details how to [get started](http://fabric8.io/guide/getStarted/index.html).

Assuming your current shell is connected to Kubernetes or OpenShift so that you can type a command like

```
kubectl get pods
```

or for OpenShift

```
oc get pods
```

Then the following command will package your app and run it on Kubernetes:

```
mvn fabric8:run
```

To call the service from a web browser you need to append the context path `/hello` to the service URL, something like

    http://192.168.99.100:31824/hello

Depending on whether `spring-boot-webmvc` is running or not, then calling the service will return different response as

    Reply: Hello World!
    
.. will be returned when `spring-boot-webmvc` is running, and 
     
    Hello Fallback
         
.. is returned.         

You can also use the [fabric8 developer console](http://fabric8.io/guide/console.html) to manage the running pods, and view logs and much more.


#### Integration Testing

The example includes a [fabric8 arquillian](https://github.com/fabric8io/fabric8/tree/master/components/fabric8-arquillian) Kubernetes Integration Test. 
Once the container image has been built and deployed in Kubernetes, the integration test can be run with:

	mvn test -Dtest=*KT

The test is disabled by default and has to be enabled using `-Dtest`. [Integration Testing](https://fabric8.io/guide/testing.html) and [Fabric8 Arquillian Extension](https://fabric8.io/guide/arquillian.html) provide more information on writing full fledged black box integration tests for Kubernetes. 

### More details

You can find more details about running this [quickstart](http://fabric8.io/guide/quickstarts/running.html) on the website. This also includes instructions how to change the Docker image user and registry.


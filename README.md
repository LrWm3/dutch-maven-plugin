# k8s-custom-plugin

I really wasn't planning on doing this

A maven plugin which interacts with kubernetes, kafka and potentially any cluster service

## Before you begin

Create a kubernetes cluster using docker-for-desktop; deploy kafka as shown below

```
kubectl create namespace kafka && \
kubectl apply -k github.com/Yolean/kubernetes-kafka/variants/dev-small/?ref=v6.0.3
```

This will deploy kafka to the kubernetes cluster.

## Testing this plugin

To install this plugin on your machine locally, run

```
mvn install
```

To run this plugin on any other project (or this project), run

```
mvn dutch:touch
```

What does `mvn dutch:touch` do?

1. runs the equivalent of `touch dutch/target/test-classes/project-to-test/target/touch.txt`, creating an empty file
2. runs the equivalent of `kubectl get pods` using the default kubernetes client available

Creating a file is kinda cool, and being able to get pods is neat too...

## Deploying a pod using a yaml file

## Extending the plugin further to support kafka

## Learning section

If I didn't have the project folder name matching the artifact ID, when I did a `mvn install`, it would install the
plugin in the wrong directory in my `.m2/repositories` folder for some reason. Took me a while to figure out.

I was using the following java kubernetes api for a while, but it kind of sucked for loading yaml

```xml
<groupId>io.kubernetes</groupId>
<artifactId>client-java</artifactId>
<version>4.0.0</version>
<scope>compile</scope>
```

However, while the fabric8 plugin was 'easier' to read things with, and had a simplier api, I couldn't get the
yaml deployment working for some reason.

I'm pretty sure if I could understand this example it would potentially be understandable but whatever:

https://github.com/fabric8io/kubernetes-client/blob/master/kubernetes-tests/src/test/java/io/fabric8/kubernetes/client/mock/LoadTest.java

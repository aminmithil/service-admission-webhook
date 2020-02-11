# Kubernetes Service Admission Webhook
Kubernetes service admission webhook is simple kubernetes mutation webhook that restrict creating kubernetes service type as a ```LoadBalancer```. If service is created with the type ```LoadBalancer``` it change the service type to ```ClusterIP```.

## Prerequisites

Kubernetes 1.9.0 or above with the `admissionregistration.k8s.io/v1beta1` API enabled. Verify that by the following command:
```
kubectl api-versions | grep admissionregistration.k8s.io/v1beta1
```
The result should be:
```
admissionregistration.k8s.io/v1beta1
```

In addition, the `MutatingAdmissionWebhook` and `ValidatingAdmissionWebhook` admission controllers should be added and listed in the correct order in the admission-control flag of kube-apiserver.

## Build
1. Build and push docker image
```
DOCKER_USER=<docker-username> ./build
```

## Kudos
1. https://banzaicloud.com/blog/k8s-admission-webhooks/
2. https://medium.com/ovni/writing-a-very-basic-kubernetes-mutating-admission-webhook-398dbbcb63ec
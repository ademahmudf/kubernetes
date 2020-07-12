# Overview

Ingress nginx [official github page](https://github.com/kubernetes/ingress-nginx/).

[Kubernetes Ingress docs](https://kubernetes.io/docs/concepts/services-networking/ingress/)

[Ingress nginx installation](https://kubernetes.github.io/ingress-nginx/deploy/)

[ingress nginx annotations](https://kubernetes.github.io/ingress-nginx/user-guide/nginx-configuration/annotations/)

[istio ingress docs](https://istio.io/latest/docs/tasks/traffic-management/ingress/kubernetes-ingress/)

## Ingress `resources`

Basic ingress resource example

[/template/yaml](../template/yaml/ingress.yaml).

```console
apiVersion: networking.k8s.io/v1beta1
kind: Ingress
metadata:
  name: {{ ingress_name }}
  annotations:
    nginx.ingress.kubernetes.io/proxy-body-size: "0"
    nginx.org/client-max-body-size: "0"
    nginx.org/proxy-connect-timeout: "0"
    nginx.org/proxy-read-timeout: "0"
    nginx.ingress.kubernetes.io/rewrite-target: /
spec:
  rules:
  - host: {{ url }}
    http:
      paths:
       - path: /testpath
         pathType: Prefix
         backend :  
            serviceName: {{ service_name }}
            servicePort: 80
```

## Ingress `class`

```console
apiVersion: networking.k8s.io/v1beta1
kind: IngressClass
metadata:
  name: istio
spec:
  controller: istio.io/ingress-controller
---
apiVersion: networking.k8s.io/v1beta1
kind: Ingress
metadata:
  name: ingress
spec:
  ingressClassName: istio
  ...
```

## TLS

[TLS certificate](https://github.com/kubernetes/ingress-nginx/blob/master/docs/examples/PREREQUISITES.md#tls-certificates)

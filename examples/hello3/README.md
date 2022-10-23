# NGINX Example packaged for LFEdge

This is a simplified NGINX wrapper as part of a Helm tutorial for LFEdge.
If you are really interested in NGINX, we encourage you to use the [bitnami chart](https://artifacthub.io/packages/helm/bitnami/nginx) that this chart depends on.

# TL;DR

```
$ helm repo add lfedge-demo https://ericvh.github.io/lfledge-catalog/charts
$ helm install example lfedge-demo/test3
```

# Overview

This chart is setup to really have a single simple user-overridable value specifying the content of the index.html in the resulting NGINX instance.
It can be set in the values.yaml or overridden when installing on the command line.  The message is intended to be short and sweet and will be embedded into an HTML file represented by a configmap.

# Prerequisites

* Kubernetes 1.19+
* Helm 3.2.0+

# Uninstalling the Chart

```
$ helm delete example
```

# Parameters

## Common parameters

| Name | Description | Value |
| ---- | ----------- | ----- |
| content | Simple text content for web page | "Hello, World!" |
| nginx.service.type | which networking to use for kubernetes | ClusterIP |

# Notes

Remember to setup the right networking to access your resulting page.  The easiest path might be to use the LoadBalancer nginx.service.type which should allow you to access the resulting page via localhost.

```
$ helm install --set nginx.service.type=LoadBalancer example lfedge-demo/test3
```



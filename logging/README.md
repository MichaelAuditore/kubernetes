# Monitoring, Logging, and Troubleshooting

In Kubernetes, we have to collect resource usage data by Pods, Services, nodes, etc., to understand the overall resource consumption and to make decisions for scaling a given application. Two popular Kubernetes monitoring solutions are the Kubernetes Metrics Server and Prometheus.

The logs can be displayed for a single container pod or a specific container of a multi-container pod (supply the pod-name and hit the TAB key for a listing of its available containers):

```$ kubectl logs pod-name```

```$ kubectl logs pod-name container-name```

```$ kubectl logs pod-name container-name -p```

In addition, a user can run a custom command in a running container of a pod, or interact with the running container from the terminal (using the -it flag and invoking the shell command line interpreter of the container):

```$ kubectl exec pod-name -- ls -la /```

```$ kubectl exec pod-name -c container-name -- env```

```$ kubectl exec pod-name -c container-name -it -- /bin/sh```

When the pod-name is followed by the -c flag, hit the TAB key for a listing of its available containers. There are scenarios when the pods of an application do not reach the expected running state, visible in the output of the kubectl get pods command. In order to discover what prevents the pod from running - whether a missing dependency, container image or runtime issue, we can view the events for the entire cluster or for a specific pod in the output of the describe command. Currently there are two distinct commands that list cluster events:

```$ kubectl get events```

```$ kubectl events```

```$ kubectl describe pod pod-name```
# Annotations

Annotations allow us to attach arbitrary non-identifying metadata to any objects, in a key-value format:
```
"annotations": {
  "key1": "value1",
  "key2": "value2"
}
```

## Annotating Existing Object

We can easily annotate an existing object, a Pod for example, as such:

```
$ kubectl annotate pod mypod key1=value1 key2=value2
```

Unlike Labels, annotations are not used to identify and select objects. Annotations can be used to:

* Store build/release IDs, PR numbers, git branch, etc.
* Phone/pager numbers of people responsible, or directory entries specifying where such information can be found.
* Pointers to logging, monitoring, analytics, audit repositories, debugging tools, etc.
* Ingress controller information.
* Deployment state and revision information.


For example, while creating a Deployment, we can add a description as seen below:
Review [pod-annotation](./pod-annotation.yaml)
```
apiVersion: apps/v1
kind: Deployment
metadata:
  name: webserver
  annotations:
    description: Deployment based PoC dates 2nd Mar'2022
....
```

Imperatively, an object can be annotated with its latest configuration using the --save-config=true option. Try the two commands presented below to test the feature’s effect, then try the same two commands again without the --save-config option to see the difference:

```
$ kubectl run saved --image=nginx:alpine --save-config=true
```
```
$ kubectl get pod saved -o yaml
```
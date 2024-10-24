# Quota and Limits Management

When there are many users sharing a given Kubernetes cluster, there is always a concern for fair usage. A user should not take undue advantage. To address this concern, administrators can use the ResourceQuota API resource, which provides constraints that limit aggregate resource consumption per Namespace.

We can set the following types of quotas per Namespace:

* #### Compute Resource Quota
    We can limit the total sum of compute resources (CPU, memory, etc.) that can be requested in a given Namespace.
* #### Storage Resource Quota
    We can limit the total sum of storage resources (PersistentVolumeClaims, requests.storage, etc.) that can be requested.
* #### Object Count Quota
    We can restrict the number of objects of a given type (Pods, ConfigMaps, PersistentVolumeClaims, ReplicationControllers, Services, Secrets, etc.).

## Limit Range

An additional resource that helps limit resource allocation to pods and containers in a namespace, is the LimitRange, used in conjunction with the ResourceQuota API resource. A LimitRange can:

* Set compute resources usage limits per Pod or Container in a namespace.
* Set storage request limits per PersistentVolumeClaim in a namespace.
* Set a request to limit ratio for a resource in a namespace.
* Set default requests and limits and automatically inject them into Containers' environments at runtime.
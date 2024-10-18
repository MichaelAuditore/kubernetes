## Secrets

Secrets allow us to decouple the configuration details from the container image. Using Secrets, we pass configuration data as key-value pairs similar to ConfigMaps, thus, we can control how the information in a Secret is used, reducing the risk for accidental exposures. In Deployments or other resources, the Secret object is referenced, without exposing its content.

Note: It is important to keep in mind that by default, the Secret data is stored as plain text inside etcd, therefore administrators must limit access to the API server and etcd. However, Secret data can be encrypted at rest while it is stored in etcd, but this feature needs to be enabled at the API server level by the Kubernetes cluster administrator.

## Creation

### From literal values

```bash
   kubectl create secret generic my-password \
  --from-literal=password=mysqlpassword
```

### List Secrets by name
After successfully creating a secret we can analyze it with the get and describe commands. They do not reveal the content of the Secret. The type is listed as Opaque.

```bash
   kubectl get secret my-password
```

```bash
   kubectl describe secret my-password
```

### From Definition Manifest

You can observe files:
 * [encoded-secret.yaml](./enconded-secret.yaml)
 * [string-secret.yaml](./string-secret.yaml)

### From a file

 First, we encode the sensitive data and then we write the encoded data to a text file: Watch [pwd.txt](./pwd.txt)

 * Then, we can create the secret by using this command:
 ```bash
   kubectl create secret generic my-file-password \
  --from-file=pwd.txt
 ```

## Usage

After creation, we can retrieve the key-value data of an entire ConfigMap or the values of specific ConfigMap keys as environment variables, inside a container or pod.

Let's see how to do it.

### Using a [deployment](../deployments/pbitty-deployment.yaml) or [pod](../pods/nginx-pod.yaml) Manifest 

After pass name and image container parameters, we add:

* Pass configmap as an entire env
    ```
    envFrom:
        - configMapRef:
        name: `config-name`
    ```
* Pass configmap env by env var by refering to an specific key of an specific configMap.
  <b>Note:</b> We can pass configMap keys from multiples configmap
    ```
    env:
    - name: SPECIFIC_ENV_VAR1
      valueFrom:
        configMapKeyRef:
          name: config-map-1
          key: SPECIFIC_DATA
    - name: SPECIFIC_ENV_VAR2
      valueFrom:
        configMapKeyRef:
          name: config-map-2
          key: SPECIFIC_INFO
    ```
* Using as volumes.
    ```
    ...
    containers:
    - name: myapp-vol-container
        image: myapp
        volumeMounts:
        - name: config-volume
        mountPath: /etc/config
    volumes:
    - name: config-volume
        configMap:
        name: vol-config-map
    ...
    ```
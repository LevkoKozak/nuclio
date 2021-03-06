# HTTP trigger

The HTTP trigger is the only trigger created by default if not configured (by default has 1 worker). It handles incoming HTTP requests at container port 8080, assigning workers to incoming requests. If a worker is not available, 503 is returned.

## Attributes

| Path | Type | Description | 
| --- | --- | --- |  
| port | int | The NodePort (or equivalent) on which the function will serve HTTP requests. If empty, chooses a random port within the platform range |
| ingresses.(name).host | string | The host to which the ingress maps to |
| ingresses.(name).paths | list of strings | The paths the ingress handles |

#### Example

```yaml
triggers:
  myHttpTrigger:
    maxWorkers: 4
    kind: "http"
    attributes:
      port: 32001
  
      # see "Invoking Functions By Name With Kubernetes Ingresses" for more details
      # on configuring ingresses
      ingresses:
        http:
          host: "host.nuclio"
          paths:
          - "/first/path"
          - "/second/path"
        http2:
          paths:
          - "/wat"
```

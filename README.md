# pulumi-k8s-operator-example
Pulumi Kubernetes Operator Example

Stack example...

```yaml
apiVersion: v1
kind: Secret
metadata:
  name: pulumi-api-secret
type: Opaque
stringData:
  accessToken: "<PUT TOKEN HERE>"
---
apiVersion: pulumi.com/v1
kind: Stack
metadata:
  name: nginx-k8s-stack
spec:
  envRefs:
    PULUMI_ACCESS_TOKEN:
      type: Secret
      secret:
        name: pulumi-api-secret
        key: accessToken
  stack: christianh814/quickstart/dev
  projectRepo: https://github.com/christianh814/pulumi-k8s-operator-example
  branch: "refs/heads/main"
  destroyOnFinalize: true
  retryOnUpdateConflict: true
  continueResyncOnCommitMatch: true
  resyncFrequencySeconds: 60
  refresh: true
...
```

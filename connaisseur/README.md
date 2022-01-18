# Connaisseur
Connaisseur allows for validating signed images. The verification only takes place on namespaces that have the following label.

```
apiVersion: v1
kind: Namespace
metadata:
  labels:
    kubernetes.io/metadata.name: test
    securesystemsengineering.connaisseur/webhook: validate
```

This can be tested by trying to deploy an image that has not been signed.
```
oc run pacman --image quay.io/rcook/pacman-nodejs-app
Error from server: admission webhook "connaisseur-svc.connaisseur.svc" denied the request: Unexpected Cosign exception for image "quay.io/rcook/pacman-nodejs-app:latest": Error: unknown mime type: application/vnd.docker.distribution.manifest.v1+prettyjws
```

## Project
The project is located at https://github.com/sse-secure-systems/connaisseur

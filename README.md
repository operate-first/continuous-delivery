# Continous Delivery

This repository contains an opinionated reference architecture to setup, manage and operate a continous delivery
pipeline. The continous delivery pipeline not only consists of the Tekton/OpenShift Pipelines parts, but also
supporting Cyborg for maintaining the source code (creating releases/tags, updating dependencies, ...).

### Prerequisites
Kustomize 3.8.1+
SOPS 3.4.0+
KSOPS 2.1.2+

Ensure you have the key to decrypt secrets.

### GPG Key access

This repo encrypts secrets using a dev test key, you can find the test key in examples/key.asc folder.

```
$ base64 -d < examples/key.asc | gpg --import
```

You will need to import this key to be able to decrypt the contents of the secrets using sops.

Do NOT use this gpg key for production purposes.

## Policy Based Control of resources

All resources created by kustomize should pass OPA conftest, you could check this by
using: `kustomize build --enable_alpha_plugins . | conftest test --policy ../policy -`.

## TODO

* outline how to use the op1st toolbox container to run tools like conftest and kustomize

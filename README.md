# sno-config
Configurations for Single Node OpenShift

This repository hosts personal configurations for my Single Node OpenShift cluster.

I use this for demonstrations and reproducers of of customer issues.

As many configurations as possible are maintained in OpenShift GitOPS (ArgoCD).

Configuring the registry in bare metal:

oc patch configs.imageregistry.operator.openshift.io cluster --type merge --patch '{"spec":{"managementState":"Managed"}}'

oc patch config.imageregistry.operator.openshift.io/cluster --type=merge -p '{"spec":{"rolloutStrategy":"Recreate","replicas":1}}'



oc create -f image-registry-pvc.yaml -n openshift-image-registry

oc edit config.imageregistry.operator.openshift.io -o yaml

storage:
  pvc:
    claim: 


apiVersion: imageregistry.operator.openshift.io/v1
kind: Config
metadata:
  creationTimestamp: "2025-06-03T19:22:55Z"
  finalizers:
  - imageregistry.operator.openshift.io/finalizer
  generation: 7
  name: cluster
  resourceVersion: "87602"
  uid: 41446d57-ffb0-426a-aecc-9b344baa63a4
spec:
  httpSecret: 8d868e206f5131e2691e89c77599b8d31d268e6586486e47e53b2b5cd7a10c10ae6b60414f71c9ce5df36e67851df74a993fd118bf431f5cf581740be5a0721d
  logLevel: Normal
  managementState: Managed
  observedConfig: null
  operatorLogLevel: Normal
  proxy: {}
  replicas: 1
  requests:
    read:
      maxWaitInQueue: 0s
    write:
      maxWaitInQueue: 0s
  rolloutStrategy: Recreate
  storage:
    managementState: Unmanaged
    pvc:
      claim: image-registry-storage
  unsupportedConfigOverrides: null

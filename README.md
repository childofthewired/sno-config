# sno-config
Configurations for Single Node OpenShift

This repository hosts personal configurations for my Single Node OpenShift cluster.

I use this for demonstrations and reproducers of of customer issues.

As many configurations as possible are maintained in OpenShift GitOPS (ArgoCD).

Configure the default storage class 

oc patch storageclass lvms-vg1 -p '{"metadata": {"annotations": {"storageclass.kubernetes.io/is-default-class": "true"}}}'


Configuring the registry in bare metal:

oc patch configs.imageregistry.operator.openshift.io cluster --type merge --patch '{"spec":{"managementState":"Managed"}}'

oc patch config.imageregistry.operator.openshift.io/cluster --type=merge -p '{"spec":{"rolloutStrategy":"Recreate","replicas":1}}'



oc create -f image-registry-pvc.yaml -n openshift-image-registry

oc edit config.imageregistry.operator.openshift.io -o yaml

storage:
  pvc:
    claim: 



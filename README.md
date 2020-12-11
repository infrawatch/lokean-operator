# lokean-operator
OpenShift Operator for managing the lifecycle of Lokean

## Build the operator
```
# registry path, for example "quay.io/infrawatch/lokean-operator:latest"
REGISTRY_PATH=
buildah bud -f build/Dockerfile -t $(REGISTRY_PATH) .
buildah push --tls-verify=false $(REGISTRY_PATH)
```

## Deploy the operator
```
oc apply -f deploy/role_binding.yaml -f deploy/role.yaml -f deploy/service_account.yaml -f deploy/operator.yaml

# make required configuration changes in deploy/crds/lokean.infra.watch_v1alpha1_lokean_cr.yaml

oc apply -f deploy/crds/lokean.infra.watch_lokeans_crd.yaml
oc apply -f deploy/crds/lokean.infra.watch_v1alpha1_lokean_cr.yaml
```

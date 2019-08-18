# kustomize-example

## Use kubectl kustomize
```bash
kubectl kustomize ./account-service/base
```

```bash
kubectl kustomize github.com/amasucci/kustomize-example.git/account-service/base\?ref=master
```

## Use standalone kustomize

Standalone kustomize allows you to create more complex structures applying multiple layers 

```bash
kustomize build ./account-service/overlays/stg/
```

## Hack for variable interpolation

```bash
export BUILD_HASH=f487d34c
export PROJECT_NAME=project-793512

# $(cat digest.txt) will also be interpolated

eval "cat <<EOF
$(kustomize build ./account-service/overlays/stg/)
EOF
"

# OR

eval "cat <<EOF
$(kustomize build github.com/amasucci/kustomize-example.git/account-service/overlays/stg\?ref=master)
EOF
"
```

# dind

```sh
kubectl create ns dind

cd helm
helm template . | k apply -n dind -f -
```

## delete

```sh
cd helm
helm template . | k delete -n dind -f -
```
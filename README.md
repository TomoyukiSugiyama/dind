# dind

## deploy

```sh
kubectl create ns dind

cd helm
helm template . | k apply -n dind -f -
```

## exec

```sh
$ kubectl get pods                                                                                                                                                                      (git)-[main]
NAME                    READY   STATUS    RESTARTS       AGE
dind-6f9bf8dd58-cgfb6   2/2     Running   3 (3m8s ago)   3m25s

$ kubectl exec -it dind-6f9bf8dd58-cgfb6 -c docker -- sh                                                                                                                                (git)-[main]
/ # docker ps
CONTAINER ID   IMAGE          COMMAND                  CREATED              STATUS              PORTS     NAMES
d23ac024756c   nginx:latest   "/docker-entrypoint.…"   About a minute ago   Up About a minute   80/tcp    optimistic_jackson
```

## delete

```sh
cd helm
helm template . | k delete -n dind -f -
```
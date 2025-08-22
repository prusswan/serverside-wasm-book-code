# `hello-world-spin`

- k3d cluster create command to avoid eviction
```shell
k3d cluster create wasm-cluster --image ghcr.io/spinframework/containerd-shim-spin/k3d:v0.19.0 --port "8081:80@loadbalancer" --agents 2 \
  --k3s-arg '--kubelet-arg=eviction-hard=imagefs.available<1%,nodefs.available<1%@agent:*' \
  --k3s-arg '--kubelet-arg=eviction-minimum-reclaim=imagefs.available=1%,nodefs.available=1%@agent:*'
```

- Pre-reqs:
    - K8s cluster w/ the container-spin-shim installed on every node.
    - cert-manager installed onto the cluster.
    - Spin's RuntimeClass applied.
    - Spin's CRDs applied.
    - Spin's operator installed.
    - Spin's executor created.


- Then, assuming you have `spin` installed, run:
```shell
spin build
spin registry push ghcr.io/<your GH username>/serverside-wasm-book-code/hello-world-spin:latest
spin kube scaffold --from ghcr.io/danbugs/serverside-wasm-book-code/hello-world-spin:latest | kubectl create -f -
```

- Then, you can test it with:
```shell
kubectl port-forward svc/hello-world-spin 8083:80
curl localhost:8083/
```

# `smart-cms`

How to run backend:

```shell
wash up --multi-local --label zone=us-east-1 -d
wash up --multi-local --label zone=us-west-1 -d
wash build
wash app deploy ./wadm.yaml
```

How to run the frontend:

```shell
http-server ./index.html
```

Use ollama-provider from https://github.com/danbugs/ollama-provider/tree/chapter08
Use ollama-provider/ollama-example to verify if the provider is working

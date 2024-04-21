# Cluster space

- To create the multi node cluster run `kind create cluster --config cluster.yaml`
- `kubectl cluster-info --context kind-kind-cluster`


# [Using The Registry](https://kind.sigs.k8s.io/docs/user/local-registry/)

The registry can be used like this.

1. First we’ll pull an image docker pull gcr.io/google-samples/hello-app:1.0
2. Then we’ll tag the image to use the local registry docker tag gcr.io/google-samples/hello-app:1.0 localhost:5001/hello-app:1.0
3. Then we’ll push it to the registry docker push localhost:5001/hello-app:1.0
4. And now we can use the image kubectl create deployment hello-server --image=localhost:5001/hello-app:1.0

If you build your own image and tag it like localhost:5001/image:foo and then use it in kubernetes as localhost:5001/image:foo. And use it from inside of your cluster application as kind-registry:5000.

# Helm

- `helm get manifest clunky-serval`

## Refrences
- [Helm Functions](https://helm.sh/docs/chart_template_guide/function_list/)
- [Built-in Objects](https://helm.sh/docs/chart_template_guide/builtin_objects/)
- [File Functions](https://helm.sh/docs/chart_template_guide/accessing_files/)
- [Tips and Tricks](https://helm.sh/docs/howto/charts_tips_and_tricks/)
- [Glob Patterns](https://helm.sh/docs/chart_template_guide/accessing_files/#glob-patterns)


## For helm dry run
`helm install --debug --dry-run goodly-guppy ./mychart`

Keep in mind that Helm is not supposed to contact the Kubernetes API Server during a `helm template|install|upgrade|delete|rollback --dry-run` operation. 
To test lookup against a running cluster, `helm template|install|upgrade|delete|rollback --dry-run=server` should be used instead to allow cluster connection.


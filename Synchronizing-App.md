# To Synchronize the an ArgoCd Application with the argocd CLI

- since the application his status is outofsync once created, because it hasn't been deployed yet, we will then sync the application with a sync command

``` bash
argo app sync {app-name}
```

- To confirm it's running, I use the command:

```bash
kubectl -n {namespace} get all
```

so you will see the application status "Running", if synchronized successfully

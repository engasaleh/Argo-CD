You should now be able to create sealed secrets.

# 1. Install the client-side tool (kubeseal) as explained in the docs below:

    https://github.com/bitnami-labs/sealed-secrets#installation-from-source

# 2. Create a sealed secret file running the command below:

```bash
    kubectl create secret generic secret-name --dry-run=client --from-literal=foo=bar -o [json|yaml] | \
    kubeseal \
      --controller-name=sealed-secrets-controller \
      --controller-namespace=default \
      --format yaml > mysealedsecret.[json|yaml]
```

The file mysealedsecret.[json|yaml] is a commitable file.

# If you would rather not need access to the cluster to generate the sealed secret you can run:

```bash
    kubeseal \
      --controller-name=sealed-secrets-controller \
      --controller-namespace=default \
      --fetch-cert > mycert.pem
```


to retrieve the public cert used for encryption and store it locally. You can then run 'kubeseal --cert mycert.pem' instead to use the local cert e.g.


```bash
    kubectl create secret generic secret-name --dry-run=client --from-literal=foo=bar -o [json|yaml] | \
    kubeseal \
      --controller-name=sealed-secrets-controller \
      --controller-namespace=default \
      --format [json|yaml] --cert mycert.pem > mysealedsecret.[json|yaml]
```


# 3. Apply the sealed secret
```bash
    kubectl create -f mysealedsecret.[json|yaml]
```

Running 'kubectl get secret secret-name -o [json|yaml]' will show the decrypted secret that was generated from the sealed secret.

Both the SealedSecret and generated Secret must have the same name and namespace.

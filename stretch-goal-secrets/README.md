Secrets Encryption can be done by gomplate.

# Tools used
    - AWS Credential manager to store the secrets
    - gomplate to replace and encode the values


# gomplate

Add all the secret files in resources folder

Run the below command for fetching secret from aws secret manager and b64 encoding it

``` gomplate -d aws="aws+sm:?type=application/json" --input-dir resources --output-dir resources.out```


The results will be in resource.out folder.

# Create secret

``` kubectl apply -f resources.out/ ```

Creation can be automated in Jenkinsfile




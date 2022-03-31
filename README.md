# terraform-module-k8s-dashboard

Terraform module to deploy the [Kubernetes Dashboard](https://github.com/kubernetes/dashboard).

Uses their Helm chart to deploy it.

Note: this module is not AWS specific but good install details here for [deploy to EKS](https://docs.aws.amazon.com/eks/latest/userguide/dashboard-tutorial.html).

Using the Dashboard
--------------------
To use it do :
```shell script
# Get our login token
kubectl -n kube-system describe secret $(kubectl -n kube-system get secret | grep dashboard-admin | awk '{print $1}')
# Invoke the Proxy to give access to the Dashboard
kubectl proxy
```
then open in [browser](http://localhost:8001/api/v1/namespaces/kubernetes-dashboard/services/https:kubernetes-dashboard:/proxy/#!/login)

and use the Token as displayed in your terminal for login. 

Note: The token is short-lived and may expire. You will then need to repeat **ALL** of the above steps, to get login again.

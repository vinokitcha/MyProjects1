# Sample Project

Create Secrets - Some Private registry can delegate authentication to a separate service. 

In these cases,image pull secrets must be defined for both the authentication and registry endpoints (eg: Gitlab and hence 2 secrets)

```bash
#Create Secrets
oc create secret docker-registry <secret_name1> --docker-server=registry.gitlab.com  --docker-username=<gitlab_uname> --docker-password=<gitlab_user_pwd>

oc create secret docker-registry <secret_name2> --docker-server=gitlab.com  --docker-username=<gitlab_uname> --docker-password=<gitlab_user_pwd>

#Link secrets to Service A/C.
oc secrets link default <secret_name1> --for=pull
oc secrets link default <secret_name2> --for=pull
```

# Airbyte Set Up 

## Helm chart sourced from
```sh
helm repo add airbyte https://airbytehq.github.io/helm-chart
```

## Deploying to OpenShift
```sh
helm install dev-release-ab .
```

## Notes: 
Get the application running with this command (Use NRM.DataFoundations@gov.bc.ca as email):
```sh
oc --namespace a1b9b0-dev port-forward svc/dev-release-ab-airbyte-webapp-svc 8080:80
```

View Minio object storage with this command: 
```sh
oc --namespace a1b9b0-dev port-forward pod/airbyte-minio-0 37373:37373
```

More info: https://apps.nrs.gov.bc.ca/int/confluence/x/zQ09Cg

![Version: 0.50.17](https://img.shields.io/badge/Version-0.50.17-informational?style=flat-square) ![Type: application](https://img.shields.io/badge/Type-application-informational?style=flat-square) ![AppVersion: 0.50.17](https://img.shields.io/badge/AppVersion-0.50.17-informational?style=flat-square)


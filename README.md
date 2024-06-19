# Airbyte Set Up 

## Helm chart sourced from
```sh
helm repo add airbyte https://airbytehq.github.io/helm-charts
```

## Deploying to OpenShift
```sh
helm install dev-release-ab .
```

## Notes: 
Get the application running with this command (Use NRM.DataFoundations@gov.bc.ca as email):
```sh
oc --namespace a1b9b0-dev port-forward svc/dev-release-ab-airbyte-webapp-svc 8090:80
```

Use the API with this commmnd: 
```sh 
oc --namespace a1b9b0-dev port-forward svc/dev-release-ab-airbyte-api-server-svc 8091:80
```

View Minio object storage with this command: 
```sh
oc --namespace a1b9b0-dev port-forward pod/airbyte-minio-0 37373:37373
```

```sh
helm upgrade -f values.yaml dev-release-ab . --version 0.48.0
```

Access database via terminal using this command:
```sh
psql -U airbyte -d db-airbyte
```

Set resource limits for a specific connection using this command:
```sh 
update connection set resource_requirements = '{"cpu_limit": "100m", "cpu_request": "50m", "memory_limit": "1Gi", "memory_request": "500Mi"}' where id = '5ff07aa0-036d-4133-a0e4-c7684d5bb7da';
```

More info: https://apps.nrs.gov.bc.ca/int/confluence/x/zQ09Cg

![Version: 0.50.17](https://img.shields.io/badge/Version-0.50.17-informational?style=flat-square) ![Type: application](https://img.shields.io/badge/Type-application-informational?style=flat-square) ![AppVersion: 0.50.17](https://img.shields.io/badge/AppVersion-0.50.17-informational?style=flat-square)


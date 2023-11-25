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

Access database via terminal using this command:
```sh
psql -U airbyte -d db-airbyte
```

Set resource limits for a specific connection using this command:
```sh 
update connection set resource_requirements = '{"cpu_limit": "5", "cpu_request": "1", "memory_limit": "1000Mi", "memory_request": "500Mi"}' where id = '5ff07aa0-036d-4133-a0e4-c7684d5bb7da';
```

November 2023 Update: Airbyte (in OpenShift Emerald cluster) is currently able to replicate json data from Oracle to Postgres. However, the 'normalization' pod is failing. This step uses DBT to flatten the replicated json data into columns. The 'normalization' pod is expected to be phased out for Postgres destinations (and replaced with a new method) by end of year: https://github.com/airbytehq/airbyte/issues/25194 https://github.com/airbytehq/airbyte/issues/26028


More info: https://apps.nrs.gov.bc.ca/int/confluence/x/zQ09Cg

![Version: 0.50.17](https://img.shields.io/badge/Version-0.50.17-informational?style=flat-square) ![Type: application](https://img.shields.io/badge/Type-application-informational?style=flat-square) ![AppVersion: 0.50.17](https://img.shields.io/badge/AppVersion-0.50.17-informational?style=flat-square)


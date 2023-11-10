## Docker login for BC Gov Artifactory
```sh
docker login https://artifacts.developer.gov.bc.ca/artifactory
```

##  Check status of repo:
```sh
oc describe artproj tools
```

## Create secret with docker login:
```sh 
oc create secret docker-registry airbyte-docker `
    --docker-server=artifacts.developer.gov.bc.ca `
    --docker-username=default-a1b9b0-sroovq `
    --docker-password=<password>`
    --docker-email=default-a1b9b0-sroovq@a1b9b0-tools.local
```

## Pass secret to service accounts:
```sh
oc secrets link default airbyte-docker
oc secrets link builder airbyte-docker
oc secrets link airbyte-admin airbyte-docker
```
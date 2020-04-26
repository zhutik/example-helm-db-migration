# Example PHP DB Migrations with Helm3

This repository contains example Helm3 chart for PHP application with simple HTTP endpoints and DB migrations.
For simplicity, we will use Slim Framework 4 and Phinx package to perform DB migration.

Goal: provide example of K8s zero-downtime deployment with database migration for PHP applications.  

## Requirements

- Kubectl installed
- Kubernetes cluster running v1.16+ (f.e. minikube)
- Helm3 installed
- Optional: docker installed (to build and push images)


## Build & Push

```bash
# build and push Nginx 1.17 docker image
docker build -t zhutik/example-helm-db-migration-nginx --force-rm -f _docker/nginx/Dockerfile .
docker push zhutik/example-helm-db-migration-nginx

# build php-fpm (PHP 7.4) docker image
docker build -t zhutik/example-helm-db-migration-php-fpm --force-rm -f _docker/php/Dockerfile .
docker push zhutik/example-helm-db-migration-php-fpm
```

## TODO:

- [ ] Add instructions on how to create namespace
- [ ] Add helm chart to deployment one pod with Nginx and php-fpm container
- [ ] Add Percona DB container and deployment
- [ ] Add DB migration job and pre-install/pre-upgrade hooks
- [ ] Add rollback instructions

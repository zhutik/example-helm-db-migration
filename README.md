# Example PHP DB Migrations with Helm3

This repository contains example Helm3 chart for PHP application with simple HTTP endpoints and DB migrations.
For simplicity, we will use Slim Framework 4 and Phinx package to perform DB migration.

Goal: provide example of K8s zero-downtime deployment with database migration for PHP applications.  

## Requirements

- [Kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/) installed
- Kubernetes cluster running v1.16+ (f.e. [minikube](https://kubernetes.io/docs/setup/learning-environment/minikube/))
- [Helm3](https://helm.sh/docs/intro/install/) installed
- Optional: docker installed (to build and push images)

## Before we start

1. We need to build and push docker images that would be used inside K8s pod.
2. (optional) We need to create separate K8s namespace. This is an optional step, but it's recommended to have applications separated into different namespaces. 

### Build & Push

```bash
# build and push Nginx 1.17 docker image
docker build -t zhutik/example-helm-db-migration-nginx --force-rm -f _docker/nginx/Dockerfile .
docker push zhutik/example-helm-db-migration-nginx

# build php-fpm (PHP 7.4) docker image
docker build -t zhutik/example-helm-db-migration-php-fpm --force-rm -f _docker/php/Dockerfile .
docker push zhutik/example-helm-db-migration-php-fpm
```

### Create new namespace and expose it

```bash
kubectl create namespace example-helm-db-migration
export KUBE_NAMESPACE=example-helm-db-migration
```

## TODO:

- [x] Add instructions on how to create namespace
- [ ] Add helm chart to deployment one pod with Nginx and php-fpm container
- [ ] Add Percona DB container and deployment
- [ ] Add DB migration job and pre-install/pre-upgrade hooks
- [ ] Add rollback instructions

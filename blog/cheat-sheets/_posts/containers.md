# Docker
## Run an image
```shell
docker run 678422363581.dkr.ecr.eu-west-2.amazonaws.com/zzish-api:1.7.0
```

## Login and pull image from AWS ECR
```shell
aws ecr get-login --region eu-west-2 --no-include-email
# Run the command returned in the output of the command above
docker pull 678422363581.dkr.ecr.eu-west-2.amazonaws.com/api:v1.7.1
```   

## Copy file from container to localhost
```shell
docker cp <containerId>:/file/path/within/container /host/path/targets
```

# Kubernetes
https://kubernetes.io/docs/reference/kubectl/cheatsheet/

kb get pods -n stag
kb delete pods quizplayer-556bd5d7f8-gxczl

kb get deployments
kb get deployments -n prod
kb edit deployment quizalize

kb port-forward carmel-9d8d57f75-9qx58 -n stag 3100:3100

kb create config stag-spitafields-25apr19v1 --from-env-file=tech-stuff/workspace/zzish/kubernetes/test-environment/spitafields/spitafields.stag.env -n stag
kb get configmap stag-spitafields-24august -n stag -o yaml
kubectl get pods -n prod | grep Evicted | awk '{print $1}' | xargs kubectl delete pod -n prod

watch -n 1 -x kubectl get pods -n prod

## View logs
kb logs stag-spitafields-99b8bf696-ffn76 -n stag -f
kb logs -l app=spitafields -n prod -f --max-log-requests=10
    
## Global config
### ??
kb config set-context $(kubectl config current-context) --namespace=test

## SSH into a pod
kb exec -it stag-spitafields-6f755588dc-vrldn sh

## Working with horizontal pod auto-scaler

Ref: https://kubernetes.io/docs/tasks/run-application/horizontal-pod-autoscale/

### Get config
```shell
kubectl get hpa
```

### Edit config
```shell
kubectl edit hpa
```

# EKS
## Create cluster
```shell
eksctl create cluster --name ak-eks-playground --version 1.13 --nodegroup-name standard-workers --node-type t3.medium --nodes 3 --nodes-min 1 --nodes-max 4 --node-ami auto --region eu-central-1
```

## Get clusters
```shell
eksctl get clusters
```

## Delete cluster
```shell
eksctl delete cluster --name ak-eks-playground --region eu-west-1
```

## Get nodegroup of a cluster
```shell
eksctl get nodegroup --cluster ak-eks-playground --region eu-central-1
```


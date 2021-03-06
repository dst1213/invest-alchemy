# Invest Alchemy Core Service

## Infrastructure

[serverless-jobs-using-fargate](https://github.com/z0ph/serverless-jobs-using-fargate)

## How to start

### env

```
mv .env_sample .env # must set .env
source .env
```

### Docker

```
docker build -t invest-alchemy/core .
docker run -t -i -e TUSHARE_API_TOKEN=xxxx invest-alchemy/core
```

#### push docker to AWS ECR

```
aws ecr get-login-password --region us-east-1 | docker login --username AWS --password-stdin 745121664662.dkr.ecr.us-east-1.amazonaws.com # Retrieve an authentication token and authenticate your Docker client to your registry

docker build -t invest-alchemy/core . # Build your Docker image

docker tag invest-alchemy/core:latest 745121664662.dkr.ecr.us-east-1.amazonaws.com/invest-alchemy/core:latest # tag your image so you can push the image to this repository

docker push 745121664662.dkr.ecr.us-east-1.amazonaws.com/invest-alchemy/core:latest # push this image to your newly created AWS repository
```

## Workflow

change src code -> make build-docker -> make apply
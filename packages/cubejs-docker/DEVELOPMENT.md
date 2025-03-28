# Development guide

## How to build

Release version

### Debian:

```sh
docker build -t cubejs/cube:latest -f latest.Dockerfile .
docker buildx build --platform linux/amd64 -t cubejs/cube:latest -f latest.Dockerfile .
docker buildx build --platform linux/amd64,linux/arm64 -t cubejs/cube:latest -f latest.Dockerfile .
```

### JDK

```sh
docker build -t cubejs/cube:latest-jdk -f latest-debian-jdk.Dockerfile .
```

### Not released, development (from `cubejs-docker` directory)

```sh
docker build -t cubejs/cube:dev -f dev.Dockerfile ../../
docker build -t cubejs/cube:v1-returnUsedPreAgg -f local.Dockerfile .
docker tag cubejs/cube:v1-returnUsedPreAgg  public.ecr.aws/v2l0r3n7/cubejs/cube:v1-returnUsedPreAgg
aws ecr-public get-login-password --region us-east-1 --profile shared-services | docker login --username AWS --password-stdin public.ecr.aws
docker push public.ecr.aws/v2l0r3n7/cubejs/cube:v1-returnUsedPreAgg
```

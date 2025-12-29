# Image Build Workflow
This workflow build and push Docker image to your registry

## Inputs
+ `image-tag`: The image tag to use
+ `push`: Whether to push the image or not (default: false)
+ `registry`: Image registry URL (default: docker.io)
+ `build-dir`: Directory to run the build (default: the Github Actions workspace)

## Secrets
+ `DOCKER_USERNAME` and `DOCKER_PASSWORD`: Used for authentication, required if `push` is enabled.

## Example workflow

```yaml
name: Build & Push

on:
  push:
    branches: [main]

jobs:
  build:
    uses: TonyQ-Lab/actions-workflows/image-build/workflow.yml
    with:
      image-tag: my-app:1.0.0
      push: true
      registry: docker.io
      build-dir: front-end
    secrets:
      DOCKER_USERNAME: ${{ secrets.DOCKER_USERNAME }}
      DOCKER_PASSWORD: ${{ secrets.DOCKER_PASSWORD }}
```
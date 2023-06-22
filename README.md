# aws-tf-deployer-image

- [aws-tf-deployer-image](#aws-tf-deployer-image)
  - [Goal](#goal)
  - [Size comparison](#size-comparison)
  - [Build](#build)
  - [References](#references)


## Goal
Build a SMALL container image for CICD pipeline usage to deploy resources to AWS using terraform.

## Size comparison

I hoped to achieve more, but thats what it is. 🤷🏻

```bash
docker inspect -f "{{ .Size }}" amazon/aws-cli:latest | numfmt --to=si
405M

docker inspect -f "{{ .Size }}" aws-tf-deployer-image:local | numfmt --to=si
204M
```

## Build

```bash
docker build -t aws-tf-deployer:local .
```
> If you are using a Mac with ARM processor add the following flag to the build command: `--platform=linux/amd64`


## References
Turns out that other people also struggled to install the AWS CLI on alpine with the missing glibc libraries. 
[This post helped a lot.](https://stackoverflow.com/questions/60298619/awscli-version-2-on-alpine-linux#:~:text=to%20the%20Dockerfile.-,Update%202022%2D08%2D01,-AWS%20has%20improved)
## [How to Create a Docker Image](https://jfrog.com/knowledge-base/a-beginners-guide-to-understanding-and-building-docker-images/)

### Interactive Method

The following is a set of simplified steps to creating an image interactively:

- Install Docker and launch the Docker engine
- Open a terminal session
- Use the following Docker run command to start an interactive shell session with a container launched from the image specified by image_name:tag_name:

```bash
$ docker run -it image_name:tag_name bash
```

- You can also identify your container with something more meaningful by assigning your own name using the `– name` operator in the `Docker run` command.

> Example:
>
> A container environment based on the latest version of Ubuntu:
>
> ```bash
> $ docker run --name ubuntu  -it ubuntu bash
> ```
>
> Now configure your container environment by, for example, installing all the frameworks, dependencies, libraries, updates, and application code you need. The following simple example adds an NGINX server:
>
> ```shell
> # apt-get update && apt-get install -y nginx
> ```
>
> List active container processes
>
> ```bash
> $ docker ps
> ```
>
> Save your image using the Docker commit command, specifying either the ID or name of the container from you which want to create it:
>
> ```bash
>  $ docker commit keen_gauss ubuntu_testbed
> ```
>
> We supplied the name of our container and called the resulting image `ubuntu_testbed`.
>
> Docker images command to see the image you’ve just created:
>
> ```bash
> $ docker images
> ```

### Dockerfile Method

The Dockerfile method is a three-step process whereby you create the Dockerfile and add the commands you need to assemble the image.

| Command    | Purpose                                                                                                                                     |
| ---------- | ------------------------------------------------------------------------------------------------------------------------------------------- |
| FROM       | To specify the parent image.                                                                                                                |
| WORKDIR    | To set the working directory for any commands that follow in the Dockerfile.                                                                |
| RUN        | To install any applications and packages required for your container.                                                                       |
| COPY       | To copy over files or directories from a specific location.                                                                                 |
| ADD        | As COPY, but also able to handle remote URLs and unpack compressed files.                                                                   |
| ENTRYPOINT | Command that will always be executed when the container starts. If not specified, the default is `/bin/sh -c`                               |
| CMD        | Arguments passed to the entrypoint. If ENTRYPOINT is not set (defaults to /bin/sh -c), the CMD will be the commands the container executes. |
| EXPOSE     | To define which port through which to access your container application.                                                                    |
| LABEL      | To add metadata to the image.                                                                                                               |

### Example

> ```bash
> # Use the official Ubuntu 18.04 as base
> FROM ubuntu:18.04
> # Install nginx and curl
> RUN apt-get update &&
> apt-get upgrade -y &&
> apt-get install -y nginx curl &&
> rm -rf /var/lib/apt/lists/*
> ```
>
> Use the Docker build command to create your Docker image. Use the -t flag to set an image name and tag:
>
> ```bash
> $ docker build -t my-nginx:0.1
> ```

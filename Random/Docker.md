## [Docker](https://docs.docker.com/get-started/overview/)

- Docker provides the ability to package and run an application in a loosely isolated environment called a container.
- `Container` is a standalone executable package of a piece of software that includes everything to run it.
- Docker provides tooling and a platform to manage the lifecycle of your containers:

  - Develop your application and its supporting components using containers.
  - The container becomes the unit for distributing and testing your application.
  - When you’re ready, deploy your application into your production environment, as a container or an orchestrated service. This works the same whether your production environment is a local data center, a cloud provider, or a hybrid of the two.

### Uses

- Docker streamlines the `development lifecycle by allowing developers to work in standardized environments using local containers which provide your applications and services. Containers are great for `continuous integration and continuous delivery (CI/CD)` workflows.
- Docker containers can run on a developer’s local laptop, on physical or virtual machines in a data center, on cloud providers, or in a mixture of environments.
- Running more workloads on the same hardware. Cost-effective alternative to a hypervisor-based virtual machine.

### Docker architecture

![Docker architecture](../assests/docker-arch.svg)

> #### Docker Daemon (dockerd)
>
> It is a persistent background process that manages the docker images, containers, network, and storage volumes. Constantly listens for Docker API requests and processes them.

> #### The Docker Client
>
> The Docker client (docker) is the primary way that many Docker users interact with Docker. When you use commands such as docker run, the client sends these commands to Dockerd, which carries them out. The docker command uses the Docker API. The Docker client can communicate with more than one daemon.

> #### Docker registries
>
> A Docker registry stores Docker images. Docker Hub is a public registry that anyone can use, and Docker is configured to look for images on Docker Hub by default. You can even run your private registry.
>
> When you use the `docker pull` or `docker run` commands, the required images are pulled from your configured registry. When you use the `docker push` command, your image is pushed to your configured registry.

> #### Docker objects
>
> A Docker registry stores Docker images. Docker Hub is a public registry that anyone can use, and Docker is configured to look for images on Docker Hub by default. You can even run your private registry.
>
> When you use the `docker pull` or `docker run` commands, the required images are pulled from your configured registry. When you use the `docker push` command, your image is pushed to your configured registry.

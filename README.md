# CollaborativeCoding101

# Table of contents

- [CollaborativeCoding101](#collaborativecoding101)
- [Table of contents](#table-of-contents)
- [Introduction](#introduction)
- [Containers](#containers)
    - [What is a container](#what-is-a-container)
    - [Containers and the cloud](#containers-and-the-cloud)
    - [Containers and storing information.](#containers-and-storing-information)
- [Docker](#docker)
    - [Docker images](#docker-images)
    - [Docker files](#docker-files)
    - [Docker swarm, compose and kubernetes](#docker-swarm-compose-and-kubernetes)
- [DevContainers](#devcontainers)
    - [What is a dev container?](#what-is-a-dev-container)
    - [Setting up a dev container](#setting-up-a-dev-container)
    - [Using a dev container](#using-a-dev-container)
    - [Customizing DevContainers](#customizing-devcontainers)
- [Github](#github)
  - [Using what we've learnt](#using-what-weve-learnt)
  - [Github and other tools](#github-and-other-tools)
- [Further reading and resources](#further-reading-and-resources)
- [License](#license)
- [Contributions](#contributions)

# Introduction

It Works on My Machine": Docker, GitHub, and DevContainers for Collaborative Code Consistency  Well, we can't sell your machine, but we can certainly sell your code! This workshop focuses on developing with Docker, GitHub, and DevContainers, guiding you in integrating these tools into your ongoing projects.


# Containers
### What is a container

"Containers are packages of software that contain all of the necessary elements to run in any environment." 
> [Google Cloud](https://cloud.google.com/learn/what-are-containers)

There are multiple tools to manage containers, such as [podman](https://podman.io/) or [docker](https://docs.docker.com/). In essence though, most should be the same in terms of what they do.

My go to is docker, so that's what I'll be refrencing in this workshop.

### Containers and the cloud

So why are containers good in the first place? Well, they can be compared to a virtual machine(VM), but they are more lightweight. This means that they are easier to move around, and can be run on any machine that has the container runtime installed. Unlike a VM, containers don't emulate hardware, but instead share the host OS's kernel.

![VM demand compared to docker on ](https://imgs.search.brave.com/BS_f9ClT8Vlc7yKX_L_DWabRpMW9z9mcneEfRVQD718/rs:fit:860:0:0/g:ce/aHR0cHM6Ly9jZG4u/dHRndG1lZGlhLmNv/bS9ybXMvb25saW5l/SW1hZ2VzL3dpbmRv/d3Nfc2VydmVyLXZp/cnR1YWxfbWFjaGlu/ZXNfdnNfY29udGFp/bmVyc19tb2JpbGUu/cG5n)


### Containers and storing information. 

There are 3 types of storage that one should have heard about when working with containers. They are: 
- Volume 
- Bind mount 
- tmpfs 

*Volume*
A volume is created and managed by docker, but is isolated from the host.

*Bind mount*
Any area of the host file system. 

*tmpfs* 
An area of memory outside the container, this can be shared but is only temporary. I.e, removed when the container is stopped.  

# Docker 

If you want to learn more about docker, there is a easy tro follow guide on their website. [Docker](https://docs.docker.com/get-started/)

### Docker images

![Showing the docker achitecture](https://imgs.search.brave.com/WAcjOFJO8OKQ-zI-VnMGgc7PUAtsAV6O2MXxlti0iQI/rs:fit:860:0:0/g:ce/aHR0cHM6Ly93d3cu/Y2hlcnJ5c2VydmVy/cy5jb20vdjMvYXNz/ZXRzL2Jsb2cvMjAy/Mi0xMi0yMC8wMi5w/bmc)

### Docker files
Docker, and most containers to my knowledge, use the yaml file format to define how the container should be built. 

```YAML

FROM node:18-alpine
WORKDIR /app
COPY . .
RUN yarn install --production
CMD ["node", "src/index.js"]
EXPOSE 3000

```

[Example of a small docker file](./example01/Dockerfile)
[Example of a flask docker file](https://github.com/Uplink036/FlaskTemplate)
[Example of a large docker file](https://github.com/cdrx/docker-pyinstaller)


### Docker swarm, compose and kubernetes
[Docker swarm](https://docs.docker.com/engine/swarm/swarm-tutorial/create-swarm/)
[Docker compose](https://docs.docker.com/compose/)
 - [Example](./example02/docker-compose.yml)



# DevContainers
### What is a dev container? 
"A development container (or dev container for short) allows you to use a container as a full-featured development environment. It can be used to run an application, to separate tools, libraries, or runtimes needed for working with a codebase, and to aid in continuous integration and testing. Dev containers can be run locally or remotely, in a private or public cloud, in a variety of supporting tools and editors."
> https://containers.dev/

### Setting up a dev container

If you're using Visual Studio Code, it's easy to use dev containers in your project right now. There is an exstenstion that you can install, and then you can use the .devcontainer.json file to define how the container should be built.

Your filesystem could look something like this:

```Filesystem 
- .devcontainer
    - devcontainer.json
    - Dockerfile
- src
    - index.js
- package.json
```

The devcontainer.json file will then look something like this:

```JSON
{
    "name": "DevContainer-Alpine-Node",
    "build": {
        "dockerfile": "Dockerfile",
    },
}
```

The Dockerfile could look something like this:

```Dockerfile
FROM mcr.microsoft.com/devcontainers/base:alpine-3.19
```

Plenty of templates to choose from found [here](https://containers.dev/templates).


Don't feel like setting up all this on your own? Don't worry, the dev extension has got you covered. By pressing 

```Ctrl + Shift + P``` (Show all commands shortcut)

and then typing 

```Dev Containers: Add Development Container Configuration Files...```

You can get your own. 

### Using a dev container

Once you have your dev container set up, you can use it by pressing 

```Ctrl + Shift + P``` 

and then typing 

```Dev Containers: Reopen in Container```

and then all you have to do is wait a bit and you're in your dev container.

### Customizing DevContainers
# Github
## Using what we've learnt

[Example](https://github.com/JulianFrattini/cira)

## Github and other tools

[Github actions](https://github.com/features/actions)
- Linting
- Code quality
- Test coverage
- Working version

[Live-share](https://visualstudio.microsoft.com/services/live-share/)
- Direct collaboration
- Real-time editing
- Shared environment


# Further reading and resources

[VScode DevContainers](https://code.visualstudio.com/docs/devcontainers/containers)
[Docker getting started guide](https://docs.docker.com/get-started/)
[MySQL and Docker](https://dev.mysql.com/doc/mysql-installation-excerpt/8.3/en/docker-mysql-getting-started.html)
[Want a minecraft server in a container?](https://github.com/itzg/docker-minecraft-server)

# License

This project uses a MIT license, see [here](./LICENSE). It's not much of software project, but feel free to do anything you like with it. 

# Contributions

[Oliver Sjödin](https://github.com/Uplink036) - [Author](https://github.com/Uplink036/CollaborativeCoding101)
[Andreas Bauer](https://github.com/andreas-bauer) - [Helped find an example](https://github.com/JulianFrattini/cira)
[IONOS] - [For the docker whale image](https://www.ionos.com/digitalguide/server/configuration/docker-tutorial-installation-and-first-steps/)
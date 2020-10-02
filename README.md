# Drone Runner Dockerized

- [Drone Runner Dockerized](#drone-runner-dockerized)
  - [Overview](#overview)
  - [Requirements](#requirements)
  - [Installation](#installation)
  - [Environment Variables](#environment-variables)

---

## Overview

This repository contains a template to deploy a [Drone Runner](https://drone.io/) using [Docker Compose](https://docs.docker.com/compose/) on a single machine running [Docker](https://www.docker.com/).

## Requirements

- [Docker](https://www.docker.com/)
- [Docker Compose](https://docs.docker.com/compose/)
- [Git](https://git-scm.com/)
- Text editor of your choice (e.g. [Vim](https://www.vim.org/))

## Installation

Clone the repository:

```sh
$ git clone https://github.com/cedrichopf/drone-runner-dockerized.git
Cloning into 'drone-runner-dockerized'...
```

Create a copy of the example configuration files:

```sh
# Drone Configuration
$ cp example.env .env
# Custom Docker Compose Configuration
$ cp override.example.yml docker-compose.override.yml
```

Configure the Drone deployment by adapting the environment variables in the `.env` file:

```sh
$ vim drone.env
```

Further information about the available environment variables can be found here: [Environment Variables](#environment-variables)

Configure the docker-compose.override.yml file:

```sh
$ vim docker-compose.override.yml
```

Download the Docker images and start the services using docker-compose:

```sh
$ docker-compose pull
$ docker-compose up -d
```

Finally, the Drone runner should be connected to the Drone Server and able to run builds.

## Environment Variables

The following table contains an overview of the environment variables which can be configured in the `drone.env` file.

| Environment Variable  | Example                            | Description                     |
| --------------------- | ---------------------------------- | ------------------------------- |
| COMPOSE_PROJECT_NAME  | `drone-runner`                     | Project name for docker-compose |
| DRONE_RPC_PROTO       | `https`                            | Protocol of Drone Server        |
| DRONE_RPC_HOST        | `drone.example.com`                | Hostname of Drone Server        |
| DRONE_RPC_SECRET      | `aad597387ba4e1d5a40c29e922a6b06b` | Drone RPC Secret (from Server)  |
| DRONE_RUNNER_CAPACITY | `2`                                | Number of concurrent pipelines  |
| DRONE_RUNNER_NAME     | `my-drone-runner`                  | Name of the Drone runner        |

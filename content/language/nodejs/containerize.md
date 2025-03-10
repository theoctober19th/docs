---
title: Containerize a Node.js application
keywords: node.js, node, containerize, initialize
description: Learn how to containerize a Node.js application.
redirect_from:
  - /get-started/nodejs/build-images/
  - /language/nodejs/build-images/
  - /language/nodejs/run-containers/
---

## Prerequisites

* You have installed the latest version of [Docker
  Desktop](../../get-docker.md).
* You have a [git client](https://git-scm.com/downloads). The examples in this
  section use a command-line based git client, but you can use any client.

## Overview

This section walks you through containerizing and running a Node.js
application.

## Get the sample application

Clone the sample application to use with this guide. Open a terminal, change
directory to a directory that you want to work in, and run the following command
to clone the repository:

```console
$ git clone https://github.com/docker/docker-nodejs-sample
```

## Test the application without Docker (optional)

You can test the application locally without Docker before you continue building
and running the application with Docker. This section requires you to have
Node.js 18 or later installed on your machine. Download and install
[Node.js](https://nodejs.org/).

Open a terminal, change directory to the `docker-nodejs-sample` directory, and
run the following command to install the packages.

```console
$ npm install
```

When the packages have finished installing, run the following command to start
the application.

```console
$ node src/index.js
```

Open a browser and view the application at [http://localhost:3000](http://localhost:3000). You should see a simple todo application.

In the terminal, press `ctrl`+`c` to stop the application.

## Initialize Docker assets

Now that you have an application, you can use `docker init` to create the
necessary Docker assets to containerize your application. Inside the
`docker-nodejs-sample` directory, run the `docker init` command in a terminal.
Refer to the following example to answer the prompts from `docker init`.

```console
$ docker init
Welcome to the Docker Init CLI!

This utility will walk you through creating the following files with sensible defaults for your project:
  - .dockerignore
  - Dockerfile
  - compose.yaml

Let's get started!

? What application platform does your project use? Node
? What version of Node do you want to use? 18.0.0
? Which package manager do you want to use? npm
? What command do you want to use to start the app: node src/index.js
? What port does your server listen on? 3000
```

You should now have the following contents in your `docker-nodejs-sample`
directory.

   ```
   ├── docker-nodejs-sample/
   │ ├── spec/
   │ ├── src/
   │ ├── .dockerignore
   │ ├── .gitignore
   │ ├── compose.yaml
   │ ├── Dockerfile
   │ ├── package-lock.json
   │ ├── package.json
   │ └── README.md
   ```

To learn more about the files that `docker init` added, see the following:
 - [Dockerfile](../../engine/reference/builder.md)
 - [.dockerignore](../../engine/reference/builder.md#dockerignore-file)
 - [compose.yaml](../../compose/compose-file/_index.md)

## Run the application

Inside the `docker-nodejs-sample` directory, run the following command in a
terminal.

```console
$ docker compose up --build
```

Open a browser and view the application at [http://localhost:3000](http://localhost:3000). You should see a simple todo application.

In the terminal, press `ctrl`+`c` to stop the application.

### Run the application in the background

You can run the application detached from the terminal by adding the `-d`
option. Inside the `docker-nodejs-sample` directory, run the following command
in a terminal.

```console
$ docker compose up --build -d
```

Open a browser and view the application at [http://localhost:3000](http://localhost:3000).

You should see a simple todo application.

In the terminal, run the following command to stop the application.

```console
$ docker compose down
```

For more information about Compose commands, see the [Compose CLI
reference](../../compose/reference/_index.md).

## Summary

In this section, you learned how you can containerize and run your Node.js
application using Docker.

Related information:
 - [Dockerfile reference](../../engine/reference/builder.md)
 - [Build with Docker guide](../../build/guide/index.md)
 - [.dockerignore file reference](../../engine/reference/builder.md#dockerignore-file)
 - [Docker Compose overview](../../compose/_index.md)

## Next steps

In the next section, you'll learn how you can develop your application using
containers.

{{< button text="Develop your application" url="develop.md" >}}
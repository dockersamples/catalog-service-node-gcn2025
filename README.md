# Container-supported development demo

This repo provides a project to help demonstrate the idea of "container-supported development"... using containers to enhance developer productivity, even if the main app itself is _not_ in a container.

## Trying it out

This project is configured to run with the app running either natively (using Node installed on the machine) or in a container.

### Running natively

1. Ensure you have Node and yarn installed on your machine.

2. Start all of the application dependencies

    ```console
    docker compose up
    ```

3. Install the app dependencies and start the main app

    ```console
    yarn install
    yarn dev
    ```

### Running completely in containers

The `compose.native.yaml` file defines an additional `app` service that will run the application in the container. 

The code is currently mounted into the app container, theoretically allowing for hot reloading. However, there is a limitation for WSL environments where the filesystem event isn't propagated, preventing nodemon from seeing the file change event.

1. Start the app using Compose, but specifying the native file

    ```console
    docker compose -f compose.native.yaml
    ```

## Utilities

Once the development environment is up and running, the following URLs can be leveraged:

- [http://localhost:5050](http://localhost:5050) - [pgAdmin](https://www.pgadmin.org/) to visualize the database
- [http://localhost:8080](http://localhost:8080) - [kafbat](https://github.com/kafbat/kafka-ui) to visualize the Kafka cluster

The `compose.traefik.*` variants make the previous accessible using hostnames, instead of hard-to-remember ports.

- [http://db.localhost](http://db.localhost) - [pgAdmin](https://www.pgadmin.org/) to visualize the database
- [http://kafka.localhost](http://kafka.localhost) - [kafbat](https://github.com/kafbat/kafka-ui) to visualize the Kafka cluster

### Helper scripts

In the `dev/scripts` directory, there are a few scripts that can be used to interact with the REST API of the application.

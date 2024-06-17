# TwinCobot-ALS-Docker (Cross-plateform HUT Only Version)

## Prerequisites

1. Linux OS. It's highly recommended to have a Linux operating system to avoid different system instabilities.
2. Docker and Docker-compose installed. OpenHab container works in a containerization system based on [Docker](https://docs.docker.com/engine/install/).
The setup requires docker-compose to launch the OpenHab container with specific parameters.

## How to install and deploy the DT in OpenHab Container?

- Plug/turn-on devices to the machine where OpenHab will be deployed.
- Create the OpenHab user (does not work on macOS):

```sh
sudo useradd -r -s /sbin/nologin openhab
```

- Add your regular user to the openhab group:

```sh
sudo usermod -aG openhab $USER
```

- Set rights for configuration backups:

```sh
sudo chown -R openhab:openhab ./oh_backups
```

- Run the container with docker compose in detached mode:

```sh
docker compose up -d
```

If you have a Z-wave or Zigbee connector, uncomment the commented lines in `compose.yml` and do the following:

```sh
docker exec -d twincobot-als-docker-openhab-1  /bin/chmod o+rw /dev/ttyACM0 /bin/chmod o+rw /dev/ttyACM0
```

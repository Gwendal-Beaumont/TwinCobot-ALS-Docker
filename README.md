# TwinCobot-ALS-Docker (HUT Only Version)

## Prerequisites 

1. Linux OS. It's hihgly recommended to have a Linux operating system to avoid different system instabilities. 
2. Docker and Docker-compose installed. OpenHab container works in a containerization system based on [Docker](https://docs.docker.com/engine/install/). 
The setup requires docker-compose to launch the OpenHab container with specific parameters. 

## How to install and deploy the DT in OpenHab Container ? 

1. Plug/turn-on devices to the machine where OpenHab will be deployed
2. Create the OpenHab user : `sudo useradd -r -s /sbin/nologin openhab`
3. Add your regular user to the openhab group : `sudo usermod -aG openhab $USER`
4. Set rights for configuration backups : `sudo chown -R openhab:openhab ./oh_backups`
5. Run the container with docker compose: `docker compose up -d`
6. Share the ttyACM0 with the container (for Z-wave/Zigbee keys) : `docker exec -d twincobot-als-docker-openhab-1  /bin/chmod o+rw /dev/ttyACM0 /bin/chmod o+rw /dev/ttyACM0`

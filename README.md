# My Mediabox

## Setup

### User

I run everything as a single user `media`, and in my setup that is UID/GID 1001

You will likely need to change the docker-compose file to match your UID/GID.

In the `media` home directory, I check this project out to create ~/mediabox

Then you need directories for each containers config - the containers will populate the directories
with the right files on startups, but you need the directories there for the container to start

You can do this from the `mediabox` directory with this

`mkdir -p {deluge,jackett,plex,radarr,sonarr,heimdall,overseer}/config`

### Storage

I have different disks mounted for this, but the structure required for this is:

/data/{TV,movies/incoming}

you can quickly create this if you don't need to mount disks with:

`mkdir -p /data/{TV,movies,incoming}`


On my system, the `fstab` bits are:

``` text
/dev/sda1 /data/movies ext4 rw,relatime 0 0
/dev/sdb1 /data/TV ext4 rw,relatime 0 0
/dev/sde1 /data/incoming ext4 rw,relatime 0 0
```





## Operations

### Ports

|Service|Port|
|-------|----|
| Deluge | 8112 |
| Jackett | 9117 |
| Plex | 32400 |
| Radarr | 7878 |
| Sonarr | 8989 |
| Heimdall | 80/443 |
| Overseer | 5055 |

For Plex to work, you need to forward the port from the internet to the container on your router.

### Starting things up

`docker-compose up -d`

### Updating containers

```
docker-compose pull
docker-compose up -d
```

## Some useful bits

* yamllint the docker-compose file so I don't screw up more:
  `sudo docker run -it --rm -v "$(pwd):/workdir" ghcr.io/ffurrer2/yamllint docker-compose.yml`

* convert `docker run` commands into `docker-compose` YAML: [https://www.composerize.com/](composerize.com)

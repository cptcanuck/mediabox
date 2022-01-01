# My Mediabox

# Setup

## Storage

I have different disks mounted for this, but the structure required for this is:

/
 - data/
   - TV
   - movies
   - incoming

you can quickly create this if you don't need to mount disks with:

`mkdir -p /data/{TV,movies,incoming}`




## Operations

### Starting things up

`docker-compose up -d`

## Updating containers

`docker-compose pull`
`docker-compuse up -d`

## Easy Links

This stack runs nginx with a simple static index.html that you can use to quickly get to the various interfaces.  

If your server doesn't have the IP `192.168.9.144` then you'll need to update the index.html file

# Some useful bits:

* yamllint the docker-compose file so I don't screw up more:
  `sudo docker run -it --rm -v "$(pwd):/workdir" ghcr.io/ffurrer2/yamllint docker-compose.yml`

* convert `docker run` commands into `docker-compose` YAML: https://www.composerize.com/

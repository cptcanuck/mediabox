My Mediabox



## Operations

### Starting things up

`docker-compose up -d`

## Updating containers

`docker-compose pull`
`docker-compuse up -d`


Some useful bits:

* yamllint the docker-compose file so I don't screw up more:
  `sudo docker run -it --rm -v "$(pwd):/workdir" ghcr.io/ffurrer2/yamllint docker-compose.yml`

* convert `docker run` commands into `docker-compose` YAML: https://www.composerize.com/

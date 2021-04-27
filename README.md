*NOTE:* Supported images are available in the [official image library](https://hub.docker.com/_/neo4j/) on Docker Hub.
Please use those for production use.

If you want to see the exact Dockerfile and entrypoint source code that is included in any Neo4j image, you can view them here:

https://github.com/neo4j/docker-neo4j-publish

# Using the Neo4j Docker Image

Documentation for the Neo4j image can be found [here](https://neo4j.com/docs/operations-manual/current/deployment/single-instance/docker/).

You can start a Neo4j container like this:

```
docker run \
    --publish=7474:7474 --publish=7687:7687 \
    --volume=$HOME/neo4j/data:/data \
    --volume=$HOME/neo4j/logs:/logs \
    neo4j:latest
```

To start a Neo4j Enterprise Edition container, you can run:

```
docker run \
    --publish=7474:7474 --publish=7687:7687 \
    --env=NEO4J_ACCEPT_LICENSE_AGREEMENT=yes \
    --volume=$HOME/neo4j/data:/data \
    --volume=$HOME/neo4j/logs:/logs \
    neo4j:enterprise
```

Mounting the `/data` and `/logs` folder is optional, 
but it means that data can persist between closing and reopening Neo4j containers.

# Neo4j images for ARM64

We provide unsupported and untested builds of ARM64 Neo4j community edition from 4.0.0 and onwards. 
These are unsuitable for production use, but may be useful for experimentation or hobbyists. 

They are available on Docker hub at:

https://hub.docker.com/r/neo4j/neo4j-arm64-experimental


The images take the name format `neo4j/neo4j-arm64-experimental:<VERSION>-arm64`.
Example usage:

```shell script
docker run \
    --publish=7474:7474 --publish=7687:7687 \
    --volume=$HOME/neo4j/data:/data \
    --volume=$HOME/neo4j/logs:/logs \
    neo4j/neo4j-arm64-experimental:4.1.0-arm64
```


# Building and Developing the Neo4j Docker Image

See [DEVELOPMENT.md](DEVELOPMENT.md)

# Getting support and contributing

For bug reports and feature requests, please create issues and pull requests against this Github repository.

If you need guidance with using Neo4j you can ask questions here: https://community.neo4j.com/

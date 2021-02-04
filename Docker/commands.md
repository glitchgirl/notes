# Commands

- An image is the application we want to run, while a container is an instance of that image running as process. App binaries and dependencies, metadata, an ordered collection of root file systems changes and the corresponding execution params for use within a container runtime.
- Caching image layers saves space.
- p 80(host):80(container)

## What happens in docker container run?

1. looks for that image locally in cache
2. then looks in that remote image repo (docker hub)
3. downloads the latest version (unless specified)
4. creates new container based on that image and prepares to start
5. gives a virtual IP on a private network inside docker engine
6. opens up ports if asked
7. starts container by using the cmd in the dockerfile

- e = enviornment variables
- d (detach runs in this the background, default is foreground)
- name

- `docker container run --rm -it <name:version> bash`

- Even if two containers have the same container port they won't have port conflicts due to the fact that each container gets its own IP behind the NAT

- inspect/stats
- shell inside containers
- using static IPs is an anti-pattern

## Service Types

- Cluster IP

  - single internal virtual IP
  - only reachable from within cluster
  - pods can reach service on apps

- Node port

  - high port allocated on each node

- Load Balancer

  - controls external endpoint
  - only infra provider
  - only for external stuff

- External Name
  - adds Cname to coreDNS creating a cluster IP service - expose

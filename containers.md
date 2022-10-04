# Docker alternatives
- containerd
- rkt (rocket) from CoreOS
- mesos
- lxc
- CRI for Kubernetes

# LXD
`lxc image list images`
`lxc launch images:ubuntu/20.04 first`
`lxc launch images:ubuntu/20.04 second`
`lxc copy first third`

## Inspect containers
`lxc list`
`lxc start third`
`lxc info first`

## Stop and delete containers
`lxc stop|delete CONTAINER_NAME [--force]`

## Instance configuration
`lxc launch images:ubuntu/20.04 limited -c limits.cpu=1 -c limits.memory=192.MiB`
`lxc config set limited limits.memory=128MiB`
`lxc config show limited`
`lxc exec first -- free -m`
`lxc exec first -- nproc`

## Interact with a container
`lxc exec first -- bash`
`lxc exec first -- apt update`

## Access files from container
`lxc file pull first/etc/hosts .`
`lxc file push hosts first/etc/hosts`
`lxc file pull first/var/log/syslog - | less`

## Snapshots
`lxc snapshot first clean`
`lxc restore first clean`
`lxc delete first/clean`

# Podman

## Set rootful mode

This machine is currently configured in rootless mode. If your containers
require root permissions (e.g. ports < 1024), or if you run into compatibility
issues with non-podman clients, you can switch using the following command: 

```sh
$ podman machine set --rootful
```

## Install Docker API socker

API forwarding listening on: /Users/sa23xj/.local/share/containers/podman/machine/podman-machine-default/podman.sock

The system helper service is not installed; the default Docker API socket
address can't be used by podman. If you would like to install it run the
following commands:

```sh
$ sudo /usr/local/Cellar/podman/4.1.1/bin/podman-mac-helper install
$ podman machine stop; podman machine start
```

You can still connect Docker API clients by setting DOCKER_HOST using the
following command in your terminal session:

```
export DOCKER_HOST='unix:///Users/sa23xj/.local/share/containers/podman/machine/podman-machine-default/podman.sock'
```

## Setting up HTTP Proxy variables for podman

Podman reads the environment variables for HTTP_PROXY information. HTTP_PROXY information should be configured as an environment variable for user running as podman or can be configured under /etc/profile.d

Example in /etc/profile.d/http_proxy.sh

```
export HTTP_PROXY=http://192.168.0.1:3128
export HTTPS_PROXY=http://192.168.0.1:3128
```

# Installation

## Deployment

1. Copy the configuration template into the `/etc/promtail/promtail.yml` location.
2. Copy the `docker-compose.yml` template into your project folder and start the container.

## Configuration

Configure your settings in the `/etc/promtail/promtail.yml` file.

_For more info visit:_ [Official Promtail Installation Documentation](https://grafana.com/docs/loki/latest/installation/docker/)

# Using Docker Driver

## Installation

The Docker plugin must be installed on each Docker host that will be running containers you want to collect logs from.

Run the following command to install the plugin:

```
docker plugin install grafana/loki-docker-driver:latest --alias loki --grant-all-permissions
```

To check installed plugins, use the docker plugin ls command. Plugins that have started successfully are listed as enabled:

```
docker plugin ls
```

## Configuration

The Docker plugin is configured using the standard Docker logging configuration options. The following example shows how to configure the plugin using the Docker CLI:

```
docker run --log-driver=loki --log-opt loki-url=http://localhost:3100/loki/api/v1/push test
```

### Change the default logging driver

To change the default logging driver, edit the daemon.json file, which is usually located in /etc/docker/ on Linux hosts or C:\ProgramData\docker\config\daemon.json on Windows server hosts.

Add or edit the log-driver and log-opts sections of the file to match the following example:

```
{
  "log-driver": "loki",
  "log-opts": {
    "loki-url": "http://localhost:3100/loki/api/v1/push"
  }
}
```

Save the file and restart the Docker daemon.

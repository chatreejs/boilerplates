# Installation

## Create App Directory

```bash
mkdir -p /data/cloudflared && chmod 777 /data/cloudflared
```

## Authorize Cloudflare Tunnel

```bash
docker run --rm -it -v /data/cloudflared:/home/nonroot/.cloudflared/ cloudflare/cloudflared:latest tunnel login
```

## Create Cloudflare Tunnel

```bash
docker run --rm -it -v /data/cloudflared:/home/nonroot/.cloudflared/ cloudflare/cloudflared:latest tunnel create <TUNNEL_NAME>
```

## Create Cloudflare Tunnel Configuration

```bash
cat << EOF > /data/cloudflared/config.yml
tunnel: <TUNNEL_NAME>
credentials-file: /home/nonroot/.cloudflared/credentials-file.json
EOF
```

See [here](https://developers.cloudflare.com/cloudflare-one/connections/connect-apps/install-and-setup/tunnel-guide/local/local-management/ingress/) for more information about ingress rules and how they can be configured

## Deploy Cloudflare Tunnel

Copy the `docker-compose.yml` template into your project folder and start the container.

# Home Assistant

Stack funcional en Orange pi pc

```yaml
version: '3'
services:
  homeassistant:
    container_name: homeassistant
    image: "ghcr.io/home-assistant/home-assistant:stable"
    volumes:
      - /path-to-config/home-assistant/config:/config
      - /etc/localtime:/etc/localtime:ro
      - /var/run/docker.sock:/var/run/docker.sock
    restart: unless-stopped
    privileged: true
    network_mode: host
```

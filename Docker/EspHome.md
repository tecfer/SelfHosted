# EspHome
Stack funcional en Orange pi pc

```yaml
version: '3'
services:
  esphome:
    container_name: esphome
    image: esphome/esphome
    volumes:
      - /path-to-config/esphome/config:/config
      - /etc/localtime:/etc/localtime:ro
    restart: always
    privileged: true
    network_mode: host
```

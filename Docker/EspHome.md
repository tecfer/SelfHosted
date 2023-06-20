# EspHome

```yaml
version: '3'
services:
  esphome:
    container_name: esphome
    image: esphome/esphome
    volumes:
      - /path/to/esphome/config:/config
      - /etc/localtime:/etc/localtime:ro
    restart: always
    privileged: true
    network_mode: host
```

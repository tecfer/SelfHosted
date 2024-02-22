# Influxdb Grafana

Docker para pruebas con home assistant sin seguridad

```yaml
version: '3'
services:
  influxdb:
    container_name: influxdb
    image: influxdb:1.8.10
    volumes:
      - /path-to-config/influxdb:/var/lib/influxdb
    ports:
      - 8086:8086
    environment:
      INFLUXDB_DB: homeassistant
    restart: unless-stopped
  grafana:
    container_name: grafana
    image: grafana/grafana:latest
    volumes:
      - /path-to-config/grafana:/var/lib/grafana
    depends_on:
      - influxdb
    ports:
      - 3000:3000
    environment:
      - GF_AUTH_DISABLE_LOGIN_FORM=true
      - GF_AUTH_ANONYMOUS_ENABLED=true
      - GF_AUTH_ANONYMOUS_ORG_ROLE=Admin
      - GF_SECURITY_ALLOW_EMBEDDING=true
    restart: unles
```

# Servidor mqtt mosquito

```yaml
version: '3.8'
services:
  mqtt:
    container_name: mosquitto
    image: eclipse-mosquitto
    ports:
      - "1883:1883"
      - "9001:9001"
    volumes:
      - /path/to/mosquitto/config:/mosquitto/config
      - /path/to/mosquitto/logs:/mosquitto/log
      - /path/to/mosquitto/data:/mosquitto/data
    restart: always
    environment:
      - TZ=Europe/Madrid 
```

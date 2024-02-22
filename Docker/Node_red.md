# Node-Red

```yaml
version: '3'
services:    
  node-red:
    image: nodered/node-red:latest
    environment:
      - TZ=Europe/Amsterdam
    ports:
      - "1880:1880"
    volumes:
      - /path-to-config/nodered/config:/data
```
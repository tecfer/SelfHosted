# Metube
Stack funcional en Orange pi pc

```yaml
version: "3"
services:
  metube:
    image: ghcr.io/alexta69/metube
    container_name: metube
    restart: unless-stopped
    ports:
      - "8081:8081"
    volumes:
      - /path-to-folder/metube:/downloads

```

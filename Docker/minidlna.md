


    # MiniDLNA
Stack minidlna funcional en un contenedor Alpine-Docker LXC Proxmox

```yaml
version: "3.8"

services:
  minidlna:
    image: vladgh/minidlna:latest
    container_name: minidlna
    network_mode: "host"  # Modo host para recibir paquetes UPnP
    volumes:
      - /path-to-media:/media    # Directorio para archivos de video,audio...
      - /path-to-data/minidlna:/config    # Configuración persistente
    environment:
      - MINIDLNA_MEDIA_DIR=/media  
      - MINIDLNA_FRIENDLY_NAME=NOMBRE    # Nombre amigable del servidor
    restart: unless-stopped
```

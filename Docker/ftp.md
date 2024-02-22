# Simple FTP

Stack funcional en Orange pi pc
```yaml
version: '3.7'
services:
  vsftpd:
    image: panubo/vsftpd
    environment:
      - FTP_USER=USUARIO_FTP
      - FTP_PASSWORD=CONTRASEÑA_FTP
    volumes:
      - /path-to-data/FTP/:/srv
    expose:
      - 21
    network_mode: host
```
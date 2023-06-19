# Simple file server

```yaml
version: '3'
services:
  static-file-server:
    image: halverneus/static-file-server:latest
    ports:
      - "8080:8080"
    volumes:
      - /path/to/data:/web
````
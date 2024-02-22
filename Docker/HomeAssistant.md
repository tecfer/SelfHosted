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



## Arrancar y parar contenedores Docker desde Home Assistant

Lo que vamos a hacer es crear una tarjeta en Home assistant con dos botones que nos sirvan para arrancar y parar contenedores docker que tenemos en la misma instalación de docker, de forma que no hará falta ejecutar un comando, o entrar en portainer para arrancar y parar los contenedores.

En el fichero configuration.yaml añadiremos los comando que queremos utilizar de la siguiente forma
```yaml
shell_command:
  start_docker_container: "docker start nombre_del_contenedor"
  stop_docker_container: "docker stop nombre_del_contenedor"
```
Tendremos que sustituir ‘nombre_del_contenedor’ por el que queramos arrancar y parar.

Lo siguiente será añadir la tarjeta necesaria en home assistant para poder pulsar los botones, un ejemplo de tarjeta sería el siguiente.

```yaml
type: entities
entities:
  - type: button
    icon: mdi:file-arrow-up-down
    name: Iniciar Contenedor
    tap_action:
      action: call-service
      service: shell_command.start_docker_container
  - type: button
    icon: mdi:file-cancel-outline
    name: Parar Contenedor
    tap_action:
      action: call-service
      service: shell_command.stop_docker_container
```
Ahora solo falta hacer que home assistant pueda «hablar» con la instalación de docker, para poder esto depende de con que permisos esté funcionando el contenedor de home asistant.

Una forma de hacerlo es añadir el volumen siguiente para que se pueda conectar al shocket

```yaml
-v /var/run/docker.sock:/var/run/docker.sock
```
Esto permitirá al contenedor comunicarse con el daemon de docker

El Docker compose que utilizas en el stack de portainer para arrancar el contenedor podría quedar asi.
```yaml
version: '3'
services:
  homeassistant:
    container_name: homeassistant
    image: "ghcr.io/home-assistant/home-assistant:stable"
    volumes:
      - /path/to/home-assistant/config:/config
      - /etc/localtime:/etc/localtime:ro
      - /var/run/docker.sock:/var/run/docker.sock
    restart: unless-stopped
    privileged: true
    network_mode: host
```
tras actualizar el stack tenemos que habrir una consola en el contenedor y ejecutar el siguiente comando para instalar la utilidad ‘Docker’ dentro del contenedor de home assistant.
```shell
apk add --no-cache docker-cli
```
Ahora después de reiniciar el contenedor de home assistant ya deverías poder arrancar y parar el contenedor con los botones de la tarjeta de Home assistant.

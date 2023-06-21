# SelfHosted

yamls de configuración para diferentes servicios creados con docker y portainer

# Instalación de Docker:
```cmd
curl -fsSL https://get.docker.com -o get-docker.sh
sh get-docker.sh

sudo usermod -aG docker $USER
```

Creación de carpetas para las configuraciones de los containers:

```cmd
sudo mkdir /path_to_data
sudo chown root.docker /path_to_data
sudo chmod 774 /path_to_data
```
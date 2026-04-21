# Instalación de Docker en Ubuntu 24.04 (sin uso de sudo)

## Objetivo
Instalar Docker desde el repositorio oficial, verificar su funcionamiento y configurarlo sin sudo.

## 1. Eliminar instalaciones previas
sudo apt remove docker docker-engine docker.io containerd runc

## 2. Instalar dependencias
sudo apt update
sudo apt install ca-certificates curl gnupg -y

## 3. Agregar clave oficial
sudo install -m 0755 -d /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
sudo chmod a+r /etc/apt/keyrings/docker.gpg

## 4. Agregar repositorio
echo "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu $(. /etc/os-release && echo $VERSION_CODENAME) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

## 5. Instalar Docker
sudo apt update
sudo apt install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin -y

## 6. Verificar
sudo docker run hello-world

## 7. Usar Docker sin sudo
sudo usermod -aG docker $USER
newgrp docker

## 8. Verificar sin sudo
docker run hello-world

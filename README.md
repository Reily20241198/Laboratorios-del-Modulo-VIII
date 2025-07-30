# Laboratorios-del-Modulo-VIII
Practica 2: Instalacion de Portainer
===============================================
   PRÁCTICA #2: INSTALACIÓN DE PORTAINER (1pt)
===============================================

1️⃣ INSTALAR DOCKER (si aún no está instalado)
-----------------------------------------------
sudo dnf install -y dnf-plugins-core
# Instala complementos necesarios para trabajar con repositorios adicionales.

sudo dnf config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
# Agrega el repositorio oficial de Docker.

sudo dnf install -y docker-ce docker-ce-cli containerd.io
# Instala Docker Engine, la CLI de Docker y el runtime containerd.

sudo systemctl start docker
# Inicia el servicio de Docker.

sudo systemctl enable docker
# Habilita Docker para que inicie automáticamente con el sistema.


2️⃣ DESCARGAR E INICIAR PORTAINER
----------------------------------
sudo docker run -d \
  -p 8000:8000 \
  -p 9443:9443 \
  --name portainer \
  --restart=always \
  -v /var/run/docker.sock:/var/run/docker.sock \
  -v portainer_data:/data \
  portainer/portainer-ce

# Este comando ejecuta Portainer en un contenedor:
# -d: en modo background (detached).
# -p: mapea puertos del host al contenedor (8000 y 9443).
# --name: asigna nombre al contenedor.
# --restart=always: reinicia automáticamente si se apaga.
# -v: monta volúmenes para acceso al Docker del host y para persistencia.
# La imagen es portainer/portainer-ce desde Docker Hub.


3️⃣ INGRESAR A LA INTERFAZ WEB
-------------------------------
Navegar a: https://127.0.0.1:9443

- Crear un usuario administrador
- Conectar al Docker local (Docker Engine)
- Acceder a la interfaz visual de administración de contenedores.


4️⃣ DETENER UN CONTENEDOR DESDE PORTAINER
------------------------------------------
- Usar la interfaz web para detener el contenedor nginx de la práctica anterior.
- Luego, visitar el puerto correspondiente en el navegador para comprobar que el servicio ya no está disponible.

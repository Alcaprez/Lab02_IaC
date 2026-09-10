# Laboratorio 02
Hoy utlizaremos docker compose para poder desplegar un servicio web y una base de
datos

STACK Tecnico

API
- Aplicación JAVA dockerizarla (crear la imagen)
- docker pull nmatsui/hello-world-api
- $ docker run -d --rm -p 3000:3000 nmatsui/hello-world-api

BD PostgreSQL
docker run --name some-postgres -e POSTGRES_PASSWORD=mysecretpassword -d postgres

COMANDOS
```bash
docker compose up -d
docker compose down
docker ps
docker image ls
Invoke-WebRequest http://localhost:3001
Invoke-WebRequest http://localhost:3002
```
el invoke es por que yo uso powershell y el curl me perida un uri

CONFIGURACIONES
.env
```
NOMBRE= Tu nombre aqui sin comillas
DBUSER= Tu usuario de tu bd en Postgree
DBPASSWORD= Tu contraseña para ingresar a tu bd
DBNAME= El nombre de tu bd
```
INVESTIGACION SOBRE REDES Y VOLUMENES

Redes
-Bridge (puente): Red interna del mismo host suele ser por default de docker 
sirve para que los contenedores se comuniquen por su nombre
-Host: Red que permite usar la red del host directamente suele ser no muy segura
pero eso lo compensa su gran rendimiento
-Overlay: Red que permite conectar multiples host docker, sirve mas en arquitecturas grandes
como kubernets o swarm
-Macvlan: Red que asigna una direccion MAC al contenedor, sirve para ayudar a algunas aplicaciones
a conectarse directamente
-IPvlan: Red clasica de manejo de IP's sea ipv4 o 6 está construida sobre VLAN, sirve para
tener una configuracion avanzada de redes
-None: Red que aisla al contenedor, sirve para quitar el acceso del contenedor a la red

Volumenes:
-Managed Volumes (Volumenes Manejados): Volumen manejado por el mismo docker suele esta ubicado en
docker/volumes/ y es la mejor opcion en cuanto a persistencia
-Bind Mounts: Volumen que crea directorios del host en el contenedor, lo que permite
acceder directamente y suele estar en la siguiente ser algo así ./ruta/local:/ruta/contenedor
-tmpfs Mounts: Volumen que permite almacenar los datos en la memoria RAM, muy util si se busca
mucho rendimiento y los datos suelen perderse cuando se detiene o apaga el contenedor 


# 🐳 docker-homelab

Bienvenido a mi laboratorio personal de Docker. Este repositorio contiene una colección de archivos `docker-compose.yml` y configuraciones necesarias para desplegar diversos servicios y herramientas de forma rápida, limpia y organizada.

## ¿Qué es Docker?

**Docker** es una plataforma de código abierto que permite automatizar el despliegue de aplicaciones dentro de **contenedores**. 

A diferencia de una máquina virtual, un contenedor no necesita un sistema operativo completo; en su lugar, comparte el núcleo del sistema operativo anfitrión, lo que los hace extremadamente ligeros, rápidos de iniciar y portátiles.

## ¿Por qué usar Docker para laboratorios en lugar de instalaciones locales?

Instalar herramientas directamente en tu sistema operativo (instalación "bare-metal") suele traer problemas a largo plazo. Aquí los beneficios de usar este Homelab:

1. **Aislamiento Total:** Evito "ensuciar" mi sistema operativo principal con dependencias, librerías y bases de datos que solo necesito para pruebas. Cada herramienta vive en su propio entorno aislado.
2. **Control de Versiones:** Puedo probar la versión 14 de una base de datos y la versión 16 simultáneamente sin conflictos de puertos o variables de entorno.
3. **Portabilidad (Infraestructura como Código):** Si cambio de computadora o formateo mi PC, solo necesito clonar este repo y ejecutar `docker-compose up -d`. Todo mi laboratorio estará listo en minutos exactamente igual a como estaba.
4. **Limpieza Absoluta:** Para eliminar una herramienta, solo detengo el contenedor y borro su imagen. No quedan archivos residuales, registros de registro (registry) ni servicios ocultos corriendo de fondo.
5. **Simulación de Redes Realistas:** Docker me permite crear redes virtuales para que los contenedores hablen entre sí, simulando un entorno de producción real en mi propia laptop.

## Estructura del Repositorio

Cada carpeta contiene un proyecto independiente

---
## Cómo usar este laboratorio

1. Asegúrate de tener instalado [Docker Desktop](www.docker.com) o Docker Engine.
2. Clona el repositorio:
   ```bash
   git clone github.com

---

## 🛠️ Docker Cheat Sheet

Esta es una guía rápida de los comandos y flags más utilizados en este laboratorio y en el día a día de un Data Engineer.

### 1. Gestión de Contenedores (Ciclo de Vida)

| Comando | Descripción | Ejemplo |
| --- | --- | --- |
| **`docker run`** | Crea y arranca un nuevo contenedor. | `docker run -d --name mi_db postgres` |
| **`docker ps`** | Lista contenedores activos. (Usa `-a` para ver todos). | `docker ps -a` |
| **`docker logs`** | Muestra la salida (errores/logs) del contenedor. | `docker logs -f postgres_db` |
| **`docker exec`** | Ejecuta un comando dentro de un contenedor vivo. | `docker exec -it postgres_db bash` |
| **`docker stop`** | Detiene un contenedor que está corriendo. | `docker stop postgres_db` |
| **`docker rm`** | Borra un contenedor (debe estar detenido). | `docker rm postgres_db` |
| **`docker images`** | Lista todas las imágenes descargadas en tu PC. | `docker images` |
| **`docker rmi`** | Borra una imagen de tu disco local. | `docker rmi postgres:15` |

---

### 🚀 Comandos de Docker Compose

Ideales para gestionar múltiples servicios (como este Lab) al mismo tiempo:

* **Levantar el entorno:** `docker compose up -d`
* **Detener servicios:** `docker compose stop`
* **Detener y borrar contenedores:** `docker compose down`
* **Borrar TODO (incluyendo volúmenes de datos):** `docker compose down -v`
* **Ver logs de todo el stack:** `docker compose logs -f`

---

### 🚩 Flags (Banderas) Esenciales

Los flags modifican el comportamiento de los comandos. Aquí los más importantes:

| Flag | Nombre | Utilidad |
| --- | --- | --- |
| **`-d`** | *Detached* | Ejecuta el contenedor en segundo plano (no bloquea tu terminal). |
| **`-p`** | *Publish* | Mapea puertos. Formato: `[Host]:[Contenedor]`. Ej: `-p 5433:5432`. |
| **`-v`** | *Volume* | Persiste datos. Formato: `[Nombre/Ruta]:[Ruta_Interna]`. |
| **`-e`** | *Env* | Define variables de entorno (passwords, users, etc.). |
| **`--name`** | *Name* | Asigna un nombre personalizado para no usar el ID aleatorio. |
| **`-it`** | *Interactive* | Te permite interactuar con la terminal interna del contenedor. |
| **`--rm`** | *Remove* | Borra el contenedor automáticamente en cuanto se detiene. |

---

### 🧹 Limpieza del Sistema

Si Docker empieza a ocupar mucho espacio en tu Windows 11, usa estos comandos de "higiene":

```bash
# Borra contenedores detenidos, redes no usadas e imágenes huérfanas
docker system prune

# Borra TODO lo anterior MÁS los volúmenes (¡Cuidado con tus datos!)
docker system prune -a --volumes

```

---

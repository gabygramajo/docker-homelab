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

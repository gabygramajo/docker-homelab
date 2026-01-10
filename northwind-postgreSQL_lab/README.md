# 📊 PostgreSQL Lab: Northwind Database

Este repositorio contiene un entorno de laboratorio basado en **Docker** para practicar SQL y análisis de datos. Despliega de forma automatizada una base de datos **PostgreSQL** con el dataset clásico **Northwind** y una interfaz gráfica **pgAdmin4**.

## 🚀 Tecnologías

* **Docker & Docker Compose**
* **PostgreSQL 15 (Alpine)**
* **pgAdmin4**

---

## 🛠️ Estructura del Proyecto

```text
.
├── init/
│   └── northwind.sql    # Script de carga inicial de la base de datos
├── .env                 # Variables de entorno (No se sube a Git)
│
└── docker-compose.yml   # Orquestación de contenedores

```

---

## ⚙️ Configuración Inicial

1. INSTALAR DOCKER DESKTOP
- https://www.docker.com/products/docker-desktop/


2.  **Clonar el repositorio:**
```bash
git clone {url-repo}
cd {directorio-del-proyecto-descargado}

```

3. Abre el proyecto con tu editor favorito.

4. **Crear el archivo de variables de entorno:**
Crea un archivo llamado `.env` en la raíz y copia el siguiente contenido:
```env
# Postgres Configuration
DB_USER=admin
DB_PASSWORD=admin_pass_123
DB_NAME=DB_LAB

# pgAdmin Configuration
PGADMIN_EMAIL=tu_correo@gmail.com
PGADMIN_PASSWORD=admin_pg_123

```

---

## 🐳 Ejecución

### Primera vez (Carga Automática)

Para levantar el laboratorio por primera vez (estando en la raiz del proyecto), ejecuta en la terminal:

```bash
docker compose up -d

```

> **¿Cómo funciona?** La imagen oficial de Postgres busca cualquier archivo `.sql` dentro de la carpeta `/docker-entrypoint-initdb.d/` (mapeada a nuestro directorio `/init`) y lo ejecuta **solo la primera vez** que se crea el volumen.

---

## 🖥️ Acceso y Configuración de pgAdmin

Una vez que los contenedores estén corriendo, sigue estos pasos para visualizar tus datos:

**1. Acceso a la Interfaz Web**

Abre tu navegador y entra a: http://localhost:8000

**2. Inicio de Sesión**

Ingresa con el correo y la contraseña que definiste en tu archivo `.env` para pgAdmin (`PGADMIN_EMAIL` y `PGADMIN_PASSWORD`).

**3. Conexión con PostgreSQL (Paso Crítico)**

Para ver la base de datos Northwind, debes registrar el servidor de Postgres dentro de pgAdmin:

1. Haz clic derecho en **"Servers" -> Register -> Server...**

2. **Pestaña "General":**

    - Name: `Northwind_DB_Server` (o el nombre que prefieras).

3. **Pestaña "Connection":**

    - Host name/address: `database` (Este es el nombre del servicio en Docker, NO uses localhost).

    - Port: `5432`

    - Maintenance database: `northwind_lab` (o el valor de `DB_NAME` en tu .env).

    - Username: `admin` (o el valor de `DB_USER` en tu .env).

    - Password: La contraseña definida en `DB_PASSWORD`.

4. **Haz clic en Save.**

---

## 🔄 Cómo forzar la recarga del laboratorio

Si realizaste cambios en el script de SQL o quieres resetear la base de datos desde cero, debes eliminar el **volumen** persistente, ya que Postgres no ejecutará el script de `/init` si detecta que ya existen datos.

**Comandos para reiniciar el volumen:**

```bash
# 1. Detener y borrar contenedores y volúmenes
docker compose down -v

# 2. Levantar todo de nuevo (esto ejecutará el script de /init otra vez)
docker compose up -d

```

*⚠️ **Advertencia:** El flag `-v` borrará todos los datos almacenados en la base de datos de forma permanente.*

---

## 📝 Notas de Implementación

* El puerto externo de Postgres se ha mapeado al **5433** para evitar conflictos con instalaciones locales de PostgreSQL en Windows.
* Se utiliza la versión `alpine` de Postgres para minimizar el consumo de recursos en Docker Desktop.

---

### Repo Oficial de Northwind database for Postgres
- https://github.com/pthom/northwind_psql



## Despliegue

Abre tu terminal en esa carpeta y ejecuta:  
1. Acceder al directorio: 
    ```bash
    cd {directorio-del-archivo}
    ```
2. Levantar entorno: 
    ```bash
    docker compose up
    ```
    ó 
    ```bash
    docker compose up -d
    ```

## Actualizar n8n
```bash 
docker compose pull
```


## env Template:

```txt
# Configuración de Red
N8N_PORT=5678

# Configuración Regional
GENERIC_TIMEZONE=America/Argentina/Buenos_Aires

# Seguridad: Autenticación Básica
N8N_BASIC_AUTH_ACTIVE=true
N8N_BASIC_AUTH_USER=admin_n8n
N8N_BASIC_AUTH_PASSWORD=TuPasswordSeguro
N8N_ENCRYPTION_KEY=1234567890abcdef1234567890abcdef

# Seguridad adicional
N8N_SECURE_COOKIE=false
# se usa en entornos de desarrollo local para permitir el acceso a través de conexiones http://localhost. En servidores reales con HTTPS, siempre debe ser true.
```
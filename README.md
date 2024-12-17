# Proyecto: Sistema de Gestión de Inventarios

## **Guía de Ejecución del Proyecto con Docker Compose**

Este proyecto incluye un **frontend** (React), un **backend** (.NET 6), y una base de datos **SQL Server**. Utiliza Docker Compose para facilitar la configuración y ejecución de todos los servicios.

---

## **1. Requisitos Previos**

1. **Docker** y **Docker Compose** instalados en tu máquina.
   - [Guía de instalación de Docker](https://docs.docker.com/get-docker/)
   - [Guía de instalación de Docker Compose](https://docs.docker.com/compose/install/)
2. Clonar el repositorio del proyecto:
   ```bash
   git clone https://github.com/maicolffsa/inventory_webapp.git
   cd inventory-management
   ```

---

## **2. Estructura del Proyecto**

```
project/
├── SecureWebSite.Server/                # Código fuente del backend (.NET 6)
├── securewebsite.client/               # Código fuente del frontend (React)
├── nginx/               # Configuración nginx
├── docker-compose.yaml      # Archivo de configuración para Docker Compose
└── README.md               # Guía del proyecto
```

---

## **3. Archivo `docker-compose.yml`**


## **4. Configuración del Backend**

1. Ve al directorio `backend`.
2. Asegúrate de que el archivo `appsettings.json` esté configurado correctamente para conectarse a la base de datos:

```json
"ConnectionStrings": {
  "DefaultConnection": "Server=db;Database=MyDatabase;User Id=sa;Password=YYourStrongPassword!123"
}
```

3. Construye el contenedor con Docker Compose (paso 5).

---

## **5. Configuración del Frontend**

1. Ve al directorio `frontend`.
2. Configura el archivo `.env` para apuntar al backend:

```
REACT_APP_API_URL=http://localhost:5000/api
```

3. Construye el contenedor con Docker Compose (paso 5).

---

## **6. Ejecutar el Proyecto**

Desde la raíz del proyecto, ejecuta el siguiente comando para construir y levantar todos los servicios:

```bash
docker-compose up --build
```

Esto hará lo siguiente:
- Construirá los contenedores para el backend, frontend y base de datos.
- Levantará los servicios en los siguientes puertos:
  - **Frontend**: [http://localhost:3000](http://localhost:3000)
  - **Backend**: [http://localhost:5003](http://localhost:5000)
  - **Base de datos**: Puerto 1433 (SQL Server).

---

## **7. Verificar la Aplicación**

1. **Base de datos**:
   - Usa un cliente SQL (como Azure Data Studio o SQL Server Management Studio) para conectarte a `localhost:1433` con las credenciales:
     - Usuario: `sa`
     - Contraseña: `YourStrongPassword!123`


2. **Frontend**:
   - Abre [http://localhost:3000](http://localhost) en tu navegador.

---

## **8. Detener los Servicios**

Para detener y eliminar los contenedores creados, usa:
```bash
docker-compose down
```

---

## **9. Notas Adicionales**

- Si realizas cambios en el código fuente, puedes reconstruir los servicios con:
  ```bash
  docker-compose up --build
  ```
- Asegúrate de que los puertos 3000, 5003 y 1433 no estén ocupados por otros servicios en tu máquina.

---

¡Listo! Ahora tienes tu sistema de gestión de inventarios corriendo en contenedores Docker.

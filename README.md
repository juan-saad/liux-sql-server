# Instancia de SQL server en container de Linux

## Guía de Inicio

Sigue estos pasos para configurar y ejecutar el proyecto en tu entorno local.

### Prerrequisitos

Asegúrate de tener instalados los siguientes programas en tu máquina:

- [Docker Desktop](https://www.docker.com/products/docker-desktop)
- [Git](https://git-scm.com/)
- Gestor de base de datos SQL conectarse al server, puede ser el Sql Sever Managemet Studio, DBEaver, VS Code, etc

### Instalación

1. **Clona el repositorio:**
   ```bash
   git clone https://github.com/juan-saad/linux-sql-server.git
   cd liux-sql-server
   ```

2. **Configura el valor de `DB_SUFFIX`:**

   El valor de `DB_SUFFIX` se utiliza para definir el sufijo de las bases de datos creadas. Para cambiarlo debes ir a:

   - **En el archivo `Dockerfile`:** Si prefieres configurar el valor directamente en el archivo `Dockerfile`, edita la línea correspondiente:
     ```dockerfile
     ENV DB_SUFFIX=01
     ```
     Cambia `01` por el sufijo que desees.

3. **Construye e inicia los contenedores:**

   Una vez configurado el valor de `DB_SUFFIX`, ejecuta el siguiente comando para construir e iniciar los contenedores en segundo plano:

   ```bash
   docker compose up -d --build
   ```

   Este comando se encargará de construir las imágenes necesarias y levantar los servicios definidos en el archivo `docker-compose.yml`.

4. **Verifica que las bases de datos se hayan creado correctamente:**
    
    Por defecto, la contraseña del SQL Server se configura como: `Sup3rS3cretPassw0rd!`

    Ingresa al contenedor de SQL Server y verifica que las bases de datos con el sufijo configurado se hayan creado correctamente:
    ```bash
    docker exec -it "<nombre_del_contenedor>" /opt/mssql-tools18/bin/sqlcmd -S localhost -U sa -P "<tu_contraseña>" -N -C -Q "SELECT name FROM sys.databases"
    ```

   Tambien podés verificarlo con tu gestor de base de datos SQL, indicando como servidor `localhost` y como `contraseña` el valor que corresponda

   Reemplaza `<nombre_del_contenedor>` y `<tu_contraseña>` con los valores correspondientes.

## Contributors

<!-- ALL-CONTRIBUTORS-LIST:START - Do not remove or modify this section -->
<!-- prettier-ignore-start -->
<!-- markdownlint-disable -->

<!-- markdownlint-restore -->
<!-- prettier-ignore-end -->

<!-- ALL-CONTRIBUTORS-LIST:END -->
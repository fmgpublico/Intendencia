
# Pendiente

- Botón volver en la página de alta y edición de cliente.
- Búsqueda de clientes. Se está intentando utilizar QueryDSL. En https://docs.spring.io/spring-data/jpa/reference/repositories/core-extensions.html#core.web.page indican que no se debe utilizar Page para devolver los resultados de una consulta porque podría cambiar. Recomiendan utilizar HATEOAS. Aunque indican que en las versiones más recientes de Spring Data hay un mecanismo de visualización de páginas mejorado.
- Iconos. ¿Utilizar Fontawesome?
- Internacionalización: ver https://vuejs.org/guide/reusability/plugins.html, donde crean un plugin para i18n.
- REST API: hacer que sea realmente un API REST utilizando HATEOAS. Ver "Building REST services with Spring" en https://spring.io/guides/tutorials/rest
- Segurización. Realizar el refresco del token de acceso.
- Segurización. ¿Cómo detectar que el usuario no está autenticado para poder redirigir a la página de autenticación?
- Segurización. Configurar la segurización para que solo se puedan realizar ciertas acciones si se tienen los roles adecuados.
- Tablas. ¿Utilizar alguna librería como Datatables?
- Utilizar variables por ejemplo para las rutas del API REST o el servidor de autorización, y que cambien según el entorno (desarrollo, producción, etc). ¿Utilizar ficheros .env? ¿Crear un plugin?
- Validaciones en los DTO.

# Páginas de la aplicación

- Página de login
Tendrá campos usuario y contraseña.
Al hacer submit se hace una petición POST a Keycloak para obtener un token JWT. Se pasan los datos del cliente Keycloak de intendencia y el usuario/contraseña que introduzca el usuario.

- Página de listado de clientes
Hacer un listado básico.
Campos a mostrar:
	- UUID
	- nombre

- Página de detalle de un cliente	
Campos a mostrar:
	- UUID
	- nombre
	- correo electrónico

Tendrá una pestaña "Productos bancarios". Al pulsarla llevará a una página con un listado de los productos bancarios.

- Página de productos bancarios
Hacer un listado básico.
Campos a mostrar:
	- Nombre banco
	- 

# Hacer una llamada al API REST de intendencia clientes.

```
curl -i -o - http://localhost:8082/clientes/findAll --header "Authorization: Bearer eyJhbGciOiJSUzI1NiIsInR5cCIgOiAiSldUIiwia2lkIiA6ICJpQmJCNWdxbWI2RGNSY0VCZUNDMkNSeUFwbkhQczZVVFo0Q1k3emlmTnV3In0.eyJleHAiOjE3NTM5NDcxNzMsImlhdCI6MTc1Mzk0Njg3MywianRpIjoib25ydHJvOjc0NGIxOGQwLWM5ZTQtNDMwNy04NTM4LTVkM2EwMTNhM2MyMyIsImlzcyI6Imh0dHA6Ly9sb2NhbGhvc3Q6OTA5MC9yZWFsbXMvaW50ZW5kZW5jaWEiLCJhdWQiOiJhY2NvdW50Iiwic3ViIjoiNmNhNmJlNjItZWFkMi00YmU2LTlmNzItMzhlMGM1OWEzOTc2IiwidHlwIjoiQmVhcmVyIiwiYXpwIjoiaW50ZW5kZW5jaWEiLCJzaWQiOiI3YzY3MGRmMS1iZTgxLTRkMjktYjJmNC1lOTE0MzRhNWJmNTgiLCJhY3IiOiIxIiwiYWxsb3dlZC1vcmlnaW5zIjpbImh0dHA6Ly9sb2NhbGhvc3Q6ODA4MiJdLCJyZWFsbV9hY2Nlc3MiOnsicm9sZXMiOlsib2ZmbGluZV9hY2Nlc3MiLCJ1bWFfYXV0aG9yaXphdGlvbiIsImRlZmF1bHQtcm9sZXMtaW50ZW5kZW5jaWEiXX0sInJlc291cmNlX2FjY2VzcyI6eyJhY2NvdW50Ijp7InJvbGVzIjpbIm1hbmFnZS1hY2NvdW50IiwibWFuYWdlLWFjY291bnQtbGlua3MiLCJ2aWV3LXByb2ZpbGUiXX19LCJzY29wZSI6ImVtYWlsIHByb2ZpbGUiLCJlbWFpbF92ZXJpZmllZCI6dHJ1ZSwicHJlZmVycmVkX3VzZXJuYW1lIjoiaW50ZW5kZW5jaWExIiwiZW1haWwiOiJmbWFydGluQGVzbGEuY29tIn0.LW4JCz8Ui_K3TR0F92naTmZUJpkzs97HSUAUWnRjMWnfoANCod9uMVaQ7M0HHQqy_ALIRi3mGmiZq8lfioZ1yshmUDmNa0r8pxTl6ze5FsbMSq9Hc3VBvYGwy6zqV4uLzDLzK7osvhLsUqqKQhCwUO9EAP0kCpkStrYhr5jW4ybOXvMDvOQAv47RdbORGZ08pc6c4fHwfif3l6gGIccU-yUzHxvCL-5veaKWqgP6F6lr3ljR89yg6mI20KXmPpKpzi8Z3iiBebLbTt8iYN5Yjin7vryRNKP5WHLpt5FdDb6QsDHvl7ysx4je7iYBP17XrBT130DCeLG6cO2fX4CgTg"
```

# Comandos para ejecutar la aplicación

Durante el desarrollo, por ejemplo con Visual Studio Code, para arrancar la aplicación se ejecuta:

```
npm run dev
```

Si se quiere construir el proyecto para desplegarlo en producción, se ejecuta:
```
npm run build
```

Crea los recursos en la carpeta dist del proyecto. Se pueden copiar en el Apache para hacerla funcionar. Se copian por ejemplo en la carpeta htdocs.

El Apache local escucha en el puerto 81. La URL es: http://localhost:81
Esta URL hay que añadirla a los orígenes permitidos en la configuración de CORS del API REST.



<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-oauth2-resource-server</artifactId>
</dependency>
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-security</artifactId>
</dependency>

En una página dicen que hay que incluir una dependencia del API JOSE para procesar el token JWT en el converter.


En https://dzone.com/articles/spring-boot-3-keycloak implementan un converter para el token JWT.

# Ejecución de la aplicación

cd C:\Proyectos\Pruebas\intendencia\intendencia.clientes

- Generación del JAR:
```
\Entorno\Maven\apache-maven-3.9.2-JAVA-21\bin\mvn -P postgresql clean package -Dmaven.test.skip=true
```

- Ejecución del del JAR:
```
\Entorno\Java\jdk-21\bin\java -jar target\intendencia.clientes-1.0.jar
```

- Ejecución del del JAR utilizando un fichero application.properties externo al JAR:
```
\Entorno\Java\jdk-21\bin\java -jar target\intendencia.clientes-1.0.jar --spring.config.location=C:/Proyectos/Pruebas/intendencia/application.properties
```

- Ejecución del del JAR con el plugin de Spring Boot:
```
\Entorno\Maven\apache-maven-3.9.2-JAVA-21\bin\mvn spring-boot:run -Dspring.profiles.active=postgresql
```

# Código de la aplicación

<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-oauth2-resource-server</artifactId>
</dependency>
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-security</artifactId>
</dependency>

En una página dicen que hay que incluir una dependencia del API JOSE para procesar el token JWT en el converter.


En https://dzone.com/articles/spring-boot-3-keycloak implementan un converter para el token JWT.

# Copia de seguridad y restauración de las bases de datos

- Desde Windows

    - intendencia_clientes

        `
        set FECHA=%date:~-4,4%%date:~-7,2%%date:~-10,2%
        `
        `
        "C:\Entorno\PostgreSQL\18\bin\pg_dump.exe" --host 192.168.0.16 --port 5418 --username postgres -W --format custom --blobs --verbose --file "C:\borrar\intendencia_clientes_%FECHA%.sql" intendencia_clientes
        `
        
        `
        C:\Entorno\PostgreSQL\18\bin\pg_restore.exe --host=192.168.0.16 --port=5418 --username=postgres -W -C -d postgres D:\compartida\intendencia_clientes_20260611125335.sql
        `

        pg_restore no ejecuta automáticamente el CREATE DATABASE salvo que se le indique que restaure también los objetos de nivel base de datos. Esto se hace con "-C", con lo que crea la base de datos definida en el dump.

        Con "-d postgres" se hace que se conecte primero a una base ya existente (postgres) para poder ejecutar el CREATE DATABASE. 

    - intendencia_productos_bancarios
    
        `
        set FECHA=%date:~-4,4%%date:~-7,2%%date:~-10,2%
        `
        `        
        "C:\Entorno\PostgreSQL\18\bin\pg_dump.exe" --host 192.168.0.16 --port 5418 --username postgres -W --format custom --blobs --verbose --file "C:\borrar\intendencia_productos_bancarios_%FECHA%.sql" intendencia_productos_bancarios
        `

        `
        C:\Entorno\PostgreSQL\18\bin\pg_restore.exe --host=192.168.0.16 --port=5418 --username=postgres -W -C -d postgres D:\compartida\intendencia_productos_bancarios_20260611125424.sql
        `

    - Keycloak
    
        `
        set FECHA=%date:~-4,4%%date:~-7,2%%date:~-10,2%
        `
        `  
        "C:\Entorno\PostgreSQL\18\bin\pg_dump.exe" --host 192.168.0.16 --port 5418 --username postgres -W --format custom --blobs --verbose --file "C:\borrar\keycloakdev_%FECHA%.sql" keycloakdev
        `

        `
        "C:\Entorno\PostgreSQL\16\bin\pg_restore.exe" --host 192.168.0.16 --port 5418 --username postgres -W --format custom --blobs --verbose --file "C:\borrar\keycloakdev_%FECHA%.sql"
        `

- Desde el contenedor PostgreSQL.18

    - intendencia_clientes
    
        `
        printf -v FECHA '%(%Y%m%d%H%M%S)T'
        `
        `
        pg_dump --host localhost --port 5432 --username postgres -W --format custom --blobs --verbose --file "/var/backups/intendencia_clientes_$FECHA.sql" intendencia_clientes
        `

    - intendencia_productos_bancarios
    
        `
        printf -v FECHA '%(%Y%m%d%H%M%S)T'
        `
        `
        pg_dump --host localhost --port 5432 --username postgres -W --format custom --blobs --verbose --file "/var/backups/intendencia_productos_bancarios_$FECHA.sql" intendencia_productos_bancarios
        `

    - Keycloak
    
        - Realización de la copia de seguridad  

            `
            printf -v FECHA '%(%Y%m%d%H%M%S)T'
            `

            `
            pg_dump --host localhost --port 5432 --username postgres -W --format custom --blobs --verbose --file "/var/backups/keycloakdev_$FECHA.sql" keycloakdev
            `
    
        - Restauración de la copia de seguridad  

            `
            pg_restore -h localhost -p 5432 -U postgres -C -d postgres /var/backups/keycloakdev_20260609111240.sql
            `
        
            El fichero keycloakdev_20260609111240.sql contiene la sentencia de creación de la base de datos:

            `
               CREATE DATABASE keycloakdev WITH TEMPLATE = template0 ENCODING = 'UTF8' LOCALE_PROVIDER = libc LOCALE = 'es_ES.utf8';
            `

            pg_restore no ejecuta automáticamente el CREATE DATABASE salvo que se le indique que restaure también los objetos de nivel base de datos. Esto se hace con "-C", con lo que crea la base de datos definida en el dump.

            Con "-d postgres" se hace que se conecte primero a una base ya existente (postgres) para poder ejecutar el CREATE DATABASE.


# Restauración de las bases de datos en el contenedor PostgreSQL en la máquina Fedora Linux

- Se copia el fichero con la copia de seguridad de la BBDD intendencia_clientes en el contenedor. Se llama intendencia_clientes_20251209.sql.

podman cp ~/compartida/equipo.paco/intendencia_clientes_20251209.sql PostgreSQL.18:/var/lib/postgresql

- Dentro del contenedor se crea un fichero /var/lib/postgresql/CREATE_BBDD_intendencia_clientes.sql con la sentencia para crear la BBDD:

CREATE DATABASE intendencia_clientes
WITH
OWNER = postgres
ENCODING = 'UTF8'
LC_COLLATE = 'es_ES.utf8'
LC_CTYPE = 'es_ES.utf8'
TABLESPACE = pg_default
CONNECTION LIMIT = -1
TEMPLATE=template0;

- Dentro del contenedor se asigna permiso de ejecución al usuario del script y se ejectua:

chmod u+x /var/lib/postgresql/CREATE_BBDD_intendencia_clientes.sql
psql -U postgres -f /var/lib/postgresql/CREATE_BBDD_intendencia_clientes.sql

- Dentro del contenedor se restaura la BBDD intendencia_clientes:

pg_restore --username postgres --password --dbname intendencia_clientes --verbose /var/lib/postgresql/intendencia_clientes_20251209.sql

- Se copia el fichero con la copia de seguridad de la BBDD intendencia_clientes en el contenedor. Se llama intendencia_productos_bancarios_20251209.sql.

podman cp ~/compartida/equipo.paco/intendencia_productos_bancarios_20251209.sql PostgreSQL.18:/var/lib/postgresql

- Dentro del contenedor se crea un fichero /var/lib/postgresql/CREATE_BBDD_intendencia_productos_bancarios.sql para crear la BBDD intendencia_clientes:

```
CREATE DATABASE intendencia_productos_bancarios
WITH
OWNER = postgres
ENCODING = 'UTF8'
LC_COLLATE = 'es_ES.utf8'
LC_CTYPE = 'es_ES.utf8'
TABLESPACE = pg_default
CONNECTION LIMIT = -1
TEMPLATE=template0;
```

- Dentro del contenedor se asigna permiso de ejecución al usuario del script y se ejectua:

chmod u+x /var/lib/postgresql/CREATE_BBDD_intendencia_productos_bancarios.sql
psql -U postgres -f /var/lib/postgresql/CREATE_BBDD_intendencia_productos_bancarios.sql

- Dentro del contenedor se restaura la BBDD intendencia_productos_bancarios:

pg_restore --username postgres --password --dbname intendencia_productos_bancarios --verbose /var/lib/postgresql/intendencia_productos_bancarios_20251209.sql


# Servicio para arrancar automáticamente el contenedor PostgreSQL.18

Se crea un servicio para que se arranque el contenedor PostgreSQL.18 automáticamente al iniciar la máquina sin que se tenga que autenticar el usuario.

El contenedor es rootless. Fue creado por el usuario paco. Por esto debe usarse un servicio de usuario en vez de uno del sistema (estaría en /etc/systemd/system).

Se crea la unidad .config/systemd/user/postgresql18-container.service con este contenido:

```
[Unit]
Description=Contenedor PostgreSQL 18
Wants=network-online.target
After=network-online.target

[Service]
Type=oneshot
RemainAfterExit=yes
ExecStart=/usr/bin/podman start PostgreSQL.18
ExecStop=/usr/bin/podman stop -t 10 PostgreSQL.18

[Install]
WantedBy=default.target
```

Se recargan los servicios, se habilita el servicio nuevo y se reinicia:
systemctl --user daemon-reload
systemctl --user disable postgresql18-container.service
systemctl --user enable postgresql18-container.service
systemctl --user restart postgresql18-container.service

systemctl --user status postgresql18-container.service
systemctl --user is-enabled postgresql18-container.service
systemctl --user is-active postgresql18-container.service

systemctl --user list-unit-files | grep postgresql18
systemctl --user list-dependencies default.target | grep postgresql
systemctl --user list-dependencies postgresql18-container.service

-- Para ver si la unidad tiene errore:
systemd-analyze verify .config/systemd/user/postgresql18-container.service


-- Si el objetivo es que el contenedor arranque automáticamente incluso sin iniciar sesión como usuario paco, conviene usar lingering:
sudo loginctl enable-linger paco

loginctl show-user paco -p Linger

podman ps -a


# Servicio para arrancar automáticamente el contenedor Keycloak.26.4.0

.config/systemd/user/keycloak-26-4-container.service

```
[Unit]
Description=Contenedor Keycloak.26.4.0
Wants=network-online.target postgresql18-container.service
After=network-online.target postgresql18-container.service

[Service]
Type=oneshot
RemainAfterExit=yes
ExecStart=/usr/bin/podman start Keycloak.26.4.0
ExecStop=/usr/bin/podman stop -t 10 Keycloak.26.4.0

[Install]
WantedBy=default.target
```

systemctl --user daemon-reload
systemctl --user disable keycloak-26-4-container.service
systemctl --user enable keycloak-26-4-container.service
systemctl --user restart keycloak-26-4-container.service

systemctl --user list-dependencies keycloak-26-4-container.service
systemctl --user show keycloak-26-4-container.service -p After -p Wants

systemctl --user status keycloak-26-4-container.service
systemctl --user is-enabled keycloak-26-4-container.service
systemctl --user is-active keycloak-26-4-container.service


# Instalar entorno

- Se instala podman

    `
    dnf search podman
    dnf install podman
    `

- ¿Se crea una máquina?

- Se crea una red con Podman

    `
    podman network create red-desarrollo
    `

- Se crea un pod para la aplicación Intendencia

    `
    podman pod create --name PodIntendencia --infra-name ContenedorInfraPodIntendencia --network red-desarrollo
    `

    Al crear un pod se crea un contenedor infra que se encarga de gestionarlo.  
    Se asigna un nombre a este contenedor para identificarlo más fácilmente.

- Se crea el contenedor de PostgreSQL 18

    `
    podman run --name PostgreSQL.18 -d -e POSTGRES_USER=postgres -e POSTGRES_PASSWORD=Progres.12345 -p 5418:5432 --network red-desarrollo --pod PodIntendencia -v /var/opt/postres/data:/var/lib/data:Z sha256:f2ec0fa6de3e914eae01d5bfe558eef5f797908d97c8ce8442bc3862816f7827
    `

    Se ve cómo se especifica la red y el pod.  
    También se crea un volumen que mapea la carpeta /var/opt/postres/data de la máquina con la carpeta /var/lib/data del contenedor.

- Se crea el contenedor Keycloak 26.4.0

    `
    podman run --name=Keycloak.26.4.0 -p 8443:8443 -d --network red-desarrollo --pod PodIntendencia -v /home/paco/SSL:/opt/keycloak/certs:Z -e KC_BOOTSTRAP_ADMIN_USERNAME=admin -e KC_BOOTSTRAP_ADMIN_PASSWORD=admin -e KC_DB=postgres -e KC_DB_URL=jdbc:postgresql://PostgreSQL.18:5432/keycloakdev?currentSchema=keycloakdev,public -e KC_DB_USERNAME=postgres -e KC_DB_PASSWORD=Progres.12345 -e KC_HTTP_ENABLED=false -e KC_HTTPS_CERTIFICATE_FILE=/opt/keycloak/certs/SSL8990251.chain.cer -e KC_HTTPS_CERTIFICATE_KEY_FILE=/opt/keycloak/certs/SSL8990251.key -e KC_HOSTNAME=keycloak.esla.com sha256:ad01f352589657a2d32886b9e4018640b24b7c0a88496ea6ddf023e92c4576ed start
    `

    Se explica la sentencia:

    - Se configura Keycloak como un **proxy**, sin necesidad de tener que instalar un Apache que haga de proxy inverso.
    - Se configura la **comunicación TLS**, por lo que se indica KC_HTTP_ENABLED=false.  
    Se indican la clave privada y el certificado. Para tenerlos en el contenedor, se monta un volumen que mapea la ruta /home/paco/SSL de la máquina con la ruta /opt/keycloak/certs en el contenedor.
    - Se establece el nombre del host **keycloak.esla.com**
    - Se mapea el puerto 8443 al 8443 del contenedor, donde Keycloak escucha peticiones HTTPS.  
    Podman se ejecuta en modo rootless.  
    En Linux, los puertos inferiores a 1024 (80, 443, 25, etc.) son puertos privilegiados. Un usuario normal no puede abrirlos.  
    Si se quiere usar el puerto 443 hay varias opciones:

        - Opción 1: Permitir puertos privilegiados a usuarios normales

            `
            sudo sysctl -w net.ipv4.ip_unprivileged_port_start=443
            `

            Para hacerlo permanente:
                
            `
            echo 'net.ipv4.ip_unprivileged_port_start=443' | sudo tee /etc/sysctl.d/99-rootless-ports.conf
            sudo sysctl --system
            `
            Después Podman rootless podrá publicar el 443.
        
        - Opción 2: Ejecutar el contenedor como root.  
        No suele ser la opción recomendada hoy en Fedora, porque se pierde parte de las ventajas de rootless Podman.
        - Opción 3: Usar un proxy inverso en el host, como Apache HTTP Server o NGINX
        Escuchará en el 443 del host y reenvíará al puerto alto (8443) donde escucha Keycloak.  
        El proceso de Apache se inicia como root, abre el puerto 443 y después cambia al usuario de servicio (normalmente apache).  
        Por tanto, sí puede escuchar en el puerto 443 aunque tu contenedor Keycloak esté ejecutándose como usuario normal.

    - Se arranca con start, no con start-dev. start-dev es para desarrollo. No realiza comprobaciones tan extrictas como con start. Para HTTPS es mejor ejecutarlo con start.

 - Se abre en la máquina el puerto que recibirá peticiones TLS:
    ```
    sudo firewall-cmd --add-port=8443/tcp --permanent
    sudo firewall-cmd --reload
    ```


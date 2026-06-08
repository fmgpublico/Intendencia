
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

- intendencia_clientes
```
set FECHA=%date:~-4,4%%date:~-7,2%%date:~-10,2%
"C:\Entorno\PostgreSQL\16\bin\pg_dump.exe" --host localhost --port 5416 --username postgres -W --format custom --blobs --verbose --file "C:\borrar\intendencia_clientes_%FECHA%.sql" intendencia_clientes
```

- intendencia_productos_bancarios
```
set FECHA=%date:~-4,4%%date:~-7,2%%date:~-10,2%
"C:\Entorno\PostgreSQL\16\bin\pg_dump.exe" --host localhost --port 5416 --username postgres -W --format custom --blobs --verbose --file "C:\borrar\intendencia_productos_bancarios_%FECHA%.sql" intendencia_productos_bancarios
```

- Keycloak
```
set FECHA=%date:~-4,4%%date:~-7,2%%date:~-10,2%
"C:\Entorno\PostgreSQL\16\bin\pg_dump.exe" --host serverjava --port 5416 --username postgres -W --format custom --blobs --verbose --file "C:\borrar\keycloakdev_%FECHA%.sql" keycloakdev
```

```
"C:\Entorno\PostgreSQL\16\bin\pg_restore.exe" --host 192.168.0.16 --port 5418 --username postgres -W --format custom --blobs --verbose --file "C:\borrar\keycloakdev_%FECHA%.sql"
```

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

CREATE DATABASE intendencia_productos_bancarios
WITH
OWNER = postgres
ENCODING = 'UTF8'
LC_COLLATE = 'es_ES.utf8'
LC_CTYPE = 'es_ES.utf8'
TABLESPACE = pg_default
CONNECTION LIMIT = -1
TEMPLATE=template0;

- Dentro del contenedor se asigna permiso de ejecución al usuario del script y se ejectua:

chmod u+x /var/lib/postgresql/CREATE_BBDD_intendencia_productos_bancarios.sql
psql -U postgres -f /var/lib/postgresql/CREATE_BBDD_intendencia_productos_bancarios.sql

- Dentro del contenedor se restaura la BBDD intendencia_productos_bancarios:

pg_restore --username postgres --password --dbname intendencia_productos_bancarios --verbose /var/lib/postgresql/intendencia_productos_bancarios_20251209.sql


# Servicio para arrancar automáticamente el contenedor PostgreSQL.18

Se crea un servicio para que se arranque el contenedor PostgreSQL.18 automáticamente al iniciar la máquina sin que se tenga que autenticar el usuario.

El contenedor es rootless. Fue creado por el usuario paco. Por esto debe usarse un servicio de usuario en vez de uno del sistema (estaría en /etc/systemd/system).

Se crea la unidad .config/systemd/user/postgresql18-container.service con este contenido:


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


systemctl --user daemon-reload
systemctl --user disable keycloak-26-4-container.service
systemctl --user enable keycloak-26-4-container.service
systemctl --user restart keycloak-26-4-container.service

systemctl --user list-dependencies keycloak-26-4-container.service
systemctl --user show keycloak-26-4-container.service -p After -p Wants

systemctl --user status keycloak-26-4-container.service
systemctl --user is-enabled keycloak-26-4-container.service
systemctl --user is-active keycloak-26-4-container.service
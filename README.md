# Obtener un token de acceso.

```
curl -X POST "http://localhost:9090/realms/intendencia/protocol/openid-connect/token" --header "Content-Type: application/x-www-form-urlencoded" --data-urlencode "grant_type=password" --data-urlencode "client_id=intendencia" --data-urlencode "client_secret=7ZnfuQRWyUTgmlo3kfbTioBVyRLuuCnh" --data-urlencode "username=intendencia1" --data-urlencode "password=Cgb.12345"
```

# Refrescar un token de acceso

Se utiliza el parámetro de la petición "grant_type=refresh_token".
En el parámetro de la petición "refresh_token" se pasa el token de refresco.

```
curl -X POST "http://localhost:9090/realms/intendencia/protocol/openid-connect/token" --header "Content-Type: application/x-www-form-urlencoded" --data-urlencode "grant_type=refresh_token" --data-urlencode "client_id=intendencia" --data-urlencode "client_secret=7ZnfuQRWyUTgmlo3kfbTioBVyRLuuCnh" --data-urlencode "refresh_token=eyJhbGciOiJIUzUxMiIsInR5cCIgOiAiSldUIiwia2lkIiA6ICJmYjdlNmZhOC0wM2Y0LTQwMWYtODBiOS04YmVkODcyYmUyZGIifQ.eyJleHAiOjE3NTQ2MzgzMDYsImlhdCI6MTc1NDYzNjUwNiwianRpIjoiNDMyMjgxNjQtODBiMC00MGY0LWE2MzctZWRjMDUzMmM5NDhjIiwiaXNzIjoiaHR0cDovL2xvY2FsaG9zdDo5MDkwL3JlYWxtcy9pbnRlbmRlbmNpYSIsImF1ZCI6Imh0dHA6Ly9sb2NhbGhvc3Q6OTA5MC9yZWFsbXMvaW50ZW5kZW5jaWEiLCJzdWIiOiI2Y2E2YmU2Mi1lYWQyLTRiZTYtOWY3Mi0zOGUwYzU5YTM5NzYiLCJ0eXAiOiJSZWZyZXNoIiwiYXpwIjoiaW50ZW5kZW5jaWEiLCJzaWQiOiJmOWQ1NTZkZS1mM2U3LTQ0MDQtYjI3MS02Yjg5MjY3NTg4M2YiLCJzY29wZSI6ImJhc2ljIGVtYWlsIHNlcnZpY2VfYWNjb3VudCBhY3Igd2ViLW9yaWdpbnMgcHJvZmlsZSByb2xlcyJ9.EQxlUxaXZPAtj9BOYYbjaf_xsNsjlxKWAzQdrNqALCqj2ZNmGoe45IS8CFu5bzIicLdftGLLJnmyFeeD6QTUSg"
```
Devuelve un nuevo token de acceso.

# Obtener el estado de un token de acceso o de refresco

En el parámetro de la petición "token" se puede poner un token de acceso o uno de refresco.

```
curl -X POST "http://localhost:9090/realms/intendencia/protocol/openid-connect/token/introspect" --header "Content-Type: application/x-www-form-urlencoded" --data-urlencode "grant_type=password" --data-urlencode "client_id=intendencia" --data-urlencode "client_secret=7ZnfuQRWyUTgmlo3kfbTioBVyRLuuCnh" --data-urlencode "username=intendencia1" --data-urlencode "password=Cgb.12345" --data-urlencode "token=eyJhbGciOiJSUzI1NiIsInR5cCIgOiAiSldUIiwia2lkIiA6ICJpQmJCNWdxbWI2RGNSY0VCZUNDMkNSeUFwbkhQczZVVFo0Q1k3emlmTnV3In0.eyJleHAiOjE3NTQ2MzY4MDYsImlhdCI6MTc1NDYzNjUwNiwianRpIjoib25ydHJvOmQ3NGYxYjkzLTk5ZTAtNGM5OC05MTZhLTkzOTZhZmM1MTEyYyIsImlzcyI6Imh0dHA6Ly9sb2NhbGhvc3Q6OTA5MC9yZWFsbXMvaW50ZW5kZW5jaWEiLCJhdWQiOiJhY2NvdW50Iiwic3ViIjoiNmNhNmJlNjItZWFkMi00YmU2LTlmNzItMzhlMGM1OWEzOTc2IiwidHlwIjoiQmVhcmVyIiwiYXpwIjoiaW50ZW5kZW5jaWEiLCJzaWQiOiJmOWQ1NTZkZS1mM2U3LTQ0MDQtYjI3MS02Yjg5MjY3NTg4M2YiLCJhY3IiOiIxIiwiYWxsb3dlZC1vcmlnaW5zIjpbImh0dHA6Ly9sb2NhbGhvc3Q6ODA4MiJdLCJyZWFsbV9hY2Nlc3MiOnsicm9sZXMiOlsib2ZmbGluZV9hY2Nlc3MiLCJ1bWFfYXV0aG9yaXphdGlvbiIsImRlZmF1bHQtcm9sZXMtaW50ZW5kZW5jaWEiXX0sInJlc291cmNlX2FjY2VzcyI6eyJhY2NvdW50Ijp7InJvbGVzIjpbIm1hbmFnZS1hY2NvdW50IiwibWFuYWdlLWFjY291bnQtbGlua3MiLCJ2aWV3LXByb2ZpbGUiXX19LCJzY29wZSI6ImVtYWlsIHByb2ZpbGUiLCJlbWFpbF92ZXJpZmllZCI6dHJ1ZSwicHJlZmVycmVkX3VzZXJuYW1lIjoiaW50ZW5kZW5jaWExIiwiZW1haWwiOiJmbWFydGluQGVzbGEuY29tIn0.PF4wjqPiqeafwzzlsRwIWNYe8xQT99Cc4XIkDLGen2UOifDhHkOhk6EU9weH-a7mo9WUxIGgFI74JxWD6jUFibYz6jmmoVz9RGDBYNru6tnUm-0qT6dtO1qFM7rT6XZuGC4P2x95MvXbc8zDU1obP9vhlykBmofcNMEECrOnUgzgikW_HrfhtEYOQimNeAemyvN8BdWdDz4FP7tsLFePRJgymfHW5_h95EpppXRMDoBirq5zQ1UHvs8__bwNRuUp-L7AjWOrOhAOUzFHF5kQu-dyPR8px05Jd0kY-zVZNL9cMfme99L09PTa8Kf7zA4EeLgAHfGeqEvxmZsfR8u35Q"
```

```
curl -X POST "http://localhost:9090/realms/intendencia/protocol/openid-connect/token/introspect" --header "Content-Type: application/x-www-form-urlencoded" --data-urlencode "grant_type=password" --data-urlencode "client_id=intendencia" --data-urlencode "client_secret=7ZnfuQRWyUTgmlo3kfbTioBVyRLuuCnh" --data-urlencode "username=intendencia1" --data-urlencode "password=Cgb.12345" --data-urlencode "token=eyJhbGciOiJIUzUxMiIsInR5cCIgOiAiSldUIiwia2lkIiA6ICJmYjdlNmZhOC0wM2Y0LTQwMWYtODBiOS04YmVkODcyYmUyZGIifQ.eyJleHAiOjE3NTQ2MzgzMDYsImlhdCI6MTc1NDYzNjUwNiwianRpIjoiNDMyMjgxNjQtODBiMC00MGY0LWE2MzctZWRjMDUzMmM5NDhjIiwiaXNzIjoiaHR0cDovL2xvY2FsaG9zdDo5MDkwL3JlYWxtcy9pbnRlbmRlbmNpYSIsImF1ZCI6Imh0dHA6Ly9sb2NhbGhvc3Q6OTA5MC9yZWFsbXMvaW50ZW5kZW5jaWEiLCJzdWIiOiI2Y2E2YmU2Mi1lYWQyLTRiZTYtOWY3Mi0zOGUwYzU5YTM5NzYiLCJ0eXAiOiJSZWZyZXNoIiwiYXpwIjoiaW50ZW5kZW5jaWEiLCJzaWQiOiJmOWQ1NTZkZS1mM2U3LTQ0MDQtYjI3MS02Yjg5MjY3NTg4M2YiLCJzY29wZSI6ImJhc2ljIGVtYWlsIHNlcnZpY2VfYWNjb3VudCBhY3Igd2ViLW9yaWdpbnMgcHJvZmlsZSByb2xlcyJ9.EQxlUxaXZPAtj9BOYYbjaf_xsNsjlxKWAzQdrNqALCqj2ZNmGoe45IS8CFu5bzIicLdftGLLJnmyFeeD6QTUSg"
```

Si el token no está activo devuelve:

```
{"active":false}
```

Si está activo devuelve información del token:

```
{
	"exp": 1754638306,
	"iat": 1754636506,
	"jti": "43228164-80b0-40f4-a637-edc0532c948c",
	"iss": "http://localhost:9090/realms/intendencia",
	"aud": [
		"http://localhost:9090/realms/intendencia",
		"account"
	],
	"sub": "6ca6be62-ead2-4be6-9f72-38e0c59a3976",
	"typ": "Refresh",
	"azp": "intendencia",
	"sid": "f9d556de-f3e7-4404-b271-6b892675883f",
	"acr": "1",
	"allowed-origins": [
		"http://localhost:8082"
	],
	"realm_access": {
		"roles": [
			"offline_access",
			"uma_authorization",
			"default-roles-intendencia"
		]
	},
	"resource_access": {
		"account": {
			"roles": [
				"manage-account",
				"manage-account-links",
				"view-profile"
			]
		}
	},
	"scope": "basic email service_account acr web-origins profile roles",
	"email_verified": true,
	"preferred_username": "intendencia1",
	"email": "fmartin@esla.com",
	"client_id": "intendencia",
	"username": "intendencia1",
	"token_type": "Refresh",
	"active": true
}
```

# Obtener las claves públicas habilitadas por el realm

Se usan por ejemplo para validar tokens cifrados.

```
curl -X POST "http://localhost:9090/realms/intendencia/protocol/openid-connect/certs
```

# Revocar un token de acceso o de refresco

```
POST /revoke HTTP/1.1
     Host: server.example.com
     Content-Type: application/x-www-form-urlencoded
     Authorization: Basic czZCaGRSa3F0MzpnWDFmQmF0M2JW

     token=45ghiukldjahdnhzdauz&token_type_hint=refresh_token
```

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

\Entorno\Maven\apache-maven-3.9.2-JAVA-21\bin\mvn -P postgresql clean package -Dmaven.test.skip=true
\Entorno\Java\jdk-21\bin\java -jar target\intendencia.clientes-1.0.jar
\Entorno\Java\jdk-21\bin\java -jar target\intendencia.clientes-1.0.jar --spring.config.location=C:/Proyectos/Pruebas/intendencia/application.properties

\Entorno\Maven\apache-maven-3.9.2-JAVA-21\bin\mvn spring-boot:run -Dspring.profiles.active=postgresql

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

# Entorno Virtual
## Pre-requisitos:
- pip install virtualenv
## Pasos
1. Crear entorno virtual: `virtualenv {nombreEntornoVirtual}`
2. Activar entorno virtual:
    1. `cd {nombreEntornoVirtual}`
    2. `cd Scripts`
    3. `. activate`
3. Desactivar entorno virtual: `deactivate`

# Dependencias
Dentro del entorno virtual (venv) se tienen que instalar las dependencias del archivo **requirements.txt** con el siguiente comando: `pip install -r requirements.txt`

# Django - REST API - JWT Authentication
Esta aplicación contiene las bases para comenzar el desarrollo de una API REST con Autenticación con JWT utilizando el framework Django (Python).

Están implementadas las siguientes funcionalidades base:
- Registro de usuario
- Inicio de sesión
- Refresco de los token **refresh** y **access**
- Cierre de sesión
- Obtencion de los datos del usuario
- Obtención y actualización de los datos del perfil del usuario
- Obtención y actualización del avatar del usuario

El identificador único utilizado para el usuario en las anteriores funcionalidades es el **email**.

## Endpoints disponibles
Las anteriores funcionalidades se ofrecen en las siguientes rutas relativas:
- **POST** /register/ 
    - **Request Body:** <pre>`{"username":"usuario","email":"usuario@mail.com","password":"conSegura"}`</pre>
    - **Response Body** <pre>```{"id":2,"username":"usuario","email":"usuario@mail.com","tokens":{"refresh":"valor_refresh_token","access":"valor_access_token"}}```</pre>

- **POST** /login/
    - **Request Body:** <pre>```{"email":"usuario@mail.com","password":"conSegura"}```</pre>
    - **Response Body:** <pre>```{"id":2,"username":"usuario","email":"usuario@mail.com","tokens":{"refresh":"valor_refresh_token","access":"valor_access_token"}}```</pre>

- **POST** token/refresh/
    - **Request Body:** <pre>```{"refresh":"valor_refresh_token"}```</pre>
    - **Response Body:** <pre>```{"access":"valor_nuevo_access_token","refresh":"valor_nuevo_refresh_token"}```</pre>

- **POST** logout/
    - **Headers:** <pre>`Authorization: Bearer valor_access_token`</pre>
    - **Request Body:** <pre>```{"refresh":"valor_refresh_token"}```</pre>
    - **Response Body:** <pre>```empty```</pre>

- **GET** /
    - **Headers:** <pre>`Authorization: Bearer valor_access_token`</pre>
    - **Response Body:** <pre>```{"id":2,"username":"usuario","email":"usuario@mail.com"}```</pre>

- **GET** /profile/
    - **Headers:** <pre>`Authorization: Bearer valor_access_token`</pre>
    - **Response Body:** <pre>```{"bio":"Info del perfil"}```</pre>

- **PUT** /profile/
    - **Headers:** <pre>`Authorization: Bearer valor_access_token`</pre>
    - **Request Body:** <pre>```{"bio":"Nueva info del perfil"}```</pre>
    - **Response Body:** <pre>```{"bio":"Nuevo info del perfil"}```</pre>



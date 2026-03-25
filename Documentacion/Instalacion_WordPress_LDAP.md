Despliegue de Aplicación Web: WordPress
Fase: Integración de Servicios (Día 12)
Alumno: Jesús González Ruiz

1. Objetivo
El objetivo de esta fase es desplegar un Gestor de Contenidos (CMS) corporativo (WordPress) para la empresa Oficinas Delta S.L., y prepararlo para que la autenticación de los usuarios se realice a través del servidor central OpenLDAP previamente configurado.

2. Creación de la Base de Datos
Se ha configurado un espacio dedicado en MariaDB para que WordPress almacene sus datos, garantizando la seguridad mediante un usuario específico. Comandos ejecutados en MySQL:

CREATE DATABASE wordpress;
CREATE USER 'wp_user'@'localhost' IDENTIFIED BY 'Admin1234';
GRANT ALL PRIVILEGES ON wordpress.* TO 'wp_user'@'localhost';
FLUSH PRIVILEGES;

3. Despliegue de la Aplicación y Permisos
Se han descargado los archivos oficiales de WordPress y se han ubicado en el directorio raíz del servidor web Apache (/var/www/html/wordpress). 

Para evitar problemas de lectura y escritura a la hora de subir archivos o instalar plugins, se han asignado los permisos correctos al usuario interno de Apache (www-data) utilizando los comandos chown y chmod.

4. Instalación Gráfica y Preparación LDAP
Una vez completada la configuración base, se ha procedido a la instalación gráfica a través del navegador web local (http://localhost/wordpress). 

Finalmente, dentro del panel de administración, se ha instalado y activado el plugin de integración "Simple LDAP Login". Este módulo es el que permitirá que los empleados puedan iniciar sesión en la Intranet utilizando sus credenciales centralizadas del Directorio Activo (Servidor LIVA).
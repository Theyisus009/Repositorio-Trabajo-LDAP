Despliegue de Aplicación Web: MediaWiki
Fase: Integración de Servicios (Día 13)
Alumno: Jesús González Ruiz

1. Objetivo
El objetivo de esta fase es desplegar una plataforma de base de conocimiento (MediaWiki) para la gestión documental de la empresa Oficinas Delta S.L., dejándola preparada para su futura integración con la autenticación centralizada OpenLDAP.

2. Creación de la Base de Datos
Se ha configurado una base de datos independiente en MariaDB para aislar los datos de la wiki del resto de aplicaciones. Comandos ejecutados en MySQL:

CREATE DATABASE mediawiki;
CREATE USER 'wiki_user'@'localhost' IDENTIFIED BY 'Admin1234';
GRANT ALL PRIVILEGES ON mediawiki.* TO 'wiki_user'@'localhost';
FLUSH PRIVILEGES;

3. Despliegue de la Aplicación y Permisos
Se ha descargado la versión estable de MediaWiki (LTS) y se ha extraído en el directorio de publicaciones del servidor Apache (/var/www/html/mediawiki). Además, se instaló la extensión php-intl necesaria para el funcionamiento del CMS.

Para garantizar el correcto funcionamiento del instalador y la futura carga de archivos multimedia, se han asignado la propiedad y permisos recursivos al usuario de Apache (www-data) mediante los comandos chown y chmod.

4. Configuración y Preparación LDAP
Se ha completado la instalación a través de la interfaz web (http://localhost/mediawiki), conectando la aplicación con su base de datos. El archivo de configuración resultante (LocalSettings.php) se ha movido al directorio raíz de la wiki de forma segura.

Para la integración con el Directorio Activo, MediaWiki utiliza extensiones que se añaden directamente al archivo LocalSettings.php, lo que permitirá que los usuarios del servidor LIVA inicien sesión sin necesidad de crear cuentas locales nuevas
Preparación del Entorno Web (LAMP) para Integración LDAP
Fase: Despliegue de Servicios Web
Alumno: Jesús González Ruiz

1. Objetivo del Despliegue
Para cumplir con los requisitos de la empresa Oficinas Delta S.L., se requiere que el sistema de Autenticación Centralizada (LDAP) gestione el acceso no solo al sistema operativo, sino también a las aplicaciones web corporativas (WordPress, MediaWiki y Moodle).

Para alojar estas aplicaciones, se ha configurado la máquina cliente (Ubuntu Desktop) para que actúe también como Servidor Web, instalando para ello un entorno LAMP completo.

2. Instalación de Paquetes (Pila LAMP)
Se han instalado los siguientes servicios en la máquina Ubuntu:

Apache2: Servidor web encargado de procesar las peticiones HTTP y mostrar las páginas.

MariaDB: Sistema de gestión de bases de datos relacionales (fork de MySQL) para almacenar el contenido de las aplicaciones.

PHP: Lenguaje de programación del lado del servidor requerido por WordPress, MediaWiki y Moodle.

Comando de instalación ejecutado:

Bash
sudo apt install apache2 mariadb-server php libapache2-mod-php php-mysql php-ldap php-xml php-mbstring php-curl php-gd php-zip -y
Nota Técnica: Es de vital importancia la inclusión del paquete php-ldap. Este módulo es el traductor que permitirá que el código PHP de las páginas web pueda comunicarse e interrogar directamente al servidor OpenLDAP a través del puerto 389.

3. Verificación del Servicio
Se ha comprobado el correcto funcionamiento del servidor web accediendo a la dirección local (http://localhost) a través del navegador web, obteniendo como respuesta la página por defecto de Apache2 ("Apache2 Ubuntu Default Page"), lo que confirma que el puerto 80 está abierto y escuchando peticiones correctamente.

El sistema está listo para comenzar el despliegue de las aplicaciones web.
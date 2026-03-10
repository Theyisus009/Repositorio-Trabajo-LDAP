Instalación y Configuración Base de OpenLDAP
Fase: Despliegue del Servicio de Directorio (Backend)
Alumno: Jesús González Ruiz

1. Instalación de Paquetes en el Servidor
Una vez el sistema base Ubuntu Server está operativo, se ha procedido a la instalación del motor de base de datos del directorio activo.

Se han instalado los siguientes paquetes mediante apt:

slapd: Es el demonio (servicio) principal de OpenLDAP. Es el programa que se queda escuchando en el puerto 389 las peticiones de los clientes.

ldap-utils: Conjunto de herramientas de cliente por línea de comandos (como ldapsearch, ldapadd) necesarias para interactuar con la base de datos localmente.

2. Reconfiguración del Dominio (dpkg-reconfigure slapd)
Por defecto, la instalación rápida de Ubuntu configura el árbol LDAP basándose en el nombre de la máquina. Para adaptarlo al proyecto, se ha reconfigurado el servicio estableciendo los siguientes parámetros clave:

Dominio DNS Base: delta.local

Base DN (Distinguished Name): dc=delta,dc=local

Organización: Oficinas Delta S.L.

Contraseña de Administrador: Configurada de forma segura para la gestión del directorio.

Motor de Base de Datos: MDB (Memory-Mapped Database), estándar actual y muy eficiente para el hardware del LIVA.

3. Verificación del Servicio
Tras la configuración, se ha comprobado el estado del demonio con systemctl status slapd, confirmando que el servicio se encuentra en estado active (running) y escuchando peticiones correctamente.
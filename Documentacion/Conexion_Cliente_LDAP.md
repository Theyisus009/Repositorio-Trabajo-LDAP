Conexión del Cliente Frontend al Servidor LDAP
Fase: Integración y Autenticación Centralizada
Alumno: Jesús González Ruiz

1. Configuración del Cliente Linux
Para que el equipo de trabajo (Ubuntu Desktop) permita el inicio de sesión a los usuarios del Directorio Activo, se han instalado los paquetes cliente que actúan como "puente" entre el sistema operativo local y el servidor LDAP:

libnss-ldapd: Modifica el archivo de resolución de nombres (/etc/nsswitch.conf) para que el sistema busque usuarios en la base de datos LDAP remota cuando no los encuentre localmente.

libpam-ldapd: Integra la autenticación en red con los módulos PAM de Linux, permitiendo verificar contraseñas contra el directorio.

Parámetros configurados:

URI del servidor LDAP: ldap://[IP_DEL_SERVIDOR]/

Base DN: dc=delta,dc=local

2. Creación Automática de Directorios Base (Home)
Los usuarios de red no tienen una carpeta personal creada físicamente en los ordenadores cliente hasta que inician sesión por primera vez.

Para solucionar esto de forma transparente, se ha ejecutado la utilidad pam-auth-update y se ha activado el módulo de creación de directorios al inicio de sesión (pam_mkhomedir). Este módulo se encarga de crear la carpeta /home/usuario y copiar los archivos base en el instante en que el login es exitoso.

3. Pruebas de Validación y Resultado Final
Se han realizado las siguientes comprobaciones de éxito en el equipo cliente:

Resolución de identidades: El comando id mlopez devuelve correctamente los datos inyectados en el servidor LIVA (UID 10001, GID 10000), demostrando que el puente NSS funciona.

Autenticación real (Login): Al ejecutar su - mlopez e introducir la contraseña en red, el sistema ha verificado el hash en el servidor OpenLDAP, ha creado la carpeta /home/mlopez y ha concedido acceso a la terminal como la empleada de Ventas. (Nota: El aviso sobre el ID del grupo es el comportamiento esperado y no interfiere con el acceso).

El sistema de Autenticación Única (SSO) de Oficinas Delta S.L. es 100% funcional.
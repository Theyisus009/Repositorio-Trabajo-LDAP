Creación de Cuentas de Usuario
Fase: Población del Directorio
Alumno: Jesús González Ruiz

1. Diseño de los Objetos Usuario
Para que los usuarios creados en LDAP puedan iniciar sesión en máquinas Linux, no basta con que sean simples contactos. Deben tener características de un sistema Unix. Se ha añadido la clase de objeto posixAccount, definiendo atributos clave:

uidNumber: ID de usuario único (ej. 10000 para Juan, 10001 para María).

gidNumber: ID del grupo principal al que pertenecen.

homeDirectory: Ruta de su carpeta personal (ej. /home/jgarcia).

loginShell: El intérprete de comandos por defecto (/bin/bash).

2. Seguridad en las Contraseñas (Hashing)
Siguiendo las mejores prácticas de seguridad, las contraseñas no se han almacenado en texto plano en los scripts .ldif.
Se ha utilizado la utilidad slappasswd para generar un hash seguro de la contraseña utilizando el algoritmo SSHA. Este hash seguro es el que se ha inyectado en el atributo userPassword.

3. Ejecución
Se han inyectado en la rama ou=People del directorio dos usuarios de prueba mediante el comando ldapadd:

jgarcia (Perfil de Dirección/Administración)

mlopez (Perfil de Empleado estándar)

Con este hito, el servidor Backend (Directorio Activo) queda completamente funcional y poblado. El siguiente paso será configurar los equipos cliente.
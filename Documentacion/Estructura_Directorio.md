Población del Directorio LDAP

Fase: Creación de Unidades Organizativas (OUs)
Alumno: Jesús González Ruiz

1. Diseño Lógico de la Organización

Para mantener un orden escalable dentro de Oficinas Delta S.L., he diseñado una jerarquía básica basada en el estándar de la industria. El árbol (DIT - Directory Information Tree) se divide en dos grandes ramas colgando del dominio base (dc=delta,dc=local):

ou=People: Unidad Organizativa destinada a almacenar todos los objetos de tipo usuario (empleados de la empresa).

ou=Groups: Unidad Organizativa destinada a almacenar los grupos de seguridad o departamentos (ej. RRHH, Ventas, Sistemas), lo que facilitará la futura asignación de permisos compartidos.

2. Ejecución del Script LDIF

Para inyectar esta estructura en el servidor Ubuntu, he creado un archivo en formato de intercambio de datos LDAP (.ldif) y he utilizado la herramienta cliente ldapadd.

El comando ejecutado ha sido:
ldapadd -x -D "cn=admin,dc=delta,dc=local" -W -f 01_estructura_base.ldif

Parámetros utilizados:

-x: Autenticación simple.

-D: Especifica el usuario Bind DN (el administrador del dominio).

-W: Obliga al sistema a preguntar la contraseña por consola (para mayor seguridad y no dejarla escrita en el historial).

-f: Especifica el fichero fuente a leer.

3. Verificación

Finalmente, he validado que las Unidades Organizativas se han escrito correctamente en la base de datos MDB utilizando el comando de consulta:
ldapsearch -x -LLL -b "dc=delta,dc=local" dn

Ambas ramas (People y Groups) aparecen registradas correctamente, dejando el directorio preparado para la inserción de cuentas de usuario reales.
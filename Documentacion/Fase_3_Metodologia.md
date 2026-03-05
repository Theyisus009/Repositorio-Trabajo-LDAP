Fase 3: Metodología de Desarrollo y Planificación
Metodología Elegida: Agile (Kanban Personal)
Alumno: Jesús González Ruiz

1. Justificación de la Metodología
Para el desarrollo de la infraestructura LDAP, he elegido la metodología Agile adaptada a un entorno de trabajo individual. Avanzaré mediante Iteraciones o Sprints cortos.

¿Por qué es ideal para este proyecto de red?

Detección temprana de fallos: Si cometo un error en la configuración de las IPs en la primera fase, lo detectaré y corregiré de inmediato.

Prototipos funcionales: Cada paso me deja con un sistema que funciona de forma independiente.

2. Organización del Trabajo Individual
Al realizar el proyecto en solitario, asumo un rol integral ("Full-Stack" de Sistemas):

Rol de Backend (Servidor): Instalación del sistema en el LIVA, configuración de slapd y diseño lógico del árbol de directorio (.ldif).

Rol de Frontend (Cliente): Preparación de máquinas virtuales cliente y edición de los ficheros de autenticación (/etc/nsswitch.conf, /etc/pam.d/).

3. Herramientas de Planificación
Para autogestionar mis tareas utilizo:

Tablero Kanban: Con columnas de "Pendiente", "En Curso" y "Completado".

Control de Versiones (Git y GitHub): Para guardar mis scripts de configuración día a día, asegurando que si rompo el servidor, puedo volver a la versión anterior.
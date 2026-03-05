Fase 1: Análisis del Contexto y la Empresa

Nombre del Proyecto: Implementación de Directorio Activo en LIVA
Alumno: Jesús González Ruiz
Curso: 2º SMR

1. Descripción de la Empresa

Nombre de la empresa (Ficticia): "Oficinas Delta S.L."

Qué productos o servicios ofrece:
Es una gestoría administrativa que maneja datos sensibles de clientes. Necesitan que sus empleados accedan a carpetas compartidas y aplicaciones de gestión desde diferentes puestos de trabajo de forma segura.

Infraestructura Actual:

Hardware: 15 ordenadores de sobremesa (Windows/Linux) y 1 servidor de archivos básico (NAS).

Personal: 18 empleados, divididos entre Administrativos, Contables y Gerencia.

Departamentos: Contabilidad, Recursos Humanos y Dirección General.


2. Análisis de lo Existente (Problemática)

Cómo funciona actualmente:
La gestión de usuarios es totalmente descentralizada (Local), lo que genera caos administrativo.

Altas y Bajas Manuales: Cuando entra un contable nuevo, el administrador tiene que ir físicamente, ordenador por ordenador, creando la cuenta de usuario local.

Descontrol de Contraseñas: Cada usuario tiene una contraseña para iniciar sesión en su PC, otra distinta para acceder al NAS y otra para el correo. Esto provoca el uso de post-its pegados en los monitores (grave fallo de seguridad).

Seguridad Deficiente: No hay control centralizado. Si un empleado es despedido, su usuario sigue activo en los PCs locales hasta que el administrador recuerda borrarlo uno por uno.

¿Qué cosas podrían mejorar?

Centralización: Gestionar todas las cuentas de usuario y permisos desde un único panel de control.

Seguridad (SSO): Que una sola contraseña sirva para todo (Inicio de sesión, Carpetas compartidas, Impresoras).

Eficiencia: Reducir el tiempo de gestión de usuarios de horas a minutos.


3. Propuesta de Solución

Implementar un Servidor de Dominio (LDAP) utilizando un equipo de bajo consumo ECS LIVA.

Funcionalidades Clave:

Login Único (Roaming): El usuario puede sentarse en cualquier ordenador de la empresa, poner su usuario/contraseña, y acceder a su escritorio y archivos.

Gestión de Grupos: Permisos automáticos por departamento (ej. RRHH no puede ver carpetas de Contabilidad).

Eficiencia Energética: Servicio encendido 24/7 con un consumo eléctrico mínimo (<10W) gracias al hardware LIVA.
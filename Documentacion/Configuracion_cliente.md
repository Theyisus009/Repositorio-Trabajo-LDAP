Configuración del Equipo Cliente

Fase: Despliegue del Frontend (Cliente Linux)
Alumno: Jesús González Ruiz

1. Justificación del Entorno Cliente

Para comprobar que la Autenticación Centralizada (LDAP) funciona correctamente, es necesario configurar un equipo cliente que simule el ordenador de un empleado de Oficinas Delta S.L. (como Juan García o María López).

En lugar de utilizar cuentas locales, este equipo estará configurado para preguntar al servidor LDAP (liva-server) si las credenciales introducidas son válidas antes de dejarles iniciar sesión.

2. Especificaciones de la Máquina Virtual

Se ha creado una nueva máquina virtual en VirtualBox con las siguientes características:

Nombre: Cliente_Ubuntu

Sistema Operativo: Ubuntu Desktop 22.04 LTS (con entorno gráfico para simular un puesto de trabajo real).

Red (Crítico): Configurada en modo Adaptador Puente (Bridged) para que esté en la misma red física que el servidor LDAP.

3. Próximos pasos

Instalar el sistema operativo base del cliente.

Hacer un "ping" al servidor LDAP para comprobar la conectividad entre ambas máquinas.

Instalar los paquetes cliente (libnss-ldap, libpam-ldap) para conectar el proceso de inicio de sesión (Login) de este PC con nuestra base de datos remota.
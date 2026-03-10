Configuración del Entorno de Pruebas (Laboratorio)

Fase: Despliegue de Servidor Base
Alumno: Jesús González Ruiz

1. Justificación del Entorno Virtualizado

Antes de desplegar el sistema LDAP directamente sobre el hardware físico ECS LIVA, he decidido montar un entorno de pruebas ("Staging") utilizando VirtualBox.

Esto me permite, siguiendo la metodología Agile, realizar "snapshots" (instantáneas) y probar configuraciones arriesgadas sin miedo a romper un sistema físico, ahorrando mucho tiempo de reinstalación si algo falla.

2. Especificaciones de la Máquina Virtual (Simulador LIVA)

He configurado la máquina virtual para que imite los recursos limitados pero eficientes del hardware real:

Nombre de la Máquina: Servidor_LDAP_LIVA

Sistema Operativo: Ubuntu Server 22.04 LTS (Jammy Jellyfish) - Versión sin GUI para optimizar recursos.

Memoria RAM: 2048 MB (2 GB)

Procesador: 1 vCPU

Almacenamiento: 20 GB de Disco Duro Virtual (VDI) dinámico.

Configuración de Red (CRÍTICO): La tarjeta de red está configurada en modo Adaptador Puente (Bridged). Esto es fundamental para que el servidor virtual obtenga una IP real del router de mi casa/instituto y los futuros clientes puedan hacerle "ping" y conectarse al puerto 389 de LDAP.

3. Próximos pasos

Iniciar la máquina virtual con la ISO de Ubuntu Server.

Realizar la instalación del SO configurando una IP estática.
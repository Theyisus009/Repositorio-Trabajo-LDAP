Fase 2: Diseño Técnico y Vinculación Curricular
Nombre del proyecto: Implementación de Directorio Activo en LIVA
Alumno: Jesús González Ruiz
Curso: 2º SMR

1. Objetivos del Proyecto
El objetivo principal es desplegar una infraestructura de Autenticación Centralizada basada en Software Libre (OpenLDAP) sobre Hardware Eficiente (LIVA).

Este sistema permitirá:

Autenticación Única (SSO): Los usuarios usarán las mismas credenciales para Iniciar Sesión en los equipos y acceder a los Recursos Compartidos en red.

Gestión Centralizada: Como administrador, podré crear, modificar o bloquear usuarios desde un único punto sin desplazarme al puesto físico de cada empleado.

Green IT (Informática Verde): Utilizar un servidor (ECS LIVA) que consuma un 90% menos de energía que una torre convencional, ideal para un servicio que debe estar encendido 24/7.

2. Arquitectura del Sistema (Stack Tecnológico)
Hardware Servidor: Mini PC ECS LIVA (Modelo de bajo consumo).

Sistema Operativo: Ubuntu Server 22.04 LTS (Instalación limpia sin entorno gráfico).

Software de Directorio: OpenLDAP (slapd).

Protocolos de Red:

LDAP (Puerto 389) para comunicación estándar.

LDAPS (Puerto 636) para autenticación segura.

Clientes: Equipos con distribuciones Linux (paquetes libpam-ldap y nss-ldap).

3. Vinculación con los Módulos de SMR
Este proyecto pone en práctica las competencias de los siguientes módulos:

Sistemas Operativos en Red (SOR): Instalación de Ubuntu Server, gestión de usuarios y grupos centralizados.

Seguridad Informática (SI): Implementación de ACLs para proteger la base de datos LDAP y contraseñas seguras.

Servicios en Red (SER): Configuración del servicio de directorio y conocimientos de red/DNS.
Instalación del Servidor Base y Configuración de Red

Fase: Despliegue del Backend
Alumno: Jesús González Ruiz

1. Instalación del Sistema Operativo

Se ha procedido a la instalación de Ubuntu Server 22.04 LTS en el entorno simulado del hardware LIVA.

Parámetros configurados durante la instalación:

Hostname: liva-server

Usuario Administrador: jesusadmin

Servicios Adicionales: Se ha instalado OpenSSH Server para permitir la administración remota desde el equipo principal, facilitando la copia de scripts y la monitorización.

2. Configuración de Red Estática (IP Fija)

Para que un servidor de Directorio Activo (LDAP) funcione correctamente y los clientes puedan encontrarlo, es estrictamente necesario que posea una dirección IP estática. Si usara DHCP (IP dinámica), la IP cambiaría al reiniciar y los clientes perderían la conexión al dominio.

Se ha configurado la interfaz de red (ej. enp0s3) en modo manual con los siguientes parámetros:

Dirección IP del Servidor LDAP: 192.168.1.250 (Ejemplo. Ajustar según la red del laboratorio).

Máscara de Subred: /24 (255.255.255.0)

Puerta de Enlace (Gateway): 192.168.1.1

Servidores DNS: 8.8.8.8 (Google DNS para salida a internet).

3. Comprobación de Conectividad

Tras el primer reinicio del sistema, se realizan las siguientes comprobaciones para asegurar que el servidor está listo para alojar el servicio LDAP:

Ping al Gateway: ping 192.168.1.1 (Éxito - Hay conexión con el router).

Ping a Internet: ping google.com (Éxito - Hay resolución DNS).

Ping desde el equipo Anfitrión: Abriendo una terminal en Windows/Linux base y ejecutando ping 192.168.1.250. (Éxito - La máquina virtual es visible en la red local gracias al Adaptador Puente).

Con el sistema base estable y comunicado en red, el servidor queda preparado para la instalación del demonio OpenLDAP (slapd).
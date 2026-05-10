# Registro de Trabajo - Día 19: Reconfiguración de Red y Rescate de Servicios

## Objetivos del Día
Restablecer la conectividad de red del Servidor LDAP tras la migración al entorno Proxmox, corrigiendo las discrepancias en el nombramiento de las interfaces de red paravirtualizadas.

## Acciones Realizadas

### 1. Diagnóstico de Conectividad
* **Problema detectado:** Al arrancar la VM 980 en Proxmox, el sistema operativo no reconocía la interfaz de red antigua (`enp0s3`), dejando al servidor en estado `DOWN` y sin dirección IP.
* **Identificación del hardware:** Mediante el comando `ip a`, se identificó la nueva interfaz de red VirtIO como `ens18`.

### 2. Reconfiguración de Netplan
* **Archivo editado:** `/etc/netplan/50-cloud-init.yaml`
* **Modificación:** Se actualizó el descriptor de la interfaz de `enp0s3` a `ens18`.
* **Asignación de Direccionamiento Estático:**
    * **IP Fija:** 192.168.1.250
    * **Máscara:** 24 (255.255.255.0)
    * **Gateway:** 192.168.1.1
    * **DNS:** 8.8.8.8

### 3. Aplicación y Verificación
* Se ejecutó `sudo netplan apply` para volcar la configuración al núcleo.
* Se verificó mediante `ip a` que la interfaz `ens18` se encuentra operativa y con la IP estática correctamente asignada.

## Estado Final
* **Servidor LDAP (980):** Operativo y visible en la red.
* **Siguiente paso:** Replicar el proceso en el Cliente Moodle (984) una vez finalice su transferencia al NAS y apuntar la configuración de autenticación LDAP a la nueva IP .250.
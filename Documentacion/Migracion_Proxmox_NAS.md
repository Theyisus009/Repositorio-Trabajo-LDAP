# Migración de Infraestructura: De VirtualBox a Proxmox VE (vía NAS)

Este documento detalla el proceso técnico seguido para migrar las máquinas virtuales del proyecto "Oficinas Delta" desde un entorno local de desarrollo hacia un entorno de virtualización profesional gestionado con Proxmox y almacenamiento centralizado.

## 1. Exportación y Preparación de Discos
Para asegurar la compatibilidad, se procedió a:
* Apagar las máquinas virtuales en **VirtualBox**.
* Localizar los archivos de disco virtual en formato `.vmdk`.
* Verificar que los discos no tuvieran snapshots pendientes para evitar inconsistencias en los datos.

## 2. Transferencia al Almacenamiento en Red (NAS)
Se utilizó un servidor NAS (Synology) como repositorio central para Proxmox.
* **Ruta de destino:** `/1DAM_A/images/`
* **Identificadores asignados:**
    * **VM 980:** Servidor LDAP (Gestión de identidades).
    * **VM 984:** Cliente Ubuntu con plataforma Moodle (Oficinas Delta).
* Se realizó la carga de los archivos `.vmdk` asegurando que la transferencia finalizara al 100% (verificación de integridad).

## 3. Configuración de Hardware en Proxmox
Se crearon las instancias en el nodo Proxmox aplicando los siguientes recursos optimizados para el entorno de producción de la empresa:

| Componente | Configuración | Razón Técnica |
| :--- | :--- | :--- |
| **CPU** | 4 Cores (Host) | Gestión fluida de peticiones Apache/PHP y Base de Datos. |
| **RAM** | 8.00 GiB | Soporte para el entorno gráfico de Ubuntu Desktop y caché de Moodle. |
| **Pantalla** | SPICE (qxl) | Optimización del refresco de imagen y puntero en consola web. |
| **Red** | VirtIO (Bridge) | Maximizar el rendimiento de red paravirtualizada. |
| **Controlador SCSI** | VirtIO SCSI single | Mayor eficiencia en operaciones de entrada/salida (I/O). |

## 4. Importación y Limpieza de Discos
Una vez los archivos estuvieron disponibles en el NAS:
1. Se utilizó la opción de **"Despegar" (Detach)** para desconectar los discos vacíos generados por defecto por Proxmox.
2. Se eliminaron dichos discos (`.qcow2`) para liberar espacio en el almacenamiento.
3. Se vinculó el disco importado (`.vmdk`) mediante el archivo descriptor del NAS.
4. Se configuró el **Boot Order** (Orden de arranque) en las opciones de la VM para priorizar el disco con el sistema operativo instalado.

## 5. Verificación Final
* Comprobación del arranque del kernel de Ubuntu.
* Verificación de conectividad entre el cliente (984) y el servidor de nombres/LDAP (980).
* Test de acceso a la plataforma Moodle mediante la IP asignada en el clúster.
# Integración de Aplicaciones Web con Autenticación Centralizada LDAP

Este proyecto documenta la configuración y despliegue de una infraestructura de red donde un servidor **OpenLDAP** centraliza la gestión de usuarios para múltiples servicios web (**GLPI, Moodle y WordPress**).

## 🌍 Escenario Técnico
* **Servidor LDAP:** Ubuntu Server 22.04 (`10.4.0.20`)
* **Cliente de Servicios:** Ubuntu Desktop con stack LAMP (`10.4.0.X`)
* **Base DN:** `dc=delta,dc=local`
* **Unidad Organizativa:** `ou=People,dc=delta,dc=local`
* **Administrador del Directorio:** `cn=admin,dc=delta,dc=local`

---

## 🛠️ Configuración por Servicio

### 1. GLPI (Gestión de Activos)
Se ha vinculado el inventario para permitir el acceso de técnicos mediante el protocolo LDAP.
- **Servidor:** `10.4.0.20`
- **Filtro de conexión:** `(objectClass=person)`
- **Campo de login:** `uid`

### 2. Moodle (Campus Virtual)
Configuración del plugin de autenticación LDAP nativo para la matriculación automática de alumnos y profesores.
- **Contextos:** `ou=People,dc=delta,dc=local`
- **Mapeo de Atributos:**
    - Nombre: `givenName`
    - Apellidos: `sn`
    - Correo: `mail`
- **Nota:** Se habilitó la creación de usuarios externos para automatizar el alta en la plataforma.

### 3. WordPress (Intranet Corporativa)
Implementación mediante el plugin *Active Directory / LDAP Integration* de miniOrange.
- **Search Base:** `ou=People,dc=delta,dc=local`
- **Username Attribute:** `uid`

---

## 🔍 Resolución de Problemas (Troubleshooting)

Durante la fase de integración se detectaron y solventaron los siguientes incidentes críticos:

### A. Errores de Ruta (DN)
Se detectó un fallo de autenticación `No such object (32)` debido a una errata en la unidad organizativa (`ou=Poeple` en lugar de `ou=People`). Se verificó la ruta correcta mediante:
```bash
ldapsearch -x -b "dc=delta,dc=local" "uid=jgarcia" dn
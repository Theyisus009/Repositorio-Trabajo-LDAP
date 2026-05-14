# Proyecto RA5: Integración de Servicios con OpenLDAP - I.E.S. San Sebastián

## 📂 Descripción del Proyecto
Este documento detalla la configuración y puesta en marcha de un sistema de gestión de identidades centralizado utilizando **OpenLDAP** en un servidor Ubuntu, integrado con tres servicios fundamentales: **GLPI**, **Moodle** y **WordPress**.

---

## 🛠️ Configuración del Servidor LDAP (Ubuntu)
Se ha configurado un servidor OpenLDAP gestionado mediante **LDAP Account Manager (LAM)**, estableciendo la siguiente estructura de Directorio:
- **Base DN:** `dc=delta,dc=local`
- **OU People:** Contenedor de usuarios (ej. `jgonz`, `mlopez`).
- **OU Groups:** Contenedor de grupos de seguridad (`Jefes`, `Trabajadores`).

### Ajustes Críticos en LAM:
- El atributo de identificación de usuario se ha establecido en `uid`.
- Los grupos se han configurado como `posixGroup`, utilizando el atributo `memberUid` para listar a sus integrantes.

---

## ⚙️ Integración con GLPI (Gestión de Inventario y Tickets)
GLPI se ha configurado para realizar una importación dinámica de usuarios y asignación de perfiles basada en grupos.

### Logros Técnicos:
1.  **Mapeo de Perfiles:**
    - **Jefes:** Asignación automática del perfil `Super-Admin`.
    - **Trabajadores (María):** Asignación del perfil `Self-Service`.
2.  **Interfaz Simplificada:** Configuración del perfil de María para mostrar una interfaz reducida (solo creación de tickets y seguimiento), optimizando la usabilidad para empleados no técnicos.
3.  **Reglas de Autorización:** Implementación de reglas basadas en el atributo `(LDAP) Grupo` y `DistinguishedName`.

---

## 🎓 Integración con Moodle 4.4.x (LMS)
Configuración de la autenticación externa para permitir el acceso unificado.

### Configuración Final:
- **Tipo de búsqueda de grupos:** Configurado en `Usuarios y Grupos` para habilitar el mapeo de roles.
- **Atributo de miembro:** `uid`.
- **Atributo de grupo:** `memberUid`.
- **Roles del Sistema:** Vinculación del rol de **Gestor** al contexto `ou=Groups` con el filtro `cn=Jefes`.

---

## 🌐 Integración con WordPress (CMS)
Implementación de autenticación LDAP mediante plugin, superando limitaciones de licenciamiento.

### Estrategia de Roles:
- **Política de Privilegio Mínimo:** Se ha establecido el rol por defecto `Subscriber` (Suscriptor) para todas las nuevas altas del LDAP.
- **Persistencia de Roles:** Activación de la opción `Keep existing roles` para permitir la elevación manual de usuarios (Jefes) a `Administrator` sin que el plugin revierta los cambios en el siguiente login.
- **Dual Login:** Configuración que permite la coexistencia de la cuenta administrativa local y las cuentas federadas del LDAP.

---

## 🏁 Conclusiones del RA5
La arquitectura final demuestra un entorno profesional de **Single Sign-On (SSO)** donde:
- La creación de un usuario en el LAM le otorga acceso inmediato a las tres plataformas.
- La pertenencia a grupos define automáticamente su capacidad de acción en el entorno de soporte (GLPI).
- Se garantiza la escalabilidad y seguridad de la infraestructura del centro educativo.

---
**Autor:** Jesús González
**Fecha:** Mayo 2026
**Ubicación:** Huelva, España

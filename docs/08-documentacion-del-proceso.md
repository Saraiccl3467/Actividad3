# 8. Documentación del proceso de desarrollo

## 8.1 Metodología y organización

El equipo de cuatro integrantes trabajó con un enfoque ágil basado en Scrum: el trabajo se dividió en historias de usuario priorizadas en un backlog, se registraron reuniones diarias (daily standups) y cada integrante tuvo tareas asignadas con criterios de aceptación y una definición de terminado.

| Herramienta | Uso |
|---|---|
| Mendix Studio Pro | Desarrollo low code: modelo de dominio, microflujos y páginas |
| GitHub (issues, etiquetas y milestones) | Backlog, asignación de tareas y seguimiento del avance |
| Lucidchart / Domain Model de Mendix | Diagrama entidad-relación |
| YouTube (video oculto) | Video demostrativo de los microflujos |

**Repositorio:** https://github.com/Saraiccl3467/Actividad3 — el trabajo de esta actividad está agrupado en el milestone [Actividad 4 - Gestión de eventos (Mendix)](https://github.com/Saraiccl3467/Actividad3/milestone/2).

El backlog quedó en 21 issues: 10 historias de usuario (HU-01 a HU-10), 10 entregables (E01 a E10) y una bitácora de reuniones diarias. Cada historia de usuario incluye:

- la historia en formato *Como <rol>, quiero <acción> para <beneficio>*;
- criterios de aceptación como lista de verificación;
- los elementos de Mendix que la implementan (entidades, microflujos, páginas);
- una definición de terminado común: funciona en Studio Pro, está probada y tiene su captura en este documento.

## 8.2 Decisiones clave

| # | Decisión | Por qué |
|---|---|---|
| 1 | Reutilizar el repositorio de la actividad anterior y separar el trabajo con etiquetas (`Actividad 3` / `Actividad 4`) y un milestone por actividad. | Conservar el historial del equipo sin mezclar los issues del sistema de inventario con los de la app de eventos. |
| 2 | Llevar el backlog como issues de GitHub con prioridad (Alta, Media, Baja) y responsable. | Cualquier integrante ve qué falta, quién lo tiene y en qué orden atacarlo. |
| 3 | Modelo de datos con una entidad intermedia `Registro` entre `Evento` y `Asistente`. | Un asistente puede ir a varios eventos y un evento tiene varios asistentes; `Registro` guarda además la fecha de registro y si asistió. |
| 4 | Convención de nombres en Mendix: `ACT_`, `SUB_`, `VAL_`, `SNIP_`, `ENUM_`. | Hace evidente qué elementos son reutilizables y facilita encontrarlos en el proyecto. |
| 5 | Centralizar las notificaciones en un solo sub-microflujo (`SUB_Notificacion_Enviar`). | Cuatro funcionalidades notifican a los asistentes; así la lógica vive en un solo lugar. |
| 6 | Cancelar eventos cambiando su estado en lugar de borrarlos. | Conservar el historial con el cliente y no perder asistentes ni tareas asociadas. |
| 7 | Dos roles de usuario: Organizador y Asistente, con reglas de acceso por entidad. | Proteger los datos de clientes de alto perfil; cada usuario solo ve lo suyo. |
| 8 | Guardar en `mendix/` el paquete exportado (`.mpk`) de cada entrega. | El proyecto de Mendix se versiona en su propio Team Server; el `.mpk` deja una copia de cada entrega junto a la documentación. |

## 8.3 Retos y cómo se resolvieron

| Reto | Solución |
|---|---|
| El repositorio asignado ya contenía los issues de la Actividad 3, que podían confundirse con los nuevos. | Se etiquetaron y cerraron como historial, y los nuevos llevan el prefijo `[A4]`, la etiqueta `Actividad 4` y su propio milestone. |
| Coordinar a cuatro personas con tareas que dependen unas de otras: las pantallas y el panel necesitan el modelo de datos terminado. | Se priorizó primero el modelo de datos (E02) y la lógica base (E03), y cada issue indica de qué entidades y microflujos depende. |
| El proyecto de Mendix no se versiona en GitHub como código normal. | Se exporta el paquete `.mpk` de cada entrega a la carpeta `mendix/` y el avance se sigue en los issues. |
| Asegurar que "terminado" signifique lo mismo para todos. | Se definió una definición de terminado común en cada historia de usuario. |

### Retos durante la implementación

*Completar conforme avance el desarrollo en Mendix.*

| Fecha | Reto | Solución | Issue |
|---|---|---|---|
| | | | |

## 8.4 Aprendizajes

*Completar al cierre de la actividad, para la presentación final (E09).*

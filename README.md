# Actividad 4 — App de gestión de eventos corporativos (Mendix)

Prototipo low code en **Mendix Studio Pro** para una empresa que organiza eventos corporativos para clientes de alto perfil: creación de eventos, registro de asistentes, asignación y seguimiento de tareas, y comunicación con los participantes.

> El repositorio se llama `Actividad3` porque se reutilizó del equipo; los issues de la Actividad 3 (sistema de inventario) están cerrados y agrupados en su propio milestone.

## Equipo

| Integrante | Usuario de GitHub | Responsable de |
|---|---|---|
| Sarai Cecilio Rascon | Saraiccl3467 | Pantallas, registro de asistentes, roles, presentación, bitácora |
| Matías Garrido Hernández | matt569 | Product Owner: definición del producto, componentes reutilizables, documentación, repositorio |
| Kevin Ramos Alarcon | RyuuJS1 | Modelo de datos (ERD), microflujos, eventos y tareas |
| Galilea Valencia Velázquez | galis-457-Developer | Pruebas, video demostrativo, notificaciones, asistencia |

## Funcionalidades

| Módulo | Historia de usuario |
|---|---|
| Eventos | [HU-01 Crear evento](https://github.com/Saraiccl3467/Actividad3/issues/13) · [HU-02 Editar/cancelar](https://github.com/Saraiccl3467/Actividad3/issues/14) · [HU-07 Calendario](https://github.com/Saraiccl3467/Actividad3/issues/19) |
| Asistentes | [HU-03 Registro](https://github.com/Saraiccl3467/Actividad3/issues/15) · [HU-09 Confirmar asistencia](https://github.com/Saraiccl3467/Actividad3/issues/21) |
| Tareas | [HU-04 Asignar](https://github.com/Saraiccl3467/Actividad3/issues/16) · [HU-05 Seguimiento](https://github.com/Saraiccl3467/Actividad3/issues/17) |
| Comunicación | [HU-06 Notificaciones](https://github.com/Saraiccl3467/Actividad3/issues/18) |
| General | [HU-08 Panel principal](https://github.com/Saraiccl3467/Actividad3/issues/20) · [HU-10 Roles](https://github.com/Saraiccl3467/Actividad3/issues/22) |

Tablero de trabajo: [milestone Actividad 4](https://github.com/Saraiccl3467/Actividad3/milestone/2).

## Modelo de datos (resumen)

- **Evento** 1 — * **Registro** * — 1 **Asistente**
- **Evento** 1 — * **Tarea**; **Asistente** 1 — * **Tarea** (responsable)
- **Notificacion**: mensajes enviados a los asistentes de un evento

## Convenciones en Mendix

| Prefijo | Uso | Ejemplo |
|---|---|---|
| `ACT_` | Microflujo que dispara un botón o acción | `ACT_Evento_Guardar` |
| `SUB_` | Sub-microflujo reutilizable | `SUB_Notificacion_Enviar` |
| `VAL_` | Validaciones | `VAL_Evento_Fechas` |
| `SNIP_` | Snippet (componente de UI reutilizable) | `SNIP_CalendarioEventos` |

## Estructura del repositorio

```
docs/          Documento Word, ERD y documentación del proceso
mendix/        Paquete exportado del proyecto (.mpk)
evidencias/    Capturas de pantalla y URL del video (YouTube oculto)
pruebas/       Casos de prueba y reporte de resultados
presentacion/  Presentación final (5–10 min)
```

## Cómo trabajamos

1. Cada tarea es un issue con etiqueta `Actividad 4` y milestone **Actividad 4**.
2. Al empezar un issue, comenta en él que ya lo estás trabajando y ve registrando tu avance.
3. Al terminar, marca la checklist del issue y ciérralo con un comentario de lo que se hizo.
4. Los errores encontrados en pruebas se abren como issue con la etiqueta `bug`.
5. Las reuniones diarias se registran en la [bitácora](https://github.com/Saraiccl3467/Actividad3/issues/33).

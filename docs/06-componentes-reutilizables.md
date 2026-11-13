# 6. Componentes reutilizables

Uno de los objetivos del prototipo es reutilizar componentes para desarrollar más rápido y facilitar el mantenimiento: si una regla o un elemento visual cambia, se modifica en un solo lugar y el cambio se refleja en todas las pantallas que lo usan. En Mendix esto se logra con tres tipos de elementos:

- **Snippets (`SNIP_`):** fragmentos de interfaz que se insertan en varias páginas.
- **Sub-microflujos (`SUB_`):** lógica de negocio que varios microflujos llaman.
- **Enumeraciones (`ENUM_`):** listas de valores compartidas por varias entidades.

## 6.1 Componentes de interfaz (snippets)

### SNIP_CalendarioEventos — Calendario de eventos

| | |
|---|---|
| **Qué es** | Snippet con el widget *Calendar* del Marketplace de Mendix que muestra los eventos por mes o por semana. |
| **Fuente de datos** | Lista de `Evento` con estado distinto de *Cancelado*, usando `FechaInicio` y `FechaFin`. |
| **Comportamiento** | Al dar clic en un evento abre su página de detalle. Permite cambiar entre vista mensual y semanal. |
| **Dónde se usa** | Panel principal del organizador (`Home_Organizador`, HU-08); página de eventos (`Evento_Calendario`, HU-07); inicio del asistente (`Home_Asistente`), donde solo ve sus eventos gracias a las reglas de acceso de su rol. |
| **Por qué se reutiliza** | El mismo calendario aparece en tres pantallas; si se cambian colores o la vista por defecto, se cambia una sola vez. |

### SNIP_FormularioAsistente — Formulario de registro de asistentes

| | |
|---|---|
| **Qué es** | Snippet con los campos de `Asistente`: nombre, correo, teléfono y empresa, con sus validaciones de campo obligatorio y formato de correo. |
| **Parámetro** | Objeto `Asistente`. |
| **Dónde se usa** | Registro desde el detalle del evento (`Registro_NewEdit`, HU-03); edición de datos del asistente (`Asistente_Edit`); alta rápida de un participante al asignar una tarea (`Tarea_NewEdit`, HU-04). |
| **Por qué se reutiliza** | Garantiza que un asistente se capture igual en cualquier pantalla, con las mismas validaciones. |

### SNIP_TarjetaIndicador — Tarjeta de indicador

| | |
|---|---|
| **Qué es** | Snippet de una tarjeta con un título, un número grande y un botón que lleva al listado correspondiente. |
| **Dónde se usa** | Cuatro veces en el panel principal (HU-08): eventos próximos, asistentes registrados, tareas pendientes y tareas atrasadas. |
| **Por qué se reutiliza** | Las cuatro tarjetas comparten diseño; cambiar el estilo de una cambia todas. |

## 6.2 Componentes de lógica (sub-microflujos)

| Sub-microflujo | Entrada → salida | Qué hace | Lo usan |
|---|---|---|---|
| `SUB_Evento_Validar` | `Evento` → Booleano | Valida campos obligatorios, que `FechaFin` ≥ `FechaInicio` y que `CupoMaximo` > 0; muestra el mensaje de validación en el campo con error. | `ACT_Evento_Guardar` (crear, HU-01 y editar, HU-02) |
| `SUB_Evento_ValidarCupo` | `Evento` → Booleano | Cuenta los registros del evento y verifica que no se supere el cupo. | `ACT_Asistente_Registrar` (HU-03) |
| `SUB_Notificacion_Enviar` | `Evento`, lista de `Asistente`, asunto, mensaje → `Notificacion` | Crea la notificación, la asocia a sus destinatarios y la deja visible en la app del asistente. | Cancelar evento (HU-02), confirmación de registro (HU-03), asignación de tarea (HU-04), comunicados (HU-06) |
| `SUB_Evento_CalcularAvance` | `Evento` → Decimal | Calcula tareas completadas ÷ tareas totales del evento (0 si no tiene tareas). | Detalle del evento (HU-05), panel principal (HU-08) |

`SUB_Notificacion_Enviar` es el caso más claro de reutilización: cuatro funcionalidades distintas notifican a los asistentes con un solo microflujo, así que si después se agrega el envío por correo electrónico, basta con cambiarlo ahí.

## 6.3 Enumeraciones compartidas

| Enumeración | Valores | Se usa en |
|---|---|---|
| `ENUM_EstadoEvento` | Planeado, En curso, Finalizado, Cancelado | `Evento`, calendario, panel |
| `ENUM_EstadoTarea` | Pendiente, En progreso, Completada, Atrasada | `Tarea`, seguimiento, panel |
| `ENUM_Prioridad` | Alta, Media, Baja | `Tarea` |

## 6.4 Resumen de reutilización

| Componente | Tipo | Veces que se usa |
|---|---|---|
| SNIP_CalendarioEventos | Snippet | 3 páginas |
| SNIP_FormularioAsistente | Snippet | 3 páginas |
| SNIP_TarjetaIndicador | Snippet | 4 tarjetas en el panel |
| SUB_Notificacion_Enviar | Sub-microflujo | 4 funcionalidades |
| SUB_Evento_Validar | Sub-microflujo | 2 funcionalidades |
| SUB_Evento_CalcularAvance | Sub-microflujo | 2 pantallas |
| SUB_Evento_ValidarCupo | Sub-microflujo | 1 funcionalidad |

> **Pendiente al implementar:** agregar una captura de cada snippet en Mendix Studio Pro y de las pantallas donde aparece, y confirmar los nombres finales de páginas y microflujos con el modelo que construya el equipo.

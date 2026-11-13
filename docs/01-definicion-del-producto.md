# 1. Definición del producto

## Contexto

La empresa organiza eventos corporativos para clientes de alto perfil. Hoy la planeación depende de hojas de cálculo, correos y mensajes sueltos, lo que provoca información duplicada, tareas que nadie sigue y asistentes que no reciben a tiempo los cambios del evento. La aplicación concentra en un solo lugar la planeación del evento, sus asistentes, el trabajo del equipo y la comunicación, con dos tipos de usuario:

- **Organizador:** crea y administra eventos, registra asistentes, asigna tareas y envía comunicados.
- **Asistente:** consulta los eventos a los que está registrado, sus tareas y los mensajes que recibe.

## Funcionalidades esenciales

### 1.1 Creación y configuración de eventos

Permite al organizador dar de alta un evento con nombre, descripción, cliente, lugar, fecha y hora de inicio y fin, y cupo máximo. El evento nace con estado **Planeado** y puede pasar a **En curso**, **Finalizado** o **Cancelado**. El sistema valida que la fecha de fin no sea anterior a la de inicio y que el cupo sea mayor a cero. Un evento cancelado no se borra, para conservar el historial con el cliente.

**Relevancia:** el evento es el centro de toda la información: asistentes, tareas y mensajes cuelgan de él. Tener sus datos validados y en un solo lugar evita errores de fecha o de sede frente a un cliente de alto perfil, donde un error tiene un costo de imagen alto.

*Historias de usuario:* HU-01 Crear y configurar un evento, HU-02 Editar y cancelar un evento.

### 1.2 Registro de asistentes

Permite registrar a los participantes de un evento con nombre, correo, teléfono y empresa. El sistema no permite registrar dos veces el mismo correo en el mismo evento ni superar el cupo máximo, y envía al asistente una notificación de confirmación. El día del evento el organizador marca quién asistió.

**Relevancia:** controlar el cupo y la lista de asistentes es indispensable para la logística (acceso, alimentos, materiales) y para medir la asistencia real contra los registrados, un dato que el cliente suele pedir al cierre.

*Historias de usuario:* HU-03 Registrar asistentes, HU-09 Consultar asistentes y confirmar asistencia.

### 1.3 Asignación de tareas

Permite crear tareas específicas de un evento (logística, catering, registro, audio y video, etc.) con título, responsable, fecha límite y prioridad. Solo se pueden asignar a personas registradas en ese evento, y la fecha límite no puede ser posterior a la fecha del evento. El responsable recibe una notificación al ser asignado.

**Relevancia:** un evento corporativo involucra muchas actividades en paralelo. Asignar cada tarea a una persona con fecha límite deja claro quién es responsable de qué y evita que algo se quede sin hacer.

*Historia de usuario:* HU-04 Asignar tareas a participantes.

### 1.4 Seguimiento de progreso

Cada tarea tiene un estado (**Pendiente**, **En progreso**, **Completada**) y las tareas vencidas que no se han completado se marcan como **Atrasadas**. El evento muestra su porcentaje de avance (tareas completadas entre tareas totales) y un panel principal resume los próximos eventos, las tareas pendientes y las atrasadas. Un calendario mensual y semanal muestra todos los eventos para detectar empalmes.

**Relevancia:** permite al organizador saber de un vistazo si el evento va a tiempo y actuar antes de que un retraso afecte al cliente. El calendario evita programar dos eventos que compitan por el mismo equipo o la misma fecha.

*Historias de usuario:* HU-05 Seguimiento del progreso, HU-07 Calendario de eventos, HU-08 Panel principal.

### 1.5 Comunicación con los participantes

Permite al organizador enviar mensajes a todos los asistentes de un evento o a uno solo (recordatorios, cambios de horario o sede, avisos). Cada mensaje queda registrado con fecha, remitente y destinatarios, y el asistente puede consultarlo dentro de la aplicación. El mismo mecanismo envía las notificaciones automáticas de registro, asignación de tareas y cancelación.

**Relevancia:** los cambios de último momento son comunes en eventos corporativos. Un canal oficial y registrado garantiza que todos reciban la misma información y deja evidencia de qué se comunicó y cuándo.

*Historia de usuario:* HU-06 Enviar comunicados y notificaciones.

### 1.6 Roles y seguridad

La aplicación usa los roles **Organizador** y **Asistente**. Cada rol solo ve y modifica lo que le corresponde: el asistente no puede editar eventos ni ver los datos de otros asistentes.

**Relevancia:** los eventos de clientes de alto perfil manejan datos personales y confidenciales, así que el acceso debe estar restringido por rol.

*Historia de usuario:* HU-10 Roles de usuario.

## Resumen

| Funcionalidad | Historias de usuario | Prioridad |
|---|---|---|
| Creación de eventos | HU-01, HU-02 | Alta / Media |
| Registro de asistentes | HU-03, HU-09 | Alta / Media |
| Asignación de tareas | HU-04 | Alta |
| Seguimiento de progreso | HU-05, HU-07, HU-08 | Alta / Media |
| Comunicación | HU-06 | Alta |
| Roles y seguridad | HU-10 | Media |

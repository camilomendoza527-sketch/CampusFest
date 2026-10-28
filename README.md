# CampusFest 

CampusFest es un proyecto universitario diseñado para gestionar eventos en el campus: consultar cupos disponibles, reservar entradas, confirmar reservas (con un plazo de 10 minutos), cancelar reservas y registrar la asistencia mediante código QR.

En este repositorio se encuentran los diagramas de análisis y diseño del sistema realizados en [Draw.io](https://app.diagrams.net/).

---

##  ¿Qué hace el sistema?

###  Estudiante
- **Consultar cupos:** Revisa cuántos cupos libres quedan en un evento.
- **Reservar:** Aparta un cupo (queda en estado *Pendiente*).
- **Confirmar reserva:** Confirma su reserva antes de 10 minutos (pasa a *Confirmada*).
- **Cancelar reserva:** Libera su lugar si ya no desea asistir.
- **Registrar asistencia:** Muestra su código QR al ingresar al evento.

###  Organizador
- **Gestionar evento:** Modifica la descripción, fecha u horario de un evento.
- **Reporte de reservas:** Genera el listado de reservas realizadas.
- **Reporte de asistencia:** Genera el listado de personas que ingresaron con su QR.

### ⏱️ Temporizador (10 minutos)
- Si una reserva no se confirma en 10 minutos, pasa a estado *Vencida* y el cupo se libera automáticamente.

---

##  Organización de carpetas

### 1. `CdU/` (Casos de Uso)
Contiene `casos_de_uso.drawio`, con los diagramas generales de casos de uso divididos en dos subsistemas:
- **CampusFest (Uso):** Acciones del estudiante.
- **CampusFest (Organización):** Acciones del organizador y del temporizador.

### 2. `Analisis/` (Diagramas de Clases y Casos de Uso)
Muestra cómo interactúan las clases por dentro para cada uno de los 9 casos de uso:
- **`colaboracion.drawio`:** Las clases que participan y sus conexiones (sin mensajes).
- **`comunicacion.drawio`:** El paso a paso numerado de cómo se envían los datos.
- **`secuencia.drawio`:** Diagrama de secuencia temporal (disponible en *Consultar Cupos*).

Además incluye:
- **`Colaboracion_General.drawio`:** Diagrama integrado con todas las clases del sistema.
- **`Clases_Entidad/`:** Clases principales de datos (`Evento`, `Reserva`, `Asistencia`, `Estudiante`), con y sin estereotipos.

### 3. `docs/` (Retos de clase)
Contiene los diagramas correspondientes a los ejercicios y retos desarrollados durante el taller (`RETO 2.drawio` a `RETO 8.drawio`).

---

## 🛠️ ¿Cómo ver los diagramas?
Los archivos `.drawio` se pueden abrir directamente en:
- [app.diagrams.net](https://app.diagrams.net/) (en el navegador, gratis).
- La aplicación de escritorio de **Draw.io**.
- La extensión **Draw.io Integration** en Visual Studio Code.

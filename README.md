# CampusFest - Análisis Orientado a Objetos (OOA)

Repositorio oficial del caso de estudio **CampusFest**, desarrollado para la asignatura de **Ingeniería de Software I** según la metodología de Análisis Orientado a Objetos de **Stephen R. Schach** (*Object-Oriented and Classical Software Engineering*, 8ª edición, Cap. 11 y 13) y el patrón **BCE (Boundary - Control - Entity)** de Ivar Jacobson.

---

## Estructura del Repositorio

El proyecto se encuentra organizado dentro de la carpeta `docs/` con trazabilidad directa a cada uno de los retos del laboratorio y los requerimientos del docente:

```text
CampusFest/
├── docs/
│   ├── CdU/                                         # Carpeta con los Casos de Uso del sistema
│   │   ├── caso_uso.drawio                          # Casos de uso de Estudiantes
│   │   └── caso_organizacion.drawio                 # Casos de uso de Organizadores
│   │
│   └── Analisis/                                    # Diagramas ordenados por Caso de Uso y Reto
│       │
│       ├── 01_Consultar_Cupos/                      # Retos 2, 3 y 4
│       │   ├── Colaboracion_sin_mensajes.drawio     # Reto 2: Clases participantes y cálculo
│       │   ├── Comunicacion_con_mensajes.drawio     # Reto 3: Diagrama de comunicación con mensajes
│       │   └── Secuencia.drawio                     # Reto 4: Diagrama de secuencia temporal
│       │
│       ├── 02_Reservar/                             # Reto 5
│       │   ├── Colaboracion_sin_mensajes.drawio     # Reto 5: Colaboración para crear y confirmar
│       │   └── Estados_Reserva.drawio               # Reto 5: Máquina de estados de la entidad Reserva
│       │
│       ├── 03_Actualizar_Evento/                    # Reto 6
│       │   └── Comunicacion_con_mensajes.drawio     # Reto 6: Operación simple (Límite directo a Entidad)
│       │
│       ├── 04_Reporte_Reservas/                     # Reto 7A
│       │   └── Comunicacion_con_mensajes.drawio     # Reto 7A: Escenario A - Reporte de Reservas
│       │
│       ├── 05_Reporte_Asistencia/                   # Reto 7B
│       │   └── Comunicacion_con_mensajes.drawio     # Reto 7B: Escenario B - Reporte de Asistencia (QR)
│       │
│       ├── 06_Colaboracion_General/                 # Tarea del Tablero
│       │   └── Colaboracion_General.drawio          # Modelo unificado de todo el sistema (Schach Fig. 13.52)
│       │
│       ├── 07_Clases_Entidad/                       # Clases de Entidad Solicitadas
│       │   ├── Clases_Entidad_Con_Estereotipos.drawio    # Con estereotipos BCE (Jacobson) y multiplicidades
│       │   └── Clases_Entidad_Sin_Estereotipos.drawio    # UML estándar (3 compartimentos: atributos y métodos)
│       │
│       └── 08_Integracion_y_Auditoria/              # Reto 8
│           └── RETO 8 - Integracion_y_Auditoria.drawio   # Modelo integrado + Tarjeta CRC + Hallazgos de auditoría
│
├── 214485 (1).pdf                                   # Guía y enunciado de los retos del laboratorio
└── README.md                                        # Documentación general del repositorio
```

---

## Mapeo de Retos del Taller

| Reto del Taller | Ubicación en el Repositorio | Descripción / Contenido |
| :--- | :--- | :--- |
| **Reto 1** | *(En el cuaderno / informe)* | Clasificación de responsabilidades BCE. |
| **Reto 2** | `docs/Analisis/01_Consultar_Cupos/Colaboracion_sin_mensajes.drawio` | Clases participantes y cálculo de los 20 cupos. |
| **Reto 3** | `docs/Analisis/01_Consultar_Cupos/Comunicacion_con_mensajes.drawio` | Diagrama de comunicación con tarjetas ordenadas (1.E a 9.A). |
| **Reto 4** | `docs/Analisis/01_Consultar_Cupos/Secuencia.drawio` | Diagrama de secuencia con llamadas y retornos punteados. |
| **Reto 5** | `docs/Analisis/02_Reservar/` | Colaboración con `Gestión Reserva` y Máquina de Estados de `Reserva`. |
| **Reto 6** | `docs/Analisis/03_Actualizar_Evento/Comunicacion_con_mensajes.drawio` | Coordinación de operación sencilla sin control (Schach). |
| **Reto 7A** | `docs/Analisis/04_Reporte_Reservas/Comunicacion_con_mensajes.drawio` | Escenario A: Reporte de reservas. |
| **Reto 7B** | `docs/Analisis/05_Reporte_Asistencia/Comunicacion_con_mensajes.drawio` | Escenario B: Reporte de asistencia con validación QR. |
| **Reto 8** | `docs/Analisis/08_Integracion_y_Auditoria/RETO 8 - Integracion_y_Auditoria.drawio` | Modelo integrado con Tarjeta CRC y Hallazgos de Auditoría. |
| **Tablero** | `docs/Analisis/06_Colaboracion_General/Colaboracion_General.drawio` | Colaboración General unificada (Stephen Schach, pág. 52). |
| **Tablero** | `docs/Analisis/07_Clases_Entidad/` | Clases entidad con estereotipos y sin estereotipos (con métodos y atributos). |

---

## Resumen del Dominio y Reglas del Negocio

* **Aforo y Disponibilidad:** Cada evento tiene un aforo máximo y cupos bloqueados por la organización.
  $$\text{Cupos Disponibles} = \text{Aforo Máximo} - (\text{Cupos Bloqueados} + \text{Reservas Confirmadas} + \text{Reservas Pendientes Vigentes})$$
  *(Las reservas Canceladas y Vencidas forman parte del historial y no descuentan cupos).*
* **Ciclo de Vida de Reserva:** Una reserva se crea en estado `Pendiente` y se mantiene durante máximo **10 minutos**. Si no se confirma, pasa automáticamente a `Vencida` y libera el cupo provisional.
* **Control de Asistencia:** Solo reservas en estado `Confirmada` pueden registrar ingreso al evento mediante la validación de un código QR único; cada ingreso se registra una única vez.

---

## Modelo de Clases Entidad

| Clase Entidad | Responsabilidad Principal | Relaciones y Multiplicidades |
| :--- | :--- | :--- |
| **`Evento`** | Residir la información a largo plazo del evento (aforo, bloqueados, fecha, modificación). | `1` a `0..*` con `Reserva`<br>`1` a `0..*` con `Asistencia` |
| **`Reserva`** | Administrar el ciclo de vida de la reserva (`Pendiente`, `Confirmada`, `Cancelada`, `Vencida`). | `0..*` a `1` con `Evento`<br>`0..*` a `1` con `Estudiante` |
| **`Asistencia`** | Registrar el ingreso físico verificado mediante código QR en fecha y hora específica. | `0..*` a `1` con `Evento`<br>`0..*` a `1` con `Estudiante` |
| **`Estudiante`** | Mantener la información del alumno que consulta, reserva y asiste a eventos. | `1` a `0..*` con `Reserva`<br>`1` a `0..*` con `Asistencia` |

---

## Cómo abrir y visualizar los diagramas

Todos los diagramas fueron diseñados en formato XML nativo de **Draw.io** (`.drawio`) con estilo **monocromático / neutro (blanco y negro)**:
1. Abra la aplicación de escritorio de [Draw.io](https://www.diagrams.net/).
2. Abra cualquier archivo `.drawio` ubicado en `docs/CdU/` o `docs/Analisis/`.

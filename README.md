# CampusFest — Análisis Orientado a Objetos (BCE / UML)

Repositorio de análisis y diseño orientado a objetos para el sistema **CampusFest** (gestión de eventos universitarios, reservas de cupos con vencimiento de 10 minutos, confirmación y control de asistencia por código QR), aplicando los estereotipos de Ivar Jacobson (**Boundary–Control–Entity**) y el método de Stephen R. Schach.

---

## Estructura del Repositorio

```text
CampusFest/
├── README.md
├── CdU/
│   └── casos_de_uso.drawio                          # Diagramas de Casos de Uso (Uso y Organización)
├── Analisis/
│   ├── Colaboracion_General.drawio                  # Diagrama de Colaboración General Integrado
│   ├── Clases_Entidad/
│   │   ├── entidad_con_estereotipos.drawio          # Diagrama de Clases Entidad (<<entidad>>)
│   │   └── entidad_sin_estereotipos.drawio          # Diagrama de Clases UML con atributos y métodos
│   ├── Consultar_Cupos/                             # CdU 1 - Consultar cupos
│   │   ├── colaboracion.drawio                      # Clases participantes y enlaces (sin mensajes)
│   │   ├── comunicacion.drawio                      # Paso a paso y mensajes numerados
│   │   └── secuencia.drawio                         # Diagrama de secuencia equivalente
│   ├── Reservar/                                    # CdU 2 - Reservar
│   │   ├── colaboracion.drawio
│   │   └── comunicacion.drawio
│   ├── Confirmar_Reserva/                           # CdU 3 - Confirmar reserva
│   │   ├── colaboracion.drawio
│   │   └── comunicacion.drawio
│   ├── Cancelar_Reserva_Estudiante/                 # CdU 4 - Cancelar reserva (Estudiante)
│   │   ├── colaboracion.drawio
│   │   └── comunicacion.drawio
│   ├── Registrarse_Asistencia/                      # CdU 5 - Registrarse (asistencia)
│   │   ├── colaboracion.drawio
│   │   └── comunicacion.drawio
│   ├── Gestionar_Evento/                            # CdU 6 - Gestionar un evento
│   │   ├── colaboracion.drawio
│   │   └── comunicacion.drawio
│   ├── Generar_Reporte_Reservas/                    # CdU 7 - Generar reporte de reservas
│   │   ├── colaboracion.drawio
│   │   └── comunicacion.drawio
│   ├── Generar_Reporte_Asistencia/                  # CdU 8 - Generar reporte de asistencia
│   │   ├── colaboracion.drawio
│   │   ├── colaboracion_nuevo.drawio
│   │   ├── comunicacion.drawio
│   │   └── comunicacion_nuevo.drawio
│   └── Cancelar_Reserva_Organizador/                # CdU 9 - Cancelar reserva (a los 10 mins)
│       ├── colaboracion.drawio
│       └── comunicacion.drawio
└── docs/                                            # Solución de los Retos del Taller
    ├── RETO 2.drawio
    ├── RETO 3.drawio
    ├── RETO 4.drawio
    ├── RETO 5.drawio
    ├── RETO 6.drawio
    ├── RETO 7A.drawio
    ├── RETO 7B.drawio
    └── RETO 8.drawio
```

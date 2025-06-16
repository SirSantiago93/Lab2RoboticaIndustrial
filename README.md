# Lab2RoboticaIndustrial
Este es el repositorio de un laboratorio desarrollado con un robot indutrial ABB

## Descripcón detallada de la solución planteada.

## Diagrama de flujo de las acciones del robot

```mermaid
flowchart TD
    A[Inicio] --> B{Entrada 1 activada?}
    B -- Sí --> C[Activar luz indicadora]
    C --> D[Activar banda transportadora]
    D --> E[Esperar llegada de caja a zona de trabajo]
    E --> F[Robot va a posición de trabajo desde Home]
    F --> G[Robot escribe nombres y decora pastel]
    G --> H[Robot regresa a Home]
    H --> I[Reactivar banda para sacar el pastel]
    I --> J[Desactivar luz indicadora]
    J --> A

    B -- No --> L{Entrada 2 activada?}
    L -- Sí --> M[Robot va a posición de mantenimiento]
    M --> A
    L -- No --> A
```

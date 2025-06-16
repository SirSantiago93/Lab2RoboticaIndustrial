# Laboratoro 2 - Robotica Industrial
Este es el repositorio de un laboratorio desarrollado con un robot indutrial ABB

<div align="center">
  <img src="https://github.com/user-attachments/assets/939dbcbb-e26d-408f-ad91-98888a410131" alt="image" width="400"/>
</div>

## Descripción detallada de la solución planteada.

La solución se basó en una simulación en RobotStudio complementada con pruebas físicas en un entorno real usando el robot ABB IRB140_6_81_C_03. El objetivo era automatizar el proceso de decoración de una caja, escribiendo nombres y agregando un pequeño diseño, además de moverla usando una banda transportadora simulada.

Para trabajar con precisión, se calibró la herramienta del robot usando el método de los cuatro puntos, apuntando hacia un mismo punto desde diferentes direcciones. Esto permitió definir bien la orientación de la herramienta con respecto al brazo del robot. También se configuró un workobject usando el método de tres puntos, estableciendo un origen y los ejes X e Y directamente sobre la caja, lo que sirvió como referencia para los movimientos de escritura.

En cuanto a la programación, se usaron instrucciones MoveJ para los movimientos rápidos entre posiciones, como cuando el robot se mueve desde Home hasta la zona de trabajo o hacia la posición de mantenimiento. Para la decoración, se usaron instrucciones MoveL, que permiten hacer trayectorias lineales más suaves y precisas, necesarias para escribir los nombres y el diseño.

En la simulación, se añadieron Smart Components para representar la banda transportadora y la caja. Estos componentes permitieron simular el movimiento de la caja hacia la zona de trabajo y su salida una vez decorada. También se usaron señales digitales simuladas para activar o desactivar la banda y para prender una luz indicadora mientras el robot estaba decorando.

En la parte física, además del robot y su controlador, se usó un teach pendant para manejar el robot de forma manual, y un tablero con pulsadores e indicadores LED. Este tablero permitió enviar señales al robot (como iniciar el proceso o moverlo a mantenimiento) y visualizar las salidas (por ejemplo, cuando se activa la luz indicadora).

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

## Diseño de la herramienta detallado.

Se presentan las dos versiones de la herramienta desarrolladas para el proceso de escritura automatizada, diferenciando entre la versión física utilizada en la práctica real y la versión adaptada para simulación en RobotStudio.

- Herramienta física

Esta versión fue diseñada específicamente para montarse en el robot ABB IRB140 durante la ejecución física del experimento. El cuerpo principal incluye un alojamiento cilíndrico para insertar un marcador convencional, con una inclinación de aproximadamente 60 grados respecto a la vertical. Esta inclinación se definió para evitar posibles singularidades durante el movimiento del robot y mejorar la accesibilidad a la superficie del objeto a decorar.

Además, se incorporó un sistema de amortiguamiento sencillo, que permite cierta flexibilidad axial. Esto ayuda a prevenir rupturas del marcador por presión excesiva y también compensa posibles errores o incertidumbres en la posición de la superficie, producto de tolerancias mecánicas o de calibración.

<div align="center">
  <img src="https://github.com/user-attachments/assets/6394050f-737e-4b22-b7af-98052e0edb66" alt="image" width="400"/>
</div>

<div align="center">
  <img src="https://github.com/user-attachments/assets/ea805f5c-cf48-4d2f-ba65-fcc3e2d20dea" alt="image" width="400"/>
</div>



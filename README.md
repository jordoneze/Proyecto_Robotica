# Proyecto Final - Robótica Industrial: Automatización del Proceso de Preparación de Arepas
## Gripper




## Diagrama de Flujo
```mermaid
---
config:
  theme: 'forest'
  layout: dagre
---
flowchart TD

    A(["Inicio"]) --> B["Declarar puntos, trayectorias y variables"]
    B --> C["Inicializar variables y reiniciar temporizadores"]
    C --> D{"¿Fue escogida una arepa y hay una posición disponible en la parrilla?"}
    D -- Si --> E[["Rutina de posicionamiento de arepa"]] 
    D -- No -->F{"¿El temporizador de coccion del lado A de la arepa supero los 30 segundos?"}
    F-- Si -->G[["Rutina de giro de arepa"]]
    F -- No -->H{"¿El temporizador de coccion del lado B de la arepa supero los 30 segundos?"}
    H-- Si -->I[["Rutina de salida de arepa"]]
    H-- No --> D
    E --> D
    G  --> D
    I  --> D
```
## Subrutinas
```mermaid
---
config:
  theme: 'forest'
  layout: dagre
---
flowchart TD
%%Posicionamiento de Arepa
    A_1(["Inicio"]) --> B_1["Ir a la Arepa"]
    B_1 --> C_1["Agarrar la Arepa"]
    C_1 --> D_1["Ir a Home"]
    D_1 --> E_1["Ir a la posición disponible"]
    E_1 --> F_1["Dejar la Arepa"]
    F_1 --> G_1["Volver a Home"]
    G_1 --> H_1(["Fin"])
```

```mermaid
---
config:
  theme: 'forest'
  layout: dagre
---
flowchart TD

%%Girar Arepa
    A_2(["Inicio"]) --> B_2["Ir a la Arepa"]
    B_2 --> C_2["Agarrar la Arepa"]
    C_2 --> D_2["Ir a Home"]
    D_2 --> E_2["Girar la ultima articulación"]
    E_2 --> F_2["Ir a la posición original"]
    F_2 --> G_2["Dejar la Arepa"]
    G_2 --> H_2["Ir a Home"]
    H_2 --> I_2(["Fin"])
```
```mermaid
---
config:
  theme: 'forest'
  layout: dagre
---
flowchart TD
%%Salida de Arepa

    A_3(["Inicio"]) --> B_3["Ir a la Arepa"]
    B_3 --> C_3["Agarrar la Arepa"]
    C_3 --> D_3["Ir a Home"]
    D_3 --> E_3["Ir a la posición de salida"]
    E_3 --> F_3["Dejar la Arepa"]
    F_3 --> G_3["Volver a Home"]
    G_3 --> H_3(["Fin"])
```





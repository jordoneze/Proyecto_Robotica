# Proyecto Final - Robótica Industrial: Automatización del Proceso de Preparación de Arepas
Jenny Ximena Ordoñez Espinosa

Juan Felipe Hincapie Gomez

Santiago Zamora Sosa

Stivens Camilo Guevara Moran

## Descripción de la solución planteada  <!--  el proceso de alistamiento, herramientas y piezas utilizadas -->




## Diagrama de Flujo  <!-- descripciones-->
En general, se muestra el planteamiento de la lógica del progrma, que al elegir una arepa la dirige a la posición disponible, considerando el orden (A1, A2, B1, B2). Tras un tiempo gira la arepa y tras otra cantidad de tiempo, retira la arepa de la parrilla.

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
Posicionamiento de la Arepa:

Para el posicionamiento de la arepa en el lugar deseado de la parrilla, el manipulador se dirige a la arepa, la sujeta, la mueve al lugar esperado y la suelta, iniciando un temporizador para el giro de la arepa.

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

Giro de la Arepa:
Cuando el temporizador supera un limite establecido, el manipulador se dirige a la arepa, la sujeta, realiza un giro en la ultima articulación, y deja la arepa en la posición inicial. Además inicia un temporizador que dara lugar a la subrutina de salida.
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

Salida de la Arepa:
Al superar el temporizador un tiempo determinado, el manipulador se dirige a la arepa, la sujeta, se dirige a la posición inicial de la arepa en toda la rutina y deja la arepa.

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

## Gripper Diseñado <!-- Descripci´on, planos y fotograf´ıas-->
Para el diseño del grrpper inicialmente se planteo el problema de dejar la arepa en una posición exacta al momento de voltearla, esto para facilitar la recogida de la arepa una vez haya finalizado la coccion de la arepa en ambos lados. Por ello se diseño un gripper tal que este no tenga un angulo respecto al plano "no" del efector final. Al principio se penso dejar una distancia entre el plano "no" del efector final y la cara inferior del gripper, pero volveriamos a tener el mismo problema, y al moemnto de girar la arepa se tendria que soltar la arepa en el aire, y habria una incertidumbre considerable de la posicion donde cae la arepa. Una vez se discutio y se dejo claro como queriamos realizar el gripper, se procedio a escoger un actuador neumatico de los que habian disponibles en el laboratorio, por lo que se escoguio un actuador neumático de doble efecto de pinzas, esto debido a la facilidad de acoples entre el actuador y el gripper, y su movimiento cumplia perfectamente con nuestra nececidad. Dicho actuador se ve acontinuacion:

<img width="400" height="400" alt="Pneumatic-Actuator-Double-Acting-Angular-Finger-Gripper-Mhc2-6D" src="https://github.com/user-attachments/assets/6216be1f-6b97-4f33-838e-5ffbb9342a7d" />



## Modelo en Software de Simulación <!-- predeterminado del entorno robótico con todos los elementos que intervienen en el proceso-->


## Comparación del tiempo de alistamiento manual y de operación automatizada para las combinaciones seleccionadas.


## Video



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
Para el diseño del gripper, inicialmente se planteó el problema de colocar la arepa en una posición exacta al momento de voltearla, con el fin de facilitar su recogida una vez haya finalizado la cocción por ambos lados. Por esta razón, se diseñó un gripper que no presentara un ángulo con respecto al plano "NO" del efector final.

En un principio se consideró dejar una distancia entre el plano "NO" (NOA) del efector final y la cara inferior del gripper. Sin embargo, esto generaría nuevamente el mismo inconveniente: al girar la arepa sería necesario soltarla en el aire, lo cual implicaría una incertidumbre considerable sobre su posición final al caer.

Una vez se discutió y definió claramente el enfoque para el diseño del gripper, se procedió a seleccionar un actuador neumático de entre los disponibles en el laboratorio. Se eligió un actuador neumático de doble efecto con pinzas, debido a la facilidad de acople entre este y el gripper, además de que su movimiento se ajustaba perfectamente con los requerimientos del proyecto. Dicho actuador se muestra a continuación:

<img width="300" height="400" alt="Pneumatic-Actuator-Double-Acting-Angular-Finger-Gripper-Mhc2-6D" src="https://github.com/user-attachments/assets/6216be1f-6b97-4f33-838e-5ffbb9342a7d" />

Posteriormente, se tomaron las medidas del actuador neumático para diseñar el respectivo acople entre este y las piezas del gripper. Además, se elaboró un modelo CAD del actuador con el objetivo de integrarlo con las piezas del gripper y generar un archivo .sat que permitiera su uso en simulaciones dentro del software RobotStudio.

Una vez se comprobó el correcto funcionamiento del conjunto gripper-actuador mediante simulaciones, se procedió a la impresión de cada una de las piezas y a su ensamblaje con el actuador neumático.

A continuación, se presentan algunas imágenes del gripper utilizado en el laboratorio, así como los planos correspondientes a cada una de sus piezas.



## Modelo en Software de Simulación <!-- predeterminado del entorno robótico con todos los elementos que intervienen en el proceso-->


## Comparación del tiempo de alistamiento manual y de operación automatizada para las combinaciones seleccionadas.


## Video



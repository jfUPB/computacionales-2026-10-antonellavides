# Unidad 1

## Bitácora de Proceso de Aprendizaje
### Actividad 01
> Crea un archivo llamado program.asm y copia el código del programa anterior. Ejecuta el programa en el simulador de la CPU Hack y observa cómo se comporta.
#### Programa (program.asm)
```js
@1
D=A
@2
D=D+A
@16
M=D
@END
(END)
0;JMP
```
### *Solución*

#### *Experimento 1*
#### *¿Qué sucede? ¿Qué valor se almacena en la dirección de memoria 16? ¿Por qué crees que es ese valor?*

Al seguir los pasos y ejecutarlo en el simulador de la CPU Hack, la computadora sigue las instrucciones paso a paso y en esta ocasión realiza una suma sencilla.

1. Comienza cargando el numero 1 en el registro A `@1`, luego, se copia en el registro D `D=A`

2. Después, carga el número 2 en el registro A `@2`, luego, suma el valor de D (1) con el valor de A (2), dando como resultado 3 `D=D+A`

3. Se busca o apunta a la dirección de memoria 16 `@16` y, el valor de esa operación (3) se guarda en esa dirección de memoria `M=D`

4. El programa llega a `@END y (END)`, esto significa que vaya a la instrucción marcada con END, que está en la posición 7 `@7`

5. Por último, tenemos `0;JMP`, esto hace que la CPU salte siempre a esa misma instrucción, creando un bucle infinito, así, el programa se queda repitiendo la misma instrucción y no cambia nada más en la memoria ni en los registros.

#### *¿Qué instrucciones se ejecutan en cada ciclo Fetch-Decode-Execute? ¿Qué cambios observas en el contenido de la memoria y los registros? ¿Qué instrucciones se ejecutan en cada ciclo Fetch-Decode-Execute?*

### Ciclo Fetch–Decode–Execute por instrucción

`@1`

Fetch: La CPU toma la instrucción de la memoria ROM.

Decode: La CPU entiende que es una instrucción A.

Execute: El registro A ahora vale 1.

`D=A`

Fetch: Toma la instrucción siguiente.

Decode: Entiende que debe mover datos a D.

Execute: El registro D ahora vale 1 (copiado desde A).

`@2`

Fetch: Lee la instrucción de la ROM.

Decode: Es otra instrucción A.

Execute: El registro A ahora vale 2.

`D=D+A`

Fetch: Lee la instrucción de suma.

Decode: Entiende que debe sumar D y A.

Execute: D = 1 + 2 = 3.

`@16`

Fetch: Lee la instrucción.

Decode: Es instrucción A.

Execute: El registro A apunta a la dirección 16 de la memoria.

`M=D`

Fetch: Lee la instrucción de memoria.

Decode: Entiende que debe guardar D en RAM[A].

Execute: RAM[16] = 3.

`@END`

Fetch: Lee la instrucción de salto.

Decode: Es instrucción A.

Execute: El registro A ahora apunta a la dirección de la etiqueta END, que es 7.

`0;JMP`

Fetch: Lee la instrucción de salto.

Decode: Entiende que debe saltar siempre.

Execute: El PC (contador de programa) se pone en 7, creando un bucle infinito.

#### *Screens Referencia*
<img width="1000" height="500" alt="Diseño sin título" src="https://github.com/user-attachments/assets/f5c2f1f8-f3c3-4bba-91ff-67e2ca6d135a" />

#### *Experimento 2*
#### *Escribe un programa en lenguaje ensablador que sume los números 5 y 10, y almacene el resultado en la dirección de memoria 20. Utiliza el simulador de la CPU Hack para ejecutar tu programa y verifica que el resultado es correcto.*
Escribí un mini programa en ensamblador para que sumara 5 y 10. Cuando lo ejecuté, al final se guardó el 15 en la dirección de memoria 20, así que salió bien. El simulador muestra cómo va paso por paso: primero carga el 5, luego el 10, los suma, y luego guarda el resultado en la memoria. Mientras se ejecuta, los registros también van cambiando. En resumen, el programa hizo lo que tenía que hacer y no se enredó.

```js
@5
D=A      // D = 5

@10
D=D+A    // D = 5 + 10 = 15

@20
M=D      // RAM[20] = 15
```

#### *Screen referencia*

<img width="1000" height="500" alt="Diseño sin título (4)" src="https://github.com/user-attachments/assets/46ecc4b7-1599-4ad6-bd78-c0fea668a7df" />

#### *¿Qué diferencia hay entre los datos almancenados en la memoria ROM y en la RAM?*
La RAM es la memoria que usa el computador mientras estás trabajando, como cuando abres programas o juegos. Es rápida pero se borra cuando apagas todo. En cambio, la ROM tiene info que el computador necesita para encender, como las instrucciones básicas, y esa no se borra. La RAM se puede escribir y cambiar todo el tiempo, pero la ROM casi no se toca.

### Actividad 02
>Responde las siguientes preguntas

#### *¿Qué diferencia hay entre los datos almancenados en la memoria ROM y en la RAM?*

Una instrucción que utiliza la ALU es:

`D=D-A`

Esta instrucción le indica a la ALU que reste el valor del registro A al valor del registro `D`.
El resultado de la operación se guarda nuevamente en el registro `D`.
En el programa, esta operación se usa para comparar el valor almacenado en memoria con el número 10, permitiendo saber si es mayor, menor o igual

#### *¿Para que sirve el registro PC?*

El registro PC (Program Counter) sirve para indicar cuál es la siguiente instrucción que debe ejecutar la CPU.
Después de cada instrucción, el PC normalmente avanza a la siguiente posición de memoria, pero si hay una instrucción de salto (`JMP`, `JLT`, etc.), el PC cambia y apunta a otra dirección del programa.

#### *¿Cuál es la diferencia entre @i y @READKEYBOARD?*

- `@i`
Es una variable simbólica. El ensamblador le asigna automáticamente una dirección de memoria en la RAM (por ejemplo, RAM[16], RAM[17], etc.) -> variable general en RAM

- `@READKEYBOARD`
Es una etiqueta o símbolo predefinido o definido por el programador, que representa una dirección específica de memoria. Normalmente se usa para acceder a dispositivos de entrada/salida, como el teclado o la pantalla -> Dirección específica con un propósito concreto

#### *Describe qué se necesita para leer el teclado y mostrar información en la pantalla.*

Para leer el teclado y mostrar información en pantalla se necesita:

- Acceder a la dirección de memoria del teclado `(KBD)`, que contiene el código de la tecla presionada.

- Usar instrucciones de carga como `D=M` para leer ese valor.

- Acceder a la memoria de pantalla `(SCREEN)` y escribir valores en sus posiciones.

- Un bucle que revise constantemente el teclado para detectar cambios.

Esto permite que el programa lea entradas del usuario y muestre resultados visuales.

#### *Identifica un bucle en el programa y explica su funcionamiento.*

***Ejemplo de bucle:***

```asm
(LOOP)
@LOOP
0;JMP
```

Este es un bucle infinito.
La instrucción `0;JMP` hace que el programa salte siempre a la etiqueta `(LOOP)`, evitando que el programa termine.
Se usa para mantener el programa en ejecución constante.

#### *Identifica una condición en el programa y explica su funcionamiento.*

***Ejemplo de condición:***

`D;JLT`

Esta instrucción evalúa el valor del registro `D`.
Si `D` es menor que 0, el programa salta a la etiqueta indicada.
En el programa, esta condición permite decidir si el valor leído de memoria es menor que 10, controlando qué valor se guarda en la memoria de salida.

### Actividad 03
>Escribe un programa que compare el valor almacenado en la dirección de memoria 5 con el valor 10. Si el valor es menor que 10, guarda el valor 1 en la dirección 7. Si el valor es mayor o igual a 10, guarda el valor 0 en la dirección 7. Simula paso a paso.

``` asm
@5
D=M   //Cargando en D lo de la posicion 5
@10
D=D-A   //Leer direccion de memoria 5 y restarlo a D10 para saber si es mayor o menor que 10

@MENOR
D;JLT   //Instruccion de salto genera un valor en registro D, salta a menor

(MAYOREQ)   //Sigo derecho
@7
M=0
@LOOP
0;JMP

(MENOR)
@7
M=1
@LOOP
0;JMP
```

#### *Screen referencia*

<img width="1000" height="500" alt="Diseño sin título (2)" src="https://github.com/user-attachments/assets/f154211c-3013-4386-9144-8ffd204c1c56" />

<img width="1000" height="500" alt="Diseño sin título (3)" src="https://github.com/user-attachments/assets/7595e2fd-3864-40c7-a780-ec94790acc61" />

#### *Paso a paso*

**1.** Cargar valor de `M[5]` en `D`

**2.** Restar 10 a `D` → `D = M[5] - 10`

**3.** Si `D < 0` → saltar a `(MENOR)`

**4.** Si `D ≥ 0` → guardar 0 en `M[7]`

**5.** Ir a bucle infinito `(LOOP)`

**6.** `(MENOR)` → guardar 1 en `M[7]`

**7.** Ir a bucle infinito `(LOOP)`

## Bitácora de aplicación 

### Actividad 04
> Crea un programa que use un ciclo para sumar los números del 1 al 5 y guarde el resultado en la dirección de memoria 12. Simula paso a paso.

``` asm
@1   //Inicializa contador en 1
D=A
@i
M=D

@0   //Inicializa acumulador en 0
D=A
@sum
M=D

(LOOP)
  @i   //Cargar contador
  D=M
  @sum
  M=D+M   //sum = sum + i

  @i
  M=M+1   //i = i + 1

  @i
  D=M
  @6   //condición: si i == 6, termina
  D=D-A
  @END
  D;JEQ

  @LOOP
  0;JMP

(END)
  @sum
  D=M
  @12
  M=D   //Guardar resultado en la dirección 12

(END2)
  @END2
  0;JMP

```

#### *Screen referencia*

<img width="1000" height="500" alt="Diseño sin título (1)" src="https://github.com/user-attachments/assets/a8be1553-bcdb-4c6c-aab1-b0201c9ca1df" />

#### *Paso a paso*

**1.** Inicializar contador: `i = 1`

**2.** Inicializar acumulador: `sum = 0`

**3.** Ciclo `(LOOP)`:

- Sumar `i` a `sum` → `sum = sum + i`
- Incrementar `i` → `i = i + 1`
- Si `i == 6`, salir del ciclo
- Si no, repetir ciclo
  
**4.** Guardar resultado final en `M[12]` → `M[12] = sum`

**5.** Bucle infinito para detener el programa
  
#### *Extra*
- Veo que la variable `i` empieza en 1 y `sum` en 0.
- El bucle se repite 5 veces, sumando 1+2+3+4+5.
- Cuando `i` llega a 6, se cumple la condición y se salta al final.
- El valor 15 queda guardado en la dirección de `memoria 12`.
- El registro `D` cambia constantemente para cargar valores temporales.
- `i` se va incrementando de uno en uno.

### Sustentación

```asm
// Inicializar suma = 0
@12
M=0

// Inicializar contador para que inicie en 25
@25
D=A
@i
M=D

(LOOP)
// Si i > 36, saltar al final
@i
D=M
@36
D=D-A
@END
D;JEQ

// suma = suma + i
@i
D=M
@12
M=D+M

// i = i + 1
@i
M=M+1

// Volver al inicio del ciclo
@LOOP
0;JMP

// Fin del programa

(END)
@END
0;JMP
```

## Bitácora de reflexión

>Responde con tus propias palabras a las siguientes preguntas.

***Describe con tus palabras las tres fases del ciclo Fetch-Decode-Execute. ¿Qué rol juega el `Program Counter (PC)` en este ciclo?***

**Fetch ->** La CPU busca la instrucción almacenada en la memoria ROM utilizando la dirección indicada por el Program Counter (PC).

**Decode ->** La instrucción es interpretada para identificar su tipo y las operaciones que se deben realizar.

**Execute ->** La CPU lleva a cabo la acción indicada, ya sea una operación aritmética o lógica, el almacenamiento de un valor en un registro o memoria, o un cambio en el flujo del programa mediante un salto.

El Program Counter (PC) cumple un rol fundamental, ya que mantiene la dirección de la siguiente instrucción a ejecutar. Normalmente se incrementa de forma secuencial, pero puede cambiar cuando se ejecuta una instrucción de salto.

***¿Cuál es la diferencia fundamental entre una instrucción-`A` (que empieza con @) y una instrucción-`C` (que involucra `D`, `M`, `A`, etc.) en el lenguaje ensamblador de Hack? Da un ejemplo de cada una.***

La instrucción-`A` comienza con el símbolo `@` y la utilizo para cargar un valor constante o una dirección de memoria en el registro `A`.

**Ejemplo:** `@10`

La instrucción-`C` me permite realizar cálculos, mover datos entre registros o ejecutar saltos condicionales, haciendo uso de la ALU y de los registros `A`, `D` y `M`.

**Ejemplo:** `D=D+1`


***Explica la función de los siguientes componentes del computador Hack: el registro `D`, el registro `A` y la ALU.***

`D` -> es un registro de propósito general que utilizo para almacenar datos temporales y resultados de operaciones.

`A` -> puede contener tanto un valor numérico como una dirección de memoria. Cuando trabajo con `M`, estoy accediendo a la posición de memoria señalada por el registro `A`.

`ALU` -> es el componente encargado de ejecutar las operaciones aritméticas y lógicas, como sumas, restas y comparaciones, además de generar las condiciones necesarias para los saltos.

***¿Cómo se implementa un salto condicional en Hack? Describe un ejemplo (p. ej., saltar si el valor de `D` es mayor que cero).***

Los saltos condicionales se implementan evaluando el contenido de un registro, usualmente el registro `D`, y aplicando una condición de salto. Si la condición se cumple, el flujo del programa cambia a la dirección indicada.

**Ejemplo:** salto si el valor de `D` es mayor que cero.

```asm
@SALTO
D;JGT
```

***¿Cómo se implementa un loop en el computador Hack? Describe un ejemplo (p. ej., un loop que decremente un valor hasta que llegue a cero).***

Los loops en Hack los implemento combinando etiquetas con saltos condicionales. De esta forma, el programa puede repetir un conjunto de instrucciones mientras se cumpla una condición específica.

**Ejemplo:** loop que decrementa un valor hasta llegar a cero.

```asm
(LOOP)
@5
M=M-1
D=M
@LOOP
D;JGT
```

***¿Cuál es la diferencia entre la instrucción `D=M` y la instrucción `M=D`?***

**`D=M`** -> Copia el valor almacenado en la memoria (apuntada por el registro `A`) al registro `D`.

**`M=D`** -> Copia el contenido del registro `D` a la dirección de memoria indicada por `A`.

La diferencia principal entre ambas instrucciones está en la dirección en la que fluye el dato.

***Describe brevemente qué se necesita para leer un valor del teclado `(KBD)` y para “pintar” un pixel en la pantalla `(SCREEN)`.***

Para leer el teclado, accedo a la dirección de memoria KBD (24576), donde se almacena el código de la tecla presionada. Para escribir en la pantalla, utilizo la memoria `SCREEN`, que inicia en la dirección `16384`. Al escribir valores distintos de cero en estas posiciones de memoria, se activan los píxeles correspondientes en la pantalla.





















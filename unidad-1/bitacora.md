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
(LOOP) // O (START)

@5
D=M 77CARGANDO EN D LO DE LA POSICION 5
@10
D=D-A //LEER DIRECCION DE MEMORIA 5 Y RESTARLO A D10 ARA SABER SI ES MAYOR O MENOR Q 10 

@MENOR
D;JLT //INSTRUCCION DE SALTO GENERA UN VALOR EN EL REGRSTRO D, SALTA A MENOR


(MAYOREQ) // SIGO DERECHO
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

#### *¿Qué diferencia hay entre los datos almancenados en la memoria ROM y en la RAM?*
La RAM es la memoria que usa el computador mientras estás trabajando, como cuando abres programas o juegos. Es rápida pero se borra cuando apagas todo. En cambio, la ROM tiene info que el computador necesita para encender, como las instrucciones básicas, y esa no se borra. La RAM se puede escribir y cambiar todo el tiempo, pero la ROM casi no se toca.

### Actividad 04
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
#### *Paso a paso*

**1.** Cargar valor de `M[5]` en `D`

**2.** Restar 10 a `D` → `D = M[5] - 10`

**3.** Si `D < 0` → saltar a `(MENOR)`

**4.** Si `D ≥ 0` → guardar 0 en `M[7]`

**5.** Ir a bucle infinito `(LOOP)`

**6.** `(MENOR)` → guardar 1 en `M[7]`

**7.** Ir a bucle infinito `(LOOP)`

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
























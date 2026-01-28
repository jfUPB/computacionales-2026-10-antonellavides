# Unidad 1

## Bitácora de Proceso de Aprendizaje
### Actividad 01
> Crea un archivo llamado program.asm y copia el código del programa anterior. Ejecuta el programa en el simulador de la CPU Hack y observa cómo se comporta.
### Programa (program.asm)
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

### *1.* ¿Qué sucede? ¿Qué valor se almacena en la dirección de memoria 16? ¿Por qué crees que es ese valor?
Al seguir los pasos y ejecutarlo en el simulador de la CPU Hack, la computadora sigue las instrucciones paso a paso y en esta ocasión realiza una suma sencilla.

1-Comienza cargando el numero 1 en el registro A `@1`, luego, se copia en el registro D `D=A`

2-Despues, carga el número 2 en el registro A (@2), luego, suma el valor de D (1) con el valor de A (2), dando como resultado 3 (D=D+A)

3- Se busca o apunta a la dirección de memoria 16 (@16) y, el valor de esa operación (3) se guarda en esa dirección de memoria (M=D)

4- El programa llega a (@END y (END)), esto significa que vaya a la instrucción marcada con END, que está en la posición 7 (@7)

5- Por último, tenemos (0;JMP), esto hace que la CPU salte siempre a esa misma instrucción, creando un bucle infinito, así, el programa se queda repitiendo la misma instrucción y no cambia nada más en la memoria ni en los registros.


 




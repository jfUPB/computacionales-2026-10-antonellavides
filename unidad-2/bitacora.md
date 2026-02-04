# Unidad 2

## Bitácora de proceso de aprendizaje

### Actividad 01
***Escribe un programa que dibuje un punto negro en la esquina superior izquierda de la pantalla.***
> Escribe el programa y simula paso a paso el programa en ensamblador. Recuerda la metodología: predice, ejecuta, observa y reflexiona.

```asm
(start)

@SCREEN

@fin
(fin)
0;JMP
```

### Actividad 02
***Modifica el programa anterior para que dibuje una línea horizontal negra de 16 pixeles de largo en la esquina superior izquierda de la pantalla.***
> Escribe el programa y simula paso a paso el programa ensamblador. Recuerda la metodología: predice, ejecuta, observa y reflexiona.

```asm
(start)

@SCREEN
M=-1
@fin
(fin)
0;JMP
```

```asm
(start)
@7
D=A
@SCREEN

M=D

@fin
(fin)
0;JMP
```

### Actividad 03
***Modifica el programa de la actividad anterior de tal manera que puedas mover la línea horizontal de derecha a izquierda usando las teclas d y i respectivamente. Tu programa no tiene que verificar si la línea se sale de la pantalla.***
> Escribe el programa y simula paso a paso el programa ensamblador. Recuerda la metodología: predice, ejecuta, observa y reflexiona.

```asm
(start)
// i = SCREEN
@SCREEN
D=A
@i
M=D
// INICIO LA PANTALLA PINTANDO UNA LINEA
@SCREEN
M=-1 // ACA LA PINTAMOS


(LOOP)
@KBD
D=M // LEER EN D LO QUE TENGO EN LA MEMORIA
@100
D=D-A //100 EN LA A
@DERECHA
D;JEQ


@KBD
D=M // LEER EN D LO QUE TENGO EN LA MEMORIA
@105
D=D-A //100 EN LA A
@IZQUIERDA
D;JEQ
@LOOP
0;JMP



(DERECHA) //LEER LO QUE TENEMOS EN i
@i  
A=M //GUARDAR EN A
M=0 // BORRO
A=A+1 // AUMENTO LO QUE TENGO EN A
M=-1 // BORRO
D=A // GUARDO EL VALOR
@i
M=D
@LOOP
0;JMP //VUELVO Y LEO LO Q TENGO EN i

(IZQUIERDA)
@i
A=M
M=0
A=A-1
M=-1
D=A
@i
M=D
@LOOP
0;JMP


@fin
(fin)
0;JMP
```

### Actividad 04
***Convierte un ciclo while en un ciclo for***
> Escribe el programa y simula paso a paso el programa ensamblador. Recuerda la metodología: predice, ejecuta, observa y reflexiona.

### Actividad 05
***Punteros***
> Convierte estos programas a ensamblador y realiza la simulación paso a paso. Recuerda la metodología: predice, ejecuta, observa y reflexiona.
```asm
int a = 10;
int* p;
p = &a;
*p = 20;
```

```asm
int a = 10;
int b = 5;
int *p;
p = &a;
b = *p;
```
**Solucion**

### Actividad 06
***Experimenta con arreglos***
> - Implementa el programa anterior en lenguaje ensamblador aplicando el concepto de punteros.
> - Considera que los datos del arreglo están almacenados desde la dirección 16. Inicializa el arreglo en lenguaje ensamblador.
> - Simula paso a paso el programa en ensamblador. Recuerda la metodología: predice, ejecuta, observa y reflexiona.
> - Construye tu programa PASO A PASO mediante pruebas. Indica qué característica vas a implementar con cada prueba y cómo la probaste.
> - Muestra el programa final y cómo lo probaste.

### Actividad 07
***Experimenta con funciones***
> Considera el siguiente programa en C++ que utiliza funciones:

## Bitácora de aplicación 



## Bitácora de reflexión


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

`C++`

```c++
int a = 10;
int* p;
p = &a;
*p = 20;
```

`ENSAMBLADOR`

```c++
//int a = 10;
@10
D=A
@a
M=D

//int* p;
// p = &a;
@a
D=A
@p
M=D

//*p = 20;
@20
D=A
// TENER EN A EL VALOR ALMACENADO EN P, PQ P APUNTA A A
@p
A=M
M=D
```

`C++`

```c++
int a = 10;
int b = 5;
int *p;
p = &a;
b = *p;
```

`ENSAMBLADOR`

```c++
//int a = 10;
@10
D=A
@a
M=D

//int b = 5;
@5
D=A
@b
M=D

//int* p;
// p = &a;
@a
D=A
@p
M=D

//b = *p;
@p  // a = contenido de p pero p tiene la direccion de A
A=M // A=16
D=M // D= contenido de la direccion 16 
@b  // A = la direccion de b --> 17
M=D // Guardando en la 17 que es b el 10 que tengo en D
```

### Actividad 06
***Experimenta con arreglos***
> - Implementa el programa anterior en lenguaje ensamblador aplicando el concepto de punteros.
> - Considera que los datos del arreglo están almacenados desde la dirección 16. Inicializa el arreglo en lenguaje ensamblador.
> - Simula paso a paso el programa en ensamblador. Recuerda la metodología: predice, ejecuta, observa y reflexiona.
> - Construye tu programa PASO A PASO mediante pruebas. Indica qué característica vas a implementar con cada prueba y cómo la probaste.
> - Muestra el programa final y cómo lo probaste.

***Importante***

- **El arreglo** = cajones seguidos

- **El puntero** = número que dice qué cajón mirar

- **El ciclo** = repetir con saltos
 
- **El contador** = para saber cuándo parar

***Cajón / Qué guarda***

`26` -> sum (la suma total)

`27` -> puntero (dice en qué cajón del arreglo estamos)

`28` -> contador (cuántos números llevamos sumados)

`29` -> 10 (para saber cuándo parar)


***Codigo***
```asm
// ===============================
// Inicialización del arreglo
// arr empieza en la dirección 16
// ===============================

@1
D=A
@16
M=D

@20
D=A
@17
M=D

@13
D=A
@18
M=D

@24
D=A
@19
M=D

@55
D=A
@20
M=D

@96
D=A
@21
M=D

@87
D=A
@22
M=D

@83
D=A
@23
M=D

@98
D=A
@24
M=D

@102
D=A
@25
M=D

// ===============================
// Inicialización de variables
// ===============================

@0
D=A
@26      // sum
M=D

@16
D=A
@27      // puntero
M=D

@0
D=A
@28      // contador
M=D

@10
D=A
@29      // limite
M=D

// ===============================
// Bucle principal
// ===============================

(LOOP)
    @28
    D=M
    @29
    D=D-M
    @END
    D;JEQ      // si contador == 10 termina

    // sum = sum + *puntero
    @27
    A=M
    D=M
    @26
    M=D+M

    // puntero++
    @27
    M=M+1

    // contador++
    @28
    M=M+1

    @LOOP
    0;JMP

// ===============================
// Fin del programa
// ===============================

(END)
    @END
    0;JMP
```

<img width="500" height="500" alt="Screenshot 2026-02-09 191231" src="https://github.com/user-attachments/assets/3040946c-0177-44a3-9bf2-d5fb4772cb14" />


## Bitácora de aplicación 

### Actividad 08

> Resolver dos problemas de traducción de C++ a ensamblador.

***Problema 1***

```asm
// ---------------- MAIN ----------------

// a = 10  (RAM[16])
@10
D=A
@16
M=D

// b = 20 (RAM[17])
@20
D=A
@17
M=D

// pasar argumentos
@16
D=A
@R0
M=D     // R0 = &a

@17
D=A
@R1
M=D     // R1 = &b

// llamar swap
@RETURN_SWAP
D=A
@R15
M=D
@SWAP
0;JMP

(RETURN_SWAP)

// fin del programa
(END)
@END
0;JMP


// ---------------- FUNCION SWAP ----------------
(SWAP)

// tmp = *pa
@R0
A=M
D=M
@R13
M=D

// *pa = *pb
@R1
A=M
D=M
@R0
A=M
M=D

// *pb = tmp
@R13
D=M
@R1
A=M
M=D

// return
@R15
A=M
0;JMP

```
***Inicialización de variables***

<img width="500" height="500" alt="Screenshot 2026-02-12 222343" src="https://github.com/user-attachments/assets/b034edba-b0eb-4734-81a3-dc83c9a5ba7c" />

- En esta captura se observa la inicialización de las variables a y b en memoria. La dirección 16 contiene el valor 10 y la dirección 17 contiene el valor 20, lo que confirma que los datos fueron almacenados correctamente antes de llamar a la función swap.

***Ejecución de la función swap***

<img width="500" height="500" alt="Screenshot 2026-02-12 222355" src="https://github.com/user-attachments/assets/98f0fe3e-f30b-4b64-b529-bc6ce8ac6c5e" />

- En esta imagen se muestra el resultado después de ejecutar la función swap. Los valores fueron intercambiados correctamente utilizando punteros, demostrando la manipulación directa de direcciones de memoria en lenguaje ensamblador.

***Problema 2***

```asm
// ------------ MAIN ------------

// arr = {10,15,2,3,50}
@10
D=A
@16
M=D

@15
D=A
@17
M=D

@2
D=A
@18
M=D

@3
D=A
@19
M=D

@50
D=A
@20
M=D

// argumentos
@16
D=A
@R0
M=D     // puntero arr

@5
D=A
@R1
M=D     // tamaño

// llamar calSum
@RETURN_SUM
D=A
@R15
M=D
@CALSUM
0;JMP

(RETURN_SUM)

// resultado queda en R0

(END)
@END
0;JMP


// ------------ FUNCION CALSUM ------------
(CALSUM)

// sum = 0
@0
D=A
@R2
M=D

// i = 0
@0
D=A
@R3
M=D


(LOOP)

// if i >= arrSize -> END
@R3
D=M
@R1
D=D-M
@FIN
D;JGE


// dirección = parr + i
@R0
D=M
@R3
D=D+M
@R13
M=D

// sum += *(parr+i)
@R13
A=M
D=M
@R2
M=M+D

// i++
@R3
M=M+1

@LOOP
0;JMP


(FIN)

// return sum
@R2
D=M
@R0
M=D

@R15
A=M
0;JMP
```

******

<img width="500" height="500" alt="Screenshot 2026-02-12 222930" src="https://github.com/user-attachments/assets/81b680df-36a1-4956-a57f-b257aff2d713" />

- Aquí se observa el inicio de la función calSum. El registro R2 se inicializa en 0 para almacenar la suma y el registro R3 actúa como contador del ciclo que recorrerá el arreglo.

******

<img width="500" height="500" alt="Screenshot 2026-02-12 222946" src="https://github.com/user-attachments/assets/803aebd0-cb48-4c02-9c70-a3e14ab4bfa5" />

- La captura muestra el resultado final de la ejecución. El registro R0 contiene el valor 80, que corresponde a la suma de todos los elementos del arreglo, confirmando que la función fue implementada correctamente.

## Bitácora de reflexión

### Actividad 09

> Implementar un programa en lenguaje ensamblador que dibuje un mapa de bits en la pantalla del computador Hack.












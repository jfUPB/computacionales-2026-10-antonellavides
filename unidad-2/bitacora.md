# Unidad 2

## Bitácora de proceso de aprendizaje

```asm
(start)

@SCREEN

@fin
(fin)
0;JMP
```
### Actividad 02
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

manualmente, dividir problemas en
poner -1 en el de antes o el de despues de 16384



## Bitácora de aplicación 



## Bitácora de reflexión

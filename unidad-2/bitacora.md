# Unidad 2

## Bitácora de proceso de aprendizaje

#### Actividad 1
```
@1
D=A
@SCREEN
M=D

(END)
@END
0;JMP
```
— se pinta un puntito en la esquina izquierda.

#### Actividad 2
```
@1
D=A
D=-D
@SCREEN
M=D

(END)
@END
0;JMP 
```
— Se pinta la línea 

#### Actividad 3
```
@SCREEN
D=A
@R0
M=D        // R0 guarda la posición actual de la línea

@1
D=A
D=-D
@R1
M=D        // R1 = -1 (línea de 16 píxeles)

(LOOP)
@KBD
D=M

@100       // tecla 'd'
D=D-A
@RIGHT
D;JEQ

@KBD
D=M
@105       // tecla 'i'
D=D-A
@LEFT
D;JEQ

@LOOP
0;JMP

(RIGHT)
@R0
A=M
M=0
@R0
M=M+1
A=M
@R1
D=M
M=D
@LOOP
0;JMP

(LEFT)
@R0
A=M
M=0
@R0
M=M-1
A=M
@R1
D=M
M=D
@LOOP
0;JMP 
```
NOTA: Funciona un poco raro, sigue mejorando

#### Actividad 4
```
@sum
M=0

@i
M=1

(LOOP)
@i
D=M
@101
D=D-A
@END
D;JGE

@i
D=M
@sum
M=M+D

@i
M=M+1

@LOOP
0;JMP

(END)
@END
0;JMP 
```
## Bitácora de aplicación 

#### Actividad 5
— Programa 1
```
@10
D=A
@16     // a
M=D

@16
D=A
@17     // p
M=D

@20
D=A
@17
A=M
M=D 
```

— Programa 2
```
@10
D=A
@16     // a
M=D

@5
D=A
@18     // b
M=D

@16
D=A
@17     // p
M=D

@17
A=M
D=M
@18
M=D
```

#### Actividad 6
```
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

@sum
M=0

@j
M=0

@16
D=A
@p
M=D

(LOOP)
@j
D=M
@10
D=D-A
@END
D;JGE

@p
A=M
D=M
@sum
M=M+D

@p
M=M+1

@j
M=M+1

@LOOP
0;JMP

(END)
@END
0;JMP 
```
Observaciones:
- Se escriben 10 valores consecutivos en las direcciones 16 a 25.
- Se inicializa sum en 0.
- Se inicializa j en 0.
- Se guarda la dirección 16 en p.
- El programa termina en un bucle infinito.

## Bitácora de reflexión
— Pintar en bitmap

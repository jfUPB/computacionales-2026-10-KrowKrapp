# Unidad 1

## Bitácora de proceso de aprendizaje
#### Actividad 1:

Con el fetch-decode-execute lo que pasa es que en ese programa se muestra una operación de 2+1=3 y guarda el resultado en el espacio de @16 quedando como @16=3.
En fetch: se toman todas las instrucciones de la aplicación, como lo que es @1 se vuelve D=A
En decode: aquí es donde se da cuenta la app que se va a hacer una suma y ve lo que se necesita y en donde se va a guardar y tales.
En execute: se haría lo que es como la suma de D=D+A por que ahí es donde la pc tiene que ver la operación que se hace y de ahí es donde sigue y se guarda en el espacio de la RAM estimado el resultado.

En la memoria lo que pasa es que se ve el cambio en el espacio 16 que se almacena el número 3, de resto en toda la memoria no hay cambios. 
Y en los registros pues se ve que A crece con los comandos que hay de @, D queda con el número 3.

Experimento del programa:
```
@5
D=A       
@10
D=D+A     
@20
M=D       
@END
(END)
0;JMP
```

Solo modifique el código pasado y ya verifique que funcionara bien :D, si se guarda en el espacio 20.

#### Actividad 2:
Como lo tenía lento, no estaba viendo que se estaba pintando la pantalla pero ya al ponerlo rápido pues me doy cuenta que con la tecla que se presione va a ir marcando y va a ir pintando la pantalla mientras va contando en el código con lo que aumenta de número y luego cuando ya se deje de presionar la tecla vuelve a estar pintado de blanco y borra el proceso ya marcado ahí.

#### Respuesta a las preguntas:
1. Instrucción que use la ALU
D=D+1
La ALU suma 1 al valor de D y guarda el resultado en el mismo registro.

2. ¿Para qué sirve el registro PC?
El PC indica qué instrucción se ejecuta a continuación y cambia cuando hay saltos.

3. Diferencia entre @i y @READKEYBOARD
@i es una variable en RAM creada por el programador.
@READKEYBOARD es una dirección especial que lee directamente el teclado.

4. ¿Qué se necesita para leer teclado y mostrar en pantalla?
Leer el valor del teclado desde su dirección de memoria y escribir datos en la memoria de la pantalla.

5. Identifica un bucle
Un bucle usa una etiqueta y un salto (JMP) para repetir instrucciones continuamente.

6. Identifica una condición
Una condición usa saltos como JEQ o JNE para decidir si se continúa o se salta según un valor.

#### Actividad 3

```
(start)
// i = SCREEN
 @SCREEN
D=A
@i
M=D // Inicio la pantalla pintando una linea
@SCREEN
M=-1
(LOOP)
@KBD
 D=M
@100
 D=D-A
 @derecha
 D;JEQ
 @KBD
 D=M
 @105
D=D-A
 @izquierda
 D;JEQ
@LOOP
 0;JMP
 (derecha)
 @i
 A=M
M=0
A=A+1
 M=-1
D=A
 @i
 M=D
@LOOP
0;JMP
 (izquierda)
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
```

## Bitácora de aplicación 
```
@sum
M=0

@i
M=1

(LOOP)
  @i
  D=M
  @6
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
  @sum
  D=M
  @12
  M=D

(STOP)
  @STOP
  0;JMP 
```

## Bitácora de reflexión
— El ciclo Fetch-Decode-Execute funciona así: primero el computador trae la instrucción desde memoria, luego la interpreta y finalmente la ejecuta. El PC se encarga de indicar qué instrucción sigue y cambia cuando hay saltos.

— La diferencia entre una instrucción-A y una instrucción-C es que la A solo carga un valor o dirección en el registro A, por ejemplo @10, mientras que la C realiza operaciones o decisiones, como D=M+1.

— El registro D se usa para guardar datos temporales, el registro A guarda direcciones o valores, y la ALU hace las operaciones aritméticas y lógicas.

— Un salto condicional se hace comparando un valor y usando una instrucción de salto, por ejemplo D;JGT salta si D es mayor que cero.

— Un loop se implementa con una etiqueta y un salto que vuelve a ella, repitiendo el código hasta que se cumpla una condición, como decrementar un valor hasta que llegue a cero.

— La instrucción D=M copia un valor de memoria al registro D, mientras que M=D copia el valor de D a memoria.

— Para leer el teclado se accede a la dirección KBD, y para pintar en pantalla se escribe un valor en una dirección de SCREEN.

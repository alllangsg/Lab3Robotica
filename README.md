# Lab3: Robótica Industrial 2, Entradas y Salidas
## Universidad Nacional de Colombia
## Integrantes: Allan Giordy Serrato Gutierrez y Juan Fernando Ramirez Montes

## Objetivo
Crear una código en RAPID que genere una rutina para un brazo robótico ABB IRB140 que en la práctica reciba dos entradas digitales y controle dos salidas digitales. La rutina debe cumplir los siguientes requistos:
- Se deben crear dos entradas y dos salidas digitales configuradas correctamente en el código de RAPID.
- La primera señal de entrada debe iniciar una rutina de escritura y encender una luz de indicación.
- Al final de la rutina el brazo debe regresar a su posición de HOME.
- La segunda señal de entrada debe posicionar el brazo en una pose de mantenimiento donde se pueda instalar o desinstalar la herramienta y se debe apagar la luz de inclinación.
- Los botones en el mando de señales digitales debe controlar la transición entre las rutinas.
-Velocidades, zonas de aproximación y otros parámetros a discreción de los estudiantes. 

A continuación se muestran los videos y los códigos correspondientes a la simulación hecha en RobotStudio 2022 y a la implementación de dicho código en el brazo robótico disponible en el LabSir (Laboratorio de Sistemas Inteligentes Robotizados) de la universidad.

## Simulación en RobotStudio

### Video

https://user-images.githubusercontent.com/62154397/194233427-4a2bc218-4aea-4b58-b0ff-1e485aabc81c.mp4


### Código RAPID Simulación

```console
PROC main()
        WaitDI DI_01,1;
        Homing;
        Set DO_01;
        WaitDI DI_02,1;
        Reset DO_01;
        Set DO_02;
        ToolLft;
        WaitDI DI_01,1;
        Reset DO_02;
        Set DO_01;
        Homing;
        WaitDI DI_03,1;
        Reset DO_01;
        Set DO_03;
        MidPoint;
        PathJ;
        PathA;
        MidPoint;
        WaitDI DI_01,1;
        Reset DO_03;
        Homing;
    ENDPROC
```

```console
PROC PathJ()
        MoveL Target_10,v150,fine,Dummy\WObj:=Tablero1;
        MoveL Target_20,v150,fine,Dummy\WObj:=Tablero1;
        MoveL Target_30,v150,fine,Dummy\WObj:=Tablero1;
        MoveL Target_40,v150,fine,Dummy\WObj:=Tablero1;
        MoveL Target_50,v150,fine,Dummy\WObj:=Tablero1;
        MoveL Target_60,v150,fine,Dummy\WObj:=Tablero1;
        MoveL Target_70,v150,fine,Dummy\WObj:=Tablero1;
        MoveL Target_80,v150,fine,Dummy\WObj:=Tablero1;
        MoveL Target_90,v150,fine,Dummy\WObj:=Tablero1;
        MoveL Target_100,v150,fine,Dummy\WObj:=Tablero1;
        MoveL Target_110,v150,fine,Dummy\WObj:=Tablero1;
        MoveL Target_120,v150,fine,Dummy\WObj:=Tablero1;
        MoveL Target_130,v150,fine,Dummy\WObj:=Tablero1;
        MoveL Target_140,v150,fine,Dummy\WObj:=Tablero1;
        MoveL Target_150,v150,fine,Dummy\WObj:=Tablero1;
        MoveL Target_160,v150,fine,Dummy\WObj:=Tablero1;
        MoveL Target_170,v150,fine,Dummy\WObj:=Tablero1;
        MoveL Target_180,v150,fine,Dummy\WObj:=Tablero1;
        MoveL Target_190,v150,fine,Dummy\WObj:=Tablero1;
        MoveL Target_200,v150,fine,Dummy\WObj:=Tablero1;
        MoveL Target_210,v150,fine,Dummy\WObj:=Tablero1;
        MoveL Target_220,v150,fine,Dummy\WObj:=Tablero1;
    ENDPROC
```

```console
  PROC PathA()
        MoveL Target_410,v150,fine,Dummy\WObj:=Tablero1;
        MoveL Target_420,v150,fine,Dummy\WObj:=Tablero1;
        MoveL Target_430,v150,fine,Dummy\WObj:=Tablero1;
        MoveL Target_440,v150,fine,Dummy\WObj:=Tablero1;
        MoveL Target_450,v150,fine,Dummy\WObj:=Tablero1;
        MoveL Target_460,v150,fine,Dummy\WObj:=Tablero1;
        MoveL Target_470,v150,fine,Dummy\WObj:=Tablero1;
        MoveL Target_480,v150,fine,Dummy\WObj:=Tablero1;
        MoveL Target_490,v150,fine,Dummy\WObj:=Tablero1;
        MoveL Target_500,v150,fine,Dummy\WObj:=Tablero1;
        MoveL Target_510,v150,fine,Dummy\WObj:=Tablero1;
        MoveL Target_520,v150,fine,Dummy\WObj:=Tablero1;
        MoveL Target_530,v150,fine,Dummy\WObj:=Tablero1;
        MoveL Target_540,v150,fine,Dummy\WObj:=Tablero1;
        MoveL Target_550,v150,fine,Dummy\WObj:=Tablero1;
        MoveL Target_560,v150,fine,Dummy\WObj:=Tablero1;
        MoveL Target_570,v150,fine,Dummy\WObj:=Tablero1;
        MoveL Target_580,v150,fine,Dummy\WObj:=Tablero1;
        MoveL Target_590,v150,fine,Dummy\WObj:=Tablero1;
    ENDPROC
 ```
 
```console
 PROC Homing()
        MoveAbsJ Home,v150,fine,Dummy\WObj:=Tablero1;
    ENDPROC
 ```    
 
```console
 PROC MidPoint()
        MoveAbsJ JointMID,v100,fine,MarcadorSR\WObj:=Tablero1;
    ENDPROC
 ``` 
     
 ```console
 PROC ToolLft()
        MoveAbsJ TooLft,v150,fine,MarcadorSR\WObj:=Tablero1;
    ENDPROC
 ```  
 
```console
    PROC ToolRg()
       MoveAbsJ ToolRgt,v150,fine,MarcadorSR\WObj:=Tablero1;
   ENDPROC
``` 

## Práctica en el LabSIR

### Video

https://user-images.githubusercontent.com/62154397/194236520-45fe867c-2d41-4265-b6f6-993b4ed881e3.mp4


### Código RAPID Implementado.

El código Implementado en el controlador del brazo robótico ABB IRB140 fue casi el mismo que el usaod en la simulación. El único cambio que se realizó con ayuda del flex pendant fue un ligero cambio en las entradas digitales del main(). Como el controlador solo tenia configuradas dos entradas digitales, se reemplazo la entrada digital DI_O3 por la señal digital DI_O1 como indicador del inicio de la rutina de dibujo. Por el mismo motivo que las entradas, también se reemplazo la salida digital DI_O3 como indicador de la rutina de dibujo por la salida digital DI_O2. Dichos cambios representaron un cambio en tres lineas de código del main(), tal y como se puede apreciar a continuación.

```console
PROC main()
        WaitDI DI_01,1;
        Homing;
        Set DO_01;
        WaitDI DI_02,1;
        Reset DO_01;
        Set DO_02;
        ToolLft;
        WaitDI DI_01,1;
        Reset DO_02;
        Set DO_01;
        Homing;
        WaitDI DI_01,1;
        Reset DO_01;
        Set DO_02;
        MidPoint;
        PathJ;
        PathA;
        MidPoint;
        WaitDI DI_01,1;
        Reset DO_02;
        Homing;
    ENDPROC
```

###Solución Implementada

Como resultado se obtuvo un comportamiento del robot ABB IRB140 que respondia a las siguientes características:
- Espera que se oprima el botón configurado como DI_01 para llevar al robot a Home y se enciende el bombillo configurado como DO_01 para indicar que la rutina inicio.
- Una vez en Home espera a que se oprima el boton configurado como DI_02 para llevar la robot a una posición comoda para poder poner la herramienta de dibujo; se apaga el bombillo DO_01 y se enciende el bombillo DO_02.
- Una vez puesta la herramienta se orpimer el boton DI_01 para llevar al robot otra vez a Home. Se paga el bombilo DO_02 y se vuelve a encender el bombillo DO_01.
- Ya en Home, se oprime nuevamente el boton DI_01 para que el robot inicie la rutina de dibujado. El botón DO_01 sigue encendido.
- Una vez se termine el dibujado, el robot espera en el punto de aproximación a que se oprima nuevamente el boton DI_01 para moverse a Home. Los dos bombillos se apagan para indicar la finalización de la rutina.

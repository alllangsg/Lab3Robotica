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

### Código RAPID Implementado.

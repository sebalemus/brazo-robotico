/*
  este programa que permite controlar un brazo robotico de 4 grados 
  de libertad,de forma manual con potenciometros y servomotores sg90

  Autor: Sebastian lemus  
*/

#include <Servo.h>  //incluimos la librería Servo
Servo servo1;          //garra ( mamo)
Servo servo2;         //brazo horizontal x ( ante brazo)
Servo servo3;         //brazo vertical y
Servo servo4;         // rotacion de la base

void setup() 
{ 
  servo1.attach(10);  // asignamos el pin 10 con salida analigica al servo 1 para la garra
  servo2.attach(9);  // asignamos el pin 9 con salida analigica al servo 2 para el ante brazo
  servo3.attach(6);  // asignamos el pin 6 con salida analigica al servo 3 para brazo vertical
  servo4.attach(5);  // asignamos el pin 5 con salida analigica al servo 4 rotación de la base

  /*
  asignamos un angulo inicial  de 0° a todos los servos
        */
        
  servo1.write(0);  
  servo2.write(0);  
  servo3.write(0);  
  servo4.write(0);  
} 

void loop() 
{                            
  int angulo1 = map(analogRead(A0), 0, 1023, 0, 90);  // leemos la entrada analogica A0, tomamos de 0 y 1023 y lo escalamos de 0° a 90° para abrir y cerrar la garra
  int angulo2 = map(analogRead(A1), 0, 1023, 0, 100); //leemos la entrada analogica A1, tomamos de 0 y 1023 y lo escalamos de 0° a 100°
  int angulo3 = map(analogRead(A2), 0, 1023, 0, 150); //leemos la entrada analogica A2, tomamos de 0 y 1023 y lo escalamos de 0° a 150°
  int angulo4 = map(analogRead(A3), 0, 1023, 0, 180); //leemos la entrada analogica A3, tomamos de 0 y 1023 y lo escalamos de 0° a 180°
  
  servo1.write(angulo1);  // 
  servo2.write(angulo2);  // el servo recibe la señal escalada.
  servo3.write(angulo3);  // el servo recibe la señal escalada.
  servo4.write(angulo4);  // el servo recibe la señal escalada.
  delay(100);            
}

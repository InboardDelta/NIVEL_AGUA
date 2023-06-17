# PRACTICA ESP32 CON ULTRASONICO Y 4 LED
Este repositorio muestra como podemos programar una **HC-SR04 Ultrasonic Distance Sensor** con el sensor ultrasonico y 4 LED el cual programaremos con los valores pedidos por el docente.
## MATERIAL NECESARIO

Para realizar esta practica necesitas lo siguiente

- [WOKWI](https://https://wokwi.com/)
- Tarjeta ESP 32
- Sensor **HC-SR04 Ultrasonic Distance Sensor**
- LED x 4
## INTRODUCCION
### DESCRIPCION
La (```Esp32```) la utilizamos en un entorno de adquision de datos, lo cual en esta practica ocuparemos un sensor (```HC-SR04 Ultrasonic Distance Sensor```) para obtener el valor de distancia y así poder obtener un nivel de agua apoyado de los LED's; Cabe aclarar que esta practica se usara un simulador llamado [WOKWI](https://https://wokwi.com/). 
### INSTRUCCIONES
1. Abrir la terminal de programación y colocar la siguente programación:

```
// defines pins numbers
const int trigPin = 4;
const int echoPin = 2;
const int led1 = 23;
const int led2 = 22;
const int led3 = 21;
const int led4 = 19;

// defines variables
long duration;
int distance;
int safetyDistance;


void setup() {
pinMode(trigPin, OUTPUT); // Sets the trigPin as an Output
pinMode(echoPin, INPUT); // Sets the echoPin as an Input
pinMode(led1, OUTPUT);
pinMode(led2, OUTPUT);
pinMode(led3, OUTPUT);
pinMode(led4, OUTPUT);
Serial.begin(9600); // Starts the serial communication
}


void loop() {
// Clears the trigPin
digitalWrite(trigPin, LOW);
delayMicroseconds(2);

// Sets the trigPin on HIGH state for 10 micro seconds
digitalWrite(trigPin, HIGH);
delayMicroseconds(10);
digitalWrite(trigPin, LOW);

// Reads the echoPin, returns the sound wave travel time in microseconds
duration = pulseIn(echoPin, HIGH);

// Calculating the distance
distance= duration*0.034/2;

safetyDistance = distance;
if (safetyDistance>=5 && safetyDistance<=10)
{
  digitalWrite(led1, HIGH);
  digitalWrite(led2, LOW);
  digitalWrite(led3, LOW);
  digitalWrite(led4, LOW);
}
else if(safetyDistance>=10 && safetyDistance<=20) 
{
  digitalWrite(led1, HIGH);
  digitalWrite(led2, HIGH);
  digitalWrite(led3, LOW);
  digitalWrite(led4, LOW);
}
else if(safetyDistance>=20 && safetyDistance<=30) 
{
  digitalWrite(led1, HIGH);
  digitalWrite(led2, HIGH);
  digitalWrite(led3, HIGH);
  digitalWrite(led4, LOW);
}
else if(safetyDistance>=30 && safetyDistance<=40) 
{
  digitalWrite(led1, HIGH);
  digitalWrite(led2, HIGH);
  digitalWrite(led3, HIGH);
  digitalWrite(led4, HIGH);
}
else 
{
  digitalWrite(led1, LOW);
  digitalWrite(led2, LOW);
  digitalWrite(led3, LOW);
  digitalWrite(led4, LOW);  
}
// Prints the distance on the Serial Monitor
Serial.print("Distance: ");
Serial.println(distance);
delay (2000);
}


```
2.- Se buscaran las herramientas necesarias en el programa como : **HC-SR04 Ultrasonic Distance Sensor** y **4 LED** como se muestra en la imagen.
![](https://github.com/InboardDelta/NIVEL_AGUA/blob/main/componentes.png?raw=true)

3.- Realizaremos las conexiones de el sensor **HC-SR04 Ultrasonic Distance Sensor** y los 4 LED's y sus tierras como se muestra en la imagen.
![](![Alt text](conexiones-1.png)
## RESULTADOS
Cuando haya funcionado, podremos verificar el funcionamiento de los led al aumentar el nivel de agua mediante el programa, como se muestra en las imagenes.

![](https://github.com/InboardDelta/NIVEL_AGUA/blob/main/led%200.png?raw=true)
![](https://github.com/InboardDelta/NIVEL_AGUA/blob/main/led%201.png?raw=true)
![](https://github.com/InboardDelta/NIVEL_AGUA/blob/main/led%202.png?raw=true)
![](https://github.com/InboardDelta/NIVEL_AGUA/blob/main/led%203.png?raw=true)
![]()

# Créditos

Desarrollado por RODRIGO VEGA
- [GitHub](https://github.com/InboardDelta)
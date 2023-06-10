# Practica 4_ ESP32 Nivel de Agua 


En esta práctica podemos programar una ESP32 con un ultrasonido. 

## Contenido 

- Introducción 
- Objetivo
- Material Requerido
- Procedimiento 
- Instrucciones de operación 
- Resultados 



## 1. Introducción

La ```Esp32``` la utilizamos en un entorno de adquision de datos, lo cual en esta practica ocuparemos un ultrasonido (```HC-SR04 Ultrasonic distance sensor```).
### 1.1 Descripción
  
 
 ### 1.2 Especificación 
 Es importante considerar que esta practica se estara realiando en un simulador llamado [WOKWI](https://https://wokwi.com/).

## 2. Objetivo 

Poder diseñar un diagrama con HC-SR04 Ultrasonic distance sesor, mediante la utilización de una ESP32.


## 3. Material Requerido

Tomar en cuenta el material necesario para realizar esta práctica:

- [WOKWI](https://https://wokwi.com/)
- Tarjeta ESP 32
- Sensor de ultrasonido de distancia 
  (HC-SR04 Ultrasonic distance sensor)
- 4 LED 
- 4 Resistencias 



## 4. Procedimiento a realizar 

 - Requisitos previos

Para poder usar este repositorio necesitas entrar a la plataforma [WOKWI](https://https://wokwi.com/).


## Paso 1 

1. Abrir la terminal de programación y colocar la siguente programación:

```
// defines pins numbers
const int trigPin = 4;
const int echoPin = 15;
const int LED1 = 22;
const int LED2 = 21;
const int LED3 = 19;
const int LED4 = 18;

// defines variables
long duration;
int distance;
int safetyDistance;


void setup() {
pinMode(trigPin, OUTPUT); // Sets the trigPin as an Output
pinMode(echoPin, INPUT); // Sets the echoPin as an Input
pinMode(LED1, OUTPUT);
pinMode(LED2, OUTPUT);
pinMode(LED3, OUTPUT);
pinMode(LED4, OUTPUT);
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
if (safetyDistance>=2 && safetyDistance<=10)
{
  digitalWrite(LED1, HIGH);
  digitalWrite(LED2, LOW);
  digitalWrite(LED3, LOW);
  digitalWrite(LED4, LOW);
}
else if(safetyDistance>=10 && safetyDistance<=20) 
{
  digitalWrite(LED1, HIGH);
  digitalWrite(LED2, HIGH);
  digitalWrite(LED3, LOW);
  digitalWrite(LED4, LOW);
}
else if(safetyDistance>=20 && safetyDistance<=30) 
{
  digitalWrite(LED1, HIGH);
  digitalWrite(LED2, HIGH);
  digitalWrite(LED3, HIGH);
  digitalWrite(LED4, LOW);
}
else if(safetyDistance>= 30 && safetyDistance<= 40) 
{
  digitalWrite(LED1, HIGH);
  digitalWrite(LED2, HIGH);
  digitalWrite(LED3, HIGH);
  digitalWrite(LED4, HIGH);
}
else
{
 digitalWrite(LED1,  LOW);
  digitalWrite(LED2, LOW);
  digitalWrite(LED3, LOW);
  digitalWrite(LED4, LOW);
}
// Prints the distance on the Serial Monitor
Serial.print("Distance: ");
Serial.println(distance);
delay (2000);
}
```


## Paso 2 

2. Hacer la conexion de **HC-SR04 Ultrasonic distance sensor** con la **ESP32** como se muestra en la siguentes imagenes:

2.1 Es importante considerar que para **ESP32** se maneja un ```Voltaje de trabajo 3.3 VDC```. 

a) Observar conexión de  **ESP32**. 

![](https://github.com/DiegoJm10/PracticaESP32conULTRASONICO/blob/main/ESP32%20ULTRASONICO%20-%20Wokwi%20ESP32,%20STM32,%20Arduino%20Simulator%20-%20Google%20Chrome%2009_06_2023%2008_32_06%20a.%20m..png?raw=true)

b) Conexión de LCD 


![](https://github.com/DulceMRZ/PRACTICA_2_DHT22_CON_LCD/blob/main/Captura3.PNG?raw=truee)



c) Conexión de LCD más ESP32 y SENSOR

![](https://github.com/DulceMRZ/PRACTICA3_ESP32_ULTRASONIDO_LCD/blob/main/Captura1.PNG?raw=true)



### 5. Instrucciónes de operación

1. Iniciar simulador.
2. Visualizar los datos en el monitor serial.
3. Puedes modificar la distancia *doble click* al sensor **** 
![](https://github.com/DulceMRZ/PRACTICA3_ESP32_ULTRASONIDO_LCD/blob/main/Captura8.PNG?raw=true)


## 6. Resultados

Cuando haya funcionado, verás los valores dentro del monitor serial como se muestra en la siguente imagen.


![](https://github.com/DulceMRZ/PRACTICA3_ESP32_ULTRASONIDO_LCD/blob/main/PRACTICA%203%20ESP32%20ULTRASONIDO%20+%20LCD%20-%20Wokwi%20ESP32,%20STM32,%20Arduino%20Simulator%20-%20Google%20Chrome%2010_06_2023%2009_05_34%20a.%20m..png?raw=true)
 
![](https://github.com/DulceMRZ/PRACTICA3_ESP32_ULTRASONIDO_LCD/blob/main/Captura%205.PNG?raw=true)

 
 
# Créditos

Desarrollado por Dulce M Rodriguez Zarate 

- [GitHub](https://github.com/DulceMRZ)
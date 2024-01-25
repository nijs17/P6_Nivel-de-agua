# P6_Nivel-de-agua
## INTRODUCCION

### DESCRIPCION 

La **Esp32**  es un dispositivo electronico en el cual podemos realizar practicas y simulaciones, en esta practica realizaremos  con ayuda del simulador un programa que nos ayudara a visualizar el nivel de agua de un tinaco, esto con ayuda de un sensor ultrasonico el cual nos dara el dato del nivel y unos LED´s que indicaran el nivel al que se encuentra el fluido ya no nos ayudaran de manera visual. En esta practica utilizaremos los condisionantes, **else** y **if**  Cabe aclarar que para esta practica se usara un simulador llamado **https://wokwi.com/**.

### MATERIAL A OCUPAR

Para realizar esta practica ocuparemos lo siguente:

-WORKI

-Tarjeta ESP 32

-4 LED´s

-Sensor ultrasonico

-4 Resistencias

### Requisitos previos

Para poder realizar esta practica es nesesario contar con conosimientos basicos de programacion y electronica.

## INSTRUCIOES DE ELAVORACION 

1.Abrir la terminal de programación y colocar el siguente codigo:

// defines pins numbers

const int trigPin = 4;

const int echoPin = 15;

const int led1 = 22;

const int led2 = 21;

const int led3 = 19;

const int led4 = 18;

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

if (safetyDistance>=25 && safetyDistance<=125)

{

  digitalWrite(led1, HIGH);
  
  digitalWrite(led2, LOW);
  
  digitalWrite(led3, LOW);
  
  digitalWrite(led4, LOW);

}

else if(safetyDistance>=125 && safetyDistance<=225) 

{

  digitalWrite(led1, HIGH);
  
  digitalWrite(led2, HIGH);
  
  digitalWrite(led3, LOW);
  
  digitalWrite(led4, LOW);
}


else if(safetyDistance>=225 && safetyDistance<=325) 

{

  digitalWrite(led1, HIGH);
  
  digitalWrite(led2, HIGH);
  
  digitalWrite(led3, HIGH);
  
  digitalWrite(led4, LOW);
}

else if(safetyDistance>=325 && safetyDistance<=400) 

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

Serial.print("Litros: ");

Serial.println(distance);

delay (2000);

}

2. Hacer las conexiones de la tarjeta con los demas elementos, anteriormente mensionados, como se muestra en la siguente imagen. 
 ![]()


## INSTRUCCIONES DE OPERACION 


    1. Iniciar simulador.
    
    2. Realizar las conexiones mostradas en la imagen anterior.
    
    3. Mover la sencibilidad del ultrazonico para simular el nivel del agua y asi poder visualizar sus diferentes estados del detector de nivel, como se muestra en la siguiente imagen.
    ![]()
    
## RESUSLTADOS
Al finalizar tendremos uns detector de nivel que nos mostrara el nivel de nuestro tinaco con LEDS que indican de manera visual el porcentaje de agua que tiene nuestro deposito.

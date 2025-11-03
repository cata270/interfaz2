# Interfaz 2 

1.[Hola mundo](https://github.com/cata270/interfaz2?tab=readme-ov-file#ejercicio-n-1-hola-mundo) <br>
2.[Led intermitente](https://github.com/cata270/interfaz2?tab=readme-ov-file#ejercicio-n-2-led-intermitente) <br>
3.[Control por pulsador](https://github.com/cata270/interfaz2/blob/main/README.md#ejercicio-n-3-control-por-pulsador) <br>
4.[Led con potenciómetro](https://github.com/cata270/interfaz2/blob/main/README.md#ejercicio-n-4-led-con-potenci%C3%B3metro) <br>
5.[Semáforo Arduino](https://github.com/cata270/interfaz2/blob/main/README.md#ejercicio-n-5-semaforo-arduino) <br>
6.[Potenciómetro + processing](https://github.com/cata270/interfaz2/blob/main/README.md#ejercicio-n-6-potenci%C3%B3metro--processing) <br>
7.[Arduino + botón + processing](https://github.com/cata270/interfaz2/blob/main/README.md#ejercicio-n-7-arduino--bot%C3%B3n--processing) <br>
8.[Arduino + botón + potenciómetro + processing](https://github.com/cata270/interfaz2/blob/main/README.md#ejercicio-8-arduino-bot%C3%B3n--potenciometro--processing) <br>
9.[Fución if - else](https://github.com/cata270/interfaz2/blob/main/README.md#ejercicio-n-9-funci%C3%B3n-if--else) <br>
10.[Botonera arduino + processing](https://github.com/cata270/interfaz2/blob/main/README.md#ejercicio-n-10-botonera-arduino--processing) <br>
11.[Entrega (potenciometro + processing)](https://github.com/cata270/interfaz2/blob/main/README.md#ejercicio-n-11-entrega-potenciometro--processing-intervenido) <br>
13.[Sensor Sharp](https://github.com/cata270/interfaz2/blob/main/README.md#ejercicio-n-12-cuerpo-video-sensor-sharp) <br>
13.[Sensor humedad](https://github.com/cata270/interfaz2/blob/main/README.md#ejercicio-n-13-promedio-de-imagenes) <br>
14.[Video,cuerpo,sensor](https://github.com/cata270/interfaz2/blob/main/README.md#ejercicio-n-12-cuerpo-video-sensor-sharp) <br>
15.[Promedio imagenes](https://github.com/cata270/interfaz2/blob/main/README.md#ejercicio-n-13-promedio-de-imagenes) <br>

### Ejercicio n 1: "Hola mundo"

```js
void setup() {
  Serial.begin(9600); // Inicia la comunicación serie a 9600 bps
  Serial.println("Hola, Mundo!"); // Envía "Hola, Mundo!" al monitor serie
}

void loop() {
  // No es necesario poner nada en el loop para este ejemplo
}
```
### Ejercicio n 2 :"Led intermitente"
```js
void setup() {  // Configuración inicial (ej: pines como entrada/salida)
  pinMode(13, OUTPUT);  // Pin 13 como salida
}

void loop() {   // Se repite infinitamente
  digitalWrite(13, HIGH);  // Encender LED
  delay(1000);             // Esperar 1 segundo
  digitalWrite(13, LOW);   // Apagar LED
  delay(1000);             // Esperar 1 segundo
}

```
<img src="https://raw.githubusercontent.com/cata270/interfaz2/refs/heads/main/img/ledparpadeante.png" width="1024" height="550" />
<img src="https://raw.githubusercontent.com/cata270/interfaz2/refs/heads/main/img/led%20parpadeante%20real.jpg" width="1024" height="550" />

### Ejercicio n 3: "Control por pulsador"
```js
void setup() {
  pinMode(2, INPUT);  // Botón como entrada
  pinMode(13, OUTPUT);
}
void loop() {
  if (digitalRead(2) == HIGH) {  // Si se presiona el botón
    digitalWrite(13, HIGH);
  } else {
    digitalWrite(13, LOW);
  }
}
```
<img src="https://raw.githubusercontent.com/cata270/interfaz2/refs/heads/main/img/ledpulsador.png" width="1024" height="550" />

### Ejercicio n 4: "Led con potenciómetro"
```js
void setup() {
  pinMode(9, OUTPUT);  // Pin PWM (símbolo ~)
}
void loop() {
  int valor = analogRead(A0);           // Leer potenciómetro (0-1023)
  int brillo = map(valor, 0, 1023, 0, 255);  // Convertir a rango PWM
  analogWrite(9, brillo);               // Ajustar brillo
}
```
<img src="https://raw.githubusercontent.com/cata270/interfaz2/refs/heads/main/img/ledpotenciometro.png" width="1024" height="550" />
<img src="https://raw.githubusercontent.com/cata270/interfaz2/refs/heads/main/img/potenciometro%204.jpg" width="1024" height="550" />

### Ejercicio n 5: "Semaforo Arduino"

```js
int LED_1 = 6;  // Luz roja autos
int LED_2 = 7;  // Luz amarilla autos
int LED_3 = 8;  // Luz verde autos
int LED_4 = 9;  // Luz verde peatones
int LED_5 = 10; // Luz roja peatones

void setup() {
  // Configuramos todos los pines como salida
  pinMode(LED_1, OUTPUT);
  pinMode(LED_2, OUTPUT);
  pinMode(LED_3, OUTPUT);
  pinMode(LED_4, OUTPUT);
  pinMode(LED_5, OUTPUT);
}

void loop() {
  // 🚦 Fase 1: Autos en verde, peatones en rojo
  digitalWrite(LED_1, LOW);   // Rojo autos apagado
  digitalWrite(LED_2, LOW);   // Amarillo autos apagado
  digitalWrite(LED_3, HIGH);  // Verde autos encendido
  digitalWrite(LED_4, LOW);   // Verde peatones apagado
  digitalWrite(LED_5, HIGH);  // Rojo peatones encendido
  delay(5000); // 5 segundos

  // 🚦 Fase 2: Amarillo autos, peatones siguen en rojo
  digitalWrite(LED_3, LOW);   // Verde autos apagado
  digitalWrite(LED_2, HIGH);  // Amarillo autos encendido
  delay(2000); // 2 segundos
  digitalWrite(LED_2, LOW);   // Amarillo autos apagado

  // 🚦 Fase 3: Rojo autos, verde peatones
  digitalWrite(LED_1, HIGH);  // Rojo autos encendido
  digitalWrite(LED_5, LOW);   // Rojo peatones apagado
  digitalWrite(LED_4, HIGH);  // Verde peatones encendido
  delay(1000); // 5 segundos
   digitalWrite(LED_4, LOW);
   delay(1000);
   digitalWrite(LED_4, HIGH);
  delay(1000);
     digitalWrite(LED_4, LOW);
   delay(1000);
   digitalWrite(LED_4, HIGH);
  delay(1000);
   delay(5000);

  // 🚦 Fase 4: Rojo autos, rojo peatones (tiempo intermedio)
  digitalWrite(LED_4, LOW);   // Verde peatones apagado
  digitalWrite(LED_5, HIGH); 
  digitalWrite(LED_1, LOW);
  digitalWrite(LED_5, HIGH);
   digitalWrite(LED_3, HIGH);
    digitalWrite(LED_5, HIGH); // Rojo peatones encendido
  delay(2000); // 2 segundos
}
// C++ code - Semáforo Autos y Peatones
```
<img src="https://raw.githubusercontent.com/cata270/interfaz2/refs/heads/main/img/semaforo.png" width="1024" height="550" />
<img src="https://raw.githubusercontent.com/cata270/interfaz2/refs/heads/main/img/semaforo%20foto.jpg" width="1024" height="620" />

### Ejercicio n 6: "Potenciómetro + Processing"
```js

ARDUINO: unsigned int ADCValue;
void setup(){
    Serial.begin(9600);
}

void loop(){

 int val = analogRead(0);
   val = map(val, 0, 300, 0, 255);
    Serial.println(val);
delay(50);
}


PROCESSING:import processing.serial.*;

Serial myPort;  // Crear objeto de la clase Serial
static String val;    // Datos recibidos desde el puerto serial
int sensorVal = 0;

void setup()
{
  background(1); 
  //fullScreen(P3D);
   size(1080, 720);
   noStroke();
  noFill();
  String portName = "COM3";// Cambia el número (en este caso) para que coincida con el puerto correspondiente conectado a tu Arduino. 

  //myPort = new Serial(this, "/dev/cu.usbmodem1101", 9600);
  myPort = new Serial(this, Serial.list()[0], 9600);

}

void draw()
{
  
  if ( myPort.available() > 0) {  // Si hay datos disponibles,
  val = myPort.readStringUntil('\n'); 
  try {
   sensorVal = Integer.valueOf(val.trim());
  }
  catch(Exception e) {
  ;
  }
  println(sensorVal); // léelos y guárdalos en vals!
  }  
 //background(0);
  // Escala el valor de mouseX de 0 a 640 a un rango entre 0 y 175
  float c = map(sensorVal, 0, width, 0, 400);
  // Escala el valor de mouseX de 0 a 640 a un rango entre 40 y 300
  float d = map(sensorVal, 0, width, 40,500);
  fill(255, c, 0);
  ellipse(width/2, height/2, d, d);   
  ellipse(width/1, height/1, d, d);  
   ellipse(width/4, height/1, d, d);
   
}
```
<img src="https://raw.githubusercontent.com/cata270/interfaz2/refs/heads/main/img/arduino%20processing.png" width="1024" height="550" />


### Ejercicio n 7 "Arduino + botón + processing"

```js

ARDUINO: int buttonPin = 2;  // Pin del botón
int buttonState = 0;

void setup() {
  pinMode(buttonPin, INPUT_PULLUP); // Botón con resistencia interna
  Serial.begin(9600);
}

void loop() {
  buttonState = digitalRead(buttonPin);

  if (buttonState == HIGH) {   // Botón presionado
    Serial.println(1);        // Enviar un "1" a Processing
    delay(200);               // Evitar rebotes
  }
}

PROCESSING:import processing.serial.*;

Serial myPort;
ArrayList<PVector> circles; 

void setup() {
  size(1920, 1080);
  background(0);
  
  // Ajusta el nombre del puerto según tu Arduino
  println(Serial.list());
  myPort = new Serial(this, "COM3", 9600);
  //myPort = new Serial(this, Serial.list()[0], 9600);
  
  circles = new ArrayList<PVector>();
}

void draw() {
  //background(0);
  
  // Dibujar círculos almacenados
  fill(random (0), random (234), random (56));
  //noStroke();
  stroke(255, 0, 0);
  for (PVector c : circles) {
    ellipse(c.x, c.y, 70, 70);
  }
  
  // Revisar si llega algo de Arduino
  if (myPort.available() > 0) {
    String val = myPort.readStringUntil('\n');
    if (val != null) {
      val = trim(val);
      if (val.equals("1")) {
        // Cada vez que se aprieta el botón, agregar un círculo en posición aleatoria
        circles.add(new PVector(random(width), random(height)));
      }
    }
  }
}
```
<img src="https://raw.githubusercontent.com/cata270/interfaz2/refs/heads/main/img/Captura%20de%20pantalla%202025-09-02%20121901.png" width="1024" height="550" />
<img src="https://raw.githubusercontent.com/cata270/interfaz2/refs/heads/main/img/pulsador%20foto.jpg" width="1024" height="550" />

### Ejercicio 8 "Arduino +botón + potenciometro + processing"
``` js
Arduino:int buttonPin = 2;       // Pin del botón
int potPin = A0;         // Pin del potenciómetro
int buttonState = 0;

void setup() {
  pinMode(buttonPin, INPUT_PULLUP); // Botón con resistencia interna
  Serial.begin(9600);
}

void loop() {
  buttonState = digitalRead(buttonPin);

  if (buttonState == HIGH) {   // Botón presionado
    int potValue = analogRead(potPin);   // 0 - 1023
    Serial.print("BTN,");     // etiqueta para Processing
    Serial.println(potValue); // mando el valor junto con el evento
    delay(200);               // debounce simple
  }
}

Processing: import processing.serial.*;

Serial myPort;
ArrayList<CircleData> circles; 

void setup() {
  size(1200, 720);
  background(0);
  
  // Ajusta el puerto según tu Arduino
  println(Serial.list());
  myPort = new Serial(this, "COM3", 9600);
  //myPort = new Serial(this, Serial.list()[0], 9600);
  
  circles = new ArrayList<CircleData>();
}

void draw() {
  //background(0);
  
  // Dibujar todos los círculos guardados
  //fill(0, 150, 255);
  //noStroke();
  fill(65, 240, 213);
  stroke(0, 0, 0);
  for (CircleData c : circles) {
    ellipse(c.x, c.y, random(c.size), random(c.size));
  }
  
  // Leer datos de Arduino
  if (myPort.available() > 0) {
    String val = myPort.readStringUntil('\n');
    if (val != null) {
      val = trim(val);
      if (val.startsWith("BTN")) {
        // Extraer el valor del potenciómetro
        String[] parts = split(val, ',');
        if (parts.length == 2) {
          float potVal = float(parts[1]);
          float circleSize = map(potVal, 0, 1023, 5, 200); // tamaño 10-100 px
          circles.add(new CircleData(random(width), random(height), circleSize));
        }
      }
    }
  }
}

// Clase para guardar datos de cada círculo
class CircleData {
  float x, y, size;
  CircleData(float x, float y, float size) {
    this.x = x;
    this.y = y;
    this.size = size;
  }
}

```

<img src="https://raw.githubusercontent.com/cata270/interfaz2/refs/heads/main/img/Bot%C3%B3n%20%2B%20potenciometro.png" width="1024" height="550" /> 

### Ejercicio n 9: "Función If + else"

```js

int leds[] = {2, 3, 4, 5}; // Creamos un arreglo con los pines donde van conectados los LEDs

void setup() {
  // Esta función corre solo una vez al iniciar Arduino
  for (int i = 0; i < 4; i++) {         // Recorre el arreglo desde i = 0 hasta i = 3
    pinMode(leds[i], OUTPUT);           // Configura cada pin del arreglo como salida (para controlar LEDs)
  }
}

void loop() {
  // Esta función corre en bucle infinito
  for (int i = 0; i < 4; i++) {         // Recorre los 4 LEDs, uno por uno
    if (i % 1 == 0) {                   // Si el índice es par (0, 2)...
      digitalWrite(leds[i], HIGH);      // Enciende el LED correspondiente
    } else {                            // Si el índice es impar (1, 3)...
      digitalWrite(leds[i], LOW);       // Apaga el LED correspondiente
    }
    delay(500);                         // Espera 0,5 segundos antes de pasar al siguiente
  }
}

```
<img src="https://raw.githubusercontent.com/cata270/interfaz2/refs/heads/main/img/if%20else.png" width="1024" height="550" /> 

### Ejercicio n 10: "Botonera arduino + processing"

En este cógido lo que ocurre es la interacción del potenciometro a través de Arduino + Procesing, generando así una imagen interactiva, mi intervención aparece en el código de processing, donde modifiqué el color del fondo

```js
A
CODIGO ARDUINO:
// --- Configuración de botones ---
const int numButtons = 3;
const int buttonPins[numButtons] = {2, 4, 7};
const int ledButtonPins[numButtons] = {9, 10, 11}; // LEDs botones

// --- Configuración de potenciómetros ---
const int numPots = 2;
const int potPins[numPots] = {A0, A1};
const int ledPotPins[numPots] = {3, 5}; // LEDs PWM

// Variables de estados previos
int lastButtonState[numButtons];
int lastPotValue[numPots];

void setup() {
  Serial.begin(9600);

  // Configurar botones y LEDs
  for (int i = 0; i < numButtons; i++) {
    pinMode(buttonPins[i], INPUT_PULLUP);
    pinMode(ledButtonPins[i], OUTPUT);
    lastButtonState[i] = digitalRead(buttonPins[i]);
  }

  // Configurar LEDs de potenciómetros
  for (int i = 0; i < numPots; i++) {
    pinMode(ledPotPins[i], OUTPUT);
    lastPotValue[i] = analogRead(potPins[i]);
  }
}

void loop() {
  // Leer y enviar botones
  for (int i = 0; i < numButtons; i++) {
    int buttonState = digitalRead(buttonPins[i]);

    // LED se enciende cuando botón está presionado
    digitalWrite(ledButtonPins[i], buttonState == LOW ? HIGH : LOW);

    if (buttonState != lastButtonState[i]) {  // enviar cambios
      Serial.print("B");
      Serial.print(i); 
      Serial.print(":");
      Serial.println(buttonState);
      lastButtonState[i] = buttonState;
    }
  }

  // Leer y enviar potenciómetros
  for (int i = 0; i < numPots; i++) {
    int potValue = analogRead(potPins[i]); // 0–1023
    int pwmValue = potValue / 4;           // 0–255

    // Ajustar LED según valor
    analogWrite(ledPotPins[i], pwmValue);

    if (abs(pwmValue - lastPotValue[i]) > 2) { // evitar ruido
      Serial.print("P");
      Serial.print(i);
      Serial.print(":");
      Serial.println(pwmValue);
      lastPotValue[i] = pwmValue;
    }
  }

  delay(10);
}
CODIGO PROCESSING:
// Importamos librería para comunicación serial
import processing.serial.*;
// Importamos librería Minim para manejar audio
import ddf.minim.*;

// Declaramos el objeto serial para comunicarnos con Arduino
Serial myPort;
// Objeto principal de Minim
Minim minim;
// Array de reproductores de audio (3 pistas)
AudioPlayer[] players;
// Variable para guardar el índice de la pista que está sonando
int currentTrack = -1;  // -1 significa que no hay pista activa al inicio

void setup() {
  size(400, 200); // Ventana de 400x200 píxeles
  
  // --- Configuración del puerto serial ---
  printArray(Serial.list()); // Muestra en consola la lista de puertos disponibles
  myPort = new Serial(this, Serial.list()[0], 9600); // Abrimos el primer puerto de la lista a 9600 baudios
  
  // --- Configuración de audio ---
  minim = new Minim(this); // Inicializamos Minim
  players = new AudioPlayer[3]; // Creamos un array de 3 reproductores
  
  // Cargamos los 3 archivos de audio desde la carpeta "data"
  players[0] = minim.loadFile("audio1.mp3", 2048); 
  players[1] = minim.loadFile("audio2.mp3", 2048); 
  players[2] = minim.loadFile("audio3.mp3", 2048); 
}

void draw() {
  background(0); // Fondo negro
  fill(255);     // Color blanco para el texto
  textSize(16);  // Tamaño del texto
  
  // Mostramos en pantalla qué botón está activo
  text("Botón actual: " + (currentTrack == -1 ? "ninguno" : currentTrack), 20, 40);
}

void serialEvent(Serial myPort) {
  // Leemos la cadena que llega desde Arduino hasta el salto de línea
  String inString = trim(myPort.readStringUntil('\n'));
  
  // Si no llega nada, salimos
  if (inString == null) return;

  // --- Si el mensaje recibido empieza con "B" significa que es un botón ---
  if (inString.startsWith("B")) {
    // Quitamos la letra "B" y separamos el mensaje en partes (ejemplo "0:0")
    String[] parts = split(inString.substring(1), ':');
    
    // Si realmente recibimos dos partes (índice y estado)
    if (parts.length == 2) {
      int buttonIndex = int(parts[0]); // Número del botón (0,1,2)
      int state = int(parts[1]);       // Estado del botón (0 = presionado, 1 = suelto)
      
      // Si el botón fue presionado (LOW = 0 en Arduino)
      if (state == 0) { 
        playTrack(buttonIndex); // Llamamos a la función para reproducir la pista correspondiente
      }
    }
  }
}

// --- Función que reproduce una pista según el botón ---
void playTrack(int index) {
  // Si ya había una pista sonando, la pausamos y la rebobinamos al inicio
  if (currentTrack != -1 && players[currentTrack].isPlaying()) {
    players[currentTrack].pause();
    players[currentTrack].rewind();
  }
  
  // Reproducimos en bucle la pista seleccionada
  players[index].loop();
  
  // Actualizamos la variable para saber cuál es la pista activa
  currentTrack = index;
}

```

<img src="https://raw.githubusercontent.com/cata270/interfaz2/refs/heads/main/img/botonera%20arduino.png" width="1024" height="550" />
<img src="https://raw.githubusercontent.com/cata270/interfaz2/refs/heads/main/img/ej%2010.jpg" width="1024" height="550" />

### Ejercicio n 11 (entrega) "Potenciometro + processing intervenido"

``` js
En este códido lo que ocurre es la interacción del potenciometro a través de Arduino + Procesing generando
así una imagen interactiva, primero explicaré lo que ocurre en el circuito físico, el potenciómetro que
utilicé podía ser conectado directamente al arduino,por lo que debí el cable negro va a tierra, el rojo
 (señal de entrada) a 5v y el azul (señal de salida) A0.
 Mi intervención apareceen el código de processing, donde modifiqué el color del fondo (background) ,añadí
 otra forma geométrica(un óvalo), agregué círculos interactivos: Variando en tamaños (width, height),
 colores (fill) y lugares, también probé superponiendolos para generar un efecto en los colores. En
este sector "float c = map(sensorVal, 0, width, 0, 420);" fui probando cambiando valores,lo que afectaba
 en el ancho de la separación de los diámetros en la interacción.




ARDUINO: unsigned int ADCValue;
void setup() {
  Serial.begin(9600);
  pinMode(9, OUTPUT);  // Pin PWM (símbolo ~)
}
void loop() {
  int val = analogRead(A0);           // Leer potenciómetro (0-1023)
  int brillo = map(val, 0, 1023, 0, 255);  // Convertir a rango PWM
  analogWrite(9, brillo);               // Ajustar brillo
      Serial.println(val);
delay(50);
}

PROCESSING: import processing.serial.*;

Serial myPort;  // Crear objeto de la clase Serial
static String val;    // Datos recibidos desde el puerto serial
int sensorVal = 0;

void setup()
{
  background(103,20,23);
  //fullScreen(P3D);
   size(1080, 720);
   noStroke();
  noFill();
  String portName = "COM3";// Cambia el número (en este caso) para que coincida con el puerto correspondiente conectado a tu Arduino.

  //myPort = new Serial(this, "/dev/cu.usbmodem1101", 9600);
  myPort = new Serial(this, Serial.list()[0], 9600);

}

void draw()
{
  if ( myPort.available() > 0) {  // Si hay datos disponibles,
  val = myPort.readStringUntil('\n');
  try {
   sensorVal = Integer.valueOf(val.trim());
  }
  catch(Exception e) {
  ;
  }
  println(sensorVal); // léelos y guárdalos en vals!
  }  
 //background(255,165,165);
  // Escala el valor de mouseX de 0 a 640 a un rango entre 0 y 175
  float c = map(sensorVal, 0, width, 0, 420);
  // Escala el valor de mouseX de 0 a 640 a un rango entre 40 y 300
  float d = map(sensorVal, 0, width, 60,500);
 
  fill(255, c, 0);
  ellipse(width/2, height/1, d, d);  
 
   fill(464,c,78);
  ellipse(width/4, height/2, 34, 16);
  fill(244,c,645);
  ellipse(width/4, height/2, d, d);
  fill(235,c,568);
  ellipse(width/4, height/2, d, d);
 
   fill(389,c,389);
  ellipse(width/1, height/3, d, d);
 
   fill(134,c,0);
  ellipse(width/2, height/3, 234, 346);
 
  fill(346,c,132);
  ellipse(width/10, height/12, d, d);
 
  fill(134,c,657);
  ellipse(width/10, height/12, d, d);
 
    fill(346,c,132);
  ellipse(width/67, height/34, d, d);
 
  fill(134,c,657);
  ellipse(width/2, height/12, d, d);
 
  fill(346,c,453);
  ellipse(width/2, height/2, d, d);
 
  fill(134,c,657);
  ellipse(width/4, height/1, d, d);
 
   fill(346,c,132);
  ellipse(width/3, height/3, d, d);
 
  fill(134,c,657);
  ellipse(width/6, height/6, d, d);
 
   fill(134,c,657);
  ellipse(width/4, height/1, d, d);
 
   fill(346,c,132);
  ellipse(width/3, height/15, d, d);
 
  fill(134,c,657);
  ellipse(width/1060, height/500, d, d);

}

¿Cómo funciona?
analogRead(A0): Lee el valor de un potenciómetro o sensor analógico, el resultado es un entero entre 0 y 1023.
gWrite(9, brillo): Modula la salida PWM del pin 9 para cambiar el brillo de un LED.


Serial.println(val): Envía el valor leído a través del puerto serial para que el ordenador lo reciba.


delay(50): Espera 50 milisegundos para evitar enviar demasiados datos muy rápido.




  map: toma el valor sensorVal que está en el rango [0, width] y lo                   transforma al rango [0, 420].


   float c: almacena ese resultado como un número decimal.
 
El valor que envía el Arduino (que depende de cuánto gira el potenciómetro) se guarda en sensorVal.








```

<img src="https://raw.githubusercontent.com/cata270/interfaz2/refs/heads/main/img/entrega.png" width="1024" height="550" />

<img src="https://raw.githubusercontent.com/cata270/interfaz2/refs/heads/main/img/entrega%20foto.jpg" width="1024" height="650" />


### Ejercicio n 12: "Sensor sharp"

```js

CODIGO ARDUINO
// Definir el pin del sensor Sharp
int sharpPin = A0;

void setup() {
  Serial.begin(9600); // Iniciar comunicación serial
}

void loop() {
  int sensorValue = analogRead(sharpPin); // Leer valor del sensor
  Serial.println(sensorValue); // Enviar valor a Processing
  delay(100); // Esperar un momento
}

CODIGO PROCESSING
import processing.serial.*;

Serial myPort;  // Create object from Serial class
static String val;    // Data received from the serial port
int sensorVal = 0;

void setup()
{
  background(0); 
  //fullScreen(P3D);
   size(1080, 720);
   noStroke();
  noFill();
  String portName = "COM5";// Change the number (in this case ) to match the corresponding port number connected to your Arduino. 

  myPort = new Serial(this, "/dev/cu.usbmodem1101", 9600);
}

void draw()
{
  if ( myPort.available() > 0) {  // If data is available,
  val = myPort.readStringUntil('\n'); 
  try {
   sensorVal = Integer.valueOf(val.trim());
  }
  catch(Exception e) {
  ;
  }
  println(sensorVal); // read it and store it in vals!
  }  
 //background(0);
  // Scale the mouseX value from 0 to 640 to a range between 0 and 175
  float c = map(sensorVal, 0, width, 0, 400);
  // Scale the mouseX value from 0 to 640 to a range between 40 and 300
  float d = map(sensorVal, 0, width, 40,500);
  fill(255, c, 0);
  ellipse(width/2, height/2, d, d);   

}

```
<img src="https://raw.githubusercontent.com/cata270/interfaz2/refs/heads/main/img/SENSOR%20SHARP.jpeg" width="1024" height="550" />

## Ejercicio 13 : "Sensor humedad"

```js

CODIGO ARDUINO
void setup()
{
  Serial.begin(9600);// abre el puerto serial y Establece la velocidad en baudios a 9600 bps
}
void loop()
{
  int sensorValue;
  sensorValue = analogRead(0);   //conectar el sensor de humedad al pin analogo 0
  Serial.println(sensorValue); //imprime el valor a serial.
  delay(200);
}

```

<img src="https://raw.githubusercontent.com/cata270/interfaz2/refs/heads/main/img/SENSOR%20HUMEDAD.jpeg" width="1024" height="550" />



### Ejercicio n 14: "Cuerpo, video, sensor sharp"
```js
CODIGO ARDUINO:
// --- Sensor Sharp conectado al pin A0 ---
int sensorPin = A0;
int valor;

void setup() {
  Serial.begin(9600);
}

void loop() {
  valor = analogRead(sensorPin);
  Serial.println(valor);
  delay(50); // envío cada 50 ms
}


CODIGO PROCESSING:
// --- Librerías necesarias ---
import processing.serial.*;
import processing.video.*;

// --- Variables de cámara y serial ---
Capture cam;
Serial myPort;

// --- Variables del sensor ---
float sensorValue = 0;
float suavizado = 0;

// --- Parámetros para detección de silueta ---
float umbral = 100; // controla el contraste para definir la silueta

void setup() {
  size(1280, 720);
  background(0);
  
  // --- Inicializar cámara ---
  String[] cameras = Capture.list();
  if (cameras.length == 0) {
    println("No se encontró cámara.");
    exit();
  } else {
    println("Cámara encontrada: " + cameras[0]);
    cam = new Capture(this, cameras[0]);
    cam.start();
  }
  
  // --- Inicializar puerto serie (Arduino) ---
  // Puedes ver la lista de puertos con println(Serial.list());
  String portName = Serial.list()[0]; 
  myPort = new Serial(this, "/dev/cu.usbmodem1101", 9600);
  //myPort = new Serial(this, portName, 9600);
}

void draw() {
  background(0);
  
  // --- Leer datos del sensor ---
  while (myPort.available() > 0) {
    String inString = trim(myPort.readStringUntil('\n'));
    if (inString != null) {
      sensorValue = float(inString);
      suavizado = lerp(suavizado, sensorValue, 0.1);
    }
  }
  
  // --- Mapear los valores del sensor ---
  float escala = map(suavizado, 0, 1023, 1.5, 0.5); // tamaño de la silueta
  float alpha = map(suavizado, 0, 1023, 255, 80);   // opacidad según distancia
  
  // --- Captura de video ---
  if (cam.available()) {
    cam.read();
  }

  // --- Dibujar silueta desde la cámara ---
  cam.loadPixels();
  loadPixels();
  
  for (int y = 0; y < cam.height; y++) {
    for (int x = 0; x < cam.width; x++) {
      int loc = x + y * cam.width;
      color c = cam.pixels[loc];
      float brillo = brightness(c);
      
      // Si el brillo es menor que el umbral, dibujamos píxel blanco (silueta)
      if (brillo < umbral) {
        int px = int(x * escala);
        int py = int(y * escala);
        if (px < width && py < height) {
          stroke(255, alpha);
          point(px, py);
        }
      }
    }
  }
}

```


<img src="https://raw.githubusercontent.com/cata270/interfaz2/refs/heads/main/img/cuerpo%20video%20sensor%20fisico.jpeg" width="1024" height="550" />
<img src="https://raw.githubusercontent.com/cata270/interfaz2/refs/heads/main/img/cuerpo%20video%20sentor%20ss.png" width="1024" height="550" />


### Ejercicio n 15: "Promedio de imagenes"
```js
CODIGO ARDUINO:
void setup() {
  Serial.begin(9600);
}

void loop() {
  int potValue = analogRead(A0);
  Serial.println(potValue);
  delay(20);
}
CODIGO PROCESSING:
import processing.serial.*;

Serial myPort;
PImage[] imgs;
int numImages = 3;
PImage avgImg;
float mixAmount = 0;

void setup() {
  size(800, 600);
  println(Serial.list());
  
  //Cambia el índice según tu puerto (0, 1, 2, etc.)
  myPort = new Serial(this, Serial.list()[0], 9600);
  //myPort = new Serial(this, "/dev/cu.usbmodem1101", 9600);
  myPort.bufferUntil('\n');

  // Cargar imágenes
  imgs = new PImage[numImages];
  imgs[0] = loadImage("img1.jpg");
  imgs[1] = loadImage("img2.jpg");
  imgs[2] = loadImage("img3.jpg");

  avgImg = createImage(imgs[0].width, imgs[0].height, RGB);
}

void draw() {
  // Dibujar la imagen promedio según el valor del potenciómetro
  background(0);
  calcAverage(mixAmount);
  image(avgImg, 0, 0, width, height);
  
  fill(255);
  textSize(20);
  text("Mezcla: " + nf(mixAmount, 1, 2), 20, height - 20);
}

void serialEvent(Serial p) {
  String val = p.readStringUntil('\n');
  if (val != null) {
    val = trim(val);
    float sensor = float(val);
    mixAmount = map(sensor, 0, 1023, 0, 1); // 0 a 1
  }
}

void calcAverage(float t) {
  avgImg.loadPixels();

  for (int i = 0; i < avgImg.pixels.length; i++) {
    color c1 = imgs[0].pixels[i];
    color c2 = imgs[1].pixels[i];
    color c3 = imgs[2].pixels[i];

    // Promedio ponderado según el potenciómetro
    float r = red(c1)*(1-t) + red(c2)*t*0.5 + red(c3)*t*0.5;
    float g = green(c1)*(1-t) + green(c2)*t*0.5 + green(c3)*t*0.5;
    float b = blue(c1)*(1-t) + blue(c2)*t*0.5 + blue(c3)*t*0.5;

    avgImg.pixels[i] = color(r, g, b);
  }
  avgImg.updatePixels();
}

```
<img src="https://raw.githubusercontent.com/cata270/interfaz2/refs/heads/main/img/promedio%20imagenes%20real.jpg" width="1024" height="550" />
<img src="https://raw.githubusercontent.com/cata270/interfaz2/refs/heads/main/img/promedio%20imagenes%20ss.png" width="1024" height="550" />

### Segunda entrega, cuerpo, video, sensor sharp modificado

```js

CODIGO ARDUINO
// --- Sensor Sharp conectado al pin A0 ---
int sensorPin = A0;
int valor;

void setup() {
  Serial.begin(9600);
}

void loop() {
  valor = analogRead(sensorPin);
  Serial.println(valor);
  delay(50); // envío cada 50 ms
}



CODIGO PROCESSING
// --- Librerías necesarias ---
import processing.serial.*;
import processing.video.*;

// --- Variables de cámara y serial ---
Capture cam;
Serial myPort;

// --- Variables del sensor ---
float sensorValue = 0;
float suavizado = 0;

// --- Parámetros para detección de silueta ---
float umbral = 100;
String simbolos = "@#%*+=-:. ";

PGraphics buffer; // para dibujar la cámara una vez

void setup() {
  size(1280, 720);
  background(0);
  textAlign(CENTER, CENTER);
  textSize(8);
  colorMode(HSB, 255);
  
  // --- Inicializar cámara ---

```
<img src="https://raw.githubusercontent.com/cata270/interfaz2/refs/heads/main/img/camaragrupo.png" width="1024" height="550" />
<img src="https://raw.githubusercontent.com/cata270/interfaz2/refs/heads/main/img/camaragrupo3.png" width="1024" height="550" />
<img src="https://raw.githubusercontent.com/cata270/interfaz2/refs/heads/main/img/camaragrupo2.png" width="1024" height="550" />





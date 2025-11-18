# interfaz-II

1. [Hola Mundo](#ejercicio-numero-1-arduino--hola-mundo) <br>
2. [Led Intermitente](#ejercicio-2-arduino-led-intermietente) <br> 
3. [Control con Pulsador](#ejercicio-3-arduino-control-por-pulsador) <br>
4. [Potenciometro](#ejercicio-4-arduino-potenciometro) <br>
5. [Semaforo](#ejercicio-5-arduino-semaforo) <br>
6. [Processing](#ejercicio-6-arduino-processing) <br>
7. [Processing+Boton](#ejercicio-7-arduino-processingboton) <br>
8. [Arduino+Boton+Processing](#ejercicio-8-arduino-processingbotonpotenciometro) <br>
9. [Processing+Potenciometro intervenido](#ejercicio-9-arduino-processingpotenciometro-intervenido) <br>
10. [Processing+Potenciometro+Sensor](#ejercicio-10-arduino-processingpotenciometrosensor) <br>
11. [Botonera](#ejercicio-n-10-botonera) <br>
12. [Sensor Sharp](#ejercicio-n-11-sensor-shar) <br>
13. [Sensor de Humedad](#ejercicio-n-12-sensor-de-humedad) <br>
14. [Cuerpo, Video, Sensor Sharp](#ejercicio-n-13-cuerpo-video-sensor-sharp)
15. [Promedio de Imágenes](#ejercicio-n-14-promedio-de-imagenes)
16. [Promedio de Imagenes, Carpeta, Potenciometro](#ejercicio-n-15-promedio-de-imagenes-llamado-una-carpeta--potenciometro)
17. [Idea Grupal](#idea-grupal) <br>
18.  [Idea Grupal, Entrega Final](#idea-grupal-entrega-final) <br>
### Ejercicio numero 1 Arduino:  "Hola Mundo" 

```js
void setup() {
  Serial.begin(9600); // Inicia la comunicación serie a 9600 bps
  Serial.println("slayyyyy"); // Envía "Hola, Mundo!" al monitor serie
 Serial.println("queeeeeen"); // Envía "Hola, Mundo!" al monitor serie
}

void loop() {
  // No es necesario poner nada en el loop para este ejemplo
}
```
### Ejercicio 2 Arduino: Led intermietente
```js
void setup() {  // Configuración inicial (ej: pines como entrada/salida)
  pinMode(13, OUTPUT);  // Pin 13 como salida
  pinMode(8, OUTPUT); // PIN 8 COMO SALIDA
}

void loop() {   // Se repite infinitamente
  digitalWrite(13, HIGH);  // Encender LED
  delay(1000);             // Esperar 1 segundo
  digitalWrite(13, LOW);   // Apagar LED
 // delay(1);             // Esperar 1 segundo
  digitalWrite(8, HIGH);  // Encender LED
  delay(1000);             // Esperar 1 segundo
  digitalWrite(8, LOW);   // Apagar LED
  //delay(1);  
}
```
<img src="https://github.com/Amandarinaa/interfaz-II/blob/main/img/parpadeante.png" with="1024" height="550" />

### Ejercicio 3 Arduino: Control por Pulsador
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
<img src="https://github.com/Amandarinaa/interfaz-II/blob/main/img/pulsador.png" with="1024" height="550" />

### Ejercicio 4 Arduino: Potenciometro 
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
<img src="https://github.com/Amandarinaa/interfaz-II/blob/main/img/potenciometro.png" width="1024"  height="550" />

### Ejercicio 5 Arduino: "Semaforo"

```js
// C++ code - Semáforo Autos y Peatones

// Definición de pines
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
  delay(5000); // 2 segundos
  digitalWrite(LED_2, LOW);   // Amarillo autos apagado

  // 🚦 Fase 3: Rojo autos, verde peatones
  digitalWrite(LED_4, HIGH);  // Verde peatones encendido
   digitalWrite(LED_1, HIGH);  // Rojo autos encendido
  digitalWrite(LED_5, LOW);   // Rojo peatones apagado
delay(2000);
  digitalWrite(LED_4, LOW); 
  delay(700);
   digitalWrite(LED_4, HIGH); 
  delay(600);
  digitalWrite(LED_4, LOW); 
  delay(500);
  digitalWrite(LED_4, HIGH); 
  delay(400);
  digitalWrite(LED_4, LOW); 
  delay(300);
   digitalWrite(LED_4, HIGH); 
  delay(200);
  digitalWrite(LED_4, LOW); 
  delay(200);
  digitalWrite(LED_4, HIGH); 
  delay(200);
  digitalWrite(LED_4, LOW); 
  delay(200);
  digitalWrite(LED_4, HIGH); 
  delay(200);
  digitalWrite(LED_4, LOW); 
  delay(200);
  digitalWrite(LED_4, HIGH); 
  delay(200);
  digitalWrite(LED_4, LOW); 
  delay(200);




  // 🚦 Fase 4: Rojo autos, rojo peatones (tiempo intermedio)
  digitalWrite(LED_4, LOW);   // Verde peatones apagado
  digitalWrite(LED_1, HIGH);   // rojo autos apagado
  digitalWrite(LED_1, LOW);   // rojo autos apagado
  digitalWrite(LED_5, HIGH);  // Rojo peatones encendido
  digitalWrite(LED_5, HIGH);   // Rojo peatones encendido
  digitalWrite(LED_3, HIGH);   // Verde peatones encendido
  delay(1000); // 5 segundos
}
```
<img src="https://github.com/Amandarinaa/interfaz-II/blob/main/img/semaforo.png" with="1024" height="550" />

### Ejercicio 6 Arduino: Processing

```js

import processing.serial.*;

Serial myPort;  // Crear objeto de la clase Serial
static String val;    // Datos recibidos desde el puerto serial
int sensorVal = 0;

void setup()
{
  background(255); 
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
   //background(255); 
  //fullScreen(P3D);
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
  float c = map(sensorVal, 0, width, 0, 300);
  // Escala el valor de mouseX de 0 a 640 a un rango entre 40 y 300
  float d = map(sensorVal, 0, width, 40,500);
  fill(137, c, 255);
  ellipse(width/2, height/2, d, d);   
 
  fill(197, c, 255);
  ellipse(width/4.5, height/4.5, d, d);   
  
  fill(50, c, 255);
  ellipse(width/1.3, height/1.3 , d, d);   
}
```
<img src="https://raw.githubusercontent.com/Amandarinaa/interfaz-II/refs/heads/main/img/Captura%20de%20pantalla%202025-08-26%20134633.png" with="1024" height="550" />

### Ejercicio 7 Arduino: Processing+Boton
codigo processing
```js
import processing.serial.*;

Serial myPort;
ArrayList<PVector> circles; 

void setup() {
  size(900, 500);
  background(119);
  
  // Ajusta el nombre del puerto según tu Arduino
  println(Serial.list());
  myPort = new Serial(this, "COM3", 9600);
  //myPort = new Serial(this, Serial.list()[0], 9600);
  
  circles = new ArrayList<PVector>();
}

void draw() {
  background(255);
  

  // Dibujar círculos almacenados
  fill(random(194), (120), (569), 0);
  //noStroke();
  stroke(random(194), 0, 247);
  for (PVector c : circles) {
    ellipse(c.x, c.y, random(300), random(300));
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
codigo arduino
```js
int buttonPin = 2;  // Pin del botón
int buttonState = 0;

void setup() {
  pinMode(buttonPin, INPUT_PULLUP); // Botón con resistencia interna
  Serial.begin(9600);
}

void loop() {
  buttonState = digitalRead(buttonPin);

  if (buttonState == HIGH) {   // Botón presionado
    Serial.println(1);        // Enviar un "1" a Processing
    delay(50);               // Evitar rebotes
  }
}
```
<img src="https://github.com/Amandarinaa/interfaz-II/blob/main/img/Captura%20de%20pantalla%202025-09-02%20124500.png" with="1024" height="550" />

### Ejercicio 8 Arduino: Processing+Boton+Potenciometro
Codigo processing
```js
import processing.serial.*;

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
  fill(random(10), random(220), 340, 68);
  stroke(255, 255, 255);
  for (CircleData c : circles) {
    ellipse(c.x, c.y,  random(c.size), random(c.size));
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
          float circleSize = map(potVal, 0, 1023, 10, 100); // tamaño 10-100 px
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
Codigo arduino
```js
int buttonPin = 2;       // Pin del botón
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
```
<img src="https://github.com/Amandarinaa/interfaz-II/blob/main/img/Captura%20de%20pantalla%202025-09-02%20132549.png"  with="1024" height="550" />

### Ejercicio 9 Arduino: Processing+Potenciometro intervenido 
Para este ejercicio utilice el circuito de arduino+led+potenciometro, luego descargue el codigo de arduino y cerré el programa de este. Y al final abri processing y abrí el codigo corespondiente al programa. 
El código de processing viene pre escrito con una sola elipse que cambia de color y tamaño al responder al potenciometro, pero yo le agreugue más elipses, les cambie el tamaño máximo (con ayuda de ia, prompt: en que parte de este codigo modifico el tamaño de las elipses?) para que fueran más grandes y cambie los colores y ubicacones de cada una de ellas.

Código Arduino: 

```js
unsigned int ADCValue;
void setup(){
    Serial.begin(9600);
}

void loop(){

 int val = analogRead(0);
   val = map(val, 0, 300, 0, 255);
    Serial.println(val);
delay(50);
}
```

Codigo processing: 
```js
import processing.serial.*;

Serial myPort;  // Crear objeto de la clase Serial
static String val;    // Datos recibidos desde el puerto serial
int sensorVal = 0;

void setup()
{
  background(0); 
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
}
```
Codigo Processing intervenido: 
```js
import processing.serial.*;

Serial myPort;  // Crear objeto de la clase Serial
static String val;    // Datos recibidos desde el puerto serial
int sensorVal = 0;

void setup()
{
  background(255); 
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
  float d = map(sensorVal, 0, width, 40, 800)
  fill(185, c, 0);
 ellipse(width/3, height/11, d, d);   
  
   fill(5, c, 0);
  //ellipse(width/15, height/5, d, d);  
  
   fill(735, c, 0);
  ellipse(width/1, height/9, d, d);
 
   fill(255, c, 255);
  ellipse(width/6, height/1, d, d); 
  
   fill(255, c, 139);
  ellipse(width/1, height/7, d, d);   
  
  
   fill(75, c, 109);
  ellipse(width/1, height/1, d, d);   
}

```
Potenciometro al minimo:


<img src="https://raw.githubusercontent.com/Amandarinaa/interfaz-II/refs/heads/main/img/Captura%20de%20pantalla%202025-10-07%20120452.png"  with="1024" height="550" />


Potenciometro al maximo: 


<img src="https://raw.githubusercontent.com/Amandarinaa/interfaz-II/refs/heads/main/img/Captura%20de%20pantalla%202025-10-07%20120507.png"  with="1024" height="550" />


### Ejercicio 10 Arduino: Processing+Potenciometro+sensor 

```js
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
### Ejercicio 11 Arduino: cuerpo, video, sensor sharp
codigo arduino

```js
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
```
codigo processing

```js
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
### EJERCICIO N° 10: BOTONERA

```js

ARDUINO:
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

PROCESSING:
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
<img src="https://github.com/clocuello/INTERFAZ2/blob/main/Botonera.png" width="1024" height="550" />

<img src="https://github.com/clocuello/INTERFAZ2/blob/main/BOTONERA.jpeg" width="1024" height="550" />

### Ejercicio N° 11: SENSOR SHARP

Codigo arduino:
```js
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
```

Codigo Processing:
```js
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
<img src="https://github.com/clocuello/INTERFAZ2/blob/main/sensorsharp.jpg" width="1024" height="550" />


### Ejercicio N° 12: SENSOR DE HUMEDAD

```js
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
<img src="https://github.com/clocuello/INTERFAZ2/blob/main/sensorhumedad.jpg" width="1024" height="550" />

### Ejercicio N° 13: CUERPO, VIDEO, SENSOR SHARP

Codigo Arduino:
```js
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
```
Codigo Processing:
```js
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
<img src="https://github.com/Amandarinaa/interfaz-II/blob/main/Captura%20de%20pantalla%202025-10-21%20130105.png" width="1024" height="550" />

### Ejercicio N° 14: PROMEDIO DE IMAGENES

Codigo Arduino:
```js
void setup() {
  Serial.begin(9600);
}

void loop() {
  int potValue = analogRead(A0);
  Serial.println(potValue);
  delay(20);
}
```

Codigo Processing:
```js
import processing.serial.*;

Serial myPort;
PImage[] imgs;
int numImages = 7;
PImage avgImg;
float mixAmount = 0;

void setup() {
  size(1800, 1600);
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
  imgs[3] = loadImage("img4.jpg");
  imgs[4] = loadImage("img5.jpg");
  imgs[5] = loadImage("img6.jpg");
  imgs[6] = loadImage("img7.jpg");

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
    mixAmount = map(sensor, 0, 1023, 0, 7); // 0 a 1
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

### Ejercicio N° 15 PROMEDIO DE IMAGENES LLAMADO UNA CARPETA + POTENCIOMETRO

Codigo arduino:
```js
void setup() {
  Serial.begin(9600);
}

void loop() {
  int potValue = analogRead(A0);
  Serial.println(potValue);
  delay(20);
}
```

Codigo Processing:
```js
// --- Librerías necesarias ---
// Importa la librería de comunicación serial para conectar con Arduino
import processing.serial.*;
// Importa la clase File de Java para listar archivos y carpetas
import java.io.File;

// --- Comunicación serial con Arduino ---
// Variable que contendrá el objeto de puerto serial (conexión con Arduino)
Serial myPort;
// Variable que guarda el valor leído del potenciómetro (0..1023)
float potValue = 0;

// --- Variables de imágenes ---
// Arreglo dinámico que contendrá todas las imágenes cargadas desde la carpeta
PImage[] imgs;
// Imagen donde se almacenará el resultado del promedio/interpolación
PImage avgImg;

// --- Configuración inicial ---
void setup() {
  // Define el tamaño de la ventana de Processing (ancho, alto)
  size(745, 1024);
  
  // Cargar imágenes desde carpeta "data/imagenes"
  // Llama a la función que busca todas las imágenes dentro de esa carpeta
  imgs = loadImagesFromFolder("imagenes");
  // Imprime en la consola cuántas imágenes se cargaron (útil para debug)
  println("Imágenes cargadas: " + imgs.length);
  
  // Redimensionar todas las imágenes al tamaño del lienzo para que coincidan pixel a pixel
  for (int i = 0; i < imgs.length; i++) {
    imgs[i].resize(width, height); // redimensiona cada imagen al ancho y alto de la ventana
  }
  
  // Crea una imagen vacía del tamaño del lienzo donde guardaremos el promedio
  avgImg = createImage(width, height, RGB);
  
  // Conectar con Arduino (ver lista de puertos)
  // Muestra en consola la lista de puertos seriales disponibles (para identificar cuál usar)
  printArray(Serial.list());
  // Alternativa automática (comentada): abrir el primer puerto disponible a 9600 baudios
  // myPort = new Serial(this, Serial.list()[0], 9600);
  // Abrir un puerto específico (ejemplo para macOS). Ajusta según el puerto real en tu sistema.
  myPort = new Serial(this, "/dev/cu.usbmodem1101", 9600);
  // Nota: si no funciona el puerto, revisa la salida de printArray(Serial.list()) y usa el nombre correcto.
}

// --- Bucle principal ---
// draw() se ejecuta continuamente (aprox. 60 veces por segundo)
void draw() {
  // Pinta el fondo de negro en cada frame
  background(0);
  // Llama a la función que lee datos desde el puerto serial (actualiza potValue)
  readSerial();
  
  // Si no hay imágenes o sólo hay una, no hacemos nada (necesitamos al menos 2 para interpolar)
  if (imgs == null || imgs.length < 2) return;
  
  // Mapear el valor del potenciómetro (0..1023) al rango de índices entre 0 y imgs.length-1
  // Esto permite moverse a lo largo de la secuencia de imágenes
  float mixValue = map(potValue, 0, 1023, 0, imgs.length - 1);
  
  // Calcular el promedio/interpolación entre las dos imágenes vecinas según mixValue
  avgImagesWeighted(mixValue);
  
  // Mostrar la imagen promedio resultante en la pantalla, en la posición (0,0)
  image(avgImg, 0, 0);
  
  // Mostrar texto con el valor actual del potenciómetro en la esquina inferior izquierda
  fill(255); // color blanco para el texto
  text("Valor pot: " + nf(potValue, 1, 0), 10, height - 10); // nf para formatear el número
}

// --- Función que calcula el promedio ponderado entre imágenes ---
// mix es un valor flotante que indica la posición entre imágenes (ej. 2.3 -> entre img2 e img3)
void avgImagesWeighted(float mix) {
  // Accede al arreglo de píxeles de avgImg para poder modificarlos directamente
  avgImg.loadPixels();
  
  // Asegura que mix esté dentro del rango válido [0, imgs.length - 1]
  mix = constrain(mix, 0, imgs.length - 1);
  
  // i1 es el índice de la imagen "inferior" (por ejemplo 2 en 2.3)
  int i1 = floor(mix);
  // i2 es la imagen siguiente (i1 + 1), pero sin pasarse del último índice
  int i2 = min(i1 + 1, imgs.length - 1);
  // t es la fracción entre i1 e i2 (por ejemplo, 0.3 si mix es 2.3)
  float t = mix - i1;
  
  // Cargar los píxeles de las dos imágenes que vamos a mezclar
  imgs[i1].loadPixels();
  imgs[i2].loadPixels();
  
  // Recorre todos los píxeles de la imagen objetivo
  for (int i = 0; i < avgImg.pixels.length; i++) {
    // Coge el color del píxel i de la imagen i1
    color c1 = imgs[i1].pixels[i];
    // Coge el color del píxel i de la imagen i2
    color c2 = imgs[i2].pixels[i];
    
    // Interpola por separado cada componente de color (rojo, verde, azul)
    // red(c1) obtiene la componente roja del color c1
    float r = lerp(red(c1), red(c2), t);
    // green(c1) obtiene la componente verde del color c1
    float g = lerp(green(c1), green(c2), t);
    // blue(c1) obtiene la componente azul del color c1
    float b = lerp(blue(c1), blue(c2), t);
    
    // Crea un nuevo color a partir de las componentes interpoladas y lo asigna al píxel i
    avgImg.pixels[i] = color(r, g, b);
  }
  
  // Aplica los cambios realizados en el arreglo de píxeles a la imagen avgImg
  avgImg.updatePixels();
}

// --- Leer valor del potenciómetro desde Arduino ---
// Lee datos desde el puerto serial hasta encontrar saltos de línea y los convierte a número
void readSerial() {
  // Mientras el puerto exista y tenga bytes disponibles para leer...
  while (myPort != null && myPort.available() > 0) {
    // Lee una línea completa hasta '\n' (salto de línea)
    String val = myPort.readStringUntil('\n');
    if (val != null) {
      // Elimina espacios y caracteres de control al inicio/final
      val = trim(val);
      // Si la cadena no está vacía, la convierte a float y la asigna a potValue
      if (val.length() > 0) {
        potValue = float(val);
      }
    }
  }
}

// --- Cargar todas las imágenes desde una carpeta ---
// Devuelve un arreglo PImage[] con todas las imágenes JPG/PNG encontradas en data/folderName
PImage[] loadImagesFromFolder(String folderName) {
  // Construye la ruta absoluta a la carpeta dentro de la carpeta data del sketch
  String path = sketchPath("data/" + folderName);
  // Crea un objeto File apuntando a esa carpeta
  File folder = new File(path);
  // Lista todos los archivos dentro de la carpeta (puede devolver null si no existe)
  File[] files = folder.listFiles();
  
  // Si files es null, la carpeta no existe o no tiene permisos -> avisar y devolver null
  if (files == null) {
    println("Carpeta no encontrada: " + path);
    return null;
  }
  
  // Crea una lista dinámica para almacenar las PImage cargadas
  ArrayList<PImage> loaded = new ArrayList<PImage>();
  // Recorre cada archivo encontrado en la carpeta
  for (File f : files) {
    // Obtiene el nombre del archivo y lo convierte a minúsculas para comparar extensiones
    String fname = f.getName().toLowerCase();
    // Si termina en .jpg o .png, lo cargamos
    if (fname.endsWith(".jpg") || fname.endsWith(".png")) {
      // loadImage busca en data/folderName el archivo y devuelve un PImage
      PImage img = loadImage(folderName + "/" + f.getName());
      // Si la imagen se cargó correctamente, la agregamos a la lista
      if (img != null) loaded.add(img);
    }
  }
  
  // Convierte la ArrayList a un arreglo PImage[] y lo retorna
  return loaded.toArray(new PImage[loaded.size()]);
}
```


### Idea Grupal

Esta proyecto nace desde la idea de hacer desorden en el orden, la intencion de querer ser ordenado pero que se vuelve imposible ser este completamente, por lo que pensamos en crear en Processing una linea de color blanco en la que se vean las letras de la palabra "ORDEN" de forma seguida y que esta palabra se moviera por la pantalla a partir del uso de Arduino y Potenciometro.

Codigo arduino:
```js
int potPin = A0; // Pin del potenciómetro
int potValue = 0;

void setup() {
Serial.begin(9600);
}

void loop() {
potValue = analogRead(potPin); // Lee valor (0 a 1023)
Serial.println(potValue); // Envia a Processing
delay(30); // Pequeño retardo
}
```

Codigo Processing:
```js
import processing.serial.*;

Serial myPort;
String textToShow = "ANY FURTHER QUESTIONS";
ArrayList<PVector> trail = new ArrayList<PVector>();

float potValue = 0; // valor leído del Arduino
float mappedX = 0; // posición mapeada

void setup() {
size(800, 400);
background(0);
textAlign(CENTER, CENTER);
textSize(24);
fill(255);

// Abrir el puerto serie correcto (ver cuál aparece en la consola)
println(Serial.list());
myPort = new Serial(this, Serial.list()[0], 9600);
}

void draw() {
background(0);

// Leer valor desde Arduino si hay datos
while (myPort.available() > 0) {
String val = myPort.readStringUntil('\n');
if (val != null) {
potValue = float(trim(val));
}
}

// Mapeo del potenciómetro a posición X en pantalla
mappedX = map(potValue, 0, 1023, 0, width);

// Crear una trayectoria con ruido vertical (como si fuera una línea viva)
float yPos = height/2 + sin(frameCount * 0.05) * 50;
trail.add(new PVector(mappedX, yPos));

// Mantener máximo 100 puntos
if (trail.size() > 100) trail.remove(0);

// Dibujar línea blanca del trazo
stroke(255);
strokeWeight(2);
noFill();
beginShape();
for (PVector p : trail) {
curveVertex(p.x, p.y);
}
endShape();

// Mostrar texto sobre la línea
for (int i = 0; i < trail.size(); i++) {
float t = map(i, 0, trail.size(), 0, textToShow.length());
int index = int(t);
if (index < textToShow.length()) {
char c = textToShow.charAt(index);
PVector p = trail.get(i);
pushMatrix();
translate(p.x, p.y);
rotate(noise(i * 0.1, frameCount * 0.01) * TWO_PI);
text(c, 0, 0);
popMatrix();
}
}
}
```

El codigo de processing lo sacamos de chat gpt, usando el prompt: al momento de mover el potenciómetro, se crea una línea blanca donde aparece un texto, código para processing y arduino uno.
import processing.serial.*;
```js
Serial myPort;
String textToShow = "ANY FURTHER QUESTIONS";
ArrayList<PVector> trail = new ArrayList<PVector>();

float potValue = 0; // valor leído del Arduino
float mappedX = 0; // posición mapeada

void setup() {
size(800, 400);
background(0);
textAlign(CENTER, CENTER);
textSize(24);
fill(255);

// Abrir el puerto serie correcto (ver cuál aparece en la consola)
println(Serial.list());
myPort = new Serial(this, Serial.list()[0], 9600);
}

void draw() {
background(0);

// Leer valor desde Arduino si hay datos
while (myPort.available() > 0) {
String val = myPort.readStringUntil('\n');
if (val != null) {
potValue = float(trim(val));
}
}

// Mapeo del potenciómetro a posición X en pantalla
mappedX = map(potValue, 0, 1023, 0, width);

// Crear una trayectoria con ruido vertical (como si fuera una línea viva)
float yPos = height/2 + sin(frameCount * 0.05) * 50;
trail.add(new PVector(mappedX, yPos));

// Mantener máximo 100 puntos
if (trail.size() > 100) trail.remove(0);

// Dibujar línea blanca del trazo
stroke(255);
strokeWeight(2);
noFill();
beginShape();
for (PVector p : trail) {
curveVertex(p.x, p.y);
}
endShape();

// Mostrar texto sobre la línea
for (int i = 0; i < trail.size(); i++) {
float t = map(i, 0, trail.size(), 0, textToShow.length());
int index = int(t);
if (index < textToShow.length()) {
char c = textToShow.charAt(index);
PVector p = trail.get(i);
pushMatrix();
translate(p.x, p.y);
rotate(noise(i * 0.1, frameCount * 0.01) * TWO_PI);
text(c, 0, 0);
popMatrix();
}
}
}
```
Con este resultado:

https://github.com/clocuello/INTERFAZ2/blob/main/Captura%20de%20pantalla%202025-11-03%20101530.png
<img src="https://github.com/clocuello/INTERFAZ2/blob/main/Captura%20de%20pantalla%202025-11-03%20101530.png" width="1024" height="550" />


despues cambiamos la frase String textToShow = "ANY FURTHER QUESTIONS";
por “ORDEN”


despues modificamos el tamaño de la letra en la parte del código:

textSize(24);
donde el vez de 24 le pusimos 50


luego modificamos el espacio que había entre cada letra, en la parte del código:

for (int i = 0; i < trail.size(); i++) {

eliminamos el segundo signo + y lo cambiamos por un signo = y despues de eso se agrego un numero, fuimos probando tamaños y llegamos a el 10


despues modificamos el grosor de la linea blanca que guia las letras en la parte del código:


strokeWeight(2);
donde pusimos 50 en vez de 20

y luego cambiamos el color de las letras de blanco: fill(255);
a negro: fill(0);



despues cambiamos el largo de la línea en la parte:
 if (trail.size() > 100) trail.remove(0);
y cambiamos el 100 por 600


Hicimos varias modificaciones dentro del código, incluyendo intentar agregar un segundo potenciómetro, agregar varias veces la misma frase, cambiar los colores del texto, línea y fondo, y cambiar los tamaños de las letras, fuera de los cambios que quedaron dentro del código.

Este es el código final y modificado, las zonas subrayadas en verde son las zonas modificadas:
```js
import processing.serial.*;

Serial myPort;
String textToShow = "NEDRO NEDRO NEDRO";
ArrayList<PVector> trail = new ArrayList<PVector>();

float potValue = 0; // valor leído del Arduino
float mappedX = 0; // posición mapeada

void setup() {
size(800, 400);
background(0);
textAlign(CENTER, CENTER);
textSize(50);
fill(0);

// Abrir el puerto serie correcto (ver cuál aparece en la consola)
println(Serial.list());
myPort = new Serial(this, Serial.list()[0], 9600);
}

void draw() {
background(0);

// Leer valor desde Arduino si hay datos
while (myPort.available() > 0) {
String val = myPort.readStringUntil('\n');
if (val != null) {
potValue = float(trim(val));
}
}

// Mapeo del potenciómetro a posición X en pantalla
mappedX = map(potValue, 0, 1023, 0, width);

// Crear una trayectoria con ruido vertical (como si fuera una línea viva)
float yPos = height/2 + sin(frameCount * 0.05) * 50;
trail.add(new PVector(mappedX, yPos));

// Mantener máximo 100 puntos
if (trail.size() > 600) trail.remove(0);

// Dibujar línea blanca del trazo
stroke(255);
strokeWeight(40);
noFill();
beginShape();
for (PVector p : trail) {
curveVertex(p.x, p.y);
}
endShape();


// Mostrar texto sobre la línea
for (int i = 5; i < trail.size(); i+=10) {
float t = map(i, 0, trail.size(), 0, textToShow.length());
int index = int(t);
if (index < textToShow.length()) {
char c = textToShow.charAt(index);
PVector p = trail.get(i);
pushMatrix();
translate(p.x, p.y);
rotate(noise(i * 0.1, frameCount * 0.01) * TWO_PI);
text(c, 0, 0);
popMatrix();
}
}
}
```
### Idea Grupal, Entrega Final 

```
codigo Processing:

import processing.serial.*;

Serial myPort;
String textToShow = "NEDRO NEDRO NEDRO";
ArrayList<PVector> trail = new ArrayList<PVector>();

float potValue1 = 0; // valor leído del Arduino (Pot X)
float mappedX = 0;   // posición mapeada (X)
float potValue2 = 0; // valor leído del Arduino (Pot Y)
float mappedY = 0;   // posición mapeada (Y)

void setup() {
  size(800, 400);
  background(0);
  textAlign(CENTER, CENTER);
  textSize(50);
  fill(0);
 
  // Abrir el puerto serie correcto (ver cuál aparece en la consola)
  println(Serial.list());
  // Asegúrate de que [0] sea el puerto correcto. La velocidad debe coincidir con Arduino.
  myPort = new Serial(this, Serial.list()[0], 9600);
}

void draw() {
  background(0);

  // Leer valor desde Arduino si hay datos
  while (myPort.available() > 0) {
    String val = myPort.readStringUntil('\n');
    if (val != null) {
      val = trim(val); // Limpiar el string
      String[] pieces = split(val, ','); // Dividir por la coma

      // **CORRECCIÓN 1: Lectura de dos valores separados**
      if (pieces.length >= 2) {
        potValue1 = float(trim(pieces[0])); // X
        potValue2 = float(trim(pieces[1])); // Y
      }
    }
  }

  // **CORRECCIÓN 2: Mapeo de valores (Usando potValue1 y potValue2)**
  mappedX = map(potValue1, 0, 1023, 0, width);
  // mappedY ahora mapea a la altura 'height'
  mappedY = map(potValue2, 0, 1023, 0, height);

  // Crear una trayectoria con ruido vertical (como si fuera una línea viva)
  // **CORRECCIÓN 3: La posición Y base es mappedY**
  float yPos = mappedY + sin(frameCount * 0.03) * 50;
 
  trail.add(new PVector(mappedX, yPos));
 
  // Mantener máximo 600 puntos
  if (trail.size() > 600) trail.remove(0);

  // Dibujar línea blanca del trazo
  stroke(255);
  strokeWeight(60);
  noFill();
  beginShape();
  // Se necesita al menos 4 puntos para curveVertex, de lo contrario podría dar error.
  // Es una buena práctica agregar puntos de control al principio y final si se usa curveVertex.
  if (trail.size() >= 2) {
      // Si el rastro es lo suficientemente largo, empieza a dibujar
      // Añade el primer punto dos veces (punto de control)
      curveVertex(trail.get(0).x, trail.get(0).y);
     
      for (PVector p : trail) {
        curveVertex(p.x, p.y);
      }
     
      // Añade el último punto dos veces (punto de control)
      curveVertex(trail.get(trail.size() - 1).x, trail.get(trail.size() - 1).y);
  }
  endShape();

  // Mostrar texto sobre la línea
  for (int i = 5; i < trail.size(); i+=10) {
    float t = map(i, 0, trail.size(), 0, textToShow.length());
    int index = int(t);
    if (index < textToShow.length()) {
      char c = textToShow.charAt(index);
      PVector p = trail.get(i);
      pushMatrix();
      translate(p.x, p.y);
      // El color del texto debe ser diferente al fondo (0) para que se vea
      fill(0);
      rotate(noise(i * 0.1, frameCount * 0.01) * TWO_PI);
      text(c, 0, 0);
      popMatrix();
      // Vuelve a poner el fill en negro/sin relleno si es necesario para otros elementos,
      // pero aquí, para el rastro, no se usa fill.
      noFill();
    }
  }
}
```
Codigo Arduino

```

int pot1Pin = A0;   // Primer potenciómetro

int pot2Pin = A1;   // Segundo potenciómetro



int pot1Value = 0;

int pot2Value = 0;



void setup() {

  Serial.begin(9600);

}



void loop() {

  pot1Value = analogRead(pot1Pin); // Lee potenciómetro 1 (0–1023)

  pot2Value = analogRead(pot2Pin); // Lee potenciómetro 2 (0–1023)



  // Envía ambos valores a Processing separados por coma

  Serial.print(pot1Value);

  Serial.print(",");

  Serial.println(pot2Value);



  delay(30); // Pequeño retardo

}

````




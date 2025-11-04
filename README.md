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

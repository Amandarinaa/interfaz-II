# interfaz-II
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
El código de processing viene pre escrito con una sola elipse que cambia de color y tamaño al responder al potenciometro, pero yo le agreugue más elipses, les cambie el tamaño máximo para que fueran más grandes y cambie los colores de cada una de ellas. 

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
  float d = map(sensorVal, 0, width, 40  <span style="color:blue;">800</span>)
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

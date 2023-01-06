# SistemEmbedded
### Disusun Oleh
- Sari Wahyuningsih 4.31.20.0.23

# Daftar Laporan JobSheet Sistem Embedded

- [JobSheet 1 - Dasar Pemrograman ESP32 Untuk Pemrosesan Data Input/Output Analog dan Digital](https://github.com/sariwhyu/JobSheet1)
- [JobSheet 1.1 - Jaringan Sensor Nirkabel Menggunakan ESP-NOW](https://github.com/sariwhyu/JobSheet1.1)
- [JobSheet 2 - Protokol Komunikasi dan Sensor](https://github.com/sariwhyu/JobSheet2)
- [JobSheet 3 - Topologi Jaringan Lokal dan WiFi](https://github.com/sariwhyu/JobSheet3)
- [Jobsheet4.1 - Cayenne(MQTT)+Sensor+Button+Website Monitoring](https://github.com/sariwhyu/TugasNo1)
- [Jobsheet4.2 - Adafruit.IO+Sensor+LED+Suara](https://github.com/sariwhyu/TugasNo2)
- [Jobsheet4.3 - ThingSpeak+Sensor](https://github.com/sariwhyu/TugasNo3)
- [Jobsheet4.4 - ESP Now+IOT](https://github.com/sariwhyu/TugasNo4)


# JobSheet 1 DASAR PEMROGRAMAN ESP32 UNTUK PEMROSESAN DATA INPUT/OUTPUT ANALOG DAN DIGITAL

## Alat & Bahan

-	ESP32
-	Breadboard
-	Kabel jumper
-	Potensiometer 10k Ohm (1)
-	Sensor Capacitive Soil Moisture
-	LED (5) dan Push Button (3)
-	Multimeter
-	Resistor 330,1K, 10K Ohm (@ 3)

## Coding

### Button Push LED ON

```bash
  // set pin numbers
const int buttonPin = 4; // the number of the pushbutton pin
const int ledPin = 5; // the number of the LED pin
// variable for storing the pushbutton status
int buttonState = 0;
void setup() {
Serial.begin(115200);
// initialize the pushbutton pin as an input
pinMode(buttonPin, INPUT);
// initialize the LED pin as an output
pinMode(ledPin, OUTPUT);
}
void loop() {
// read the state of the pushbutton value
buttonState = digitalRead(buttonPin);
Serial.println(buttonState);
// check if the pushbutton is pressed.
// if it is, the buttonState is HIGH
if (buttonState == HIGH) {
// turn LED on
digitalWrite(ledPin, HIGH);
} else {
// turn LED off
digitalWrite(ledPin, LOW);
}
}

```

### Button Push LED BLINK

```bash
  // set pin numbers
const int buttonPin = 4; // the number of the pushbutton pin
const int ledPin = 5; // the number of the LED pin
const int buttonPin1 = 2;
const int ledPin1 = 19;
// variable for storing the pushbutton status
int buttonState = 0;
int buttonState1 = 0;
void setup() { 
 Serial.begin(115200);
 // initialize the pushbutton pin as an input
 pinMode(buttonPin, INPUT);
 pinMode(buttonPin1, INPUT);
 // initialize the LED pin as an output
 pinMode(ledPin, OUTPUT);
 pinMode(ledPin1, OUTPUT);
}
void loop() {
  
 // read the state of the pushbutton value
 buttonState = digitalRead(buttonPin);
 Serial.println(buttonState);
 // check if the pushbutton is pressed.
 // if it is, the buttonState is HIGH
 if (buttonState == HIGH) {
 // turn LED on
 digitalWrite(ledPin, HIGH);
 } else {
 // turn LED off
 digitalWrite(ledPin, LOW);
 }
 buttonState1 = digitalRead(buttonPin1);
 Serial.println(buttonState1);
 if (buttonState1 == HIGH) {
 // turn LED on
  digitalWrite(ledPin1, HIGH);   // turn the LED on (HIGH is the voltage level)
  delay(500);                       // wait for a second
  digitalWrite(ledPin1, LOW);    // turn the LED off by making the voltage LOW
  delay(500);                       // wait for a second
 } else {
 // turn LED off
 digitalWrite(ledPin1 , LOW);
 }
}

```

### Button Push LED RUNNING

```bash
  // set pin numbers
const int buttonPin = 4; // the number of the pushbutton pin
const int ledPin = 5; // the number of the LED pin
const int buttonPin1 = 2;
const int ledPin1 = 19;
const int buttonPin2 = 33;
//const int ledPin2 = 25;
//const int ledPin3 = 26;
//const int ledPin4 = 27;
// variable for storing the pushbutton status
int buttonState = 0;
int buttonState1 = 0;
int buttonState2 = 0;
void setup() { 
 Serial.begin(115200);
 // initialize the pushbutton pin as an input
 pinMode(buttonPin, INPUT);
 pinMode(buttonPin1, INPUT);
 pinMode(buttonPin2, INPUT);
 // initialize the LED pin as an output
 pinMode(ledPin, OUTPUT);
 pinMode(ledPin1, OUTPUT);
//pinMode(ledPin2, OUTPUT);
 //pinMode(ledPin3, OUTPUT);
 //pinMode(ledPin4, OUTPUT);
}
void loop() {
  
 // read the state of the pushbutton value
 buttonState = digitalRead(buttonPin);
 Serial.println(buttonState);
 // check if the pushbutton is pressed.
 // if it is, the buttonState is HIGH
 if (buttonState == HIGH) {
 // turn LED on
 digitalWrite(ledPin, HIGH);
 } else {
 // turn LED off
 digitalWrite(ledPin, LOW);
 }
 buttonState1 = digitalRead(buttonPin1);
 Serial.println(buttonState1);
 
 if (buttonState1 == HIGH) {
 // turn LED on
  digitalWrite(ledPin1, HIGH);   // turn the LED on (HIGH is the voltage level)
  delay(500);                       // wait for a second
  digitalWrite(ledPin1, LOW);    // turn the LED off by making the voltage LOW
  delay(500);                       // wait for a second
 } else {
 // turn LED off
 digitalWrite(ledPin1 , LOW);
 }
 
 buttonState2 = digitalRead(buttonPin2);
 Serial.println(buttonState2);
  if (buttonState2 == HIGH) {
  //LED yang ada di Pin 3 menyala, Pin 4 & 5 mati
  digitalWrite(25, HIGH);
  digitalWrite(26, LOW);
  digitalWrite(27, LOW);
  //kecepatan kedip 0,5 detik
  delay(500);
 
  //LED yang ada di Pin 4 menyala, Pin 3 & 5 mati
  digitalWrite(25, LOW);
  digitalWrite(26, HIGH);
  digitalWrite(27, LOW);
  //kecepatan kedip 0,5 detik
  delay(500);
 
  //LED yang ada di Pin 5 menyala, Pin 3 & 4 mati
  digitalWrite(25, LOW);
  digitalWrite(26, LOW);
  digitalWrite(27, HIGH);
  //kecepatan kedip 0,5 detik
  delay(500);                      
 } else {
 // turn LED off
 digitalWrite(25 , LOW);
 digitalWrite(26 , LOW);
 digitalWrite(27 , LOW);
 }
}

```

### PWM 1 LED

```bash
  // the number of the LED pin
const int ledPin = 16; // 16 corresponds to GPIO16
// setting PWM properties
const int freq = 5000;
const int ledChannel = 0; //PWM Channel
const int resolution = 8; //resolution bit
void setup(){
// configure LED PWM functionalitites
ledcSetup(ledChannel, freq, resolution);
// attach the channel to the GPIO to be controlled
ledcAttachPin(ledPin, ledChannel);
}
void loop(){
// increase the LED brightness
for(int dutyCycle = 0; dutyCycle <= 255; dutyCycle++){
// changing the LED brightness with PWM
ledcWrite(ledChannel, dutyCycle);
delay(15);
}
// decrease the LED brightness
for(int dutyCycle = 255; dutyCycle >= 0; dutyCycle--){
// changing the LED brightness with PWM
ledcWrite(ledChannel, dutyCycle);
delay(15);
}
}

```

### PWM 3 LED

```bash
  // the number of the LED pin
const int ledPin = 16; // 16 corresponds to GPIO16
const int ledPin2 = 17; // 17 corresponds to GPIO17
const int ledPin3 = 5; // 5 corresponds to GPIO5
// setting PWM properties
const int freq = 5000;
const int ledChannel = 0;
const int resolution = 8;
void setup(){
// configure LED PWM functionalitites
ledcSetup(ledChannel, freq, resolution);
// attach the channel to the GPIO to be controlled
ledcAttachPin(ledPin, ledChannel);
ledcAttachPin(ledPin2, ledChannel);
ledcAttachPin(ledPin3, ledChannel);
}
void loop(){
// increase the LED brightness
for(int dutyCycle = 0; dutyCycle <= 255; dutyCycle++){
// changing the LED brightness with PWM
ledcWrite(ledChannel, dutyCycle);
delay(15);
}
// decrease the LED brightness
for(int dutyCycle = 255; dutyCycle >= 0; dutyCycle--){
// changing the LED brightness with PWM
ledcWrite(ledChannel, dutyCycle);
delay(15);
}
}

```

### ADC & DAC

```bash
  // Potentiometer is connected to GPIO 34 (Analog ADC1_CH6)
const int potPin = 34;
// variable for storing the potentiometer value
int potValue = 0;
void setup() {
Serial.begin(115200);
delay(1000);
}
void loop() {
// Reading potentiometer value
potValue = analogRead(potPin);
Serial.println(potValue);
delay(500);
}

```

### ADC & DAC LED

```bash
  const int analogInPin = 34; 
const int analogOutPin = 5; 
const int freq = 5000;
const int ledChannel = 0;
const int resolution = 8;
int sensorValue = 0; 
int outputValue = 0;

void setup() {
  Serial.begin(115200);
  ledcSetup(ledChannel, freq, resolution);
  ledcAttachPin(analogOutPin, ledChannel);
}

void loop() {
  sensorValue = analogRead(analogInPin);
  outputValue = map(sensorValue, 0, 4095, 0, 255);
  ledcWrite(ledChannel, outputValue);
  Serial.print("sensor = ");
  Serial.print(sensorValue);
  Serial.print("\t output = ");
  Serial.println(outputValue);
  delay(500);
}

```

## Hasil

https://github.com/sariwhyu/JobSheet1/blob/main/1%20LED.mp4

https://github.com/sariwhyu/JobSheet1/blob/main/3%20LED.mp4

https://github.com/sariwhyu/JobSheet1/blob/main/BLINK.mp4

https://github.com/sariwhyu/JobSheet1/blob/main/Button%20LED.mp4

https://github.com/sariwhyu/JobSheet1/blob/main/Running.mp4

https://github.com/sariwhyu/JobSheet1/blob/main/Serial%20Mon.mp4

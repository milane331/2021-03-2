# 2021-03-2
2021/03/2
## 七段顯示器
8*c++
int a [10][7]= {{1,1,1,1,1,1,0},
                 {0,1,1,0,0,0,0},
                 {1,1,0,1,1,0,1},
                 {1,1,1,1,0,0,1},
                 {0,1,1,0,0,1,1},
                 {1,0,1,1,0,1,1},
                 {0,0,1,1,1,1,1},
                 {1,1,1,0,0,1,0},
                 {1,1,1,1,1,1,1},
                 {1,1,1,0,0,1,1,}};
void setup() { 
int i;
for (i = 2;i<13;i++)
  pinMode(i,OUTPUT);
}

void loop() {
  // put your main code here, to run repeatedly:
digitalWrite(9,HIGH);
for (int t =0; t<10;t++)
{for (int i = 2; i<9; i++)
 digitalWrite(i,a[t][i-2]);
 delay(1000);}
}
```
![image](https://github.com/milane331/2021-03-2/blob/main/image.jpg)
# 顯示2碼
```c++
int a [10][7]= {{1,1,1,1,1,1,0},
                 {0,1,1,0,0,0,0},
                 {1,1,0,1,1,0,1},
                 {1,1,1,1,0,0,1},
                 {0,1,1,0,0,1,1},
                 {1,0,1,1,0,1,1},
                 {0,0,1,1,1,1,1},
                 {1,1,1,0,0,1,0},
                 {1,1,1,1,1,1,1},
                 {1,1,1,0,0,1,1,}};
int com [4]={9,10,11,12}; 
int c;
void setup() { 
int i;
for (i = 2;i<13;i++)
  pinMode(i,OUTPUT);
  c=millis();
}

void loop() {
  // put your main code here, to run repeatedly:
 // for (int i =0; i<4;i++)digitalWrite(com[i],1);
digitalWrite(9,HIGH);
digitalWrite(10,LOW);
for (int i = 2; i<9; i++)
digitalWrite(i,a[0][i-2]);
delay(10);

for (int STATUS = 9; STATUS<13; i++)

digitalWrite(9,LOW);
digitalWrite(10,HIGH);
for (int i = 2; i<9; i++)
digitalWrite(i,a[1][i-2]);
delay(10);
//digitalWrite(10,HIGH);
//for (int t =0; t<10;t++)
//{for (int i = 2; i<9; i++)
 //digitalWrite(i,a[t][i-2]);
 //delay(200);}
}
```
![image](https://github.com/milane331/2021-03-2/blob/main/4A70F824-FE95-49D3-BEBB-677CA4EB757F.jpeg)
# 指定顯示4碼
```c++
int b [4][4]={{1,0,0,0},
              {0,1,0,0},
              {0,0,1,0}, 
              {0,0,0,1}};
int d [4]={1,2,3,5};
void setup() { 
int i;
for (i = 2;i<13;i++)
  pinMode(i,OUTPUT);
  c=millis();
  Serial.begin(9600);
}

void loop() {
  // put your main code here, to run repeatedly:
for (int j=0; j<4; j++)
{
  for (int k=9; k<13; k++)
     digitalWrite(k,b[j][k-9]);

  for (int i=2; i<9; i++)
     digitalWrite(i,a[d[j]][i-2]);
     delay(5);
}
```
![image](https://github.com/milane331/2021-03-2/blob/main/BB37B161-8607-4D54-80F3-20C5DCBDECD1.jpeg)

## LCD 功能加按鈕控制

```c++
include <LiquidCrystal.h>
const int rs = 12, en = 11, d4 = 5, d5 = 4, d6 = 3, d7 = 2;
LiquidCrystal lcd(rs, en, d4, d5, d6, d7);
byte smiley[8] = {
  B00000,
  B10001,
  B00000,
  B00000,
  B11111,
  B00000,
  B00000,
};
byte ak[8] = {
  B00001,
  B00010,
  B00100,
  B01001,
  B10010,
  B00100,
  B01001,
};
int b = 0;
void setup() {
  // set up the LCD's number of columns and rows:
  // Print a message to the LCD.
  lcd.begin(16, 2);
  lcd.setCursor(0, 1);
  lcd.print("Hello, teacher!");
  lcd.createChar(0, smiley);
  lcd.createChar(1, ak);
  pinMode(6, OUTPUT);
  for (int p = 6; p < 8; p++)
  {
    pinMode(p, INPUT);
    digitalWrite(p, 1);
  }
  for (int p = 6; p < 8; p++)
  {
    pinMode(6, OUTPUT);
    digitalWrite(6, 0);
  }
 
  delay(2000);
  lcd.clear();
  lcd.setCursor(2, 0);
  lcd.print("w e l c o m e");
  lcd.setCursor(3, 1);
  lcd.print("My program");
  lcd.setCursor(14, 1);
  lcd.write(byte(1));
  lcd.noBlink();
  delay(800);

  b = 0;
  for (int a = 0; a < 17; a++)
  {
    if (a == 16 && b != 1)
    {
      a = 0;
      b = 1;
    }
    for (int i = 0; i < 2; i++)
    { lcd.setCursor(a, b);
      lcd.write(byte(0));

    }
    delay(300);
  }
  lcd.clear();

}


void loop() {
  // Turn off the blinking cursor:


  lcd.setCursor(2, 1);
  lcd.print("My program");

  if (digitalRead(8) == 0)
  {
    while (digitalRead(8) == 0); {
      delay(300);
    }
    lcd. scrollDisplayLeft();
  }
  if (digitalRead(7) == 0)
  {
    while (digitalRead(7) == 0); {
      delay(30);
    }
    lcd.scrollDisplayRight();
  }
  // Turn on the blinking cursor:
  lcd.blink();
  delay(300);
}
```
#控制風扇
```c++
void setup() {
  // put your setup code here, to run once:
pinMode(5,OUTPUT);
pinMode(6,OUTPUT);
}

void loop() {
 for (int i = 100; i <255 ; i+=76)
  {
    analogWrite(5, 1);
    analogWrite(6, i);
    delay(800);
  }
  ```
![image](https://github.com/milane331/2021-03-2/blob/main/6541D171-206C-46B8-BFFA-D1915A04078B.gif)
#老師寫法
```c++
float a = millis();
int x = 80;
void setup() {
  // put your setup code here, to run once:

  pinMode(5, OUTPUT);
  pinMode(6, OUTPUT);
}

void loop() {
  float b = millis();
  if (x>=254) x=80;
  if((b-a)>=5000)
  {
    x=x+87;
    a=b;
  }
  analogWrite(5,x);
  digitalWrite(6,0);
  ```
 #按鈕控制
  ```c++
int x;
void setup() {
  // put your setup code here, to run once:

  pinMode(5, OUTPUT);
  pinMode(6, OUTPUT);
  pinMode(2, INPUT);
  pinMode(3, INPUT);
  Serial.begin(9600);

}
void motor(int x)
{
  analogWrite(5, x);
  digitalWrite(6, 0);
}
void loop() {
 
 if ( digitalRead(2) == LOW)
  {
    while (digitalRead(2) == LOW);
    x = x + 35;
  }
  if (x >= 255){
    x = 255;
  }
  motor(x);
   if ( digitalRead(4) == LOW)
  {
    while (digitalRead(4) == LOW);
    x = x - 35;
  }
  if (x <= 0){
    x = 0;
  }
  if(x<=120)x=120;
  motor(x);
  Serial.println(x);int x;
void setup() {
  // put your setup code here, to run once:

  pinMode(5, OUTPUT);
  pinMode(6, OUTPUT);
  pinMode(2, INPUT);
  pinMode(3, INPUT);
  Serial.begin(9600);

}
void motor(int x)
{
  analogWrite(5, x);
  digitalWrite(6, 0);
}
void loop() {
 
 if ( digitalRead(2) == LOW)
  {
    while (digitalRead(2) == LOW);
    x = x + 35;
  }
  if (x >= 255){
    x = 255;
  }
  motor(x);
   if ( digitalRead(4) == LOW)
  {
    while (digitalRead(4) == LOW);
    x = x - 35;
  }
  if (x <= 0){
    x = 0;
  }
  if(x<=120)x=120;
  motor(x);
  Serial.println(x);
  }
   ```
   #按鈕控制開關
   ```c++
    if ( digitalRead(7) == LOW)
  {
    while (digitalRead(7) == LOW);
    x = 80;
  }
  if ( digitalRead(8) == LOW)
  {
    while (digitalRead(8) == LOW);
    x = 120;
  }
  ```
 #溫溼度感測器
  ```c++
 void loop() {
  double a ;
  // Delay between measurements.
  delay(delayMS);
  // Get temperature event and print its value.
  sensors_event_t event;
  dht.temperature().getEvent(&event);
  if (isnan(event.temperature)) {
    Serial.println(F("Error reading temperature!"));
  }
  else {
    Serial.print(F("Temperature: "));
    Serial.print(event.temperature);
    Serial.println(F("°C"));
  }
  a=event.temperature;
  // Get humidity event and print its value.
  dht.humidity().getEvent(&event);
  if (isnan(event.relative_humidity)) {
    Serial.println(F("Error reading humidity!"));
  }
  else {
    Serial.print(F("Humidity: "));
    Serial.print(event.relative_humidity);
    Serial.println(F("%"));
    if(a>=27)
    {
      tone(3,1000);
      delay(500);
      noTone(3);
      delay(500);
      Serial.print(a);
    }
  }
}
 ```
#溫度控制風扇
// DHT Temperature & Humidity Sensor
// Unified Sensor Library Example
// Written by Tony DiCola for Adafruit Industries
// Released under an MIT license.

// REQUIRES the following Arduino libraries:
// - DHT Sensor Library: https://github.com/adafruit/DHT-sensor-library
// - Adafruit Unified Sensor Lib: https://github.com/adafruit/Adafruit_Sensor

#include <Adafruit_Sensor.h>
#include <DHT.h>
#include <DHT_U.h>

#define DHTPIN 2     // Digital pin connected to the DHT sensor 
// Feather HUZZAH ESP8266 note: use pins 3, 4, 5, 12, 13 or 14 --
// Pin 15 can work but DHT must be disconnected during program upload.

// Uncomment the type of sensor in use:
//#define DHTTYPE    DHT11     // DHT 11
#define DHTTYPE    DHT22     // DHT 22 (AM2302)
//#define DHTTYPE    DHT21     // DHT 21 (AM2301)

// See guide for details on sensor wiring and usage:
//   https://learn.adafruit.com/dht/overview

DHT_Unified dht(DHTPIN, DHTTYPE);

uint32_t delayMS;

void setup() {
  pinMode(5, OUTPUT);
  pinMode(6, OUTPUT);
  Serial.begin(9600);
  // Initialize device.
  dht.begin();
  Serial.println(F("DHTxx Unified Sensor Example"));
  // Print temperature sensor details.
  sensor_t sensor;
  dht.temperature().getSensor(&sensor);
  Serial.println(F("------------------------------------"));
  Serial.println(F("Temperature Sensor"));
  Serial.print  (F("Sensor Type: ")); Serial.println(sensor.name);
  Serial.print  (F("Driver Ver:  ")); Serial.println(sensor.version);
  Serial.print  (F("Unique ID:   ")); Serial.println(sensor.sensor_id);
  Serial.print  (F("Max Value:   ")); Serial.print(sensor.max_value); Serial.println(F("°C"));
  Serial.print  (F("Min Value:   ")); Serial.print(sensor.min_value); Serial.println(F("°C"));
  Serial.print  (F("Resolution:  ")); Serial.print(sensor.resolution); Serial.println(F("°C"));
  Serial.println(F("------------------------------------"));
  // Print humidity sensor details.
  dht.humidity().getSensor(&sensor);
  Serial.println(F("Humidity Sensor"));
  Serial.print  (F("Sensor Type: ")); Serial.println(sensor.name);
  Serial.print  (F("Driver Ver:  ")); Serial.println(sensor.version);
  Serial.print  (F("Unique ID:   ")); Serial.println(sensor.sensor_id);
  Serial.print  (F("Max Value:   ")); Serial.print(sensor.max_value); Serial.println(F("%"));
  Serial.print  (F("Min Value:   ")); Serial.print(sensor.min_value); Serial.println(F("%"));
  Serial.print  (F("Resolution:  ")); Serial.print(sensor.resolution); Serial.println(F("%"));
  Serial.println(F("------------------------------------"));
  // Set delay between sensor readings based on sensor details.
  delayMS = sensor.min_delay / 1000;
}
void Motor(int a)
{
  if(a==1)
  {
    digitalWrite(5,1);
    digitalWrite(6,0);
  }
  else
  {
    digitalWrite(5,1);
    digitalWrite(6,1);
  }
}
void loop() {
  double a ;
  // Delay between measurements.
  delay(delayMS);
  // Get temperature event and print its value.
  sensors_event_t event;
  dht.temperature().getEvent(&event);
  if (isnan(event.temperature)) {
    Serial.println(F("Error reading temperature!"));
  }
  else {
    Serial.print(F("Temperature: "));
    Serial.print(event.temperature);
    Serial.println(F("°C"));
  }
  a=event.temperature;
  // Get humidity event and print its value.
  dht.humidity().getEvent(&event);
  if (isnan(event.relative_humidity)) {
    Serial.println(F("Error reading humidity!"));
  }
  else {
    Serial.print(F("Humidity: "));
    Serial.print(event.relative_humidity);
    Serial.println(F("%"));
    if(a>=26)
    {
      
      tone(3,1000);
      delay(500);
      noTone(3);
      delay(500);
      Serial.print(a);
      Motor(1);
    }
    else
    {
      Motor(0);
    }
  }
}
![image](https://github.com/milane331/2021-03-2/blob/main/BEAF79A6-31C8-429C-9CD7-C8D63B64EA59.gif)

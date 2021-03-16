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
![image](https://github.com/milane331/2021-03-2/blob/main/6541D171-206C-46B8-BFFA-D1915A04078B.gif)

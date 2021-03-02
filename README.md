# 2021-03-2
2021/03/2
## 七段顯示器
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
}```
![image](https://github.com/milane331/2021-03-2/blob/main/BB37B161-8607-4D54-80F3-20C5DCBDECD1.jpeg)

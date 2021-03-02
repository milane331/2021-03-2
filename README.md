# 2021-03-2
2021/03/2
##七段顯示器
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

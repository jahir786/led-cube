# jahir-
Yes creats new one /made by Jahir & Ishani 
15 August
Smart-dastbin
ec"# hello-jahir1" >> README.md
git init
git add README.md
git commit -m "first commit"
git remote add origin https://github.com/jahirisha3/hello-jahir1.git
git push -u origin master
///

#include <Servo.h>   //servo library
Servo servo;     
int trigPin = 13;    
int echoPin = 11;   
int servoPin = 6;
int led= 10;
long duration, dist, average;   
long aver[3];   //array for average


void setup() {       
    Serial.begin(9600);
    servo.attach(servoPin);  
    pinMode(trigPin, OUTPUT);  
    pinMode(echoPin, INPUT);  
    servo.write(0);         //close cap on power on
    delay(100);
    servo.detach(); 
} 

void measure() {  
 digitalWrite(10,HIGH);
digitalWrite(trigPin, LOW);
delayMicroseconds(5);
digitalWrite(trigPin, HIGH);
delayMicroseconds(15);
digitalWrite(trigPin, LOW);
pinMode(echoPin, INPUT);
duration = pulseIn(echoPin, HIGH);
dist = (duration/2) / 29.1;    //obtain distance
}
void loop() { 
  for (int i=0;i<=2;i++) {   //average distance
    measure();               
   aver[i]=dist;            
    delay(10);              //delay between measurements
  }
 dist=(aver[0]+aver[1]+aver[2])/3;    

if ( dist<30 ) {
//Change distance as per your need
 servo.attach(servoPin);
  delay(1);
 servo.write(0);  
 delay(3000);       
 servo.write(150);    
 delay(3000);
 servo.detach();      
}
Serial.print(dist);
}

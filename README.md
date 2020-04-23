# Iot2
Smart Water Tank System
int time_US;
int distance_US;
int trigger=7;
int echo=6;
//int buzzer=10;
int relay=8;
void setup() {
  Serial.begin(9600);
  pinMode(echo,INPUT);
  pinMode(trigger,OUTPUT);
  //pinMode(buzzer,OUTPUT);
  pinMode(relay,OUTPUT);
}
void loop() {

  digitalWrite (trigger,0);
  delayMicroseconds(3) ;
  digitalWrite(trigger,1);
  delayMicroseconds(10);
  digitalWrite(trigger,0);
  time_US=pulseIn(echo,1);
  distance_US=time_US*.034/2;
  Serial.print("Distance==");
  Serial.print(distance_US);
  Serial.println();
  delay(1000);
  if (distance_US<3 ) 
  {
    //tone(buzzer,500);
    //delay (2000);
    //noTone (buzzer);
    digitalWrite(relay,LOW);
  }
  else if(distance_US>9){
    //tone(buzzer,1000);
    //delay(2000);
    //noTone(buzzer);
    digitalWrite(relay,HIGH);
  }
}

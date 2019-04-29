# my-scrapbook code

int motorPin1 = 7;
int motorPin2 = 8;
int motorPin3 = 9;
int motorPin4 = 10;
int trigPin = 12; 
int echoPin = 11;
long sure;
long uzaklik;
int trigPin1 = 5; 
int echoPin1 = 6;
long sure1;
long uzaklik1;
int trigPin2 = 4; 
int echoPin2 = 13;
long sure2;
long uzaklik2;
int trigPin3 = 2; 
int echoPin3 = 3;
long sure3;
long uzaklik3;

void setup() {
  pinMode(motorPin1, OUTPUT);
 pinMode(motorPin2, OUTPUT);
 pinMode(motorPin3, OUTPUT);
 pinMode(motorPin4, OUTPUT);

 pinMode(trigPin, OUTPUT); 
  pinMode(echoPin,INPUT); 
  Serial.begin(9600);
  
  pinMode(trigPin1, OUTPUT); 
  pinMode(echoPin1,INPUT); 
  Serial.begin(9600);

  pinMode(trigPin2, OUTPUT); 
  pinMode(echoPin2,INPUT); 
  Serial.begin(9600);

  pinMode(trigPin3, OUTPUT); 
  pinMode(echoPin3,INPUT); 
  Serial.begin(9600);
}

void loop()
{
  digitalWrite(trigPin, LOW); 
  delayMicroseconds(5);
  digitalWrite(trigPin, HIGH); 
  delayMicroseconds(10);
  digitalWrite(trigPin, LOW);  
  sure = pulseIn(echoPin, HIGH); 
  uzaklik= sure /29.1/2 ;

  digitalWrite(trigPin1, LOW); 
  delayMicroseconds(5);
  digitalWrite(trigPin1, HIGH); 
  delayMicroseconds(10);
  digitalWrite(trigPin1, LOW); 
  sure1 = pulseIn(echoPin1, HIGH); 
  uzaklik1= sure1 /29.1/2 ;

  digitalWrite(trigPin2, LOW); 
  delayMicroseconds(5);
  digitalWrite(trigPin2, HIGH); 
  delayMicroseconds(10);
  digitalWrite(trigPin2, LOW); 
  sure2 = pulseIn(echoPin2, HIGH); 
  uzaklik2= sure2 /29.1/2 ;

  digitalWrite(trigPin3, LOW); 
  delayMicroseconds(5);
  digitalWrite(trigPin3, HIGH); 
  delayMicroseconds(10);
  digitalWrite(trigPin3, LOW);  
  sure3 = pulseIn(echoPin3, HIGH); 
  uzaklik3= sure3 /29.1/2 ;

     if(uzaklik3 > 55)
           {
            delayMicroseconds(250000);
            digitalWrite(motorPin1, HIGH);
            digitalWrite(motorPin2, LOW);

            digitalWrite(motorPin3, HIGH);
            digitalWrite(motorPin4, LOW);
            if((uzaklik1 <15) && (uzaklik2 >15))
            {
               digitalWrite(motorPin1, LOW);
               digitalWrite(motorPin2, LOW);

               digitalWrite(motorPin3, LOW);
               digitalWrite(motorPin4, LOW);
               if(uzaklik2 >12)
               {
                
                digitalWrite(motorPin1, HIGH);
                digitalWrite(motorPin2, LOW);

                digitalWrite(motorPin3, LOW);
                digitalWrite(motorPin4, HIGH);
               }
            }
           }
           else if(uzaklik > 15)
           {
                delayMicroseconds(500000);
                digitalWrite(motorPin1, LOW);
                digitalWrite(motorPin2, HIGH);

                digitalWrite(motorPin3, LOW);
                digitalWrite(motorPin4, HIGH);
                if(uzaklik3<=15) 
                {
                  delayMicroseconds(500000);
                  digitalWrite(motorPin1, LOW);
                  digitalWrite(motorPin2, HIGH);

                  digitalWrite(motorPin3, HIGH);
                  digitalWrite(motorPin4, LOW);
                }
           }
           else
           {
                digitalWrite(motorPin1, LOW);
                digitalWrite(motorPin2, LOW);

                digitalWrite(motorPin3, LOW);
                digitalWrite(motorPin4, LOW);
           }
}

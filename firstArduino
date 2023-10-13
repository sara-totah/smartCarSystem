int printing ;
int MotorAndLed = 8;// LED is used to indicate that the motor is on
int OnButton = 7;

volatile int motorState = LOW; //Define the output status of the LED and the Motor


//seatbelt
 #define fsrpin A0
#define seatLed 5
#define buzzer 6
#define seatBeltButton 4
int force = 0;
int beltCount = 1;
volatile int beltState = LOW;


//light bulb detector
#define bulbLed 13
#define bulbSensor A1
#define bulbButton 2
#define bulbAlarmLed 9
int bulbCount = 1;
volatile int bulbState = LOW;

void changeBulbState(){
	bulbState = !bulbState;
  //checking if the bulb is working or not
      
      if(digitalRead(bulbButton) == HIGH){
     bulbCount++;
        
        /*Serial.print("Car Light button is pressed, bulb Count:");
       	Serial.print(bulbCount);*/
        //Serial.print('\n'); 
  
      //delay so the button won't be clicked twice
      }
      
      // checking if the car light bulb is on or not
      if (bulbCount % 2==0)
        		bulbState = HIGH;
          else 
    			bulbState = LOW;
        
       
     
     
    
}

//wheel Pressure sensor
#define wheelSensor A2
#define wheelLed 17

// Reverse Mode
#define reverseLed 18
#define driveLed 19
#define reverseButton 3
const int trigPin = 12;
const int echoPin = 11;
long duration;
int distanceCm;
int reverseState = LOW;
volatile int reverseCount = 1;

void changeReverseState(){
  //Reverse Mode
  
     
     reverseCount++;
        
        /*Serial.print("Car reverse button is pressed,reverse Count:");
       	Serial.print(reverseCount);*/
       
        //Serial.print('\n'); 
  
     
      
      // checking if the car REVERSE MODE IS ON
      if (reverseCount % 2==0){
        		reverseState = HIGH;
      			
      			
      } else{ 
    			reverseState = LOW;
        		
      }
}
void setup()
{
    Serial.begin(9600);
  // Turning the motor on
    pinMode(OnButton, INPUT); //Defining OnButton as an input to know when the car is switched on
    pinMode(MotorAndLed, OUTPUT); //Motor is an output
    
	
  ////////////////////////
  
  //force sensor setup --> seatbelt sensor
  
    pinMode(fsrpin, INPUT);
    pinMode(seatLed, OUTPUT);
    pinMode(buzzer, OUTPUT);
	pinMode(seatBeltButton, INPUT);

  //Light bulb setup --> damaged bulb sensor
  	attachInterrupt(0,changeBulbState,CHANGE);
  	pinMode(bulbButton, INPUT);
  	pinMode(bulbSensor, INPUT);
  	pinMode(bulbAlarmLed, OUTPUT);
  	pinMode(bulbLed, OUTPUT);
  	
 
	digitalWrite(bulbAlarmLed, 0);
  
  
  //Wheel Pressure sensor setup
  	
  	pinMode(wheelSensor, INPUT);
  	pinMode(wheelLed, OUTPUT);
  
  //Reverse Mode Sensor
  	attachInterrupt(1,changeReverseState,RISING);
  	pinMode(trigPin, OUTPUT);
	pinMode(echoPin, INPUT);
 
  	pinMode(reverseButton, INPUT);
  	pinMode(driveLed, OUTPUT);
    pinMode(reverseLed, OUTPUT);
}


void loop()
{ 
  
//  turning the motor on when clicking the push button
  if(digitalRead(OnButton) == LOW) 
  { 
    delay(10);
  if (digitalRead(OnButton) == LOW) //CONFIRM ONBUTTON IS PRESSED
    {
    while (digitalRead(OnButton)==LOW)
    { //WHILE THE BUTTON IS NOT PRESSED
             delay (10);
      
      // Checking if the seatBelt is inserted in the buckle
      if (digitalRead(seatBeltButton) == HIGH){
    beltCount++;
		
    	/*Serial.print("SeatBelt button is pressed, seatbelt Count:");
       	Serial.print(beltCount);
        Serial.print('\n'); */ 
        
        delay(15); //delay so the button won't be clicked twice
       
      }
      // if the button is clicked an even number of times, then the seatbeld is inserted in the buckle
        if (beltCount % 2==0)
        	beltState = HIGH;
        else
    		beltState = LOW;
    
      
       if (motorState == HIGH && analogRead (fsrpin) > 300 && beltState == LOW){ 
        //CHECK IF THE MOTOR IS ON && there is a weight on the seat && 
         //the seatbelt is not inserted
         
     	digitalWrite(seatLed, HIGH); //TURN ON THE LIGHT 
        digitalWrite(buzzer, HIGH);
         Serial.write("1");
         
           
        
      }
      else{
        digitalWrite (seatLed, LOW);
 		digitalWrite(buzzer, LOW);
      }
      
       // checking if the car light bulb is on or not
       if (motorState == HIGH && bulbState == HIGH && analogRead(bulbSensor) > 100 ){
      		
     		digitalWrite(bulbAlarmLed, LOW);
         	digitalWrite(bulbLed, HIGH);
         
      } else if (motorState == HIGH && bulbState == HIGH && analogRead(bulbSensor) < 100) {
       
     	digitalWrite(bulbAlarmLed, HIGH);
       	digitalWrite(bulbLed, LOW);
           Serial.write("2");
       }else{
       	digitalWrite(bulbAlarmLed, LOW);
      	digitalWrite(bulbLed, LOW);
       }
      //measuring the pressure of the wheel using force sensor
       if (motorState == HIGH && analogRead (wheelSensor) > 700){ 
        //CHECK IF THE MOTOR IS ON && there is no air in the wheel 
  
     	digitalWrite(wheelLed, HIGH); //TURN ON THE Wheel Alarm
          Serial.write("3");
        
      }
      else
     	 digitalWrite(wheelLed, LOW); //TURN OFF THE Wheel Alarm
      
      //Reverse Mode and Sensor
      
     digitalWrite(trigPin, LOW);
	delayMicroseconds(2);
	digitalWrite(trigPin, HIGH);
	delayMicroseconds(10);
	digitalWrite(trigPin, LOW);
	duration = pulseIn(echoPin, HIGH);
	distanceCm= duration*0.034/2;
	
      if (motorState == HIGH && reverseState == HIGH){
        digitalWrite(reverseLed, HIGH);
      digitalWrite(driveLed, LOW);
         
      }
      else if (motorState == HIGH && reverseState == LOW){
        digitalWrite(reverseLed, LOW);
      	digitalWrite(driveLed, HIGH);
      
      }
      if (motorState == HIGH && reverseState == HIGH && distanceCm < 150){
        digitalWrite(buzzer, HIGH);
         Serial.write("4");
                 

        
      }
      else {
        digitalWrite(buzzer, LOW);
      }
      }//end of while 
    
    
    
     while (digitalRead(OnButton)==LOW); //Confirm onButton is released
             motorState = !motorState;
  			 //Controls wether the LED is on or off
            digitalWrite(MotorAndLed, motorState);//Controls wether the Motor is on or off
             
             }   
  }
 
}            






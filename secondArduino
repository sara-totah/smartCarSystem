#include<LiquidCrystal.h>
char printingState;
LiquidCrystal lcd(12, 10, 5, 4, 3, 2);
void setup()
{
	lcd.begin(16, 2);
	Serial.begin(9600);
}

void loop()
{
 
 
  lcd.setCursor(0,0);
  if(Serial.available()){
    
     printingState = Serial.read();
    if(printingState == '1'){
       
    lcd.print("Put on                 ");
      lcd.setCursor(0,1); 
	 lcd.print("the seatbelt          ");
      
    }
   else if (printingState == '2'){
      
 	 lcd.print("fix the car          ");
     lcd.setCursor(0,1);
  	lcd.print("bulb please           ");
    }else if (printingState == '3'){
       
 	 lcd.print("blow your            ");
     lcd.setCursor(0,1);
  	 lcd.print("wheeeel SARA         ");
    }else if (printingState == '4'){
      
 	 lcd.print("  Youre gonna      ");
     lcd.setCursor(0,1);
  	 lcd.print("craaaaash             ");
    }
    
    
    
    
  } else {
  lcd.clear();
  }
  
   
}

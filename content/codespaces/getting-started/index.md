#include<LiquidCrystal.h>

LiquidCrystal lcd(13, 12, 5, 4, 3, 2);  // selección de pines para LCD
int conversor; // variable para adquidir datos del conversor entre 0-1023
float voltaje; // variable de conversión de conversor a voltaje
int dutty;   // variable para uso de pwm
int sw=7;
int btn=6;
void setup() {
  lcd.begin(16, 2);   // inicializa la LCD
  pinMode(sw,INPUT);
  pinMode(btn,INPUT);
}

void loop(){  
  if(digitalRead(sw)==HIGH){
  delay(100);
  conversor=analogRead(0);//lectura de canal 0
  voltaje=(conversor*5.0)/1023.0;// conversión a voltaje 
  dutty=conversor/4;
  // cambio de escala para dutty cicle
  analogWrite(11,dutty); 
  // envío de valor a pin
  lcd.setCursor(0,0); // selección de ubicación en LCD
  lcd.print("CAD:");  // Impresión de datos en LCD
  lcd.setCursor(7,0); // selección de ubicación en LCD
 lcd.print(conversor); // Impresión de datos en LCD
  lcd.setCursor(0,1); // selección de ubicación en LCD
  lcd.print("V:");    // Impresión de datos en LCD
  lcd.setCursor(3,1); // selección de ubicación en LCD
 lcd.print(voltaje,2); // Impresión de datos en LCD
  lcd.setCursor(8,1); // selección de ubicación en LCD
  lcd.print("PWM:"); // Impresión de datos en LCD
  lcd.setCursor(12,1); // selección de ubicación en LCD
  lcd.print((dutty*100)/255); // Impresión de datos en LCD
  delay(300); // tiempo de espera para siguiente lectura
  lcd.clear(); // borrar LCD
  } 
  else if(digitalRead(btn)==HIGH){
    delay(100);
  conversor=analogRead(0);//lectura de canal 0
  voltaje=(conversor*5.0)/1023.0;// conversión a voltaje 
  dutty=conversor/4;
  // cambio de escala para dutty cicle
  analogWrite(10,dutty); 
  // envío de valor a pin
  lcd.setCursor(0,0); // selección de ubicación en LCD
  lcd.print("CAD:");  // Impresión de datos en LCD
  lcd.setCursor(7,0); // selección de ubicación en LCD
 lcd.print(conversor); // Impresión de datos en LCD
  lcd.setCursor(0,1); // selección de ubicación en LCD
  lcd.print("V:");    // Impresión de datos en LCD
  lcd.setCursor(3,1); // selección de ubicación en LCD
 lcd.print(voltaje,2); // Impresión de datos en LCD
  lcd.setCursor(8,1); // selección de ubicación en LCD
  lcd.print("PWM:"); // Impresión de datos en LCD
  lcd.setCursor(12,1); // selección de ubicación en LCD
  lcd.print((dutty*100)/255); // Impresión de datos en LCD
  delay(300); // tiempo de espera para siguiente lectura
  lcd.clear(); // borrar LCD
    
    }
}

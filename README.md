# Examen2

























1:
#include <Wire.h>
#include <LiquidCrystal_I2C.h>

LiquidCrystal_I2C lcd(0x27, 16, 2);  

const int buzzerPin = 9;  


const int NOTE_C4 = 261;
const int NOTE_D4 = 293;
const int NOTE_E4 = 329;
const int NOTE_F4 = 349;
const int NOTE_G4 = 392;
const int NOTE_A4 = 440;
const int NOTE_B4 = 494;


int melody[] = {
  NOTE_C4, NOTE_D4, NOTE_E4, NOTE_F4, NOTE_G4, NOTE_A4, NOTE_B4,
  NOTE_C4, NOTE_D4, NOTE_E4, NOTE_F4, NOTE_G4, NOTE_A4, NOTE_B4,NOTE_C4, NOTE_D4, NOTE_E4, NOTE_F4, NOTE_G4, NOTE_A4, NOTE_B4,
  NOTE_C4, NOTE_D4, NOTE_E4, NOTE_F4, NOTE_G4, NOTE_A4, NOTE_B4,NOTE_C4, NOTE_D4, NOTE_E4, NOTE_F4, NOTE_G4, NOTE_A4, NOTE_B4,
  NOTE_C4, NOTE_D4, NOTE_E4, NOTE_F4, NOTE_G4, NOTE_A4, NOTE_B4,
 
};


char lyrics[] = "titutiititutututititiiii :3";


int noteDurations[] = {
  250, 250, 250, 250, 250, 250, 250,
  250, 250, 250, 250, 250, 250, 250,
  
};

void setup() {
  lcd.init();                      
  lcd.backlight();                 
  lcd.setCursor(0, 0);            
  lcd.print("titutotidlti:");
  lcd.setCursor(0, 1);            
  lcd.print(lyrics);

  pinMode(buzzerPin, OUTPUT);
}

void loop() {
  
  for (int i = 0; i < sizeof(melody) / sizeof(melody[0]); i++) {
    int noteDuration = noteDurations[i];
    tone(buzzerPin, melody[i], noteDuration);

    
    lcd.setCursor(0, 1);
    lcd.print("                "); 
    lcd.setCursor(0, 1);
    lcd.print(lyrics[i]);

    delay(noteDuration);
    noTone(buzzerPin);
  }
 
  delay(200); 
}



1:
#include <LiquidCrystal_I2C.h>
#include <Servo.h>
//librerias//
#DEFINE	 tmp A0
#DEFINE ldr A1
#DEFINE amarillo 3
#DEFINE rojo 9
#DEFINE boton 11
#DEFINE blanco 2

void setup()
{ 
  pinMode( rojo    , OUTPUT);
  pinMode( boton   , INPUT);
  pinMode(  blanco, OUTPUT);
  pinMode(  amarillo, OUTPUT);
  pinMode(  tmp   , INPUT);
  pinMode(  ldr , INPUT);
     
}

void loop()
{
 
 //void procedimiento
//DEFINIMOS funciones

// 200
 //igitalWrite(9,HIGH); // procedimiento
 //nt a = digitalRead();// funcion
//delay( 200);
//analogRead();
//analogWrite();
//map( luz , 0 , 222 , 0 , 100);
}
#define tmp       A0
#define ldr       A3
#define boton     3
#define verde     9
#define amarillo  10
#define azul      11

void setup()
{
  pinMode( tmp      , INPUT);
  pinMode( ldr      , INPUT);
  pinMode( boton    , INPUT);
  pinMode( verde    , OUTPUT);
  pinMode( amarillo , OUTPUT);
  pinMode( azul     , OUTPUT);
}
Gonzalo Consorti20:02
.
.
.
.
#include <Servo.h>
#include <LiquidCrystal.h>
/*************************/
/* importamos bibliotecas
/*************************/

#define tmp       A0
#define ldr       A3
#define boton     3
#define verde     9
#define amarillo  10
#define azul      11
/***********************/
/* definimos variables
/***********************/

void setup()
{
  pinMode( tmp      , INPUT);
  pinMode( ldr      , INPUT);
  pinMode( boton    , INPUT);
  pinMode( verde    , OUTPUT);
  pinMode( amarillo , OUTPUT);
  pinMode( azul     , OUTPUT);
Serial.begin(9600);
}

void loop()
{	
  //prenderLed( amarillo , 500  );
  //prenderLed( verde    , 1000 );
  //prenderLed( azul     , 1000 );
  
  int   t  = indicadorLuz(  ldr );
  float t2 = indicadorTemp( tmp );
t2 = leerSensorX( tmp , 't' );
  t  = leerSensorX( ldr , 'l' );
  
  Serial.println( t );	
}

/**********************/
/* definimos funciones
/**********************/

void prenderLed( int led , int t) //no devuelve nada(void) = procedimiento
{
digitalWrite( led , HIGH );
  	delay( t );
  	digitalWrite( led , LOW  );
  	delay( t );
}

float leerSensorX( int pin , char tipo )
{
float valor=0;
  /*( tipo == 't' )
  {	
    valor = indicadorTemp( pin );
  }else if( tipo == 'l' ){
    valor = indicadorLuz( pin );
  }*/
  switch()
  {
    case 't':
    break
      case 't':
    valor = indicadorLuz (pin);
    break;
    default:
    //case 'm':
    //valor = indicadorMovimiento (pin);
    Serial.printl("no es pecifcaste"};
  }
  
  return valor;
}
float indicadorTemp( int pin)
{
  int dato = analogRead( pin );
  float volt = (5.0 / 1024 * dato);
  
  float temperatura = volt * 100 - 50;
   
  return temperatura;  
}
int indicadorLuz(int pin)  // funcion que devuelve datos(int) 
{
	int valor = analogRead( pin );
  	//Serial.println( valor );
  	int luz = map( valor , 1 , 310 , 0 , 100);	
  	
	return luz;
}

2:

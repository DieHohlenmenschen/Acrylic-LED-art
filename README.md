Acrylic-LED-art
===============

Acrylic LED art

int receiverpin = 11;
#include <IRremote.h>
IRrecv irrecv(11);
decode_results results;

int counter  ;
float r;
float g;
float b;

void setup (){
  irrecv.enableIRIn();
  // 2=810 3=410 4=C10 5=210 6=A10 7=610  compare it to 0xnumber 
int RED = 3;
int GREEN = 2;
int BLUE = 1;


pinMode( 6,OUTPUT);
pinMode( 5,OUTPUT);
pinMode( 3,OUTPUT);
Serial.begin(9600);

}
void ledWHITE () {
  r=255;
 g= 255;
 b= 255;
 analogWrite(3, r);
 analogWrite(5, g);
 analogWrite(6, b);
}
//////////////////////////////
void ledRED () {
 r= 255;
g= 0;
 b= 0;
 analogWrite(6, r);
 analogWrite(5, g);
 analogWrite(3, b);
}
//////////////////////////////
void ledORANGE () {
 r= 0;
 g= 69;
 b= 255;
 analogWrite(3, b);
 analogWrite(5, g);
 analogWrite(6, r);
}
//////////////////////////////
void ledYELLOW  () {
  r= 0;
  g= 255;
  b= 255;
 analogWrite(3, b);
 analogWrite(5, g);
 analogWrite(6, r);
}
//////////////////////////////
void ledGREEN  () {
  r= 0;
  g= 255;
  b= 0;
 analogWrite(3, b);
 analogWrite(5, g);
 analogWrite(6, r);
}
//////////////////////////////
void ledBLUE () {
  r= 0;
  g= 0;
  b= 255;
 analogWrite(3, b);
 analogWrite(5, g);
 analogWrite(6, r);
 }
//////////////////////////////
void ledPURPLE () {
  r= 255;
  g= 0;
 b= 255;
 analogWrite(3, b);
 analogWrite(5, g);
 analogWrite(6, r);
}
//////////////////////////////
void ledMAGENTA () {
 r= 252;
  g= 96;
  b= 231;
 analogWrite(3, b);
 analogWrite(5, g);
 analogWrite(6, r);
}
//////////////////////////////
void ledCYAN () {
  r= 36;
  g= 236;
  b= 250;
 analogWrite(3, b);
 analogWrite(5, g);
 analogWrite(6, r);
}
//////////////////////////////
void ledPINK () {
  r= 255;
  g= 10;
  b= 153;
 analogWrite(3, b);
 analogWrite(5, g);
 analogWrite(6, r);
}
//////////////////////////////
void OFF () {
  r= 0;
  g= 0;
  b= 0;
 analogWrite(3, b);
 analogWrite(5, g);
 analogWrite(6, r);
}
//////////////////////////////
void ON () {

 analogWrite(3, b);
 analogWrite(5, g);
 analogWrite(6, r);
}
//////////////////////////////
void FLICKR() {
 float f= random(.7,2);
  
  
 analogWrite(3, b*f);
 analogWrite(5, g*f);
 analogWrite(6, r*f);
 delay(75);

}
///////////////////////////////











void loop () {
if (irrecv.decode(&results)){
  
 if (results.value==0x10){
   ledWHITE();
 }

else  if (results.value==0x810){
   ledRED();
  }
  
  
  else if (results.value==0x410){
    ledORANGE();
  }
  
  
  else if (results.value==0xC10){
   ledYELLOW ();
  }
  
  else if (results.value==0x210){
   ledGREEN ();
  }
  
  else if (results.value==0xA10){
   ledBLUE();
  }
  
  else if (results.value==0x610){
   ledPURPLE ();
  }
  
  else if (results.value==0xE10){
   ledMAGENTA ();
  }
  
  else if (results.value==0x910){
   ledCYAN ();
  }

 else if (results.value==0x110){
   ledPINK ();
  }
//power

else if (results.value==0xA90){
if (counter==1){
  ON();
  delay(100);
  counter++;
}
 else {
  OFF();
  delay(100);
  counter = 0;
 }
}



  else if (results.value==0x290){ 
    
    FLICKR();
}



  

  
   Serial.print(results.value,HEX); 
Serial.print(" ");
irrecv.resume();
  

  
  for (int z =0; z<2; z++){
    irrecv.resume();
  }

}




}










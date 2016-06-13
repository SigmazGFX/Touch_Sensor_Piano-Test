#include <ADCTouch.h>

#define NOTE_C  262
#define NOTE_D  294
#define NOTE_E  330
#define NOTE_F  349
#define NOTE_G  392
 
int ref0, ref1, ref2, ref3, ref4;       //reference values to remove offset
int speakerPin = 9; //Depends on which pin is used for the speaker
 
void setup()
{
    // No pins to setup, pins can still be used regularly, although it will affect readings
 
    Serial.begin(9600);
 
    ref0 = ADCTouch.read(A0, 500);    //create reference values 
    ref1 = ADCTouch.read(A1, 500);
    ref2 = ADCTouch.read(A2, 500);
    ref3 = ADCTouch.read(A3, 500);
    ref4 = ADCTouch.read(A4, 500);
    
    pinMode(speakerPin, OUTPUT);
}
 
void loop()
{
    int thumb = ADCTouch.read(A0);   
    int index = ADCTouch.read(A1);
    int middle = ADCTouch.read(A2);
    int ring = ADCTouch.read(A3);
    int pinky = ADCTouch.read(A4);  
 
    thumb -= ref0;       //remove offset
    index -= ref1;  
    middle -= ref2;  
    ring -= ref3;  
    pinky -= ref4;  
    
    if (thumb > 50) { 
      if (index > 60) 
        { Serial.print("A"); //TI  (thumb and index)
          tone(9, NOTE_C + NOTE_D);
        }   
      else if (middle > 60)
        { Serial.print("B"); //TM (thumb and middle)
          tone(9, NOTE_C + NOTE_E);
        }          
      else if (ring > 60)
        { Serial.print("C"); //TR (thumb and ring)
          tone(9, NOTE_C + NOTE_F);
        }          
      else if (pinky > 50)
        { Serial.print("D"); //TP (thumb and pinky)
          tone(9, NOTE_C + NOTE_G);
        }          
      else
        {  Serial.print("T"); 
           tone(9, NOTE_C);
        }
    }
    else if (index > 60){ 
      if (middle > 60)
        { Serial.print("E"); //IM (index and middle)
          tone(9, NOTE_D + NOTE_E);
        }          
      else if (ring > 60)
        { Serial.print ("F"); //IR (index and ring)
          tone(9, NOTE_D + NOTE_F);
        }          
      else if (pinky > 50)
        { Serial.print("G"); //IP (index and pinky)
          tone(9, NOTE_D + NOTE_G);
        }          
      else
        {  Serial.print("I");
           tone(9, NOTE_D);
        }
    }

    else if (middle > 60){
      if (ring > 60)
        { Serial.print("H"); //MR (middle and ring)
          tone(9, NOTE_E + NOTE_F);
        }          
      else if (pinky > 50)
        { Serial.print("J"); //MP (middle and pinky)
          tone(9, NOTE_E + NOTE_G);
        }          
      else
        {  Serial.print("M");
           tone(9, NOTE_E);
        }
    }
    
    else if (ring > 60){
      if (pinky > 50)
        { Serial.print("K"); //RP (ring and pinky)
          tone(9, NOTE_F + NOTE_G);
        }          
      else
        {  Serial.print("R");
           tone(9, NOTE_F);
        }
    }

    else if (pinky > 50)
      { Serial.print("P");     
        tone(9, NOTE_G);
      }
    else 
      { Serial.print("N");
        noTone(9);
      }
     
    delay(10);

}

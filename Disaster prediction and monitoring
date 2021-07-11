#include <iostream>
#include <stdlib.h>
#include "mbed.h"
#include <stdio.h>
#include <time.h>
#include "C12832.h"
#include "Sht31.h"
int button;
bool check;
int p;
int c=0;
C12832 lcd(SPI_MOSI, SPI_SCK, SPI_MISO, p8, p11);
Sht31 sht31(I2C_SDA, I2C_SCL);

DigitalOut green(p20);
DigitalOut white(p21);
DigitalOut red(p22);
Ticker t1;
Timeout t2;
InterruptIn btn(BUTTON1);
InterruptIn reversebtn(p24);
 int i, s,f,l;
void starting(){
    
     lcd.locate(30, 0);
       lcd.printf("WELCOME TO");
       lcd.locate(10, 10);
       lcd.printf("IOT Based Disaster");
       lcd.locate(3, 20);
       lcd.printf(" Prediction And Monitoring");
       wait(5);
       lcd.cls();

}

void topics(){
    check= true;
   for (i = -5; i <25 ; i++) { // scrolling text
        lcd.locate(3, i);
       lcd.printf("TOPIC_1: Lightnings");
        wait(0.2);
        lcd.cls();
        i = i + 1;
        white=!white;
       p=1;
    }   
    
     for (i = -5; i <25 ; i++) { // scrolling text
        lcd.locate(10, i);
       lcd.printf("TOPIC_2: Floods");
        wait(0.2);
        lcd.cls();
        i = i + 1;
         white=!white;
        p=2;
    }
    
   for (i = -5; i <25 ; i++) { // scrolling text
        lcd.locate(10, i);
       lcd.printf("TOPIC_3: Landslides");
        wait(0.2);
        lcd.cls();
        i = i + 1;
         white=!white;
         p=3;
    } 
    
   for (i = -5; i <25 ; i++) { // scrolling text
        lcd.locate(10, i);
       lcd.printf("TOPIC_4: Volcano Eruption");
        wait(0.2);
        lcd.cls();
        i = i + 1;
         white=!white;
         p=4;
    } 
     
    
    for (i = -5; i <25 ; i++) { // scrolling text
        lcd.locate(10, i);
       lcd.printf("TOPIC_5: Earthquakes");
        wait(0.2);
        lcd.cls();
        i = i + 1;
         white=!white;
         p=5;
    } 
      
    
    
    
}
void temp_local_time(){
    check=true; p=4;
        time_t rawtime;
   struct tm *info;
    float temp = sht31.readTemperature();
      lcd.set_auto_up(0);
   time( &rawtime );
   info = localtime( &rawtime );
  // printf("Current local time and date: %s", asctime(info));
        lcd.locate(2, 3);
    lcd.printf(" %s", asctime(info));
    lcd.locate(5, 15);
       lcd.printf("Local Temperature: %.2fC ", temp);
        wait(3);
        lcd.cls();
         white=!white;
   }
   
void reading(){
    if(check==true and (p==1 or p==4)){
        printf("content\n");
printf("............................................\n");
        printf("Lightning is an electrical discharge btwn cloud and ground\n");
        printf("There are three common types of lightning: cloud to ground\n");
        printf("cloud to cloud and cloud to air. Cloud to ground lightning is the most dangerous\n");
        printf("Karongi Site Lightning: 123KV\n");
        printf("Status: LOW\n");
        printf("Kirehe Site Lightning: 501.2KV\n");
        printf("Status: HIGH\n");
        printf("..................\t\t.....................\n");
         p=0;
         printf("\n\n\n\n\n\n\n\n\n\n\n\n\n");
         green=1;
   
}  
    if(check==true and p==2){
printf("content\n");
printf("............................................\n");  
printf("Flood is an overflow of water that submerges land that is usually dry\n");
printf("Floods are an area of study in the discipline of hydrology");
        printf("Burera Site Floods level: 38.9mm\n");
        printf("Status: HIGH\n");
        printf("Karongi Site Floods level: 88.9mm\n");
        printf("Status: Very HIGH\n");
        printf("..................\t\t.....................\n");
       p=0;
     printf("\n\n\n\n\n\n\n\n\n\n\n\n\n\n");
     green=1;
} 

if(check==true and p==3){
printf("content\n");
printf("............................................\n");
printf("Landslide, the movement downslope of a mass of rock, debris, earth, or soil\n");
printf("Hazard level at Rulindo:60/100\n");
printf("Status:Intermediate\n");
printf("Hazard level at Rubavu:40/100\n");
printf("Status:LOW\n");
printf("..................\t\t.....................\n");
p=0;
printf("\n\n\n\n\n\n\n\n\n\n\n\n\n\n");
green=1;

}

if(check==true and p==4){
printf("content\n");
printf("............................................\n");
printf("Volcanic eruptions happen when lava and gas are discharged from a volcanic vent.\n");
printf("Volcanic eruptions often cause temporary food shortages and volcanic ash landslides called Laharn");
printf("Mount Nyiragongo erupted in the Democratic Republic of Congo on May 22\n");
printf("killed 31 people and forcing 30,000 to flee their homes\n");
printf("Volcanic Alert Level:4\n");
printf("..................\t\t.....................\n");
p=0;
printf("\n\n\n\n\n\n\n\n\n\n\n\n\n\n");
green=1;

}

if(check==true and p==5){
printf("content\n");
printf("............................................\n");
printf("An earthquake is the shaking of the surface of the Earth resulting from a sudden release of\n");
printf("energy in the Earth's lithosphere that creates seismic waves.\n");
printf("Earthquake occured at Rubavu:40/100\n");
printf("Slight damage to buildings and other structures.\n");
printf("Status: 7.0 earthquake");
printf("..................\t\t.....................\n");
p=0;
printf("\n\n\n\n\n\n\n\n\n\n\n\n\n\n");
green=1;

}




}   

int main () {
    startup:
    printf("\t\t****Press Button To Read****\n");
    printf("\n");
    btn.rise(callback(&reading));
    starting();
   while (1){
  temp_local_time();
   wait_ms(0.2);
   topics();
   button=btn;
   if(button==1){
       lcd.cls();
    lcd.locate(5, 15);
       lcd.printf("hello");   
       
   }
    wait_ms(1);
    
          int reversecount=reversebtn;
       if(reversecount==1){
           c=c+1;
       printf("count is:%d\n",c);
       if(c==3){
          printf("Direction changed"); 
        
       }
       if(c==5){
          printf("Resert to factory"); 
          c=0;
          red=!red;
          wait(10);
          goto startup;
       }
       }
        wait(1);
    }

}

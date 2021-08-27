#include <SoftwareSerial.h>

SoftwareSerial RF(7, 6); // RX, TX

char input[12];        

int count = 0; 

String tag1 = "16004D464A57";

String tag2 = "2C00FF8C401F"; 

String tag3 = "15008BFA4723"; 

String tag4 = "15008DBE486E";

String t;

int led = 13;


bool a, b, c, d = false;


int a1, b1, c1, d1 = 0;


unsigned long previousMillis = 0;

unsigned long currentMillis = 0;

const long interval = 3600000;


unsigned long previousMillis1 = 0;

unsigned long currentMillis1 = 0;

const long interval1 = 60000;


int hr = 0;

int counT = 0;


void setup()

{

  Serial.begin(9600);   // START SERIAL AT BAUD RATE OF 9600 BITS/SEC   

  RF.begin(9600);

  pinMode(led, OUTPUT);

  Serial.println("Ready");

}


void loop()

{   

  currentMillis = millis();

  currentMillis1 = millis(); 

  if (currentMillis - previousMillis >= interval) 

  {

    previousMillis = currentMillis;

    hr++;

  }

  if (currentMillis1 - previousMillis1 >= interval1) 

  {

    previousMillis1 = currentMillis1;

    Serial.print("Number Of Days : ");

    Serial.print(counT);

    Serial.print("     ");

    Serial.print("Card 1 Count : ");

    Serial.print(a1);

    Serial.print("     ");

    Serial.print("Card 2 Count : ");

    Serial.print(b1);

    Serial.print("     ");

    Serial.print("Card 3 Count : ");

    Serial.print(c1);

    Serial.print("     ");

    Serial.print("Card 4 Count : ");

    Serial.println(d1);

  }  

  if(hr == 24)

  {

    counT++;

    if(a)

    {

      a1++;

    }

    if(b)

    {

      b1++;

    }

    if(c)

    {

      c1++; 

    }

    if(d)

    {

      d1++; 

    }

    a = false;

    b = false;

    c = false;

    d = false;

    hr = 0;

  }

  if(RF.available())

  {

    count = 0;      // Reset the counter to zero

    while(RF.available() && count < 12)

    {

      input[count] = RF.read();

      count++;          // increment counter

      delay(5);

    }

//    Serial.println("");

     // PRINTING RFID TAG           

    for(int i=0;i<12;i++)

    {

//     Serial.print(input[i]);

     t = (t + input[i]);

    }

//    Serial.print("    ");

    for(int i=0;i<12;i++)

    {

     input[i] = 'F';

//     Serial.print(input[i]);

    }

//    Serial.print("    ");

//    Serial.print("t : ");

//    Serial.print(t);

//    Serial.print("    ");

    if(t == tag1)

    {

      blik();

      Serial.println("Attendance Granted For Card1");

      a = true;

    }

    if(t == tag2)

    {

      blik();

      Serial.println("Attendance Granted For Card2");

      b = true;

    }

    if(t == tag3)

    {

      blik();

      Serial.println("Attendance Granted For Card3");

      c = true;

    }

    if(t == tag4)

    {

      blik();

      Serial.println("Attendance Granted For Card4");

      d = true;

    }

    t = "";

//  Serial.print("Tag 1 : ");

//  Serial.print(tag1);

//  Serial.print("    ");

//  Serial.print("Tag 2 : ");

//  Serial.print(tag2);

//  Serial.print("    ");

//  Serial.print("t : ");

//  Serial.println(t);

  }

}

void blik()

{

  digitalWrite(led, HIGH);   // turn the LED on (HIGH is the voltage level)

  delay(100);                       // wait for a second

  digitalWrite(led, LOW);    // turn the LED off by making the voltage LOW

  delay(200);

}

//# preference-code
//The custom made code written solely by the competition entrant in order to quantify odor preferences in a novel apparatus.
#include <SPI.h>
#include <SD.h>

int analog1 = 1;
int analog2 = 2;
int analog3 = 3;
int analog4 = 4;
int analog5 = 5;
int analogVal1 = 0;
int analogVal2 = 0;
int analogVal3 = 0;
int analogVal4 = 0;
int analogVal5 = 0;
int ledreset = 9;
int led1 = 39;
int led2 = 37;
int led3 = 35;
int led4 = 33;
int led5 = 31;
int sdpin = 10;
const char compile_date[] = "__DATE__" "__TIME__";
const char filename[] = "odordata.txt";
unsigned long start, finished, elapsed;

void setup()
{
  pinMode(ledreset, OUTPUT);
  digitalWrite(ledreset, HIGH);
  delay(500);
  digitalWrite(ledreset, LOW);
  Serial.begin(9600);
  Serial.println("Initializing Card");
  pinMode(sdpin, OUTPUT);
  if(!SD.begin(sdpin))
  {
    Serial.println("Card Failed");
  }
  else
  {
  Serial.println("Card Ready");
  }
  Serial.println(compile_date);
  File dataFile = SD.open(filename, FILE_WRITE);
  if(dataFile)
  {
    dataFile.println(compile_date);
    dataFile.close();
  }
  pinMode(led1, OUTPUT);
  pinMode(led2, OUTPUT);
  pinMode(led3, OUTPUT);
  pinMode(led4, OUTPUT);
  pinMode(led5, OUTPUT);
}

void loop()
{
  analogVal1 = analogRead(analog1);
  analogVal2 = analogRead(analog2);
  analogVal3 = analogRead(analog3);
  analogVal4 = analogRead(analog4);
  analogVal5 = analogRead(analog5);
  if(analogVal1 > 500)
  {
    start = millis();
    loop1();
    finished = millis();
    elapsed = finished - start;
    Serial.print("\t");
    Serial.println(elapsed);
    File dataFile = SD.open(filename, FILE_WRITE);
    if(dataFile);
    {
      dataFile.print("\t");
      dataFile.println(elapsed);
      dataFile.close();
    }
  }
  digitalWrite(led1, LOW);
  if(analogVal2 > 500)
  {
    start = millis();
    loop2();
    finished = millis();
    elapsed = finished - start;
    Serial.print("\t");
    Serial.println(elapsed);
    File dataFile = SD.open(filename, FILE_WRITE);
    if(dataFile);
    {
      dataFile.print("\t");
      dataFile.println(elapsed);
      dataFile.close();
    }
  }
  digitalWrite(led2, LOW);
  if(analogVal3 > 500)
  {
    start = millis();
    loop3();
    finished = millis();
    elapsed = finished - start;
    Serial.print("\t");
    Serial.println(elapsed);
    File dataFile = SD.open(filename, FILE_WRITE);
    if(dataFile);
    {
      dataFile.print("\t");
      dataFile.println(elapsed);
      dataFile.close();
    }
  }
  digitalWrite(led3, LOW);
  if(analogVal4 > 500)
  {
    start = millis();
    loop4();
    finished = millis();
    elapsed = finished - start;
    Serial.print("\t");
    Serial.println(elapsed);
    File dataFile = SD.open(filename, FILE_WRITE);
    if(dataFile);
    {
      dataFile.print("\t");
      dataFile.println(elapsed);
      dataFile.close();
    }
  }
  digitalWrite(led4, LOW);
  if(analogVal5 > 500)
  {
    start = millis();
    loop5();
    finished = millis();
    elapsed = finished - start;
    Serial.print("\t");
    Serial.println(elapsed);
    File dataFile = SD.open(filename, FILE_WRITE);
    if(dataFile);
    {
      dataFile.print("\t");
      dataFile.println(elapsed);
      dataFile.close();
    }
  }
  digitalWrite(led5, LOW);
}

void loop1()
{
  digitalWrite(led1, HIGH);
  Serial.print("1");
  String dataString1 = "1";
  File dataFile = SD.open(filename, FILE_WRITE);
  if(dataFile)
  {
    dataFile.print(dataString1);
    dataFile.close();
  }
  delay(10);
}

void loop2()
{
  digitalWrite(led2, HIGH);
  Serial.print("2");
  String dataString2 = "2";
  File dataFile = SD.open(filename, FILE_WRITE);
  if(dataFile)
  {
    dataFile.print(dataString2);;
    dataFile.close();
  }
  delay(10);
}

void loop3()
{
  digitalWrite(led3, HIGH);
  Serial.print("3");
  String dataString3 = "3";
  File dataFile = SD.open(filename, FILE_WRITE);
  if(dataFile)
  {
    dataFile.print(dataString3);
    dataFile.close();
  }
  delay(10);
}

void loop4()
{
  digitalWrite(led4, HIGH);
  Serial.print("4");
  String dataString4 = "4";
  File dataFile = SD.open(filename, FILE_WRITE);
  if(dataFile)
  {
    dataFile.print(dataString4);
    dataFile.close();
  }
  delay(10);
}

void loop5()
{
  digitalWrite(led5, HIGH);
  Serial.print("5");
  String dataString5 = "5";
  File dataFile = SD.open(filename, FILE_WRITE);
  if(dataFile)
  {
    dataFile.print(dataString5);
    dataFile.close();
  }
  delay(10);
}

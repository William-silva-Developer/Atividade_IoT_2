# ` Integração do projeto com o Node-Red ` 

![Badge em Desenvolvimento](http://img.shields.io/static/v1?label=STATUS&message=EM%20DESENVOLVIMENTO&color=GREEN&style=for-the-badge)

**Equipe:**
- [Amanda Rodrigues](https://github.com/amanda-rosa)
- [Williamis Silva](https://github.com/William-silva-Developer)

## Descrição da integração do projeto

  O nosso projeto de trava elétrica no momento é uma versão beta, que está em teste para a versão final.


## Construção do dashboard

**Imagens do dashboard**



**Imagens dos flows**



**Json exportado do Node-red**

## Práticas realizadas com sucesso

### Funcionamento do Servo Motor e do Buzzer:

**Código usado para o funcionamento do Servo Motor e do Buzzer:**
~~~C++
#include <Servo.h>
 
#define SERVO 11 // Porta Digital 11 PWM
 
Servo s; // Variável Servo
int pos; // Posição Servo
int buzzer = 10;
 
void setup ()
{
  s.attach(SERVO);
  Serial.begin(9600);
  s.write(0); // Inicia motor posição zero
  pinMode(buzzer, OUTPUT);
}
 
void loop()
{
  tone(buzzer,1500);
  delay(500);

  noTone(buzzer);
  delay(500);
 
  for(pos = 0; pos < 90; pos++)
  {
    s.write(pos);
  delay(15);
  }
delay(1000);
  for(pos = 90; pos >= 0; pos--)
  {
    s.write(pos);
    delay(10);
  }
}
~~~
#### Imagens

<div>
  <img style={margin="8px"} src="https://user-images.githubusercontent.com/98723501/175783436-45e650cf-baa5-436e-9145-fa5f10cd898d.jpeg" alt=Servo Motor width="500"  />
  <img src="https://user-images.githubusercontent.com/98723501/175783952-c09da35e-b816-4b7e-bc95-48576f67daa4.jpeg" alt="Servo motor e o Buzzer" width="500"/>
</div>

#### Portas usadas pelo Servo motor
- Fio marrom com GND;
- Fio vermelho no 5v;
- Fio laranja no D11
#### Buzzer
- Resistor 220 ohms;
- Fio vermelho no pino digital 11;
- Fio preto no GND


**Código para o funcionamento do sensor biométrico:**
Este código ainda não está em conjunto com o do Servo motor.
~~~C++
/*****************
  This is an example sketch for our optical Fingerprint sensor

  Designed specifically to work with the Adafruit BMP085 Breakout
  ----> http://www.adafruit.com/products/751

  These displays use TTL Serial to communicate, 2 pins are required to
  interface
  Adafruit invests time and resources providing this open source code,
  please support Adafruit and open-source hardware by purchasing
  products from Adafruit!

  Written by Limor Fried/Ladyada for Adafruit Industries.
  BSD license, all text above must be included in any redistribution
 ******************/


#include <Adafruit_Fingerprint.h>


#if (defined(_AVR) || defined(ESP8266)) && !defined(AVR_ATmega2560_)
// For UNO and others without hardware serial, we must use software serial...
// pin #2 is IN from sensor (GREEN wire)
// pin #3 is OUT from arduino  (WHITE wire)
// Set up the serial port to use softwareserial..
SoftwareSerial mySerial(2, 3);

#else
// On Leonardo/M0/etc, others with hardware serial, use hardware serial!
// #0 is green wire, #1 is white
#define mySerial Serial1

#endif


Adafruit_Fingerprint finger = Adafruit_Fingerprint(&mySerial);

void setup()
{
  Serial.begin(9600);
  while (!Serial);  // For Yun/Leo/Micro/Zero/...
  delay(100);
  Serial.println("\n\nAdafruit finger detect test");

  // set the data rate for the sensor serial port
  finger.begin(57600);
  delay(5);
  if (finger.verifyPassword()) {
    Serial.println("Found fingerprint sensor!");
  } else {
    Serial.println("Did not find fingerprint sensor :(");
    while (1) { delay(1); }
  }

  Serial.println(F("Reading sensor parameters"));
  finger.getParameters();
  Serial.print(F("Status: 0x")); Serial.println(finger.status_reg, HEX);
  Serial.print(F("Sys ID: 0x")); Serial.println(finger.system_id, HEX);
  Serial.print(F("Capacity: ")); Serial.println(finger.capacity);
  Serial.print(F("Security level: ")); Serial.println(finger.security_level);
  Serial.print(F("Device address: ")); Serial.println(finger.device_addr, HEX);
  Serial.print(F("Packet len: ")); Serial.println(finger.packet_len);
  Serial.print(F("Baud rate: ")); Serial.println(finger.baud_rate);

  finger.getTemplateCount();

  if (finger.templateCount == 0) {
    Serial.print("Sensor doesn't contain any fingerprint data. Please run the 'enroll' example.");
  }
  else {
    Serial.println("Waiting for valid finger...");
      Serial.print("Sensor contains "); Serial.print(finger.templateCount); Serial.println(" templates");
  }
}

void loop()                     // run over and over again
{
  getFingerprintID();
  delay(50);            //don't ned to run this at full speed.
}

uint8_t getFingerprintID() {
  uint8_t p = finger.getImage();
  switch (p) {
    case FINGERPRINT_OK:
      Serial.println("Image taken");
      break;
    case FINGERPRINT_NOFINGER:
      Serial.println("No finger detected");
      return p;
    case FINGERPRINT_PACKETRECIEVEERR:
      Serial.println("Communication error");
      return p;
    case FINGERPRINT_IMAGEFAIL:
      Serial.println("Imaging error");
      return p;
    default:
      Serial.println("Unknown error");
      return p;
  }

  // OK success!

  p = finger.image2Tz();
  switch (p) {
    case FINGERPRINT_OK:
      Serial.println("Image converted");
      break;
    case FINGERPRINT_IMAGEMESS:
      Serial.println("Image too messy");
      return p;
    case FINGERPRINT_PACKETRECIEVEERR:
      Serial.println("Communication error");
      return p;
    case FINGERPRINT_FEATUREFAIL:
      Serial.println("Could not find fingerprint features");
      return p;
    case FINGERPRINT_INVALIDIMAGE:
      Serial.println("Could not find fingerprint features");
      return p;
    default:
      Serial.println("Unknown error");
      return p;
  }

  // OK converted!
  p = finger.fingerSearch();
  if (p == FINGERPRINT_OK) {
    Serial.println("Found a print match!");
  } else if (p == FINGERPRINT_PACKETRECIEVEERR) {
    Serial.println("Communication error");
    return p;
  } else if (p == FINGERPRINT_NOTFOUND) {
    Serial.println("Did not find a match");
    return p;
  } else {
    Serial.println("Unknown error");
    return p;
  }

  // found a match!
  Serial.print("Found ID #"); Serial.print(finger.fingerID);
  Serial.print(" with confidence of "); Serial.println(finger.confidence);

  return finger.fingerID;
}

// returns -1 if failed, otherwise returns ID #
int getFingerprintIDez() {
  uint8_t p = finger.getImage();
  if (p != FINGERPRINT_OK)  return -1;

  p = finger.image2Tz();
  if (p != FINGERPRINT_OK)  return -1;

  p = finger.fingerFastSearch();
  if (p != FINGERPRINT_OK)  return -1;

  // found a match!
  Serial.print("Found ID #"); Serial.print(finger.fingerID);
  Serial.print(" with confidence of "); Serial.println(finger.confidence);
  return finger.fingerID;
}
~~~
#### Imagens
<div>
  <img src="https://user-images.githubusercontent.com/98723501/175784049-8cadb1c8-ecc6-4d8e-819a-60c7693a1849.jpeg" alt=Servo Motor width="500"  />
</div>

#### Portas:
- Fio vermelho no 5v;
- Fio preto no GND;
- Fio branco na porta 3;
- Fio verde na porta 2


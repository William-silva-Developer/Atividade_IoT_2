# ` Integração do projeto com o Node-Red ` 

![Badge em Desenvolvimento](http://img.shields.io/static/v1?label=STATUS&message=EM%20DESENVOLVIMENTO&color=GREEN&style=for-the-badge)

**Equipe:**
- [Amanda Rodrigues](https://github.com/amanda-rosa)
- [Williamis Silva](https://github.com/William-silva-Developer)

## Descrição da integração do projeto

  O nosso projeto de trava elétrica no momento é uma versão beta, que está em teste para a versão final.
  
  Nas aulas práticas fizemos os testes com o servo motor, o buzzer, o sensor biométrico e utilizando o MQTT.
  
  Fizemos por parte os testes, só fizemos junto o servo motor com o buzzer.
  
  Não deu para ver o teste de todos juntos funcionando por causa do bloqueio de segurança do IFRN.


## Construção do dashboard

**Imagens do dashboard**
![Captura de tela de 2022-09-02 22-14-26](https://user-images.githubusercontent.com/98723501/188250185-3a1baaa9-0770-4898-ac06-0a8a1f8e939e.png)


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


**Código completo com o MQTT:** Código completo - Servo motor, buzzer, sensor biométrico e o uso do MQTT. 

**Obs:** Não deu para ver o teste de todos juntos funcionando por causa do bloqueio de segurança do IFRN. 
~~~c
#include <SPI.h>
#include <Ethernet.h>
#include <PubSubClient.h>


// Endereçamento IP utilizado para o cliente e servidor
byte mac[]    = { 0xDE, 0xED, 0xBA, 0xFE, 0xFE, 0xED };
IPAddress ip(192, 168, 1, 50);
IPAddress server(192, 168, 1, 19);

EthernetClient ethClient;
PubSubClient client(ethClient);


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


 /// Configuração MQTT
 Serial.begin(57600);

  pinMode(4, OUTPUT);

  client.setServer(server, 1883);
  client.setCallback(callback);

  Ethernet.begin(mac, ip);
  delay(5000); // Allow the hardware to sort itself out
 
  delay(10000);

 
}


void abrir(){
    for(pos = 0; pos < 90; pos++)
    {
      s.write(pos);
      delay(15);
    }
}

void fechar(){
  delay(1000);
  for(pos = 90; pos >= 0; pos--)
  {
    s.write(pos);
    delay(10);
  }

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



/// Configuração MQTT

 // Aguarda conexão    
  while (!client.connected()) {

    Serial.print("Attempting MQTT connection...");

    //Mensagem lastWill
    byte willQoS = 0;
    const char* willTopic = "arduino/status";
    const char* willMessage = "OFF_LINE";
    boolean willRetain = true;
    //Conexão
    if (client.connect("arduinoClient", willTopic, willQoS, willRetain, willMessage)) {
      Serial.println("connected");
      //Uma vez conectado publica status
      char* message = "Trava aberta";
      int length = strlen(message);
      boolean retained = true; //Retain message
      client.publish("arduino/status", (byte*)message, length, retained);
      // ... and resubscribe
      delay(5000);
      client.publish("arduino/status", (byte*)"Trava fechada", length, retained);
      client.subscribe("arduino/led");
    } else {
      Serial.print("failed, rc=");
      Serial.print(client.state());
      Serial.println(" try again in 5 seconds");
      delay(5000);
    }
  }
  //Uma vez conectado client.loop() deve ser chamada periodicamente para manter conexão
  //e aguardar recebimento de mensagens
  client.loop();



}




//Função callback chamada quando uma mensagem for recebida para subscrições:
void callback(char* topic, byte* payload, unsigned int length) {
  Serial.print("message arrived [");
  Serial.print(topic);
  Serial.print("] ");
  for (int i=0;i<length;i++) {
    Serial.print((char)payload[i]);
  }
  Serial.println();
  //comanda o LED
  if ((char)payload[0] == '1') {
    // Chamar a função para abrir

  abrir();
 
    digitalWrite(4, HIGH);
  } else if  ((char)payload[0] == '0') {
     // Chamar a função para fechar
     
  fechar();
   
    digitalWrite(4, LOW);
  }
~~~

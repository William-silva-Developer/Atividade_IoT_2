# `Disciplina: Programação para Internet das Coisas`

## ` Projeto: Sistema de trava elétrica com senha biométrica`

**Equipe:**
- [Amanda Rodrigues](https://github.com/amanda-rosa)
- [Williamis Silva](https://github.com/William-silva-Developer)



### Sumário

- Introdução
- Justificativa
- Metodologia
- Conclusão
- Trabalhos futuros
- Vantagens e Desvantagens
- Referência



### `Introdução:`

  O sistema de trava elétrica com senha biométrica destina-se a controlar o acesso dos usuários a determinada sala; evitando assim o acesso livre de usuários não cadastrados.
Tendo em vista, que hoje em dia a tecnologia se tornou essencial para várias coisas no mundo, principalmente quando se fala de segurança. 

Pois, como vermos, a cada dia o mundo está inovando com sistemas, equipamentos e dispositivos em várias áreas. Uma dessas várias áreas podemos citar a IoT(Internet das Coisas). Com ela estamos observando a criação de vários itens destinados as residencias, como: Lampadas que acendem via palmas ou via aplicação; TVs com acesso a internet, fechaduras digitais entre outras coisas. 
Mas isso, tem aumentado também com o intuito de auxiliar na proteção de casas, condomínios, empresas, centros acadêmicos, entre outras. 
Dessa forma, este sistema será de grande importância na segurança de todos os usuários .

### `Justificativa:`

  Este sistema é direcionado á usuários cadastrados via biometria, buscando tornar a vida dos mesmos mais seguras, evitando o acesso de pessoas não autorizadas. Porque sabemos que a cada dia a insegurança tem aumentado, aonde um indivíduo entra na sua casa, e rouba os seus bens materiais, que você conquistou em anos com o suor do seu trabalho, em questão de segundos. Outro exemplo muito importante é no contexto educacional, que será também resolvido o problema de insegurança, pois só terá o acesso a determinadas salas os que tiverem cadastrados no sistema, isso ajudará a evitar furtos. Os alunos só terão acesso com os professores em sala de aula, 

mas principalmente preservar-se de indivíduos de fora que possam vir a entrar no local para tentar fazer um arrastão, dessa forma o sistema irá impedir o acesso deles a salas, especialmente as salas específicas que possuem bens mais caros, evitando um desastre. 

O sistema de trava elétrica com senha biométrica tem como objetivo ajudar o usuários de maneira a ter uma vida mais segura, um imóvel ou um centro educacional mais seguro. 

Esse sistema também irá auxiliar na vida diária de cada pessoa que possui o sistema, como por exemplo, o sistema irá guardar o histórico de acesso a porta, saberá a data, a hora e quem acessou o local. Também será emitido um bip quando o usuário colocar sua digital. O sistema de trava elétrica com senha será um projeto relacionado a programação da internet das coisas, e por meio desse sistema milhares de pessoas poderão viver uma vida mais tranquila de forma duradoura.

### `Proposta Metodologica:`

### Local:
Trabalho será realizado nos laboratórios do campus do [IFRN](https://portal.ifrn.edu.br/campus/parnamirim)

### Participantes do projeto:
A realização deste trabalho será por [Amanda Rodrigues](https://github.com/amanda-rosa) e [Williamis Silva](https://github.com/William-silva-Developer)

### Tipo estudo: 
Quantitativo

### Tipo pesquisa: 
Este trabalho envolverá pesquisas exploratórias como também experimental.



### Tempo:
O projeto levará aproximadamente 4 mês para sua devida realização.

### Apresentação
Nosso projeto será realizado por componentes ou por etapas. Cada etapa será sincronizada com a outra. Com isso cada parte será acomplada na outra.
1° passo em nosso projeto:

#### Código usado para o funcionamento do Servo Motor e do Buzzer:
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
- Fio laranja no D6
#### Buzzer
- Resistor 220 ohms;
- Fio vermelho no pino digital 11;
- Fio preto no GND


#### Código para o funcionamento do sensor biométrico:
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


### `Conclusão:`

  O sistema de trava elétrica com senha possibilitará que usuários, sejam eles no ramo de empresas, no contexto educacional, ou na vida cotidiana de qualquer pessoa
que possuir tenham uma vida de menos preocupação em relação a segurança, e que possam controlar o acesso de usuários por meio de um cartão ssd que serão armazenados, nisso estará disponível um histórico de acesso a porta, e terá o controle de quem acessou o local, junto com a data e a hora. E caso seja um usuário cadastrado irá emitir uma luz verde que dará acesso e se não for cadastrado irá emitir uma luz vermelha que terá o acesso negado.
  Diante disso, esse sistema tem como solução de trazer de forma satisfatória uma segurança permanente aos usuários.

### `Trabalhos futuros:`

Como possíveis trabalhos futuros, pode-se apontar a implementação de um aplicativo ou um possível relógio de pulso onde poderão ser capazes de liberar o acesso ao local. Nossa intensão é cada vez mais aprimorar aquilo que criamos para que possamos cada vez mais fornecer aos usuários uma maior facilidade em usá-las 



### `Vantagens e Desvantagens:`

-
-

### `Referência:`


FECHADURA DIGITAL: COMO DEIXAR SUA CASA MAIS MODERNA E SEGURA. Intelbras blog, 2020. Disponível em: https://blog.intelbras.com.br/fechadura-digital-sua-casa-mais-moderna-e-segura/.
Acesso em: 18 de junho de 2022.

KIT ARDUINO 37 SENSORES EM 1 + CAIXA ORGANIZADORA. UsinaInfo, [s.d.]. Disponível em: https://www.usinainfo.com.br/kit-arduino/kit-arduino-sensores-37-em-1-caixa-organizadora-5516.html .
Acesso em: 3 de junho de 2022.

MICRO SERVO MOTOR 9G SG90 COM ARDUINO UNO. FilipeFlop, 2013. Disponível em: https://www.filipeflop.com/blog/micro-servo-motor-9g-sg90-com-arduino-uno/#:~:text=As%20conex%C3%B5es%20desse%20motor%20com,Porta%20Digital%206%20(D6).
Acesso em: 24 de junho de 2022.

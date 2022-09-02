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

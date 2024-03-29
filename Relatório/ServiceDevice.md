# `Seminário sobre comunicação de serviços web para IoT`
![Badge em Desenvolvimento](http://img.shields.io/static/v1?label=STATUS&message=EM%20DESENVOLVIMENTO&color=GREEN&style=for-the-badge)

**Equipe:**
- [Williamis Silva](https://github.com/William-silva-Developer)
- [Amanda Rodrigues](https://github.com/amanda-rosa)


### Sumário

- Introdução
- Aplicabilidade
- Estudo de caso do projeto da disciplina
- Considerações finais
- Referências


# AWS IoT Device Management

## Introdução
### O que é?
  O AWS IoT Device Management é um tipo de serviço que a AWS oferece a seus clientes. Esse serviço pode fazer com que o cliente gerencie remotamente seus dispositivos IoT. Esse serviço dá a possibilidade de monitorar, registrar e organizar todos os dispositivos conectados com esse serviço que vem em uma crescente expansão desses dispositivos. Esse serviço hoje é de grande ajuda, pois à medida que mais dispositivos são criados com recursos de rede, mais essa demanda cresce. Logo abaixo poderemos observar alguns dos principais recursos que esse serviço da AWS oferece.


- `Integração em massa`: o software deve permitir a integração usando uma chave de rede e credenciais de identificação.
- `Solução de problemas remotamente`: o serviço fornece suporte a soluções de possíveis problemas de maneira remota. Evitando os esforços manuais.
- `Relatórios e análises`: Geralmente os dispositivos IoT são fornecidos com recursos de análise de borda. Essas análises são fornecidas em tempo real por meio de painéis GUI. Onde também podem ser convertidos para uma melhor compreensão do usuário.

Aqui elencamos apenas alguns dos recursos que são obrigatórios nesse tipo de serviço. Mas a contratação pode vir com outros tipos de recursos.

#

## Aplicabilidade

### Como posso usar o AWS IoT Device Management? e quais requisitos para sua utilização? 
  Bem. Para responder a essas perguntas devemos começar primeiro falando sobre os requisitos para seu uso. E o principal requisito é você criar uma conta na AWS para que você ou sua empresa tenha acesso.

 Também é interessante que tenha um bom conhecimento em comandos utilizados no sistema operacional Linux, pois isso ajudará bastante no processo.

### Quais os passos tecnicos para utilizar?

Então vamos lá!. Feita a contratação do serviço na AWS. Temos que seguir um passo a passo para que os dispositivos estejam conectados a ela. Então feita a autenticação no sistema e preciso então procurar pelo EC2( o EC2 é uma forma dos usuários poderem alugarem computadores virtuais para rodarem as aplicações) e clicamos para seguimos em diante.

![Captura de tela de 2022-08-30 23-37-57](https://user-images.githubusercontent.com/98723501/187580464-d2aa29dc-df78-4db1-8185-6cd47baf4c6d.png)

Feito o passo acima devemos agora buscar opção referente a executar instancia 

![Captura de tela de 2022-08-31 21-24-56](https://user-images.githubusercontent.com/98723501/187809213-d80e6a9d-6096-47ab-aabf-369ed36af7b1.png)

![Captura de tela de 2022-08-31 21-25-53](https://user-images.githubusercontent.com/98723501/187809832-57d7c3e3-8cb4-4a40-a340-d439e3ac0da0.png)

![Captura de tela de 2022-08-31 21-57-00](https://user-images.githubusercontent.com/98723501/187810292-6acdf87f-aac2-4374-8097-b7ea26080fb0.png)

![Captura de tela de 2022-08-31 21-58-13](https://user-images.githubusercontent.com/98723501/187810401-d947b2f6-521e-452b-8bef-8d0ff2955634.png)

![Captura de tela de 2022-08-31 22-01-55](https://user-images.githubusercontent.com/98723501/187811038-cc28b3e3-4249-4786-9a78-1a904fa02da8.png)


![Captura de tela de 2022-08-31 22-45-27](https://user-images.githubusercontent.com/98723501/187815349-5b6e2342-2941-4f4b-be36-d51132bf3e2c.png)


![Captura de tela de 2022-08-31 23-11-05](https://user-images.githubusercontent.com/98723501/187817942-012c8a07-9354-45cd-8d1e-16e8cabd8499.png)

![Captura de tela de 2022-08-31 23-25-34](https://user-images.githubusercontent.com/98723501/187819126-9de25b45-ec8d-46fb-8429-68610bf0e9c3.png)


![Captura de tela de 2022-08-31 23-26-33](https://user-images.githubusercontent.com/98723501/187819229-527673a4-304d-4f9a-8c12-3586879b3bcd.png)

![Captura de tela de 2022-08-31 23-31-37](https://user-images.githubusercontent.com/98723501/187819715-c992ccf0-3362-4c8b-9732-9069cf0ab6ff.png)

![Captura de tela de 2022-08-31 23-33-08](https://user-images.githubusercontent.com/98723501/187820003-be3da634-2dc4-4800-b9ba-4c2c3484b0d6.png)

![Captura de tela de 2022-08-31 23-35-55](https://user-images.githubusercontent.com/98723501/187820155-db5696b1-2664-4263-a278-edcf905ee9a8.png)

![Captura de tela de 2022-08-31 23-35-55](https://user-images.githubusercontent.com/98723501/187820472-86374a69-bdb1-4f58-8916-43e43cc49e35.png)

![Captura de tela de 2022-08-31 23-38-09](https://user-images.githubusercontent.com/98723501/187821006-7218d26c-e235-4e2c-9b2f-5410ba1fe214.png)

![Captura de tela de 2022-08-31 23-46-18](https://user-images.githubusercontent.com/98723501/187821362-5201722e-5fc4-40d8-81a3-c11a6eb07b43.png)

![Captura de tela de 2022-08-31 23-49-06](https://user-images.githubusercontent.com/98723501/187821661-09a253f9-f2e6-45b5-88c9-397f12472b3f.png)

#

##  Estudo de caso do projeto relacionado com a disciplina
### Como pode ser empregado no seu projeto? e como poder ser a comunicação com o dispositivo programado com a utilização do Ethernet Shield?

O Ethernet Shield tem suporte para trabalhar com o protocolo MQTT(Message Queuing Telemetry Transport) que é provido de uma biblioteca que podemos encontrar no Arduino IDE ou no endereço eletronico:  https://github.com/knolleary/pubsubclient . Para haver interação com a rede é necessário que coloquemos o ethernet shield sobre a placa do arduíno e conectá-la à rede via cabo de rede, pois o ethernet shield possui entrada para o RJ45. 
Também é necessário fazermos algumas configurações dentro do arquivo ou biblioteca, como: configuramos para que o dispositivo possua um endereço ip como também o enderço do servidor. Logo abaixo é possível vermos o código da bibliotema **PubSubClient** que foi usada em nosso pequeno projeto.

~~~c
#include <SPI.h>
#include <Ethernet.h>
#include <PubSubClient.h>

// Endereçamento IP utilizado para o cliente e servidor
byte mac[]    = { 0xDE, 0xED, 0xBA, 0xFE, 0xFE, 0xED };
IPAddress ip(192, 168, 2, 20);
IPAddress server(192, 168, 2, 10);

EthernetClient ethClient;
PubSubClient client(ethClient);

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
    digitalWrite(4, HIGH);
  } else if  ((char)payload[0] == '0') {
    digitalWrite(4, LOW);
  } 
}

void setup()
{
  Serial.begin(57600);

  pinMode(4, OUTPUT);

  client.setServer(server, 1883);
  client.setCallback(callback);

  Ethernet.begin(mac, ip);
  delay(5000); // Allow the hardware to sort itself out
  
  delay(10000);
}

void loop(){
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
      char* message = "ON_LINE";
      int length = strlen(message);
      boolean retained = true; //Retain message
      client.publish("arduino/status", (byte*)message, length, retained);
      // ... and resubscribe
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
~~~






#

## Considerações finais

A IoT é um dos players do mercado de cloud. Uma empresa que ao longo dos últimos anos cresceu exponencialmente e as soluções de IoT voltados para área empresarial também vem crescendo. A AWS é uma empresa com vários recursos para a área de IoT no mercado. Permitindo que seus clientes possam conectar vários dispositivos à nuvem da Amazon e possam operar ou controlá-los remotamente. Porém ela não é o único player existente no mercado de cloud. Ela possui  concorrentes de alto nível também,como a Microsoft Azure e a Google Cloud Platform. Essas oferecem produtos tão bons quanto a AWS. Hoje quando pensamos em serviço de cloud computing a primeira empresa que nos vem à mente é a AWS ou como também é conhecida Amazon.

#

## Referências

**BASUMALLICK. Chiradeep**. What Is IoT Device Management? Definition, Key Features, and Software. **Spice works**,2022. Disponível em:<https://www.spiceworks.com/tech/iot/articles/what-is-iot-device-management/>.Acesso em: 14 ago. 2022.

RECURSOS do AWS IoT Device Management. **AWS**. Disponível em: <https://aws.amazon.com/pt/iot-device-management/features/?pg=ln&sec=uc>. Acesso em: 16 ago. 2022.


**TEBALDI.Pedro César**.Conheça os 20 principais serviços da AWS: Amazon Web Services. **Opservices**,2018. Disponível em: <https://www.opservices.com.br/principais-servicos-da-aws-amazon-web-services/>. Acesso em: 15 ago. 2022.


**LUNN.John**.Oque é AWS IoT. **Petri**,2022.Disponível em: <https://petri.com/what-is-aws-iot/#An_essential_communication_service_for_IoT_devices>. Acesso em: 25 ago. 2022.

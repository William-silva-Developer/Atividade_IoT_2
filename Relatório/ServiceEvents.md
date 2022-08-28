# `Seminário sobre comunicação de serviços web para IoT`


**Equipe:**
- [Amanda Rodrigues](https://github.com/amanda-rosa)
- [Williamis Silva](https://github.com/William-silva-Developer)


### Sumário

- Introdução
- Aplicação do serviço
- Estudo de caso do projeto da disciplina
- Considerações finais
- Referência


# AWS IoT Events 

## Introdução

 **A solução** é um serviço gerenciado que favorece a detecção e a resposta a eventos de sensores e aplicativos de IoT, essa solução é a AWS IoT Events. Na utilização, tem facilidade de detectar eventos entre os milhares sensores de IoT que enviam dados de telemetria diferentes. Esse serviço monitora constantemente os dados de vários sensores e aplicativos de IoT.

**Aplicações e as relações com IoT?** A IoT Events faz integração com outros serviços, como o IoT Core e AWS IoT Analytics, permitindo a detecção antecipada e informações exclusivas.
**As relações que possue com IoT** é a forma como o serviço funciona. Como por exemplo: Ele detecta facilmente eventos entre os milhares de sensores de IoT que enviam dados de telemetria diferentes, como a temperatura de um freezer, a umidade do equipamento respiratório e a velocidade da correia em um motor. Exemplos de IoT são os sensores de temperatura, umidade, entre outros.

## Aplicação do serviço

 **Como usar?** Para a utilização do IoT Events tem que selecionar as fontes de dados relevantes a serem inseridos, definir a lógica de cada evento usando instruções simples "if-then-else" (se-então-senão) e selecionar a ação de alerta ou personalizada a ser acionada quando ocorrer um evento, ou seja, configuramos a AWS IoT Events detectores para reconhecer os eventos usando expressões lógicas simples em vez de código complexo. Dessa forma, será fácil detectar eventos entre os milhares de sensores e aplicativos de IoT. No IoT Events define uma detecção de evento de duas maneiras. A primeira é usar o console do AWS IoT Events para definir as condições sob as quais um evento ocorre e acionar ações quando as condições forem avaliadas como "true". A segunda é criar programaticamente uma detecção de evento chamando a API “Create_Detector”.

**Requisitos para utilização:** Os requisitos para a utilização da IoT Events, primeiramente criar uma conta na AWS, durante o procedimento da inscrição receberá uma chamada telefonica e inserir um código de verificação no telefone. Logo depois criará dois tópicos do Amazon Simple Notification Service (Amazon SNS). 
Após criar os tópicos, Os ARNs desses tópicos são mostrados como:arn:aws:sns:us-east-1:123456789012:underPressureActionearn:aws:sns:us-east-1:123456789012:pressureClearedAction. Então irá Substituir esses valores pelos ARNs dos tópicos do Amazon SNS que foi criado.

Continuando os passos... Como alternativa à publicação de alertas para tópicos do Amazon SNS, você pode fazer com que os detectores enviem mensagens MQTT com um tópico que você especificar. Com essa opção, você pode verificar se o modelo do detector está criando instâncias e se essas instâncias estão enviando alertas usando oAWS IoTConsole principal para assinar e monitorar mensagens enviadas para esses tópicos do MQTT. Você também pode definir o nome do tópico MQTT dinamicamente em tempo de execução usando uma entrada ou variável criada no modelo do detector. observa continuamente os dados do sensor de IoT de dispositivos, processos, aplicativos e outrosAWSserviços para identificar eventos significativos para que você possa agir.

Por fim, escolher uma AWS Região que oferece suporte AWS IoT Events. Seguindo esses requisitos poderemos utilizar a IoT Events para permitir monitorar os equipamentos e as frotas de dispositivos em busca de falhas ou alterações na operação, além de acionar ações caso esses eventos ocorram. 

**Quais passos técnicos para utilizar?** 

Neste exemplo, oAWS IoT Events APIs usando AWS CLI comandos para criar um detector que modela dois estados de um motor: um estado normal e uma condição de sobrepressão.

**Resumo do exemplo:** Quando a pressão medida no motor excede um determinado limite, o modelo passa para o estado de sobrepressão e envia uma mensagem do Amazon Simple Notification Service (Amazon SNS) para alertar um técnico sobre a condição. Quando a pressão cai abaixo do limite para três leituras de pressão consecutivas, o modelo retorna ao estado normal e envia outra mensagem do Amazon SNS como uma confirmação de que a condição foi eliminada. Exigimos três leituras consecutivas abaixo do limite de pressão para eliminar a possível gagueira de mensagens de sobrepressão/normal no caso de uma fase de recuperação não linear ou uma leitura de recuperação anômala única.

**Etapas do exemplo:** 

**Criar entrada para capturar dados do dispositivo**

![image](https://user-images.githubusercontent.com/70977967/187050415-e2157d21-c539-4fd6-8b6e-57062bf05f68.png)

**Crie um modelo de detector para representar os estados do dispositivo**

 Este é um modelo de detector que responde a um evento de sobrepressão em um motor.

Você pode criar o modelo do detector usando o AWS CLI comando: 

aws iotevents create-detector-model  --cli-input-json file://motorDetectorModel.json


Você cria dois estados:”Normal“, e”Dangerous“. Cada detector (instância) entra no campo”Normal“estado quando é criado. A instância é criada quando uma entrada com um valor exclusivo para okey "motorid“chega.

Se a instância do detector receber uma leitura de pressão igual ou superior a 70, ela entrará no campo”Dangerous“e envia uma mensagem do Amazon SNS como um aviso. Se as leituras de pressão retornarem ao normal (menos de 70) por três entradas consecutivas, o detector retornará ao”Normal“e envia outra mensagem do Amazon SNS como um todo claro.

Foi criado dois tópicos do Amazon SNS cujos nomes de recursos da Amazon (ARNs) são mostrados na definição como"targetArn": "arn:aws:sns:us-east-1:123456789012:underPressureAction"e"targetArn": "arn:aws:sns:us-east-1:123456789012:pressureClearedAction".

Foi criado AWS Identity and Access Managementfunção (IAM) com permissões apropriadas. O ARN dessa função é mostrado na definição do modelo do detector como"roleArn": "arn:aws:iam::123456789012:role/IoTEventsRole".

![image](https://user-images.githubusercontent.com/70977967/187050519-24795dc4-3623-4720-9b1a-dc5eccee202f.png)

![Capturar11](https://user-images.githubusercontent.com/70977967/187050728-6016ede5-6a6a-419f-acd7-691d8d698564.PNG)

![image](https://user-images.githubusercontent.com/70977967/187050544-2f320ab2-3549-4696-b69b-a6f708cae777.png)

![Capturar12](https://user-images.githubusercontent.com/70977967/187050781-facbf525-3110-470c-8a53-ef67af365544.PNG)

![Capturar13](https://user-images.githubusercontent.com/70977967/187050786-5d1287c2-9715-4997-991a-d2fd49b8981e.PNG)

![Capturar14](https://user-images.githubusercontent.com/70977967/187050788-d0c9880d-7222-4d20-adc2-a66a09b22d3c.PNG)


**Enviar mensagens como entradas para um detector**

Use o seguinteAWS CLI comando para enviar uma mensagem com dados que violam o limite:


aws iotevents-data batch-put-message --cli-input-json file://highPressureMessage.json 

![Capturar15](https://user-images.githubusercontent.com/70977967/187050886-92269b16-1e50-444f-acb9-5bf11cd79534.PNG)
![Capturar16](https://user-images.githubusercontent.com/70977967/187050896-57d9198c-eda0-4111-a4c1-35084039f904.PNG)

Neste ponto, um detector (instância) é criado para monitorar eventos para o motor"Fulton-A32". Este detector entra no"Normal"estado quando é criado. Mas como enviamos um valor de pressão acima do limite, ele passa imediatamente para o"Dangerous"estado. Ao fazer isso, o detector envia uma mensagem para o endpoint do Amazon SNS cujo ARN éarn:aws:sns:us-east-1:123456789012:underPressureAction.

Execute o seguinte no AWS CLI comando para enviar uma mensagem com dados abaixo do limite de pressão:


aws iotevents-data batch-put-message --cli-input-json file://normalPressureMessage.json 

![Capturar17](https://user-images.githubusercontent.com/70977967/187050944-3fcda66b-8e4b-4023-ada7-1185128674c4.PNG)
![Capturar18](https://user-images.githubusercontent.com/70977967/187050950-743a0446-6881-455f-8b19-abf1f34ee38a.PNG)

A seguir estão exemplos de cargas úteis de mensagens do SNS criadas pelo exemplo de modelo de detector descrito.

**No evento “Limite de pressão violado”**

![Capturar19](https://user-images.githubusercontent.com/70977967/187050978-26c60c11-1423-48ee-963b-13a11f798f5a.PNG)

**No evento “Pressão normal restaurada”**

![Capturar20](https://user-images.githubusercontent.com/70977967/187050992-b68b4f94-726d-4e78-b19e-1b8b8ebccbf5.PNG)

Se você tiver definido temporizadores, seu estado atual também será mostrado nas cargas de mensagem do SNS.

As cargas de mensagem contêm informações sobre o estado do detector (instância) no momento em que a mensagem foi enviada (ou seja, no momento em que a ação SNS foi executada).


## Estudo de caso do projeto da disciplina

**Como pode ser empregado no projeto?**

O IoT Events pode ser utilizado no projeto para a criação dos eventos, para o envio de dados, para disparar um alerta, digo em relação ao acesso, caso seja verde a led (cadastrado) ou vermelho (recusado/não cadastrado).

**Como pode ser a comunicação com o dispositivo?** 

A comunicação será com o uso do MQTT para publicar e assinar mensagens, ou seja, as mensagens de eventos serão publicadas por meio do MQTT com uma carga JSON.

**Página principal do AWS Management Console**

![Capturar21](https://user-images.githubusercontent.com/70977967/187052210-a10df7f8-147a-4bad-b86a-3ef2b73a907d.PNG)

**Mensagem publicada para o tópico OrdersTopic**

![Capturar22](https://user-images.githubusercontent.com/70977967/187052251-107e3bab-a43b-4018-9d61-7493c75bb7b4.PNG)

**Detalhamento da mensagem recebida**

![Capturar23](https://user-images.githubusercontent.com/70977967/187052289-429e874a-7d1d-4508-876f-bce26c007f2d.PNG)

**Descrição da mensagem**

![Capturar24](https://user-images.githubusercontent.com/70977967/187052307-14c13d1e-1a4c-4700-bbc4-1d6355b8ee52.PNG)

**Função Lambda**

![Capturar25](https://user-images.githubusercontent.com/70977967/187052326-7e87ae4e-a13e-494d-b7be-dc25754994df.PNG)


## Considerações finais

**Quais os principais resultados obtidos?**
Foi o uso com a comunicação MQTT. A criação dos eventos, o envio de dados e os gatilhos (os alertas) para o acesso ou não acesso do usuário para o nosso sistema de trava elétrica digital.

**Serviços concorrentes?**
Hubs de Evento (Azure) --> Serviços que facilitam a ingestão em massa de eventos (mensagens), normalmente de dispositivos e sensores. Os dados podem ser processados em microlotes em tempo real ou gravados no armazenamento para análise posterior.
Hubs de Evento é simples, seguro, escalonável, aberto e faz integração com outros serviços do Azure.

## Referência

AWS IoT Events. **AWS Amazon**. Disponível em: 
<https://aws.amazon.com/pt/iot-events/?c=i&sec=srv/>.
Acesso em: 21 de jul. de 2022.

HUBS De Eventos. **Azure**. Disponível em: <https://azure.microsoft.com/pt-br/services/event-hubs/#overview>. Acesso em: 24 de ago. de 2022.

SIMPLE step-by-step example. **AWS Amazon**. Disponível em: <https://docs.aws.amazon.com/iotevents/latest/developerguide/iotevents-simple-example.html/>. Acesso em: 22 de jul. de 2022.



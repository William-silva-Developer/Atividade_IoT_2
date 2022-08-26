# `Seminário sobre comunicação de serviços web para IoT`


**Equipe:**
- [Amanda Rodrigues](https://github.com/amanda-rosa)
- [Williamis Silva](https://github.com/William-silva-Developer)


### Sumário

- Introdução
- Aplicação do serviço
- Estudo de caso do projeto da disciplina
- Considerações finais


# AWS IoT Events 

## Introdução

 **A solução** é um serviço gerenciado que favorece a detecção e a resposta a eventos de sensores e aplicativos de IoT, essa solução é a AWS IoT Events. Na utilização, tem facilidade de detectar eventos entre os milhares sensores de IoT que enviam dados de telemetria diferentes. Esse serviço monitora constantemente os dados de vários sensores e aplicativos de IoT.

**Aplicações e as relações com IoT?** A IoT Events faz integração com outros serviços, como o IoT Core e AWS IoT Analytics, permitindo a detecção antecipada e informações exclusivas.
**As relações que possue com IoT** é a forma como o serviço funciona. Como por exemplo: Ele detecta facilmente eventos entre os milhares de sensores de IoT que enviam dados de telemetria diferentes, como a temperatura de um freezer, a umidade do equipamento respiratório e a velocidade da correia em um motor. Exemplos de IoT são os sensores de temperatura, umidade, entre outros.

## Aplicação do serviço

 **Como usar?** Para a utilização do IoT Events tem que selecionar as fontes de dados relevantes a serem inseridos, definir a lógica de cada evento usando instruções simples "if-then-else" (se-então-senão) e selecionar a ação de alerta ou personalizada a ser acionada quando ocorrer um evento, ou seja, configuramos a AWS IoT Events detectores para reconhecer os eventos usando expressões lógicas simples em vez de código complexo. Dessa forma, será fácil detectar eventos entre os milhares de sensores e aplicativos de IoT.

**Requisitos para utilização:** Os requisitos para a utilização da IoT Events, primeiramente criar uma conta na AWS, durante o procedimento da inscrição receberá uma chamada telefonica e inserir um código de verificação no telefone. Logo depois criará dois tópicos do Amazon Simple Notification Service (Amazon SNS). 
Após criar os tópicos, Os ARNs desses tópicos são mostrados como:arn:aws:sns:us-east-1:123456789012:underPressureActionearn:aws:sns:us-east-1:123456789012:pressureClearedAction. Então irá Substituir esses valores pelos ARNs dos tópicos do Amazon SNS que foi criado.

Continuando os passos... Como alternativa à publicação de alertas para tópicos do Amazon SNS, você pode fazer com que os detectores enviem mensagens MQTT com um tópico que você especificar. Com essa opção, você pode verificar se o modelo do detector está criando instâncias e se essas instâncias estão enviando alertas usando oAWS IoTConsole principal para assinar e monitorar mensagens enviadas para esses tópicos do MQTT. Você também pode definir o nome do tópico MQTT dinamicamente em tempo de execução usando uma entrada ou variável criada no modelo do detector. observa continuamente os dados do sensor de IoT de dispositivos, processos, aplicativos e outrosAWSserviços para identificar eventos significativos para que você possa agir.

Por fim, escolher uma AWS Região que oferece suporte AWS IoT Events. Seguindo esses requisitos poderemos utilizar a IoT Events para permitir monitorar os equipamentos e as frotas de dispositivos em busca de falhas ou alterações na operação, além de acionar ações caso esses eventos ocorram. 

**Quais passos técnicos para utilizar?** 

# `Proposta de sistema de trava eletrica com senha` 
![Badge em Desenvolvimento](http://img.shields.io/static/v1?label=STATUS&message=EM%20DESENVOLVIMENTO&color=GREEN&style=for-the-badge)

## `Resumo` 
- Nosso projeto tem como objetivo a implementação de uma fechadura ou trava eletrica onde será acionada por um sensor biométrico. Essa fechadura terá um módulo relogio onde será possível guardar o dia e a hora que uma sala por exemplo foi acessada. Garantindo assim um controle melhor do ambiente. Para isso usaremos algumas ferramentas como: Arduino uno, Ethernet shield entre outros.

##
## `Autores`
- [Amanda Rodrigues](https://github.com/amanda-rosa)
- [William Silva](https://github.com/William-silva-Developer)

##

## `Material` 

| Item | Descrição |
| --- | --- |
| <img align="center" alt="Arduino uno" height="200" width="200" src="https://www.usinainfo.com.br/1019683-thickbox_default/led-vermelho-5mm-difuso-kit-com-5-unidades.jpg" /> |  `Dois Leds` Um na cor verde para indicar que a trava foi aberta e o outro na cor vermelha para indicar falha ou trava fechada.|
|<img align="center" alt="Arduino uno" height="200" width="200" src="https://upload.wikimedia.org/wikipedia/commons/9/9b/220_ohms_5%25_axial_resistor.jpg" />   | `Dois Resistor 220 ohms` |
|<img align="center" alt="Arduino uno" height="200" width="200" src="https://cdn.leroymerlin.com.br/products/trinco_ferrolho_redondo_latao_oxidado_60xcm_1_peca_87239061_0001_600x600.jpg" />| `Trinco Ferrolho Redondo Latão Oxidado 60xcm` Será movimentado de acordo com o movimento do servo motor.|
|<img align="center" alt="Arduino uno" height="200" width="200" src="https://www.usinainfo.com.br/1017427-thickbox_default/micro-servo-motor-9g-sg90-180-de-posicao.jpg" />| `Micro Servo Motor 9g SG90 180° de Posição` O módulo relé é o responsável em abrir ou fechar a trava. Ele funcionará como um interruptor de pulsos eletricos. |
|<img align="center" alt="Arduino uno" height="200" width="auto" src="https://www.usinainfo.com.br/1019675-thickbox_default/ethernet-shield-r3-w5100-para-arduino.jpg" />| `Ethernet Shield R3 W5100 para arduino` A Ethernet shield será a parte necessaria para nos dá possibilidade de comunicação com a internet onde trabalharemos futuramente ccom o protocolo MQTT. |
| <img align="center" alt="Arduino uno" height="200" width="200" src="https://www.usinainfo.com.br/1021246-thickbox_default/modulo-relogio-tempo-real-rtc-ds1302.jpg" /> | `Módulo Relógio Tempo Real RTC - DS1302` |
| <img align="center" alt="Arduino uno" height="200" width="200" src="https://www.usinainfo.com.br/1012957-thickbox_default/placa-uno-r3-arduino-cabo-usb.jpg" /> | `Placa Uno R3 Arduino` |
| <img align="center" alt="Arduino uno" height="200" width="200" src="https://www.usinainfo.com.br/1019044-thickbox_default/buzzer-ativo-12v-bip-continuo-pci-12mm.jpg" /> | `Buzzer Ativo 12V Bip Contínuo PCI 12mm` Será resposável em emitir o som para dar ao usuário um retorno sonoro da abertura ou fechamento da trava |
| <img align="center" alt="Arduino uno" height="200" width="200" src="https://www.usinainfo.com.br/1017451-thickbox_default/leitor-biometrico-para-arduino-jm101-cabo.jpg" /> | `Leitor Biométrico para Arduino JM101 + Cabo` |

# Projeto AURA – Documentação de Imagens

Este documento apresenta e explica algumas imagens que ilustram a arquitetura, funcionamento e prototipagem do **Projeto AURA**.

---

## 📷 Imagem 1 – Dispositivo ESP32 LoRa Heltec V3
**Arquivo:** `esp32.jpg`

O dispositivo mostrado é o **ESP32 LoRa modelo Heltec V3**, utilizado como unidade de processamento e comunicação.  
Na imagem, é possível observar o procedimento de **conexão de um smartphone com o dispositivo via Bluetooth**. Durante esse processo, um **código PIN** é exibido no display OLED integrado.  

O display OLED não serve apenas para autenticação: ele também funciona como uma **interface local**, permitindo que o usuário acompanhe em tempo real:  
- A tramitação de dados via LoRa  
- O envio e recebimento de mensagens  
- O status da conexão e intensidade do sinal  
- Leituras dos sensores conectados  

Essa interface proporciona maior transparência no funcionamento do sistema, tornando a interação mais intuitiva e acessível.

---

## 📷 Imagem 2 – Prototipagem do Dispositivo de Campo
**Arquivo:** `prototipagem_sensores.jpg`

A imagem mostra a fase de **prototipagem em uma protoboard** do dispositivo de campo.  

- A alimentação observada via USB será futuramente substituída por uma **bateria com sistema de carregamento solar**, garantindo autonomia energética em ambientes remotos.  
- É possível visualizar a **antena de 5 dB** conectada ao módulo Heltec, responsável pela comunicação LoRa de longo alcance.  
- O **barramento I²C** está ligado ao dispositivo, com sensores de **temperatura, pressão e umidade** acoplados.  

Os dados coletados por esses sensores são transmitidos via **rádio LoRa** até o **dispositivo da base**, onde são recebidos, processados e tratados.  
Além disso, o sistema é capaz de realizar **envio de alertas em qualquer direção**, ampliando suas aplicações em monitoramento ambiental e automação.  



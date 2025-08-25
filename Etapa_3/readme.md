# Projeto AURA

## Estado Atual
O **Projeto AURA** encontra-se em estágio de **protótipo funcional altamente eficaz**, validando sua arquitetura e funcionalidades principais.  
Atualmente, o sistema:

- Lê dados de múltiplos sensores ambientais conectados ao barramento **I²C**.  
- Transmite as informações via **rádio LoRa** com eficiência energética notável.  
- Possui **alcance de até 3 km** em campo aberto.  

O projeto se destaca pela **alta escalabilidade** e **baixo custo de hardware**, permitindo a expansão da rede e aumentando a densidade de dados para maior precisão em previsões climáticas.  

Além disso, oferece múltiplas ferramentas de interação:  
- **Aplicativos móveis (Android e iOS)**  
- **Interface Web**  
- **Ferramenta de linha de comando (CLI) em Python**  

Todas possibilitam **configuração remota (OTA)** dos dispositivos.

---

## Configurações OTA Suportadas
O AURA herda grande parte das capacidades do **Meshtastic**, permitindo a configuração remota de diversos parâmetros:

- **Configurações de Rede:** Wi-Fi, Ethernet, servidores NTP e IPv4.  
- **Configurações LoRa:** região, potência de transmissão, fator de espalhamento, frequência etc.  
- **Configurações de Energia:** modos de economia, deep sleep, monitoramento de bateria.  
- **Configurações de Dispositivo:** papel na rede (nó sensor/gateway), retransmissão, LEDs etc.  
- **Configurações de Telemetria e MQTT:** envio de métricas e integração com servidor MQTT.  

---

## Sensores Suportados
O firmware detecta automaticamente os sensores conectados via I²C, simplificando a integração.  
Sensores já compatíveis incluem:

- **Temperatura, Umidade e Pressão:** AHT10/AHT20, BME280, BMP280, BME68x, SHT31, SHT4X, BMP388  
- **Luminosidade e UV:** OPT3001, VEML7700, TSL2591, LTR390UV  
- **Tensão e Corrente:** INA219, INA226, INA260, INA3221  
- **Outros:** LPS22 (pressão), RCWL9620 (distância), DFROBOT_RAIN (chuva), RadSens (dosímetro)  

---

## Desafios e Melhorias Planejadas

### 1. Fragilidade e Alcance Físico
- **Desafio:** O protótipo de bancada é vulnerável a fatores ambientais e exige instalação da antena em locais elevados.  
- **Melhoria:** Desenvolvimento de uma **estrutura robusta e à prova de intempéries**, que permita instalação adequada da antena.

### 2. Integração e Automação de Dados
- **Desafio:** Hoje os dados só podem ser acompanhados de forma passiva.  
- **Melhoria:** Integração com o **Home Assistant**, permitindo armazenar dados em banco de dados e criar **rotinas de automação** (ex.: irrigação automática, alertas inteligentes).  

### 3. Autonomia Energética em Locais Remotos
- **Desafio:** Necessidade de funcionamento em locais sem acesso à rede elétrica.  
- **Melhoria:** Uso de **bateria + placa solar de carregamento**, com monitoramento remoto do consumo energético.  

### 4. Proteção do Equipamento
- **Desafio:** Instalações remotas expõem o dispositivo a risco de furto.  
- **Melhoria:** Inclusão de **sensor de presença (PIR)** integrado ao **GPS**, permitindo alertas de movimentação suspeita.  

---

## Conclusão
O Projeto AURA demonstra grande potencial como solução de **monitoramento ambiental distribuído**, combinando:  
- **Baixo custo**,  
- **Escalabilidade**,  
- **Flexibilidade de integração**,  
- **Confiabilidade de comunicação**.  

As melhorias planejadas visam torná-lo viável para **implantação em larga escala**, tornando-se uma ferramenta poderosa para **telemetria, automação e proteção ambiental**.

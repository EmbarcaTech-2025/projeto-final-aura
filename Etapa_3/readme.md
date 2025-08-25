# Projeto AURA: Estado Atual, Desafios e Evolução Futura

## Estado Atual
O Projeto AURA alcançou um estágio de protótipo funcional altamente eficaz, validando sua arquitetura e capacidades centrais. Atualmente, o sistema é plenamente capaz de ler dados de múltiplos sensores ambientais conectados ao barramento I²C e transmiti-los via rádio LoRa com uma eficiência energética notável, permitindo um longo alcance de até 3 km.

Um dos diferenciais competitivos do projeto reside em sua alta escalabilidade e baixo custo de hardware, o que facilita a expansão da rede para aumentar a densidade de dados e, consequentemente, a precisão das previsões climáticas. A flexibilidade da solução é ampliada por um conjunto robusto de ferramentas de interação, que inclui aplicativos para smartphones (Android e iOS), uma interface web e uma ferramenta de linha de comando (CLI) em Python, todas permitindo a configuração remota (OTA) dos dispositivos.

A capacidade de configuração OTA é um dos pontos fortes do Meshtastic, permitindo ao usuário gerenciar remotamente uma ampla gama de parâmetros. Embora o projeto não utilize todas as configurações, sua capacidade de expansão é notável, abrangendo:

### Configurações de Rede
- Habilitação de Wi-Fi  
- Ethernet  
- Definição de servidores NTP e IPv4  

### Configurações LoRa
- Ajustes de região  
- Potência de transmissão  
- Fator de espalhamento  
- Frequência  
- Outras opções cruciais para a comunicação  

### Configurações de Energia
- Gerenciamento do modo de economia de energia  
- Intervalos de deep sleep  
- Monitoramento de bateria  

### Configurações de Dispositivo
- Papel na rede (nó sensor ou gateway)  
- Modo de retransmissão  
- Ativação de LEDs  
- Entre outros  

### Configurações de Telemetria e MQTT
- Habilitação do módulo de telemetria  
- Envio de métricas de dispositivo  
- Encaminhamento de dados para um servidor MQTT  

---

## Sensores Suportados para Telemetria
O projeto é capaz de ler dados de diversos sensores que se conectam ao dispositivo via barramento I²C. A detecção automática no firmware simplifica a integração de uma vasta gama de sensores, incluindo:

### Temperatura, Umidade e Pressão
- AHT10/AHT20  
- BME280  
- BMP280  
- BME68x  
- SHT31  
- SHT4X  
- BMP388  

### Luminosidade e UV
- OPT3001  
- VEML7700  
- TSL2591  
- LTR390UV  

### Tensão e Corrente
- INA219  
- INA226  
- INA260  
- INA3221  

### Outros
- LPS22 (pressão)  
- RCWL9620 (distância)  
- DFROBOT_RAIN (chuva)  
- RadSens (dosímetro)  

---

## Desafios e Melhorias Planejadas

### 1. Desafio: Fragilidade e Alcance Físico
O protótipo atual, em sua forma de bancada, é vulnerável a fatores ambientais. Para o alcance ideal do LoRa, a antena precisa ser instalada em locais elevados, o que exige uma estrutura robusta.  

**Melhoria Planejada:** Desenvolvimento de uma estrutura física robusta e à prova de intempéries, capaz de abrigar todos os componentes. Esta estrutura permitirá a instalação da antena em locais altos e favoráveis, maximizando o alcance e a confiabilidade da rede.  

---

### 2. Desafio: Integração e Automação de Dados
O sistema atual permite apenas o acompanhamento passivo dos dados via smartphones e web. Para uma solução mais robusta, é essencial que os dados de telemetria possam acionar rotinas e interagir com outros sistemas.  

**Melhoria Planejada:** Integração com o Home Assistant. Essa melhoria permitirá que os dados coletados sejam armazenados em um banco de dados sólido e sejam usados para criar rotinas de automação, como ligar um sistema de irrigação ou ativar alertas com base em leituras específicas dos sensores.  

---

### 3. Desafio: Autonomia Energética em Locais Remotos
Para instalações em campo, longe de fontes de energia, a autonomia do dispositivo é um requisito fundamental.  

**Melhoria Planejada:** Implementação de uma solução de alimentação baseada em bateria e uma placa solar de carregamento. O firmware já é capaz de transmitir informações de energia do dispositivo (tensão e corrente), o que possibilita uma manutenção eficiente e o monitoramento da saúde energética dos nós a distância.  

---

### 4. Desafio: Proteção do Equipamento
A instalação em locais remotos e sem vigilância expõe o equipamento a riscos de furto.  

**Melhoria Planejada:** Adição de um sensor de presença (PIR). Esta funcionalidade, quando combinada com o GPS do dispositivo, poderá alertar sobre movimentação nas proximidades, funcionando como uma medida de segurança para proteger o equipamento de furtos e vandalismo.  

# Projeto AURA

**Estação Autônoma de Reconhecimento Ambiental com Transmissão LoRa**  
**Data:** 16 de Julho de 2025  
**Integrantes:** Gabriel da Conceição Miranda, Pedro Henrique Dias Avelar e João Magno Lourenço Soares.

---

## 📌 Descrição do Projeto

O monitoramento ambiental em áreas remotas ou extensas, como em aplicações agrícolas, reservas ecológicas ou bacias hidrográficas, enfrenta um desafio fundamental de conectividade. Soluções tradicionais baseadas em Wi-Fi ou Bluetooth possuem alcance limitado, enquanto alternativas via satélite ou celular apresentam um custo elevado e alto consumo de energia, tornando-as inviáveis para implementações em larga escala e de baixo orçamento.

Essa lacuna tecnológica dificulta a coleta de dados ambientais granulares e em tempo real, informações que são cruciais para a tomada de decisão em agricultura de precisão, pesquisa científica e gestão de desastres naturais. Há uma necessidade clara de um sistema de monitoramento que seja, ao mesmo tempo, de baixo custo, de baixo consumo energético e capaz de transmitir dados a longas distâncias.

Este projeto propõe o desenvolvimento de uma estação de observação ambiental de dois módulos (nó sensor e estação base) que utiliza a tecnologia LoRa (Long Range) para superar essas limitações, permitindo a coleta de dados de forma acessível e confiável em locais sem infraestrutura de comunicação convencional.

---

## 🆔 Por que "AURA"?

O nome **AURA** pode ser interpretado como um acrônimo para:

**Autonomous Unattended Remote Analysis**  
(*Análise Remota Autônoma e Não Monitorada*)

ou

**Autonomous Units for Remote Assessment**  
(*Unidades Autônomas para Avaliação Remota*)

Além disso, o termo "aura" também evoca a ideia de um campo sutil ao redor de algo — uma metáfora apropriada para sensores ambientais que "percebem" mudanças ao seu redor, de forma quase invisível.

---

## ✅ Requisitos do Sistema

### 🔧 Requisitos Funcionais (RF)

- **RF01**: O nó sensor deve coletar dados de sensores ambientais (temperatura, pressão, umidade do ar e do solo, luminosidade, vibração).
- **RF02**: O nó sensor deve transmitir os dados via protocolo LoRa.
- **RF03**: A estação base deve receber os pacotes de dados via LoRa.
- **RF04**: A estação base deve decodificar e exibir os dados recebidos em um display OLED (ou similar).
- **RF05 (Opcional)**: O acelerômetro deve detectar impactos ou vibrações anômalas.
- **RF06 (Opcional)**: O nó sensor pode armazenar leituras em um cartão MicroSD (data logging).
- **RF07 (Opcional)**: A estação base pode incluir um teclado matricial como interface de controle.

### ⚙️ Requisitos Não Funcionais (RNF)

- **RNF01**: Comunicação obrigatoriamente via LoRa, com alcance de quilômetros em linha de visada.
- **RNF02**: O nó sensor deve ser otimizado para baixo consumo de energia (uso de baterias ou painéis solares).
- **RNF03**: O projeto deve ter baixo custo, utilizando componentes comerciais e ESP32.
- **RNF04**: O código será modular, com separação entre sensores, comunicação e interface.
- **RNF05**: A interface da estação base deve ser clara e objetiva.
- **RNF06**: O projeto será desenvolvido fora da plataforma BitDogLab, mas poderá ser integrado futuramente.

---

## 🧰 Lista de Materiais Preliminar

| Componente                           | Quantidade | Função Principal                                             |
|--------------------------------------|------------|--------------------------------------------------------------|
| Placa Heltec WiFi LoRa 32 V3        | 2          | 1x Nó Sensor (TX), 1x Estação Base (RX)                     |
| Sensor de Temp., Pressão, Umidade   | 1          | Medição de dados atmosféricos                               |
| Sensor de Umidade do Solo Capacitivo| 1          | Medição da umidade do solo                                   |
| Sensor de Luminosidade              | 1          | Medição de luz ambiente                                     |
| Acelerômetro e Giroscópio           | 1          | Detecção de vibração/anomalias                              |
| Módulo Leitor de Cartão MicroSD     | 1          | (Opcional) Armazenamento local de dados                     |
| Teclado Matricial 4x4               | 1          | (Opcional) Interface de controle para estação base          |
| Protoboard e Jumpers                | 1 (kit)    | Montagem e conexões de prototipagem                         |
| Fonte de Alimentação / Bateria     | 2          | Alimentação dos módulos durante o desenvolvimento           |

---

## 🚀 Objetivo

Oferecer uma alternativa viável, escalável e de baixo custo para o monitoramento ambiental em locais remotos, com foco na autonomia energética, simplicidade de uso e robustez na comunicação.

---

## 📚 Plataforma de Desenvolvimento

- **Microcontrolador:** ESP32 (Heltec LoRa 32 V3)
- **Ambiente de Desenvolvimento:** Arduino IDE / VS Code + PlatformIO
- **Protocolos de Comunicação:** LoRa
- **Interface local:** Display OLED (integrado) + [Opcional] Teclado Matricial
- **Armazenamento:** [Opcional] Cartão MicroSD

---

## 📅 Status Atual

- ✅ Definição de escopo e requisitos
- 🔧 Início da prototipagem com sensores e comunicação LoRa
- 📦 Planejamento modular do código e interfaces
- 🚧 Integração futura com armazenamento e controle local (opcional)


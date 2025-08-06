# 🌤️ Projeto AURA: Rede Meteorológica de Baixo Custo com Meshtastic

**Data:** 06 de Agosto de 2025  
**Integrantes:** Gabriel da Conceição Miranda, Pedro Henrique Dias Avelar e João Magno Lourenço Soares

---

## 📌 Descrição do Projeto

O Projeto AURA propõe uma solução inovadora para a coleta de dados ambientais em áreas rurais e remotas. Utilizando estações meteorológicas de baixo custo e alta autonomia energética, conectadas por uma rede **LoRa Mesh com o framework Meshtastic**, o sistema oferece **monitoramento climático de microescala** em tempo real, sem depender de infraestrutura celular ou Wi-Fi.

Esses dados são transmitidos a um servidor central via **MQTT**, possibilitando **análises históricas** e **previsões de chuva** com alta precisão para áreas específicas, como fazendas, bacias hidrográficas e reservas ecológicas.

---

## 🌧️ A Importância da Previsão de Chuva no Campo

- **Otimização da Irrigação**  
- **Planejamento Logístico Agrícola**  
- **Aplicação Inteligente de Defensivos Agrícolas**  
- **Prevenção de Doenças por Umidade**  

Previsões climáticas localizadas ajudam na economia de recursos e na proteção da produção.

---

## 🚀 Vantagens Estratégicas do Projeto

- **💰 Baixo Custo de Hardware**  
- **🔋 Baixo Consumo de Energia (deep sleep + solar)**  
- **📡 Grande Cobertura com Rede Mesh Meshtastic**  
- **🧩 Sistema Escalável e Modular**  

---

## 🧠 O Papel do Meshtastic

- **Rede Mesh Autônoma:** Nós se reorganizam dinamicamente.  
- **Módulo de Telemetria Integrado:** Coleta de dados nativa via sensores.  
- **Gateway MQTT:** Envia dados LoRa da rede para um broker MQTT (local ou na nuvem).  

---

## ✅ Requisitos Funcionais

- **RF01:** Coletar dados de temperatura, pressão, luminosidade e UV.  
- **RF02:** Transmitir dados via LoRa Mesh com Meshtastic.  
- **RF03:** Encaminhar dados para broker MQTT via nó gateway.  
- **RF04:** Armazenar os dados recebidos em um banco de dados para análise.  
- **RF05 (Opcional):** Notificação por sensor de presença (PIR).  

---

## ⚙️ Requisitos Não Funcionais

- **RNF01:** Comunicação obrigatoriamente via rede Mesh LoRa.  
- **RNF02:** Consumo energético otimizado (modo deep sleep).  
- **RNF03:** Uso de componentes de baixo custo e ESP32.  
- **RNF04:** Integração modular com sensores via Meshtastic.  
- **RNF05:** Interface de visualização simples e clara.  
- **RNF06:** Desenvolvimento fora da BitDogLab, mas com possibilidade de futura integração.  

---

## 🧰 Lista de Materiais

| Componente                            | Quantidade | Função Principal                                                    |
|--------------------------------------|------------|---------------------------------------------------------------------|
| Placa Heltec WiFi LoRa 32 V3         | 2+         | 1x Gateway MQTT, 1x ou mais nós sensores                            |
| Sensor BME280                         | 1 por nó   | Temperatura, Umidade e Pressão                                      |
| Sensor de Luz e UV (LTR-390)         | 1 por nó   | Luminosidade e Índice UV                                            |
| Sensor de Luz Alternativo (ex: OPT3001) | 1 por nó   | Alternativa para medição precisa da luz ambiente                    |
| Sensor PIR (HC-SR501)                | 1 (opcional) | Detecção de presença (alerta de segurança)                         |
| Bateria / Fonte / Painel Solar       | 1 por nó   | Alimentação autônoma dos módulos em campo                           |
| Raspberry Pi 4 (ou similar)          | 1 (opcional) | Hospedagem local do broker MQTT e banco de dados                   |
| Protoboard e Jumpers                 | 1 kit       | Conexões de prototipagem                                            |

---

## 🎯 Objetivo

Desenvolver e implantar uma **rede meteorológica escalável**, **de baixo custo** e **autônoma em energia**, baseada em **LoRa Mesh com Meshtastic**, para fornecer dados de microclima em tempo real e auxiliar decisões inteligentes em **aplicações agrícolas e ambientais**.

---

## 📚 Plataforma de Desenvolvimento

- **Microcontrolador:** ESP32 (Heltec WiFi LoRa 32 V3)  
- **Firmware:** [Meshtastic](https://meshtastic.org) (configurável via app ou interface web)  
- **Protocolos:** LoRa Mesh, MQTT  
- **Sensores:** Comunicação via I²C  
- **Backend:** Broker MQTT (ex: Mosquitto), Banco de Dados (ex: InfluxDB), Visualização (ex: Grafana)  

---

> Este projeto representa um passo significativo na democratização do acesso à informação meteorológica de precisão, especialmente em regiões de difícil conectividade.

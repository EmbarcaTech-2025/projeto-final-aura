# 🌤️ Projeto AURA: Guia de Instalação e Arquitetura do Sistema

## 1. Visão Geral

O Projeto AURA cria uma rede de monitoramento climático de baixo custo, ideal para áreas remotas. Este guia irá orientá-lo no processo de instalação do firmware **Meshtastic** nos seus dispositivos LoRa e na configuração do **Home Assistant** como sua central de dados e automação.

## 2. Instalação e Configuração

Para utilizar o projeto, você precisará configurar dois componentes principais, os dispositivos da rede Meshtastic e o servidor Home Assistant.

### 2.1. Configurando os Dispositivos Meshtastic (Nós Sensores e Gateway)

Cada dispositivo de rádio LoRa (como o Heltec WiFi LoRa 32 V3) precisa ter o firmware Meshtastic instalado. O método mais simples é usar o instalador via web.

#### **Passo 1: Instalação do Firmware**
Você pode seguir o guia de build/flash oficial: https://meshtastic.org/docs/development/firmware/build/

Ou pode seguir o seguinte processo (instalador web):

1.  **Conecte o dispositivo LoRa** ao seu computador via cabo USB.
2.  **Acesse o Instalador Web:** Abra o navegador Google Chrome ou Microsoft Edge e acesse o [Meshtastic Web Flasher](https://flasher.meshtastic.org).
3.  **Selecione o Dispositivo:** A página geralmente detectará seu dispositivo automaticamente. Escolha o modelo correto na lista (ex: `Heltec V3`).
4.  **Escolha a Versão do Firmware:** Selecione a versão mais recente e estável (`Stable`).
5.  **Instale:** Clique em "Install" e siga as instruções na tela para selecionar a porta serial correta e iniciar o processo. Em poucos minutos, o firmware estará instalado.

#### **Passo 2: Configuração Inicial via Aplicativo**

Após instalar o firmware, você precisa configurar cada dispositivo usando o aplicativo Meshtastic, que se conecta via Bluetooth.

1.  **Baixe o Aplicativo:** Instale o aplicativo Meshtastic em seu smartphone (disponível para [Android](https://play.google.com/store/apps/details?id=com.geeksville.mesh) e [iOS](https://apps.apple.com/us/app/meshtastic/id1586431213)).
2.  **Emparelhe com o Dispositivo:** Ative o Bluetooth no seu celular, abra o aplicativo e procure por novos dispositivos. Selecione seu rádio Meshtastic para emparelhar. Um código pode ser exibido na tela OLED do dispositivo para confirmação.
3.  **Configurações Essenciais:**
    * **Região (Region):** No aplicativo, vá para "Configurações" -> "LoRa" e defina a região correta para sua localização (`BR` para o Brasil). Isso é crucial para que os rádios operem na frequência permitida.
    * **Canal (Channel):** Para que seus dispositivos se comuniquem eles precisam estar no mesmo canal. Você pode manter o canal padrão ou criar um novo com nome e chave de criptografia personalizados para uma rede privada.
4.  **Ativar o Módulo de Telemetria (Para os Nós Sensores):**
    * Vá para "Configurações" -> "Módulos" -> "Telemetria".
    * **Ative o módulo** e defina o **"Intervalo de atualização"** (ex: 300 segundos para enviar dados a cada 5 minutos). O Meshtastic detectará automaticamente os sensores I2C conectados (como BME280).
5.  **Configurar o Nó Gateway:**
    * Para o dispositivo que será sua ponte com o Home Assistant, vá para "Configurações" -> "Módulos" -> "MQTT".
    * **Ative o MQTT** e marque a opção **"Habilitado como proxy MQTT"**.
    * Insira o **endereço IP** do seu servidor Home Assistant e as credenciais do seu Broker MQTT (que você configurará no próximo passo).

### 2.2. Configurando o Home Assistant como Central de Dados

O Home Assistant será o que recebe, armazena e age com base nos dados climáticos. A forma mais recomendada de instalá-lo é usando o **Home Assistant OS**.

#### **Passo 1: Instalação do Home Assistant OS**

1.  **Escolha o Hardware:** Um Raspberry Pi 4 (com 4GB+ de RAM) ou um mini PC são excelentes opções. Você precisará de um cartão SD ou SSD para a instalação.
2.  **Grave a Imagem:**
    * Acesse a [página oficial de instalação do Home Assistant](https://www.home-assistant.io/installation/).
    * Selecione seu tipo de hardware e baixe a imagem do sistema operacional.
    * Use uma ferramenta como o [Raspberry Pi Imager](https://www.raspberrypi.com/software/) ou [BalenaEtcher](https://www.balena.io/etcher/) para gravar a imagem no seu cartão SD/SSD.
3.  **Primeira Inicialização:**
    * Insira o SD/SSD no seu dispositivo, conecte um cabo de rede e ligue-o.
    * Aguarde alguns minutos. Em seu computador, acesse `http://homeassistant.local:8123` no navegador.
    * Siga o processo de criação de conta e configuração inicial (localização, unidades, etc.).

#### **Passo 2: Configuração do Broker MQTT**

O Home Assistant precisa de um extensão para receber as mensagens do seu Gateway Meshtastic. Faremos isso instalando o **Mosquitto Broker**.

1.  **Acesse a Loja de Add-ons:** No menu do Home Assistant, vá para "Configurações" -> "Add-ons" -> "Loja de Add-ons".
2.  **Instale o Mosquitto:** Procure por "Mosquitto broker" e clique em "Instalar".
3.  **Configure o Broker:**
    * Após a instalação, vá para a aba "Configuração" do add-on.
    * Para facilitar, nós disponibilizamos os arquivos de configuração prontos. Você pode encontrá-los no diretório de configuração deste projeto. Faça o download e utilize-os para configurar seu Broker e a integração MQTT. Isso garantirá que o usuário e as permissões sejam criados corretamente para a comunicação com a rede Meshtastic.

#### **Passo 3: Integração MQTT no Home Assistant**

1.  **Adicione a Integração:** Vá para "Configurações" -> "Dispositivos e Serviços" e clique em "+ Adicionar Integração".
2.  Procure por "MQTT" e selecione-o. O Home Assistant geralmente descobrirá o broker que você acabou de instalar. Siga os passos e forneça as credenciais que você criou.

Com isso, seu sistema está pronto para receber os dados. Agora você pode criar as entidades de sensor no seu arquivo `configuration.yaml` para visualizar e usar os dados da sua rede AURA.

## 3. Visão Geral da Arquitetura do Sistema

Basicamente, o sistema AURA opera em três partes:

1.  **Coleta de Dados (Nós Sensores):**
    * Dispositivos de campo, equipados com sensores I2C (ex: BME280 para temperatura/pressão, LTR-390 para UV), são controlados pelo firmware Meshtastic.
    * Em intervalos de tempo pré-configurados, o dispositivo "acorda" do modo de baixo consumo (*deep sleep*), realiza a leitura dos sensores e formata os dados em um pacote de telemetria.
2.  **Comunicação (Rede LoRa Mesh e Gateway):**
    * O pacote de telemetria é transmitido via rádio LoRa. A natureza "mesh" da rede Meshtastic permite que outros nós retransmitam essa mensagem, aumentando drasticamente o alcance e a confiabilidade da comunicação, contornando obstáculos.
    * Um nó específico, o **Gateway**, está posicionado para ter acesso tanto à rede LoRa quanto a uma rede Wi-Fi local. Sua função é "escutar" os pacotes de telemetria da rede e atuar como uma ponte.
3.  **Processamento (Home Assistant):**
    * O Gateway converte os dados do pacote LoRa para o formato JSON e os publica em um tópico específico no **Broker MQTT** que roda no Home Assistant.
    * O Home Assistant, que está "inscrito" nesse tópico, recebe os dados instantaneamente. As leituras são mapeadas para "entidades" dentro do sistema, permitindo que sejam usadas em painéis de visualização, gráficos históricos e, mais importante, como gatilhos para automações inteligentes (ex: acionar irrigação, enviar alertas de geada, etc.).


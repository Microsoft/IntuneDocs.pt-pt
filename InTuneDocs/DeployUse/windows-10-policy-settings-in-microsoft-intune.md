---
title: "Definições de políticas do Windows 10 | Microsoft Intune"
description: 
keywords: 
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 00a602d9-b339-4fd8-ab70-defbf6686855
ms.reviewer: heenamac
ms.suite: ems
ms.sourcegitcommit: 1cccafa5f740bad50779ae36c899fd23ee7dc5f3
ms.openlocfilehash: 70347776f72a3534a4c384957aef01a909767b99


---

# Definições de política do Windows 10 no Microsoft Intune

Utilize as definições de política indicadas neste tópico para ajudá-lo a configurar as definições para dispositivos com o ambiente de trabalho Windows 10 e o Windows 10 Mobile inscritos.

## Definições de política de configuração geral

Utilize a **política de configuração geral** do Microsoft Intune para Windows 10 para configurar as definições gerais para dispositivos com o ambiente de trabalho Windows 10 e o Windows 10 Mobile inscritos. Não é possível utilizar esta política quando gere PCs com o Windows 10 com o software do cliente Intune.


### Palavra-passe

|Nome da definição|Detalhes|
|----------------|----------------------|
|**Pedir uma palavra-passe para desbloquear dispositivos**|Exigir uma palavra-passe em dispositivos suportados.|
|**Tipo obrigatório de palavra-passe**|Especifica o tipo de palavra-passe que será necessária, como apenas numérica ou alfanumérica|
|**Tipo obrigatório de palavra-passe** - **Número mínimo de conjuntos de carateres**|Existem quatro conjuntos de carateres, letras minúsculas, letras maiúsculas, números e símbolos. Esta definição especifica quantos conjuntos de carateres diferentes têm de ser incluídos na palavra-passe.|
|**Comprimento mínimo da palavra-passe**|Especifica o número mínimo de carateres que a palavra-passe do utilizador tem de ter.<br>(Apenas Windows 10 Mobile)|
|**Número de falhas de início de sessão consecutivas a permitir antes do dispositivo ser apagado**|Apaga o dispositivo em caso de falha deste número de tentativas de início de sessão.|
|**Minutos de inatividade antes de o ecrã se desligar**|Especifica o período de tempo durante o qual o dispositivo tem de estar inativo antes de o ecrã ser bloqueado.|
|**Expiração da Palavra-passe (dias)**|Especifica o período de tempo após o qual a palavra-passe do dispositivo tem de ser alterada.|
|**Memorizar histórico de palavras-passe**|Especifica se pretende impedir que o utilizador final crie palavras-passe utilizadas anteriormente.|
|**Memorizar histórico de palavras-passe** - **Evita a reutilização de palavras-passe anteriores**|Especifica o número de palavras-passe utilizadas anteriormente memorizadas pelo dispositivo.|
|**Permitir palavra-passe por imagem e PIN**|Permite-lhe utilizar gestos simples numa imagem ou um PIN simples para iniciar sessão.<br>(apenas para ambiente de trabalho Windows 10)|
|**Exigir uma palavra-passe quando o dispositivo regressa de um estado inativo**|Se estiver ativada, o utilizador tem de introduzir uma palavra-passe para desbloquear o dispositivo de um estado inativo.<br>(Apenas Windows 10 Mobile)|

### Encriptação

|Nome da definição|Detalhes|
|----------------|----------------------|
|**Encriptação obrigatória no dispositivo móvel**|Ativa a encriptação nos dispositivos visados.<br>(Apenas Windows 10 Mobile)|

### Sistema

|Nome da definição|Detalhes|
|----------------|----------------------|
|**Permitir captura de ecrã**|Permite que o utilizador efetue uma captura do ecrã do dispositivo como uma imagem.<br>(Apenas Windows 10 Mobile)|
|**Permitir anular inscrições manualmente**|Permite que o utilizador elimine manualmente a conta da área de trabalho do dispositivo.|
|**Permitir instalação do certificado de raiz manual**|Especifica se o utilizador pode instalar manualmente certificados de raiz.<br>(Apenas Windows 10 Mobile)|
|**Permitir que os dados de diagnóstico e de utilização sejam enviados à Microsoft**|Determina a quantidade de dados de diagnóstico e de utilização que são enviadas à Microsoft a partir dos dispositivos.<br><br>**Não** - Não são enviados dados à Microsoft<br>**Básico** - O dispositivo envia apenas informações limitadas à Microsoft<br>**Melhorado** - Envia dados de diagnóstico melhorados à Microsoft<br>**Completo (recomendado)** -Envia os mesmos dados que **Melhorado**, juntamente com dados adicionais sobre o estado do dispositivo|


### Conta e sincronização

|Nome da definição|Detalhes|
|----------------|----------------------|---------------------|
|**Permitir conta Microsoft**|Permite que o utilizador associe uma conta Microsoft ao dispositivo.|
|**Permitir adicionar contas de terceiros manualmente**|Permite que o utilizador adicione contas de e-mail ao dispositivo, que não estão associadas a uma conta Microsoft.|
|**Permitir a sincronização de definições para contas Microsoft**|Permite que as definições do dispositivo e de aplicações associadas a uma conta Microsoft sejam sincronizadas entre dispositivos.|

### Definições de e-mail

|Nome da definição|Detalhes|
|----------------|----------------------|---------------------|
|**Torne a conta Microsoft opcional na aplicação Windows Mail**|Configure esta definição para remover o requisito de uma conta Microsoft no Windows Mail.<br>Apenas para ambiente de trabalho Windows 10|



### Microsoft Edge

|Nome da definição|Detalhes|
|----------------|----------------------|
|**Permitir browser**|Permite a utilização do browser Edge no dispositivo.<br>(Apenas Windows 10 Mobile)|
|**Permitir sugestões de pesquisa na barra de endereço**|Permite que o motor de busca sugira sites à medida que escreve expressões de pesquisa.|
|**Permitir o envio de tráfego da intranet para o Internet Explorer**|Permite que os utilizadores abram sites da intranet no Internet Explorer.<br>(apenas para ambiente de trabalho Windows 10)|
|**Permitir não controlar**|Configura o browser Edge para enviar cabeçalhos Do Not Track para sites que os utilizadores visitam.|
|**Ativar SmartScreen**|Permite a definição de browser SmartScreen nos dispositivos.|
|**Permitir scripting ativo**|Permite a execução de scripts, como JavaScript, no browser Edge.|
|**Permitir pop-ups**|Ativa ou desativa o bloqueador de janelas pop-up do browser.<br>(apenas para ambiente de trabalho Windows 10)|
|**Permitir cookies**|Permitir ou desativar cookies.|
|**Permitir Preenchimento Automático**|Permite que os utilizadores alterem as definições de conclusão automática no browser.<br>(apenas para ambiente de trabalho Windows 10)|
|**Permitir Gestor de Palavras-passe**|Ativar ou desativar a funcionalidade Gestor de Palavras-passe do Edge.|
|**Localização da lista de sites do Modo Empresarial**|Especifica onde encontrar a lista de Web sites que serão abertos no modo Empresarial. Os utilizadores não podem editar esta lista.<br>(apenas para ambiente de trabalho Windows 10)|

### Aplicações

|Nome da definição|Detalhes|
|----------------|----------------------|---------------------|
|**Permitir loja de aplicações**|Permite que o utilizador aceda à loja de aplicações no dispositivo.<br>(Apenas Windows 10 Mobile)|



### Rede móvel

|Nome da definição|Detalhes|
|----------------|----------------------|---------------------|
|**Permitir roaming de dados**|Permitir roaming entre redes ao aceder a dados.|
|**Permitir VPN sobre redes móveis**|Controla se o dispositivo pode aceder a ligações VPN quando ligado a uma rede celular.|
|**Permitir roaming do VPN sobre redes móveis**|Controla se o dispositivo pode aceder a ligações VPN quando está em roaming numa rede celular.|

### Hardware

|Nome da definição|Detalhes|
|----------------|----------------------|
|**Permitir câmara**|Especifica se a câmara do dispositivo pode ser utilizada.|
|**Permitir armazenamento amovível**|Especifica se os dispositivos de armazenamento externo, como um cartão SD, podem ser utilizados com o dispositivo.|
|**Permitir Wi-Fi**|Permite a utilização da capacidade Wi-Fi dos dispositivos.<br>(Apenas Windows 10 Mobile)|
|**Permitir partilha da internet**|Permite a utilização da partilha de ligação à Internet no dispositivo.|
|**Permitir configuração de Wi-Fi manual**|Controla se o utilizador pode configurar as suas próprias ligações Wi-F ou se podem utilizar apenas as ligações configuradas por um perfil Wi-Fi.<br>(Apenas Windows 10 Mobile)|
|**Permitir ligação automática a hotspots Wi-Fi**|Permite que o dispositivo ligue automaticamente a hotspots Wi-Fi gratuitos e aceite automaticamente os termos e condições para a ligação.|
|**Permitir geolocalização**|Especifica se o dispositivo pode utilizar informações de serviços de localização.|
|**Permitir NFC**|Permite que o dispositivo utilize as capacidades de comunicação de proximidade.|
|**Permitir Bluetooth**|Permite a utilização das capacidades de Bluetooth no dispositivo.|
|**Permitir modo detetável do Bluetooth**|Permite que este dispositivo seja detetado por outros dispositivos com capacidade de Bluetooth.|
|**Permitir publicidade do Bluetooth**|Permite que os dispositivos recebam anúncios sobre o Bluetooth.|
|**Permitir modo conectável do Bluetooth**|**Importante:** o Windows 10 já não suporta esta definição, que será removida no futuro.|
|**Permitir reposição do telefone**|Controla se o utilizador pode efetuar a reposição de fábrica do seu dispositivo.|
|**Permitir ligação USB**|Controla se os dispositivos podem aceder a dispositivos de armazenamento externo através de uma ligação USB.|
|**Permitir modo Anti-roubo**|Configurar se o modo Anti-roubo do Windows estiver ativado.|

### Funcionalidades

|Nome da definição|Detalhes|
|----------------|----------------------|---------------------|
|**Permitir copiar e colar**|Ativar ou desativar a utilização das ações copiar e colar no dispositivo.<br>(Apenas Windows 10 Mobile)|
|**Permitir gravação de chamadas**|Ativar ou desativar as funcionalidades de gravação de voz no dispositivo.<br>(Apenas Windows 10 Mobile)|
|**Permitir Cortana**|Ativar ou desativar o assistente de voz Cortana.|
|**Permitir notificações de centro de ação**|Ativar ou desativar notificações do centro de ação no ecrã de bloqueio do dispositivo.<br>(Apenas Windows 10 Mobile)|

### Defender

Todas as definições são apenas para ambiente de trabalho Windows 10.

|Nome da definição|Detalhes|
|-|-|
|**Permitir monitorização em tempo real**|Permite a análise em tempo real de software maligno, spyware e outro software indesejável.|
|**Permitir monitorização de comportamento**|Permite que o Defender verifique a existência de determinados padrões conhecidos de atividade suspeita nos dispositivos.|
|**Ativar o Sistema de Inspeção de Rede**|O Sistema de Inspeção de Rede (NIS) ajuda a proteger os dispositivos contra exploits baseados na rede, utilizando as assinaturas de vulnerabilidades conhecidas do Microsoft Endpoint Protection Center para ajudar a detetar e a bloquear tráfego malicioso.|
|**Analisar todas as transferências**|Controla se o Defender analisa todos os ficheiros transferidos da Internet.|
|**Permitir análise de script**|Permite que o Defender analise os scripts que são utilizados no Internet Explorer.|
|**Monitorizar a atividade dos ficheiros e programas**|Ative esta definição para permitir que o Defender monitorize a atividade de programas e ficheiros nos dispositivos.|
|**Dias para controlar o software maligno resolvido**|Permite que o Defender continue a controlar o software maligno resolvido durante o número de dias que especificar, para que possa verificar manualmente os dispositivos afetados anteriormente. Se definir o número de dias como **0**, o software maligno permanece na pasta Quarentena e não é removido automaticamente. |
|**Permitir o acesso à IU de cliente**|Controla se a interface de utilizador do Windows Defender está ocultada dos utilizadores finais.<br>Quando esta definição é alterada, será aplicada da próxima vez que o PC do utilizador final for reiniciado.|
|**Agendar uma análise rápida diária**|Permite agendar uma análise rápida que ocorre diariamente à hora que selecionar.|
|**Agendar uma análise do sistema**|Permite agendar uma análise completa ou rápida do sistema, que ocorre regularmente no dia e na hora que selecionar.|
|**Limitar a utilização da CPU durante a análise**|Permite limitar a quantidade de CPU que as análises estão autorizadas a utilizar (de **1** a **100**)|
|**Analisar ficheiros de arquivo**|Permite que o Defender analise os ficheiros arquivados, tais como ficheiros Zip ou Cab.|
|**Analisar mensagens de e-mail**|Permite que o Defender analise mensagens de e-mail quando chegam ao dispositivo.|
|**Analisar unidades amovíveis**|Permite que o Defender analise unidades amovíveis, como pens USB.|
|**Analisar unidades de rede mapeadas**|Permite que o Defender analise ficheiros em unidades de rede mapeadas.<br>Se os ficheiros na unidade forem só de leitura, o Defender não conseguirá remover qualquer software maligno encontrado nos mesmos.|
|**Analisar ficheiros abertos a partir de pastas partilhadas na rede**|Permite que o Defender analise ficheiros em unidades de rede partilhadas (por exemplo, aquelas às quais o acesso é feito a partir de um caminho UNC.<br>Se os ficheiros na unidade forem só de leitura, o Defender não conseguirá remover qualquer software maligno encontrado nos mesmos.|
|**Intervalo de atualização de assinatura**|Especifique o intervalo no qual o Defender irá verificar a existência de novos ficheiros de assinatura.|
|**Permitir proteção da nuvem**|Permitir ou impedir que o Serviço de Proteção Ativa Microsoft receba informações sobre a atividade de software maligno nos dispositivos que gere. Estas informações são utilizadas para melhorar o serviço no futuro.|
|**Solicitar aos utilizadores o envio de amostras**|Controla se os ficheiros que possam exigir análise adicional pela Microsoft para determinar se são maliciosos são automaticamente enviados à Microsoft.|
|**Deteção de Aplicação Potencialmente Indesejável**|Esta definição pode ser utilizada para proteger computadores de secretária Windows inscritos contra software em execução classificado pelo Windows Defender como potencialmente indesejado. Pode proteger contra estas aplicações em execução ou utilizar o modo de auditoria para relatar quando uma aplicação potencialmente indesejável é instalada.|
|**Ficheiros e pastas a serem excluídos ao executar uma análise ou utilizar a proteção em tempo real**|Adicione um ou mais ficheiros e pastas, como **C:\Path** ou **%ProgramFiles%\Path\filename.exe** à lista de exclusões. Estes ficheiros e pastas não serão incluídos em análises em tempo real ou agendadas.|
|**Extensões de ficheiro a serem excluídas ao executar uma análise ou ao utilizar a proteção em tempo real**|Adicione uma ou mais extensões de ficheiro, como **jpg** ou **txt**, à lista de exclusões. Quaisquer ficheiros com estas extensões não serão incluídos em análises em tempo real ou agendadas.|
|**Processos a serem excluídos ao executar uma análise ou ao utilizar a proteção em tempo real**|Adicione um ou mais processos do tipo **.exe**, **.com** ou **.scr** à lista de exclusões. Estes processos não serão incluídos em análises em tempo real ou agendadas.| 


### Definições das atualizações

|Nome da definição|Detalhes|
|----------------|---------------|
|**Permitir atualizações automáticas**|Ative esta definição para permitir atualizações automáticas. Em seguida, configure uma das seguintes definições para controlar o comportamento da atualização:<br /><br />**Notificar carregamento**<br /><br />**Instalação automática ao tempo de manutenção**<br /><br />**Instalação automática e reinicio ao tempo de manutenção**<br /><br />**Instalação automática e reinício à hora agendada** **Nota**: quando esta opção está selecionada, também pode configurar as seguintes definições: **Suprimir a notificação para o utilizador final** e **Definir o dia da instalação de atualizações agendadas**.<br>(apenas para ambiente de trabalho Windows 10)|

## Definições de política personalizada
Utilize a **política de configuração personalizada** do Microsoft Intune para Windows 10 e Windows 10 Mobile para implementar definições OMA-URI (Open Mobile Alliance Uniform Resource Identifier) que podem ser utilizadas para controlar as funcionalidades nos dispositivos Windows 10 e Windows 10 Mobile. Tratam-se de definições padrão utilizadas por inúmeros fabricantes de dispositivos móveis para controlar as funcionalidades dos dispositivos.

Esta capacidade destina-se a permitir a implementação de definições do Windows 10 que não são configuráveis com uma política de configuração geral do Intune.



### Definições gerais de política personalizada

|Nome da definição|Detalhes|
    |----------------|--------------------|
    |**Nome**|Introduza um nome exclusivo para a política para o ajudar a identificá-la na consola do Intune.|
    |**Descrição**|Indique uma descrição geral da política e outras informações relevantes que poderão ajudá-lo a localizá-la.|

### Definições OMA-URI de política personalizada

|Nome da definição|Detalhes|
    |--------|--------------------|
    |**Nome da definição**|Introduza um nome exclusivo para a definição OMA-URI para o ajudar a identificá-la na lista de definições.|
    |**Descrição da definição**|Indique uma descrição geral da definição e outras informações relevantes para o ajudar a localizá-la.|
    |**Tipo de dados**|Selecione o tipo de data em que especificará esta definição OMA-URI. Escolha entre:<br /><br />-   **Cadeia**<br />-   **Cadeia (XML)**<br />-   **Data e Hora**<br />-   **Número inteiro**<br />-   **Vírgula flutuante**<br />-   **Booleano**|
    |**OMA-URI (sensível às maiúsculas e minúsculas)**|Especifique o OMA-URI para o qual pretende fornecer uma definição.|
    |**Valor**|Indique o valor a associar ao OMA-URI especificado anteriormente.|


## Definições personalizadas de URI para dispositivos Windows 10
Este tópico lista as definições que pode configurar em dispositivos Windows 10 e Windows 10 Mobile numa **Política Personalizada do Windows 10** do Microsoft Intune.

Se pretender utilizar a Política de URI Personalizada do Windows, todos os dispositivos têm de ser inscritos no Intune.

### Definições de política de URI

|Nome da política|Detalhes|
|---------------|------------|-----------|
|**​Permitir Atualização Automática**<br>(apenas ambiente de trabalho)|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Update/AllowAutoUpdate<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br>**0** - **5** (predefinição: **1**)|
|**Agendar Dia da Instalação**<br>(apenas dispositivos móveis)|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Update/ScheduledInstallDay<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br>**0** - Todos os dias (predefinição)<br>**1** - Domingo<br>**2** - Segunda-feira<br>**3** - Terça-feira<br>**4** - Quarta-feira<br>**5** - Quinta-feira<br>**6** - Sexta-feira<br>**7** - Sábado|
|**Agendar Hora da Instalação**<br>(ambiente de trabalho e dispositivos móveis)|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Update/ScheduledInstallTime<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br>**0** – **23** horas (**0** é meia-noite) (predefinição: **3**)|
|**DeviceLock/AllowIdleReturnWithoutPassword**<br>(apenas dispositivos móveis)|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/DeviceLock/AllowIdleReturnWithoutPassword<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br>**0** - o utilizador não consegue definir o temporizador do período de tolerância da palavra-passe e o valor é definido como "sempre"<br>**1** - o utilizador consegue definir o temporizador do período de tolerância da palavra-passe (predefinição)|
|**WiFi/AllowWiFi**<br>(apenas dispositivos móveis)|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/WiFi/AllowWiFi<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br>**0** – não permitir a **utilização de ligação Wi-Fi**.<br>**1** –** permitir a utilização de ligação Wi-Fi** (predefinição)|
|**WiFi/AllowInternetSharing**<br>(ambiente de trabalho e dispositivos móveis)|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/WiFi/AllowInternetSharing<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br>**0** – não permitir Partilha da Internet.<br>**1** – permitir Partilha da Internet (predefinição)|
|**WiFi/AllowAutoConnectToWiFiSenseHotspots**<br>(ambiente de trabalho e dispositivos móveis)|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/WiFi/AllowAutoConnectToWiFiSenseHotspots<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br>**0** – não permitido<br>**1** – permitido (predefinição)|
|**WiFi/AllowManualWiFiConfiguration**<br>(apenas dispositivos móveis)|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/WiFi/AllowManualWiFiConfiguration<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br>**0** – não é permitida uma ligação Wi-Fi fora da MDM aprovisionada.<br>**1** – é permitido adicionar novos SSIDs de rede para além dos que já são aprovisionados pelo MDM (predefinição)|
|**System/AllowLocation**<br>(ambiente de trabalho e dispositivos móveis)|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/System/AllowLocation<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br>**0** – não permitido<br>**1** – permitido (predefinição)|
|**System/AllowTelemetry**<br>(ambiente de trabalho e dispositivos móveis)|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/System/AllowTelemetry<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br>**0** – não permitido (definição apenas para empresas)<br>**1** – limitado<br>**2** – completo (predefinição)<br>**3** - completo e informações de diagnóstico|
|**System/AllowExperimentation**<br>(ambiente de trabalho e dispositivos móveis)|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/System/AllowExperimentation<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br>**0** – não permitido<br>**1**- apenas definições (predefinição)<br>**2**- definições e experimentação|
|**Security/AntiTheftMode**<br>(apenas dispositivos móveis)|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Security/AntiTheftMode<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br>**0** - não permitir modo Anti Roubo<br>**1** - preferência do utilizador (predefinição)|
|**Connectivity/AllowUSBConnection**<br>(apenas dispositivos móveis)|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Connectivity/AllowUSBConnection<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br>**0** – não permitido<br>**1** – permitido (predefinição)|
|**System/AllowUserToResetPhone**<br>(apenas dispositivos móveis)|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/System/AllowUserToResetPhone<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br>**0** – não permitido<br>**1** – permitido (predefinição)|
|**Connectivity/AllowCellularDataRoaming**<br>(ambiente de trabalho e dispositivos móveis)|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Connectivity/AllowCellularDataRoaming<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br>**0** – não permitido<br>**1** – permitido (predefinição)|
|**Connectivity/AllowVPNOverCellular**<br>(ambiente de trabalho e dispositivos móveis)|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Connectivity/AllowVPNOverCellular<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br>**0** - não é permitida VPN por rede móvel<br>**1** – a VPN pode utilizar qualquer ligação, incluindo rede móvel (predefinição)|
|**Connectivity/AllowVPNRoamingOverCellular**<br>(apenas dispositivos móveis)|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Connectivity/AllowVPNRoamingOverCellular<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br>**0** – não permitido<br>**1** – permitido (predefinição)|
|**Connectivity/AllowVPNRoamingOverCellular**<br>(apenas dispositivos móveis)|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Connectivity/AllowVPNRoamingOverCellular<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br>**0** – não permitido<br>**1** – permitido (predefinição)|
|**Connectivity/AllowBluetooth**<br>(ambiente de trabalho e dispositivos móveis)|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Connectivity/AllowBluetooth<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br>**0** – não permitir que o utilizador ligue o Bluetooth.<br>**1** – reservado. O utilizador pode ligar e configurar o Bluetooth (não suportado no Windows Phone 8.1 para MDM, EAS, ambiente de trabalho do Windows 10 ou Windows 10 Mobile)<br>**2** - permitido. O utilizador pode ligar e configurar o Bluetooth (predefinição)|
|**Experience/AllowScreenCapture**<br>(apenas dispositivos móveis)|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Experience/AllowScreenCapture<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br>**0** – não permitido<br>**1** – permitido (predefinição)|
|**Experience/AllowTaskSwitcher**<br>(apenas dispositivos móveis)|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Experience/AllowTaskSwitcher<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br>**0** – não permitido<br>**1** – permitido (predefinição)|
|**Experience/AllowVoiceRecording**<br>(apenas dispositivos móveis)|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Experience/AllowVoiceRecording<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br>**0** – não permitido<br>**1** – permitido (predefinição)|
|**Experience/AllowSyncMySettings**<br>(apenas dispositivos móveis)|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Experience/AllowSyncMySettings<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br>**0** – não permitir roaming<br>**1** – permitir roaming (predefinição)|
|**Experience/AllowManualMDMUnenrollment**<br>(ambiente de trabalho e dispositivos móveis)|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Experience/AllowManualMDMUnenrollment<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br>**0** – não permitido<br>**1** – permitido (predefinição)|
|**Accounts/AllowMicrosoftAccountConnection**<br>(ambiente de trabalho e dispositivos móveis)|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Accounts/AllowMicrosoftAccountConnection<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br>**0** – não permitido<br>**1** – permitido (predefinição)|
|**Accounts/AllowAddingNonMicrosoftAccountsManually**<br>(ambiente de trabalho e dispositivos móveis)|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Accounts/AllowAddingNonMicrosoftAccountsManually<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br>**0** – não permitido<br>**1** – permitido (predefinição)|
|**Security/AllowManualRootCertificateInstallation**<br>(apenas dispositivos móveis)|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Security/AllowManualRootCertificateInstallation<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br>**0** – não permitido<br>**1** – permitido (predefinição)|
|**Security/AllowAddProvisioningPackages**<br>(ambiente de trabalho e dispositivos móveis)|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Security/AllowAddProvisioningPackages<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br>**0** – não permitido<br>**1** – permitido (predefinição)|
|**Search/DisableBackoff**<br>(ambiente de trabalho e dispositivos móveis)|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Search/DisableBackoff<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br>**0** (predefinição)<br>**1**|
|**Search/PreventRemoteQueries**<br>(ambiente de trabalho e dispositivos móveis)|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Search/PreventRemoteQueries<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br>**0**<br>**1** (predefinição)|
|**Search/AllowUsingDiacritics**<br>(ambiente de trabalho e dispositivos móveis)|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Search/AllowUsingDiacritics<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br> **0** (predefinição)<br>**1**|
|**Search/AlwaysUseAutoLangDetection**<br>(ambiente de trabalho e dispositivos móveis)|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Search/AlwaysUseAutoLangDetection<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br>**0** (predefinição)<br>**1**|
|**Search/DisableRemovableDriveIndexing**<br>(ambiente de trabalho e dispositivos móveis)|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Search/DisableRemovableDriveIndexing<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br>**0** (predefinição)<br>**1**|
|**Search/PreventIndexingLowDiskSpaceMB**<br>(ambiente de trabalho e dispositivos móveis)|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Search/PreventIndexingLowDiskSpaceMB<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br>**0**<br>**1** (predefinição)|
|**Search/AllowIndexingEncryptedStoresOrItems**<br>(ambiente de trabalho e dispositivos móveis)|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Search/AllowIndexingEncryptedStoresOrItems<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br>**0** (predefinição)<br>**1**|
|**Security/AllowRemoveProvisioningPackage**<br>(ambiente de trabalho e dispositivos móveis)|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Security/AllowRemoveProvisioningPackage<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br>**0** – não permitido<br>**1** – permitido (predefinição)|
|**Security/RequireProvisioningPackageSignature**<br>(ambiente de trabalho e dispositivos móveis)|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Security/RequireProvisioningPackageSignature<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br>**0** (predefinição)<br>**1**|
|**AboveLock/AllowActionCenterNotifications**<br>(ambiente de trabalho e dispositivos móveis)|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/AboveLock/AllowActionCenterNotifications<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br>**0** – não permitido<br>**1** – permitido (predefinição)|
|**TextInput/AllowIMENetworkAccess**<br>(apenas ambiente de trabalho)|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/TextInput/AllowIMENetworkAccess<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br>**0** – não permitir<br>O Dicionário Expandido Aberto está desativado.<br>O utilizador não pode:<br>Adicionar um novo Dicionário Expandido Aberto<br /><br />Adicionar um novo ficheiro de configuração de integração de pesquisa<br>Utilizar a funcionalidade de candidato na nuvem<br>Enviar palavras registadas pelo utilizador<br>Além disso,<br>Um Dicionário Expandido Aberto que tenha sido adicionado antes da ativação desta definição de política não é utilizado para conversão.<br>Um ficheiro de configuração de integração de pesquisa que tenha sido instalado antes da ativação desta definição de política não é utilizado.<br>**1** - permitir<br>É possível adicionar e utilizar um Dicionário Expandido Aberto como predefinição. Além disso, a função de integração de pesquisas pode ser utilizada como predefinição.<br>O utilizador pode:<br>Utilizar a funcionalidade de candidato na nuvem<br>Enviar palavras registadas pelo utilizador.|
|**TextInput/AllowIMELogging**<br>(apenas ambiente de trabalho)|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/TextInput/AllowIMELogging<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br>**0** - o registo de conversões incorretas está desativado. Os dados otimizados automaticamente e os dados do histórico de entradas não são guardados num ficheiro.<br>**1** - o registo de conversões incorretas está ativado. Os dados otimizados automaticamente e os dados do histórico de entradas são guardados num ficheiro (predefinição)|
|**TextInput/AllowJapaneseNonPublishingStandardGlyph**<br>(apenas ambiente de trabalho)|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/TextInput/AllowJapaneseNonPublishingStandardGlyph<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br>**0** – não permitido<br>**1** – permitido (predefinição)|
|**TextInput/AllowJapaneseIVSCharacters**<br>(apenas ambiente de trabalho)|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/TextInput/AllowJapaneseIVSCharacters<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br>**0** – não permitido<br>**1** – permitido (predefinição)|
|**TextInput/AllowJapaneseUserDictionary**<br>(apenas ambiente de trabalho)|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/TextInput/AllowJapaneseUserDictionary<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br>**0** – não permitido<br>**1** – permitido (predefinição)|
|**TextInput/AllowJapaneseIMESurrogatePairCharacters**<br>(apenas ambiente de trabalho)|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/TextInput/AllowJapaneseIMESurrogatePairCharacters<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br>**0** – não permitido<br>**1** – permitido (predefinição)|
|**TextInput/ExcludeJapaneseIMEExceptShiftJIS**<br>(apenas ambiente de trabalho)|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/TextInput/ExcludeJapaneseIMEExceptShiftJIS<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br>**0** - não é filtrado nenhum caráter (predefinição)<br>**1** - são filtrados todos os carateres, exceto os Shift JIS|
|**TextInput/ExcludeJapaneseIMEExceptJIS0208**<br>(apenas ambiente de trabalho)|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/TextInput/ExcludeJapaneseIMEExceptJIS0208<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br /><br />**0** - não é filtrado nenhum caráter (predefinição)<br>**1** - são filtrados todos os carateres, exceto os JIS0208|
|**TextInput/ExcludeJapaneseIMEExceptJIS0208andEUDC**<br>(apenas ambiente de trabalho)|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/TextInput/ExcludeJapaneseIMEExceptJIS0208andEUDC<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br>**0** - não é filtrado nenhum caráter (predefinição)<br>**1** - são filtrados todos os carateres, exceto os JIS0208 ou os EUDC|
|**TextInput/AllowInputPanel**<br>(apenas ambiente de trabalho)|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/TextInput/AllowInputPanel<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br>**0** – não permitido<br>**1** – permitido (predefinição)|
|**Bluetooth/AllowDiscoverableMode**<br>(ambiente de trabalho e dispositivos móveis)|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Bluetooth/AllowDiscoverableMode<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br>**0** – não permitido<br>**1** – permitido (predefinição)|
|**Bluetooth/AllowAdvertising**<br>(ambiente de trabalho e dispositivos móveis)|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Bluetooth/AllowAdvertising<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br>**0** – não permitido<br>**1** – permitido (predefinição)|
|**Settings/AllowDataSense**<br>(ambiente de trabalho e dispositivos móveis)|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Settings/AllowDataSense<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br>**0** – não permitido<br>**1** – permitido (predefinição)|
|**Settings/AllowVPN**<br>(ambiente de trabalho e dispositivos móveis)|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Settings/AllowVPN<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br>**0** – não permitido<br>**1** – permitido (predefinição)|
|**Settings/AllowWorkplace**<br>(apenas ambiente de trabalho)|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Settings/AllowWorkplace<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br>**0** – não permitido<br>**1** – permitido (predefinição)|
|**Settings/AllowDateTime**<br>(ambiente de trabalho e dispositivos móveis)|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Settings/AllowDateTime<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br>**0** – não permitido<br>**1** – permitido (predefinição)|
|**Settings/AllowLanguage**<br>(apenas ambiente de trabalho)|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Settings/AllowLanguage<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br>**0** – não permitido<br>**1** – permitido (predefinição)|
|**Settings/AllowRegion**<br>(apenas ambiente de trabalho)|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Settings/AllowRegion<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br>**0** – não permitido<br>**1** – permitido (predefinição)|
|**Settings/AllowSignInOptions**<br>(apenas ambiente de trabalho)|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Settings/AllowSignInOptions<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br>**0** – não permitido<br>**1** – permitido (predefinição)|
|**Settings/AllowYourAccount**<br>(ambiente de trabalho e dispositivos móveis)|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Settings/AllowYourAccount<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br>**0** – não permitido<br>**1** – permitido (predefinição)|
|**Settings/AllowPowerSleep**<br>(apenas ambiente de trabalho)|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Settings/AllowPowerSleep<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br>**0** – não permitido<br>**1** – permitido (predefinição)|
|**Settings/AllowAutoPlay**<br>(apenas ambiente de trabalho)|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Settings/AllowAutoPlay<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br>**0** – não permitido<br>**1** – permitido (predefinição)|
|**Experience/AllowCortana**<br>(ambiente de trabalho e dispositivos móveis)|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Experience/AllowCortana<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br>**0** – não permitido<br>**1** – permitido (predefinição)|
|**Search/SafeSearchPermissions**<br>(apenas dispositivos móveis)|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Search/SafeSearchPermissions<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br>**0** – rígida, filtragem mais estrita de conteúdos para adultos<br>**1** – moderada, filtragem moderada de conteúdos para adultos (os resultados de pesquisa válidos não serão filtrados - predefinição)|
|**Experience/AllowCopyPaste**<br>(apenas ambiente de trabalho)|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Experience/AllowCopyPaste<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br>**0** – não permitido<br>**1** – permitido (predefinição)|
|**Forçar Tamanho Inicial**<br>(apenas dispositivos móveis)|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Start/ForceStartSize<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br>**0** - permitir que o utilizador altere o tamanho (predefinição)<br>**1** - forçar não utilização do ecrã inteiro<br>**2** - forçar ecrã inteiro|
|**Atualização/RequireDeferUpgrade**<br>(ambiente de trabalho e dispositivos móveis)|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Update/RequireDeferUpgrade<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br>**0**: não difere da atualização (mantenha-se no ramo atual, CB - predefinição)<br>**1**: permite que as atualizações sejam adiadas (o dispositivo segue o ramo atual para empresa, CBB, regras)<br /><br />Para obter mais informações, consulte:<br>[Introdução à manutenção do Windows](https://technet.microsoft.com/library/mt598226.aspx)<br>[Plano de implementação do Windows 10](https://technet.microsoft.com/library/mt574241.aspx)|
|**Atualização/DeferUpdatePeriod**<br>(ambiente de trabalho e dispositivos móveis)|**Descrição:** política para diferir atualizações de software para até quatro semanas<br /><br />**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Update/DeferUpdatePeriod<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br> **0**: aplicar atualizações imediatamente (predefinição)<br>**1**-**4**: número de semanas para diferir atualizações de software.<br /><br />Para obter mais informações, consulte:<br>[Introdução à manutenção do Windows](https://technet.microsoft.com/library/mt598226.aspx)<br>[Plano de implementação do Windows 10](https://technet.microsoft.com/library/mt574241.aspx)|
|**Atualização/DeferUpgradePeriod**<br>(ambiente de trabalho e dispositivos móveis)|**Descrição:** política para diferir atualizações de funcionalidade para até oito meses<br /><br />**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Update/DeferUpgradePeriod<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br>**0**: aplicar atualizações imediatamente (predefinição)<br>**1**-**8**: número de meses para diferir atualizações de funcionalidade.<br /><br />Para obter mais informações, consulte:<br>[Introdução à manutenção do Windows](https://technet.microsoft.com/library/mt598226.aspx)<br>[Plano de implementação do Windows 10](https://technet.microsoft.com/library/mt574241.aspx)|
|**Atualização/PauseDeferrals**<br>(ambiente de trabalho e dispositivos móveis)|**Descrição:** permite que uma máquina CBB deixe de receber atualizações durante cinco semanas. Isto deve ser utilizado caso exista um problema com uma atualização.<br /><br />**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Update/PauseDeferrals<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br>**0**: aplicar atualizações imediatamente (predefinição)<br>**1**: colocar atualizações em pausa (expira após cinco semanas)|

### Definições de URI do Windows Defender

|Nome da política|Detalhes|
|---------------|-----------|
|**AllowRealtimeMonitoring**<br>(apenas ambiente de trabalho)|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Defender/AllowRealtimeMonitoring<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br>**0** – não permitido<br>**1** – permitido (predefinição)|
|**AllowBehaviorMonitoring**<br>(apenas ambiente de trabalho)|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Defender/AllowBehaviorMonitoring<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br>**0** – não permitido<br>**1** – permitido (predefinição)|
|**AllowIntrusionPreventionSystem**<br>(apenas ambiente de trabalho)|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Defender/AllowIntrusionPreventionSystem<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br>**0** – não permitido<br>**1** – permitido (predefinição)|
|**AllowIOAVProtection**<br>(apenas ambiente de trabalho)|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Defender/AllowIOAVProtection<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br>**0** – não permitido<br>**1** – permitido (predefinição)|
|**AllowScriptScanning**<br>(apenas ambiente de trabalho)|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Defender/AllowScriptScanning<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br>**0** – não permitido<br>**1** – permitido (predefinição)|
|**AllowOnAccessProtection**<br>(apenas ambiente de trabalho)|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Defender/AllowOnAccessProtection<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br>**0** – não permitido<br>**1** – permitido (predefinição)|
|**RealTimeScanDirection**<br>(apenas ambiente de trabalho)|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Defender/RealTimeScanDirection<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br>**0** – monitorizar todos os ficheiros (bidirecional - predefinição)<br>**1** – monitorizar ficheiros recebidos<br>**2** – monitorizar ficheiros enviados|
|**DaysToRetainCleanedMalware**<br>(apenas ambiente de trabalho)|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Defender/DaysToRetainCleanedMalware<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br>**0** - **90** – representa o período de retenção do software maligno<br>**Valor predefinido:** **0** – mantém na pasta de quarentena indefinidamente e não remove automaticamente|
|**AllowUserUIAccess**<br>(apenas ambiente de trabalho)|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Defender/AllowUserUIAccess<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br>**0** – não permitido<br>**1** – permitido (predefinição)|
|**ScanParameter**<br>(apenas ambiente de trabalho)|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Defender/ScanParameter<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br>**1** – análise rápida (predefinição)<br>**2** - análise completa|
|**ScheduleScanDay**<br>(apenas ambiente de trabalho)|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Defender/ScheduleScanDay<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br>**0** -todos os dias (predefinição)<br>**1** - Segunda-feira<br>**2** - Terça-feira<br>**3** - Quarta-feira<br>**4** - Quinta-feira<br>**5** - Sexta-feira<br>**6** - Sábado<br>**7** - Domingo<br>**8** – nenhuma análise agendada|
|**ScheduleScanTime**<br>(apenas ambiente de trabalho)|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Defender/ScheduleScanTime<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br>**0** - 24:00<br>**60** – 01:00<br>**120** – 2:00 (predefinição)<br>**180** – 03:00<br>**240** – 04:00<br>**300** – 05:00<br>**360** – 06:00<br>**420** – 07:00<br>**480** – 08:00<br>**540** – 09:00<br>**600** – 10:00<br>**660** – 11:00<br>**720** – 12:00<br>**780** – 13:00<br>**840** – 14:00<br>**900** – 15:00<br>**960** – 16:00<br>**1020** – 17:00<br>**1080** – 18:00<br>**1140** – 19:00<br>**1200** – 20:00<br>**1260** – 21:00<br>**1320** – 22:00<br>**1381** – janela de manutenção|
|**ScheduleQuickScanTime**<br>(apenas ambiente de trabalho)|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Defender/ScheduleQuickScanTime<br>**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br>**0** - 24:00<br>**60** – 01:00<br>**120** – 2:00 (predefinição)<br>**180** – 03:00<br>**240** – 04:00<br>**300** – 05:00<br>**360** – 06:00<br>**420** – 07:00<br>**480** – 08:00<br>**540** – 09:00<br>**600** – 10:00<br>**660** – 11:00<br>**720** – 12:00<br>**780** – 13:00<br>**840** – 14:00<br>**900** – 15:00<br>**960** – 16:00<br>**1020** – 17:00<br>**1080** – 18:00<br>**1140** – 19:00<br>**1200** – 20:00<br>**1260** – 21:00<br>**1320** – 22:00<br>**1380** – 23:00|
|**AVGCPULoadFactor**<br>(apenas ambiente de trabalho)|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Defender/AVGCPULoadFactor<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:0** - **100** (predefinição: **50**)|
|**AllowArchiveScanning**<br>(apenas ambiente de trabalho)|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Defender/AllowArchiveScanning<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br>**0** – não permitido<br>**1** – permitido (predefinição)|
|**AllowEmailScanning**<br>(apenas ambiente de trabalho)|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Defender/AllowEmailScanning<br /><br />**Tipo de dados:** Número inteiro<br>**Valores permitidos:**<br>**0** – não permitido (predefinição)<br>**1** – permitido|
|**AllowFullScanRemovableDriveScanning**<br>(apenas ambiente de trabalho)|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Defender/AllowFullScanRemovableDriveScanning<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br>**0** – não permitido (predefinição)<br>**1** – permitido|
|**AllowFullScanOnMappedNetworkDrives**<br>(apenas ambiente de trabalho)|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Defender/AllowFullScanOnMappedNetworkDrives<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br>**0** – não permitido<br>**1** – permitido (predefinição)|
|**AllowScanningNetworkFiles**<br>(apenas ambiente de trabalho)|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Defender/AllowScanningNetworkFiles<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br>**0** – não permitido<br>**1** – permitido (predefinição) - também é executada quando o RTP está definido como permitido|
|**SignatureUpdateInterval**<br>(apenas ambiente de trabalho)|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Defender/SignatureUpdateInterval<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br>**0** – não verificar assinaturas num intervalo<br>**1** - verificar assinaturas a cada hora<br>**2** – verificar assinaturas a cada duas horas, etc.<br>**24** – verificar assinaturas todos os dias<br>**Valor predefinido:** 8 – verificar assinaturas a cada oito horas|
|**AllowCloudProtection**<br>(apenas ambiente de trabalho)|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Defender/AllowCloudProtection<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br>**0** – não permitido<br>**1** – permitido (predefinição)|
|**SubmitSamplesConsent**<br>(apenas ambiente de trabalho)|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Defender/SubmitSamplesConsent<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br>**0** – perguntar sempre (predefinição)<br>**1** – enviar automaticamente amostras seguras<br>**2** – nunca enviar<br>**1** – enviar automaticamente todas as amostras|
|**ExcludedExtensions**<br>(apenas ambiente de trabalho)|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Defender/ExcludedExtensions<br /><br />**Tipo de dados:** Cadeia<br /><br />**Valores permitidos:**<br>*&lt;lista de extensões separadas por ponto e vírgula&gt;* Por exemplo, **obj;lib**<br>**Predefinição**: não é excluída nenhuma extensão|
|**ExcludedPaths**<br>(apenas ambiente de trabalho)|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Defender/ExcludedPaths<br /><br />**Tipo de dados:** Cadeia<br /><br />**Valores permitidos:**<br /><br />*&lt;lista de caminhos separados por ponto e vírgula&gt;*<br /><br />Exemplo: **c:\test;c:\test1.exe**<br /><br />**Valor predefinido:** Não são excluídos caminhos|
|**ExcludedProcesses**<br>(apenas ambiente de trabalho)|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Defender/ExcludedProcesses<br /><br />**Tipo de dados:** Cadeia<br /><br />**Valores permitidos:**<br>*&lt;lista de caminhos separados por ponto e vírgula&gt;*<br>Exemplo: **c:\test.exe;c:\test1.exe**<br>**Valor predefinido:** Não são excluídos processos|

### Definições de URI do browser Edge

|Nome da política|Detalhes|
|---------------|------------|-----------|
|**Permitir Browser**<br>(apenas dispositivos móveis)|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Browser/AllowBrowser<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br>**0**: navegação desativada<br>**1**: navegação ativada (predefinição)|
|**AllowSearchSuggestionsinAddressBar**<br>(ambiente de trabalho e dispositivos móveis)|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Browser/AllowSearchSuggestionsinAddressBar<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br>**0**: não mostrar sugestões de pesquisa<br>**1**: mostrar sugestões de pesquisa (predefinição)|
|**SendIntranetTraffictoInternetExplorer**<br>(apenas ambiente de trabalho)|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Browser/SendIntranetTraffictoInternetExplorer<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br>**0**: desativado (abrir sites da intranet no browser Edge - predefinição)<br>**1** - ativado (abrir sites da intranet no Internet Explorer).|
|**Permitir Não Controlar**<br>(ambiente de trabalho e dispositivos móveis)|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Browser/AllowDoNotTrack<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br>**0** – desativado (DNT não enviado - predefinição)<br>**1** – ativado (enviar DNT)|
|**Configurar SmartScreen**<br>(ambiente de trabalho e dispositivos móveis)|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Browser/AllowSmartScreen<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br>**0** – não permitir<br>**1** – permitir (predefinição)|
|**Permitir Pop-ups**<br>(apenas ambiente de trabalho)|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Browser/AllowPopups<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br>**0** – bloquear pop-ups (predefinição)<br>**1** – permitir pop-ups|
|**Permitir Cookies**<br>(ambiente de trabalho e dispositivos móveis)|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Browser/AllowCookies<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br>**0** – não Bloquear. Permitir cookies de todos os Web sites (predefinição)<br>**1** – bloquear apenas cookies de terceiros<br>**2** – bloquear todos os cookies|
|**Permitir Guardar Palavra-passe**<br>(ambiente de trabalho e dispositivos móveis)|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Browser/AllowPasswordManager<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br>**0** – o gestor de palavras-passe está desativado; <br>**1** – o gestor de palavras-passe está ativado (predefinição)|
|**Permitir Preenchimento Automático**<br>(apenas ambiente de trabalho)|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Browser/AllowAutofill<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br>**0** – desativado (predefinição)<br>**1** – ativado|
|**Configurar a Lista de Sites da Empresa**<br>(apenas ambiente de trabalho)|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Browser/EnterpriseModeSiteList<br /><br />**Tipo de dados:** Cadeia<br /><br />**Valores permitidos:<br>0** – não configurado<br>**1** – utilizar a lista de sites de modo empresarial do IE, se estiver configurada (predefinição)<br>**2**  – especificar a localização da lista de sites da empresa|

### Consulte também
[Gerir definições e funcionalidades nos seus dispositivos com as políticas do Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)




<!--HONumber=Jun16_HO3-->



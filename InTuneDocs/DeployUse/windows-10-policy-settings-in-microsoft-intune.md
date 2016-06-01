---
# required metadata

title: Definições de política do Windows 10 no Microsoft Intune | Microsoft Intune
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

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Definições de política do Windows 10 no Microsoft Intune

Utilize as definições de política indicadas neste tópico para ajudá-lo a configurar as definições para dispositivos com o ambiente de trabalho Windows 10 e o Windows 10 Mobile inscritos.

## Definições de política de configuração geral

Utilize a **política de configuração geral** Microsoft para Windows 10, para configurar as definições gerais para dispositivos com o ambiente de trabalho Windows 10 e o Windows 10 Mobile inscritos:


### Palavra-passe

|Nome da definição|Detalhes|Windows 10 Desktop|Windows 10 Mobile|
|----------------|----------------------|---------------------|
|**Pedir uma palavra-passe para desbloquear dispositivos**|Exigir uma palavra-passe em dispositivos suportados.|Sim|Sim|
|**Tipo obrigatório de palavra-passe**|Especifica o tipo de palavra-passe que será necessária, como apenas numérica ou alfanumérica|Sim|Sim|
|**Tipo obrigatório de palavra-passe** - **Número mínimo de conjuntos de carateres**|Existem quatro conjuntos de carateres, letras minúsculas, letras maiúsculas, números e símbolos. Esta definição especifica quantos conjuntos de carateres diferentes têm de ser incluídos na palavra-passe.|Sim|Sim|
|**Comprimento mínimo da palavra-passe**|Especifica o número mínimo de carateres que a palavra-passe do utilizador tem de ter.|Não|Sim|
|**Número de falhas de início de sessão consecutivas a permitir antes do dispositivo ser apagado**|Apaga o dispositivo em caso de falha deste número de tentativas de início de sessão.|Sim|Sim|
|**Minutos de inatividade antes de o ecrã se desligar**|Especifica o período de tempo durante o qual o dispositivo tem de estar inativo antes de o ecrã ser bloqueado.|Sim|Sim|
|**Expiração da Palavra-passe (dias)**|Especifica o período de tempo após o qual a palavra-passe do dispositivo tem de ser alterada.|Sim|Sim|
|**Memorizar histórico de palavras-passe**|Especifica se pretende impedir que o utilizador final crie palavras-passe utilizadas anteriormente.|Sim|Sim|
|**Memorizar histórico de palavras-passe** - **Evita a reutilização de palavras-passe anteriores**|Especifica o número de palavras-passe utilizadas anteriormente memorizadas pelo dispositivo.|Sim|Sim|
|**Permitir palavra-passe por imagem e PIN**|Permite-lhe utilizar gestos simples numa imagem ou um PIN simples para iniciar sessão.|Sim|Não|
|**Exigir uma palavra-passe quando o dispositivo regressa de um estado inativo**|Se estiver ativada, o utilizador tem de introduzir uma palavra-passe para desbloquear o dispositivo de um estado inativo.|Não|Sim|

### Encriptação

|Nome da definição|Detalhes|Windows 10 Desktop|Windows 10 Mobile|
|----------------|----------------------|---------------------|
|**Encriptação obrigatória no dispositivo móvel**|Ativa a encriptação nos dispositivos visados.|Não|Sim|

### Sistema

|Nome da definição|Detalhes|Windows 10 Desktop|Windows 10 Mobile|
|----------------|----------------------|---------------------|
|**Permitir captura de ecrã**|Permite que o utilizador efetue uma captura do ecrã do dispositivo como uma imagem.|Não|Sim|
|**Permitir anular inscrições manualmente**|Permite que o utilizador elimine manualmente a conta da área de trabalho do dispositivo.|Sim|Sim|
|**Permitir instalação do certificado de raiz manual**|Especifica se o utilizador pode instalar manualmente certificados de raiz|Não|Sim|
|**Permitir que os dados de diagnóstico e de utilização sejam enviados à Microsoft**|Determina a quantidade de dados de diagnóstico e de utilização que são enviadas à Microsoft a partir dos dispositivos.<br>**Não** - Não são enviados dados à Microsoft<br>**Básico** - O dispositivo envia apenas informações limitadas à Microsoft<br>**Melhorado** - Envia dados de diagnóstico melhorados à Microsoft<br>**Completo (recomendado)** -Envia os mesmos dados que **Melhorado**, juntamente com dados adicionais sobre o estado do dispositivo|Sim|Sim|


### Conta e sincronização

|Nome da definição|Detalhes|Windows 10 Desktop|Windows 10 Mobile|
|----------------|----------------------|---------------------|
|**Permitir conta Microsoft**|Permite que o utilizador associe uma conta Microsoft ao dispositivo.|Sim|Sim|
|**Permitir adicionar contas de terceiros manualmente**|Permite que o utilizador adicione contas de e-mail ao dispositivo, que não estão associadas a uma conta Microsoft.|Sim|Sim|
|**Permitir a sincronização de definições para contas Microsoft**|Permite que as definições do dispositivo e de aplicações associadas a uma conta Microsoft sejam sincronizadas entre dispositivos.|Sim|Sim|

### Definições de e-mail

|Nome da definição|Detalhes|Windows 10 Desktop|Windows 10 Mobile|
|----------------|----------------------|---------------------|
|**Torne a conta Microsoft opcional na aplicação Windows Mail**|Configure esta definição para remover o requisito de uma conta Microsoft no Windows Mail.|Sim|Não|



### Microsoft Edge

|Nome da definição|Detalhes|Windows 10 Desktop|Windows 10 Mobile|
|----------------|----------------------|---------------------|
|**Permitir browser**|Permite a utilização do browser Edge no dispositivo.|Não|Sim|
|**Permitir sugestões de pesquisa na barra de endereço**|Permite que o motor de busca sugira sites à medida que escreve expressões de pesquisa.|Sim|Sim|
|**Permitir o envio de tráfego da intranet para o Internet Explorer**|Permite que os utilizadores abram sites da intranet no Internet Explorer.|Sim|Não|
|**Permitir não controlar**|Configura o browser Edge para enviar cabeçalhos Do Not Track para sites que os utilizadores visitam.|Sim|Sim|
|**Ativar SmartScreen**|Permite a definição de browser SmartScreen nos dispositivos.|Sim|Sim|
|**Permitir scripting ativo**|Permite a execução de scripts, como JavaScript, no browser Edge.|Sim|Sim|
|**Permitir pop-ups**|Ativa ou desativa o bloqueador de janelas pop-up do browser.|Sim|Não|
|**Permitir cookies**|Permitir ou desativar cookies.|Sim|Sim|
|**Permitir Preenchimento Automático**|Permite que os utilizadores alterem as definições de conclusão automática no browser.|Sim|Não|
|**Permitir Gestor de Palavras-passe**|Ativar ou desativar a funcionalidade Gestor de Palavras-passe do Edge.|Sim|Sim|
|**Localização da lista de sites do Modo Empresarial**|Especifica onde encontrar a lista de Web sites que serão abertos no modo Empresarial. Os utilizadores não podem editar esta lista.|Sim|Não|

### Aplicações

|Nome da definição|Detalhes|Windows 10 Desktop|Windows 10 Mobile|
|----------------|----------------------|---------------------|
|**Permitir loja de aplicações**|Permite que o utilizador aceda à loja de aplicações no dispositivo.|Não|Sim|



### Rede móvel

|Nome da definição|Detalhes|Windows 10 Desktop|Windows 10 Mobile|
|----------------|----------------------|---------------------|
|**Permitir roaming de dados**|Permitir roaming entre redes ao aceder a dados.|Sim|Sim|
|**Permitir VPN sobre redes móveis**|Controla se o dispositivo pode aceder a ligações VPN quando ligado a uma rede celular.|Sim|Sim|
|**Permitir roaming do VPN sobre redes móveis**|Controla se o dispositivo pode aceder a ligações VPN quando está em roaming numa rede celular.|Sim|Sim|

### Hardware

|Nome da definição|Detalhes|Windows 10 Desktop|Windows 10 Mobile|
|----------------|----------------------|---------------------|
|**Permitir câmara**|Especifica se a câmara do dispositivo pode ser utilizada.|Sim|Sim|
|**Permitir armazenamento amovível**|Especifica se os dispositivos de armazenamento externo, como um cartão SD, podem ser utilizados com o dispositivo.|Sim|Sim|
|**Permitir Wi-Fi**|Permite a utilização da capacidade Wi-Fi dos dispositivos.|Não|Sim|
|**Permitir partilha da internet**|Permite a utilização da partilha de ligação à Internet no dispositivo.|Sim|Sim|
|**Permitir configuração de Wi-Fi manual**|Controla se o utilizador pode configurar as suas próprias ligações Wi-F ou se podem utilizar apenas as ligações configuradas por um perfil Wi-Fi.|Não|Sim|
|**Permitir ligação automática a hotspots Wi-Fi**|Permite que o dispositivo ligue automaticamente a hotspots Wi-Fi gratuitos e aceite automaticamente os termos e condições para a ligação.|Sim|Sim|
|**Permitir geolocalização**|Especifica se o dispositivo pode utilizar informações de serviços de localização.|Sim|Sim|
|**Permitir NFC**|Permite que o dispositivo utilize as capacidades de comunicação de proximidade.|Sim|Sim|
|**Permitir Bluetooth**|Permite a utilização das capacidades de Bluetooth no dispositivo.|Sim|Sim|
|**Permitir modo detetável do Bluetooth**|Permite que este dispositivo seja detetado por outros dispositivos com capacidade de Bluetooth.|Sim|Sim|
|**Permitir publicidade do Bluetooth**|Permite que os dispositivos recebam anúncios sobre o Bluetooth.|Sim|Sim|
|**Permitir modo passível de ligação Bluetooth** **Importante:** |Esta definição já não é suportada pelo Windows 10 e será removida no futuro.|Sim|Sim|
|**Permitir reposição do telefone**|Controla se o utilizador pode efetuar a reposição de fábrica do seu dispositivo.|Sim|Sim|
|**Permitir ligação USB**|Controla se os dispositivos podem aceder a dispositivos de armazenamento externo através de uma ligação USB.|Sim|Sim|
|**Permitir modo Anti-roubo**|Configurar se o modo Anti-roubo do Windows estiver ativado.|Sim|Sim|

### Funcionalidades

|Nome da definição|Detalhes|Windows 10 Desktop|Windows 10 Mobile|
|----------------|----------------------|---------------------|
|**Permitir copiar e colar**|Ativar ou desativar a utilização das ações copiar e colar no dispositivo.|Não|Sim|
|**Permitir gravação de chamadas**|Ativar ou desativar as funcionalidades de gravação de voz no dispositivo.|Não|Sim|
|**Permitir Cortana**|Ativar ou desativar o assistente de voz Cortana.|Sim|Sim|
|**Permitir notificações de centro de ação**|Ativar ou desativar notificações do centro de ação no ecrã de bloqueio do dispositivo.|Não|Sim|

### Defender

|Nome da definição|Detalhes|Windows 10 Desktop|Windows 10 Mobile|
|-|-|
|**Permitir monitorização em tempo real**|Permite a análise em tempo real de software maligno, spyware e outro software indesejável.|Sim|Não|
|**Permitir monitorização de comportamento**|Permite que o Defender verifique a existência de determinados padrões conhecidos de atividade suspeita nos dispositivos.|Sim|Não
|**Ativar o Sistema de Inspeção de Rede**|O Sistema de Inspeção de Rede (NIS) ajuda a proteger os dispositivos contra exploits baseados na rede, utilizando as assinaturas de vulnerabilidades conhecidas do Microsoft Endpoint Protection Center para ajudar a detetar e a bloquear tráfego malicioso.|Sim|Não
|**Analisar todas as transferências**|Controla se o Defender analisa todos os ficheiros transferidos da Internet.|Sim|Não
|**Permitir análise de script**|Permite que o Defender analise os scripts que são utilizados no Internet Explorer.|Sim|Não
|**Monitorizar a atividade dos ficheiros e programas**|Ative esta definição para permitir que o Defender monitorize a atividade de programas e ficheiros nos dispositivos.|Sim|Não
|**Dias para controlar o software maligno resolvido**|Permite que o Defender continue a controlar o software maligno resolvido durante o número de dias que especificar, para que possa verificar manualmente os dispositivos afetados anteriormente. Se definir o número de dias como **0**, o software maligno permanece na pasta Quarentena e não é removido automaticamente. |Sim|Não
|**Permitir o acesso à IU de cliente**|Controla se a interface de utilizador do Windows Defender está ocultada dos utilizadores finais.<br>Quando esta definição é alterada, será aplicada da próxima vez que o PC do utilizador final for reiniciado.|Sim|Não
|**Agendar uma análise rápida diária**|Permite agendar uma análise rápida que ocorre diariamente à hora que selecionar.|Sim|Não
|**Agendar uma análise do sistema**|Permite agendar uma análise completa ou rápida do sistema, que ocorre regularmente no dia e na hora que selecionar.|Sim|Não
|**Limitar a utilização da CPU durante a análise**|Permite limitar a quantidade de CPU que as análises estão autorizadas a utilizar (de **1** a **100**)|Sim|Não
|**Analisar ficheiros de arquivo**|Permite que o Defender analise os ficheiros arquivados, tais como ficheiros Zip ou Cab.|Sim|Não
|**Analisar mensagens de e-mail**|Permite que o Defender analise mensagens de e-mail quando chegam ao dispositivo.|Sim|Não
|**Analisar unidades amovíveis**|Permite que o Defender analise unidades amovíveis, como pens USB.|Sim|Não
|**Analisar unidades de rede mapeadas**|Permite que o Defender analise ficheiros em unidades de rede mapeadas.<br>Se os ficheiros na unidade forem só de leitura, o Defender não conseguirá remover qualquer software maligno encontrado nos mesmos.|Sim|Não
|**Analisar ficheiros abertos a partir de pastas partilhadas na rede**|Permite que o Defender analise ficheiros em unidades de rede partilhadas (por exemplo, aquelas às quais o acesso é feito a partir de um caminho UNC.<br>Se os ficheiros na unidade forem só de leitura, o Defender não conseguirá remover qualquer software maligno encontrado nos mesmos.|Sim|Não
|**Intervalo de atualização de assinatura**|Especifique o intervalo no qual o Defender irá verificar a existência de novos ficheiros de assinatura.|Sim|Não
|**Permitir proteção da nuvem**|Permitir ou impedir que o Serviço de Proteção Ativa Microsoft receba informações sobre a atividade de software maligno nos dispositivos que gere. Estas informações são utilizadas para melhorar o serviço no futuro.|Sim|Não
|**Solicitar aos utilizadores o envio de amostras**|Controla se os ficheiros que possam exigir análise adicional pela Microsoft para determinar se são maliciosos são automaticamente enviados à Microsoft.|Sim|Não
|**Ficheiros e pastas a serem excluídos ao executar uma análise ou utilizar a proteção em tempo real**|Adicione um ou mais ficheiros e pastas, como **C:\Path** ou **%ProgramFiles%\Path\filename.exe** à lista de exclusões. Estes ficheiros e pastas não serão incluídos em análises em tempo real ou agendadas.|Sim|Não
|**Extensões de ficheiro a serem excluídas ao executar uma análise ou ao utilizar a proteção em tempo real**|Adicione uma ou mais extensões de ficheiro, como **jpg** ou **txt**, à lista de exclusões. Quaisquer ficheiros com estas extensões não serão incluídos em análises em tempo real ou agendadas.|Sim|Não
|**Processos a serem excluídos ao executar uma análise ou ao utilizar a proteção em tempo real**|Adicione um ou mais processos do tipo **.exe**, **.com** ou **.scr** à lista de exclusões. Estes processos não serão incluídos em análises em tempo real ou agendadas.|Sim|Não| 


### Definições das atualizações

|Nome da definição|Detalhes|Windows 10 Desktop|Windows 10 Mobile|
|----------------|---------------|----------------------|---------------------|
|**Permitir atualizações automáticas**|Ative esta definição para permitir atualizações automáticas. Em seguida, configure uma das seguintes definições para controlar o comportamento da atualização:<br /><br />**Notificar carregamento**<br /><br />**Instalação automática ao tempo de manutenção**<br /><br />**Instalação automática e reinicio ao tempo de manutenção**<br /><br />**Instalação automática e reinício à hora agendada** **Nota:** quando esta opção está selecionada, também pode configurar as seguintes definições:  **Suprimir notificação ao utilizador final** e **Definir dia da instalação de atualizações agendadas**.|Sim|Não|

## Definições de política personalizada
Utilize a **política de configuração personalizada** do Microsoft Intune para Windows 10 e Windows 10 Mobile para implementar definições OMA-URI (Open Mobile Alliance Uniform Resource Identifier) que podem ser utilizadas para controlar as funcionalidades nos dispositivos Windows 10 e Windows 10 Mobile. Tratam-se de definições padrão utilizadas por inúmeros fabricantes de dispositivos móveis para controlar as funcionalidades dos dispositivos.

Esta capacidade destina-se a permitir a implementação de definições do Windows 10 que não são configuráveis com uma política de configuração geral do Intune. Para obter informações sobre as definições que pode configurar com estas políticas, consulte [Gerir as definições e funcionalidades nos seus dispositivos com as políticas do Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)..

Para obter uma lista de definições OMA-URI que pode configurar nos dispositivos Windows 10 inscritos, consulte Definições personalizadas de URI para dispositivos Windows 10, mais à frente neste tópico.

### Definições gerais

|Nome da definição|Detalhes|
    |----------------|--------------------|
    |**Nome**|Introduza um nome exclusivo para a política para o ajudar a identificá-la na consola do Intune.|
    |**Descrição**|Indique uma descrição geral da política e outras informações relevantes que poderão ajudá-lo a localizá-la.|

### Definições OMA-URI

|Nome da definição|Detalhes|
    |--------|--------------------|
    |**Nome da definição**|Introduza um nome exclusivo para a definição OMA-URI para o ajudar a identificá-la na lista de definições.|
    |**Descrição da definição**|Indique uma descrição geral da definição e outras informações relevantes para o ajudar a localizá-la.|
    |**Tipo de dados**|Selecione o tipo de data em que especificará esta definição OMA-URI. Escolha entre:<br /><br />-   **Cadeia**<br />-   **Cadeia (XML)**<br />-   **Data e Hora**<br />-   **Número inteiro**<br />-   **Vírgula flutuante**<br />-   **Booleano**|
    |**OMA-URI (sensível às maiúsculas e minúsculas)**|Especifique o OMA-URI para o qual pretende fornecer uma definição.|
    |**Valor**|Indique o valor a associar ao OMA-URI especificado anteriormente.|


## Definições personalizadas de URI para dispositivos Windows 10
Este tópico lista as definições que pode configurar em dispositivos Windows 10 e Windows 10 Mobile numa **Política Personalizável do Windows 10** do Microsoft Intune..


> [!NOTE]
> Na coluna **Suporta** da tabela seguinte, são utilizados os seguintes valores:
> 
> -   **Ambiente de Trabalho** – a definição suporta computadores Windows 10 Professional e Enterprise que só estão inscritos no Intune.
> -   **Móvel** – a definição apenas suporta dispositivos Windows 10 Mobile.
> -   **Ambos** – a definição suporta computadores e dispositivos móveis.
> 
> Se pretender utilizar a Política de URI Personalizada do Windows, todos os dispositivos têm de ser inscritos no Intune.

### Política

|Nome da política|Suporta|Detalhes|
|---------------|------------|-----------|
|**​Permitir Atualização Automática**|Ambiente de Trabalho|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Update/AllowAutoUpdate<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:0** - **5**<br /><br />**Valor predefinido:** 1|
|**Agendar Dia da Instalação**|Ambos|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Update/ScheduledInstallDay<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br /><br />**0** - Todos os dias.<br /><br />**1** - Domingo<br /><br />**2** - Segunda-feira<br /><br />**3** - Terça-feira<br /><br />**4** - Quarta-feira<br /><br />**5** - Quinta-feira<br /><br />**6** - Sexta-feira<br /><br />**7** - Sábado.<br /><br />**Valor predefinido:** 0|
|**Agendar Hora da Instalação**|Ambos|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Update/ScheduledInstallTime<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:0** – **23** horas (0 corresponde a meia-noite)<br /><br />**Valor predefinido:** 3|
|**DeviceLock/AllowIdleReturnWithoutPassword**|Móvel|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/DeviceLock/AllowIdleReturnWithoutPassword<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br /><br />**0** - o utilizador não consegue definir o temporizador do período de tolerância da palavra-passe e o valor é definido como "sempre"<br /><br />**1** - o utilizador consegue definir o temporizador do período de tolerância da palavra-passe<br /><br />**Valor predefinido:** 1|
|**WiFi/AllowWiFi**|Móvel|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/WiFi/AllowWiFi<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br /><br />**0** – Não permitir a **utilização de ligação Wi-Fi**.<br /><br />**1** –** Permitir a utilização de ligação Wi-Fi**.<br /><br />**Valor predefinido:** 1|
|**WiFi/AllowInternetSharing**|Ambos|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/WiFi/AllowInternetSharing<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br /><br />**0** – não permitir Partilha da Internet.<br /><br />**1** – permitir Partilha da Internet<br /><br />**Valor predefinido:** 1|
|**WiFi/AllowAutoConnectToWiFiSenseHotspots**|Ambos|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/WiFi/AllowAutoConnectToWiFiSenseHotspots<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br /><br />**0** – não permitido<br /><br />**1** – permitido<br /><br />**Valor predefinido:** 1|
|**WiFi/AllowManualWiFiConfiguration**|Móvel|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/WiFi/AllowManualWiFiConfiguration<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br /><br />**0** – não é permitida uma ligação Wi-Fi fora da MDM aprovisionada.<br /><br />**1** – é permitido adicionar novos SSIDs de rede para além dos que já são aprovisionados pelo MDM.<br /><br />**Valor predefinido:** 1|
|**System/AllowLocation**|Ambos|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/System/AllowLocation<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br /><br />**0** – não permitido<br /><br />**1** – permitido<br /><br />**Valor predefinido:** 1|
|**System/AllowTelemetry**|Ambos|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/System/AllowTelemetry<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br /><br />**0** – não permitido (definição apenas para empresas)<br /><br />**1** – limitado<br /><br />**2** – completo<br /><br />**3** - completo e informações de diagnóstico<br /><br />**Valor predefinido:** 2|
|**System/AllowExperimentation**|Ambos|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/System/AllowExperimentation<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br /><br />**0** – não permitido<br /><br />**1**- apenas definições<br /><br />**2**- definições e experimentação<br /><br />**Valor predefinido:** 1|
|**Security/AntiTheftMode**|Móvel|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Security/AntiTheftMode<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br /><br />**0** - não permitir modo Anti Roubo<br /><br />**1** - preferência do utilizador<br /><br />**Valor predefinido:** 1|
|**Connectivity/AllowUSBConnection**|Móvel|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Connectivity/AllowUSBConnection<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br /><br />**0** – não permitido<br /><br />**1** – permitido<br /><br />**Valor predefinido:** 1|
|**System/AllowUserToResetPhone**|Móvel|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/System/AllowUserToResetPhone<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br /><br />**0** – não permitido<br /><br />**1** – permitido<br /><br />**Valor predefinido:** 1|
|**Connectivity/AllowCellularDataRoaming**|Ambos|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Connectivity/AllowCellularDataRoaming<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br /><br />**0** – não permitido<br /><br />**1** – permitido<br /><br />**Valor predefinido:** 1|
|**Connectivity/AllowVPNOverCellular**|Ambos|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Connectivity/AllowVPNOverCellular<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br /><br />**0** - não é permitida VPN por rede móvel<br /><br />**1** – a VPN pode utilizar qualquer ligação, incluindo rede móvel.<br /><br />**Valor predefinido:** 1|
|**Connectivity/AllowVPNRoamingOverCellular**|Móvel|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Connectivity/AllowVPNRoamingOverCellular<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br /><br />**0** – não permitido<br /><br />**1** – permitido<br /><br />**Valor predefinido:** 1|
|**Connectivity/AllowVPNRoamingOverCellular**|Móvel|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Connectivity/AllowVPNRoamingOverCellular<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br /><br />**0** – não permitido<br /><br />**1** – permitido<br /><br />**Valor predefinido:** 1|
|**Connectivity/AllowBluetooth**|Ambos|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Connectivity/AllowBluetooth<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br /><br />**0** – não permitir que o utilizador ligue o Bluetooth.<br /><br />**1** – reservado. O utilizador pode ligar e configurar o Bluetooth (não suportado no Windows Phone 8.1 para MDM, EAS, ambiente de trabalho do Windows 10 ou Windows 10 Mobile)<br /><br />**2** - permitido. O utilizador pode ligar e configurar o Bluetooth.<br /><br />**Valor predefinido:** 2|
|**Experience/AllowScreenCapture**|Móvel|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Experience/AllowScreenCapture<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br /><br />**0** – não permitido<br /><br />**1** – permitido<br /><br />**Valor predefinido:** 1|
|**Experience/AllowTaskSwitcher**|Móvel|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Experience/AllowTaskSwitcher<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br /><br />**0** – não permitido<br /><br />**1** – permitido<br /><br />**Valor predefinido:** 1|
|**Experience/AllowVoiceRecording**|Móvel|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Experience/AllowVoiceRecording<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br /><br />**0** – não permitido<br /><br />**1** – permitido<br /><br />**Valor predefinido:** 1|
|**Experience/AllowSyncMySettings**|Móvel|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Experience/AllowSyncMySettings<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br /><br />**0** – não permitir roaming<br /><br />**1** – permitir roaming<br /><br />**Valor predefinido:** 1|
|**Experience/AllowManualMDMUnenrollment**|Ambos|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Experience/AllowManualMDMUnenrollment<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br /><br />**0** – não permitido<br /><br />**1** – permitido<br /><br />**Valor predefinido:** 1|
|**Accounts/AllowMicrosoftAccountConnection**|Ambos|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Accounts/AllowMicrosoftAccountConnection<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br /><br />**0** – não permitido<br /><br />**1** – permitido<br /><br />**Valor predefinido:** 1|
|**Accounts/AllowAddingNonMicrosoftAccountsManually**|Ambos|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Accounts/AllowAddingNonMicrosoftAccountsManually<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br /><br />**0** – não permitido<br /><br />**1** – permitido<br /><br />**Valor predefinido:** 1|
|**Security/AllowManualRootCertificateInstallation**|Móvel|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Security/AllowManualRootCertificateInstallation<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br /><br />**0** – não permitido<br /><br />**1** – permitido<br /><br />**Valor predefinido:** 1|
|**Security/AllowAddProvisioningPackages**|Ambos|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Security/AllowAddProvisioningPackages<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br /><br />**0** – não permitido<br /><br />**1** – permitido<br /><br />**Valor predefinido:** 1|
|**Search/DisableBackoff**|Ambos|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Search/DisableBackoff<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br /><br />**0**<br /><br />**1**<br /><br />**Valor predefinido:** 0|
|**Search/PreventRemoteQueries**|Ambos|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Search/PreventRemoteQueries<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br /><br />**0**<br /><br />**1**<br /><br />**Valor predefinido:** 1|
|**Search/AllowUsingDiacritics**|Ambos|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Search/AllowUsingDiacritics<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br /><br />**0**<br /><br />**1**<br /><br />**Valor predefinido:** 0|
|**Search/AlwaysUseAutoLangDetection**|Ambos|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Search/AlwaysUseAutoLangDetection<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br /><br />**0**<br /><br />**1**<br /><br />**Valor predefinido:** 0|
|**Search/DisableRemovableDriveIndexing**|Ambos|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Search/DisableRemovableDriveIndexing<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br /><br />**0**<br /><br />**1**<br /><br />**Valor predefinido:** 0|
|**Search/PreventIndexingLowDiskSpaceMB**|Ambos|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Search/PreventIndexingLowDiskSpaceMB<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br /><br />**0**<br /><br />**1**<br /><br />**Valor predefinido:** 1|
|**Search/AllowIndexingEncryptedStoresOrItems**|Ambos|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Search/AllowIndexingEncryptedStoresOrItems<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br /><br />**0**<br /><br />**1**<br /><br />**Valor predefinido:** 0|
|**Security/AllowRemoveProvisioningPackage**|Ambos|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Security/AllowRemoveProvisioningPackage<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br /><br />**0** – não permitido<br /><br />**1** – permitido<br /><br />**Valor predefinido:** 1|
|**Security/RequireProvisioningPackageSignature**|Ambos|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Security/RequireProvisioningPackageSignature<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br /><br />**0**<br /><br />**1**<br /><br />**Valor predefinido:** 0|
|**AboveLock/AllowActionCenterNotifications**|Ambos|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/AboveLock/AllowActionCenterNotifications<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br /><br />**0** – não permitido<br /><br />**1** – permitido<br /><br />**Valor predefinido:** 1|
|**TextInput/AllowIMENetworkAccess**|Ambiente de Trabalho|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/TextInput/AllowIMENetworkAccess<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br /><br />**0** – não permitir<br /><br />O Dicionário Expandido Aberto está desativado.<br /><br />O utilizador não pode:<br /><br />Adicionar um novo Dicionário Expandido Aberto<br /><br />Adicionar um novo ficheiro de configuração de integração de pesquisa<br /><br />Utilizar a funcionalidade de candidato na nuvem<br /><br />Enviar palavras registadas pelo utilizador<br /><br />Além disso,<br /><br />Um Dicionário Expandido Aberto que tenha sido adicionado antes da ativação desta definição de política não é utilizado para conversão.<br /><br />Um ficheiro de configuração de integração de pesquisa que tenha sido instalado antes da ativação desta definição de política não é utilizado.<br /><br />**1** - permitir<br /><br />É possível adicionar e utilizar um Dicionário Expandido Aberto como predefinição. Além disso, a função de integração de pesquisas pode ser utilizada como predefinição.<br /><br />O utilizador pode:<br /><br />Utilizar a funcionalidade de candidato na nuvem<br /><br />Enviar palavras registadas pelo utilizador<br /><br />**Valor predefinido:**|
|**TextInput/AllowKoreanExtendedHanja**|Ambiente de Trabalho|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/TextInput/AllowKoreanExtendedHanja<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br /><br />**0** – não permitido<br /><br />**1** – permitido<br /><br />**Valor predefinido:** 1|
|**TextInput/AllowIMELogging**|Ambiente de Trabalho|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/TextInput/AllowIMELogging<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br /><br />**0** - o registo de conversões incorretas está desativado. Os dados otimizados automaticamente e os dados do histórico de entradas não são guardados num ficheiro.<br /><br />**1** - o registo de conversões incorretas está ativado. Os dados otimizados automaticamente e os dados do histórico de entradas são guardados num ficheiro.<br /><br />**Valor predefinido:** 1|
|**TextInput/AllowJapaneseNonPublishingStandardGlyph**|Ambiente de Trabalho|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/TextInput/AllowJapaneseNonPublishingStandardGlyph<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br /><br />**0** – não permitido<br /><br />**1** – permitido<br /><br />**Valor predefinido:** 1|
|**TextInput/AllowJapaneseIVSCharacters**|Ambiente de Trabalho|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/TextInput/AllowJapaneseIVSCharacters<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br /><br />**0** – não permitido<br /><br />**1** – permitido<br /><br />**Valor predefinido:** 1|
|**TextInput/AllowJapaneseUserDictionary**|Ambiente de Trabalho|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/TextInput/AllowJapaneseUserDictionary<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br /><br />**0** – não permitido<br /><br />**1** – permitido<br /><br />**Valor predefinido:** 1|
|**TextInput/AllowJapaneseIMESurrogatePairCharacters**|Ambiente de Trabalho|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/TextInput/AllowJapaneseIMESurrogatePairCharacters<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br /><br />**0** – não permitido<br /><br />**1** – permitido<br /><br />**Valor predefinido:** 1|
|**TextInput/ExcludeJapaneseIMEExceptShiftJIS**|Ambiente de Trabalho|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/TextInput/ExcludeJapaneseIMEExceptShiftJIS<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br /><br />**0** - são filtrados todos os carateres, exceto os JIS<br /><br />**1** - não é filtrado nenhum caráter<br /><br />**Valor predefinido:** 1|
|**TextInput/ExcludeJapaneseIMEExceptJIS0208**|Ambiente de Trabalho|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/TextInput/ExcludeJapaneseIMEExceptJIS0208<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br /><br />**0** - são filtrados todos os carateres, exceto os JIS0208<br /><br />**1** - não é filtrado nenhum caráter<br /><br />**Valor predefinido:** 1|
|**TextInput/ExcludeJapaneseIMEExceptJIS0208andEUDC**|Ambiente de Trabalho|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/TextInput/ExcludeJapaneseIMEExceptJIS0208andEUDC<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br /><br />**0** - são filtrados todos os carateres, exceto os JIS0208 ou os EUDC<br /><br />**1** - não é filtrado nenhum caráter.<br /><br />**Valor predefinido:** 1|
|**TextInput/AllowInputPanel**|Ambiente de Trabalho|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/TextInput/AllowInputPanel<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br /><br />**0** – não permitido<br /><br />**1** – permitido<br /><br />**Valor predefinido:** 1|
|**Bluetooth/AllowDiscoverableMode**|Ambos|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Bluetooth/AllowDiscoverableMode<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br /><br />**0** – não permitido<br /><br />**1** – permitido<br /><br />**Valor predefinido:** 1|
|**Bluetooth/AllowAdvertising**|Ambos|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Bluetooth/AllowAdvertising<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br /><br />**0** – não permitido<br /><br />**1** – permitido<br /><br />**Valor predefinido:** 1|
|**Settings/AllowDataSense**|Ambos|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Settings/AllowDataSense<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br /><br />**0** – não permitido<br /><br />**1** – permitido<br /><br />**Valor predefinido:** 1|
|**Settings/AllowVPN**|Ambos|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Settings/AllowVPN<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br /><br />**0** – não permitido<br /><br />**1** – permitido<br /><br />**Valor predefinido:** 1|
|**Settings/AllowWorkplace**|Ambiente de Trabalho|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Settings/AllowWorkplace<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br /><br />**0** – não permitido<br /><br />**1** – permitido<br /><br />**Valor predefinido:** 1|
|**Settings/AllowDateTime**|Ambos|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Settings/AllowDateTime<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br /><br />**0** – não permitido<br /><br />**1** – permitido<br /><br />**Valor predefinido:** 1|
|**Settings/AllowLanguage**|Ambiente de Trabalho|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Settings/AllowLanguage<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br /><br />**0** – não permitido<br /><br />**1** – permitido<br /><br />**Valor predefinido:** 1|
|**Settings/AllowRegion**|Ambiente de Trabalho|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Settings/AllowRegion<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br /><br />**0** – não permitido<br /><br />**1** – permitido<br /><br />**Valor predefinido:** 1|
|**Settings/AllowSignInOptions**|Ambiente de Trabalho|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Settings/AllowSignInOptions<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br /><br />**0** – não permitido<br /><br />**1** – permitido<br /><br />**Valor predefinido:** 1|
|**Settings/AllowYourAccount**|Ambos|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Settings/AllowYourAccount<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br /><br />**0** – não permitido<br /><br />**1** – permitido<br /><br />**Valor predefinido:** 1|
|**Settings/AllowPowerSleep**|Ambiente de Trabalho|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Settings/AllowPowerSleep<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br /><br />**0** – não permitido<br /><br />**1** – permitido<br /><br />**Valor predefinido:** 1|
|**Settings/AllowAutoPlay**|Ambiente de Trabalho|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Settings/AllowAutoPlay<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br /><br />**0** – não permitido<br /><br />**1** – permitido<br /><br />**Valor predefinido:** 1|
|**Experience/AllowCortana**|Ambos|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Experience/AllowCortana<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br /><br />**0** – não permitido<br /><br />**1** – permitido<br /><br />**Valor predefinido:** 1|
|**Search/SafeSearchPermissions**|Móvel|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Search/SafeSearchPermissions<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br /><br />**0** – rígida, filtragem mais estrita de conteúdos para adultos<br /><br />**1** – moderada, filtragem moderada de conteúdos para adultos (os resultados de pesquisa válidos não serão filtrados)<br /><br />**Valor predefinido:** 1|
|**Experience/AllowCopyPaste**|Móvel|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Experience/AllowCopyPaste<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br /><br />**0** – não permitido<br /><br />**1** – permitido<br /><br />**Valor predefinido:** 1|
|**Forçar Tamanho Inicial**|Móvel|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Start/ForceStartSize<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br /><br />**0** - permitir que o utilizador altere o tamanho<br /><br />**1** - forçar não utilização do ecrã inteiro<br /><br />**2** - forçar ecrã inteiro<br /><br />**Valor predefinido:** 0|
|**Atualização/RequireDeferUpgrade**|Ambos|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Update/RequireDeferUpgrade<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br /><br />**0**: não difere da atualização (mantenha-se no ramo atual, CB)<br /><br />**1**: permite que as atualizações sejam adiadas (o dispositivo segue o ramo atual para empresa, CBB, regras)<br /><br />**Valor predefinido:0**<br /><br />Para obter mais informações, consulte:<br /><br />[Introdução à manutenção do Windows](https://technet.microsoft.com/library/mt598226(v=vs.85).aspx)<br /><br />[Plano de implementação do Windows 10](https://technet.microsoft.com/library/mt574241(v=vs.85).aspx)|
|**Atualização/DeferUpdatePeriod**|Ambos|**Descrição:** política para diferir atualizações de software para até quatro semanas<br /><br />**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Update/DeferUpdatePeriod<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:** 0: aplicar atualizações imediatamente; 1-4: número de semanas para diferir atualizações de software.<br /><br />**Valor predefinido:0**<br /><br /><br />Para obter mais informações, consulte:<br /><br />[Introdução à manutenção do Windows](https://technet.microsoft.com/library/mt598226(v=vs.85).aspx)<br /><br />[Plano de implementação do Windows 10](https://technet.microsoft.com/library/mt574241(v=vs.85).aspx)|
|**Atualização/DeferUpgradePeriod**|Ambos|**Descrição:** política para diferir atualizações de funcionalidade para até oito meses<br /><br />**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Update/DeferUpgradePeriod<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:** 0: aplicar atualizações imediatamente; 1-8: número de meses para diferir atualizações de funcionalidades.<br /><br />**Valor predefinido:0**<br /><br />Para obter mais informações, consulte:<br /><br />[Introdução à manutenção do Windows](https://technet.microsoft.com/library/mt598226(v=vs.85).aspx)<br /><br />[Plano de implementação do Windows 10](https://technet.microsoft.com/library/mt574241(v=vs.85).aspx)|
|**Atualização/PauseDeferrals**|Ambos|**Descrição:** permite que uma máquina CBB deixe de receber atualizações durante cinco semanas. Isto deve ser utilizado caso exista um problema com uma atualização.<br /><br />**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Update/PauseDeferrals<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br /><br />**0**: aplicar atualizações imediatamente (predefinição)<br /><br />**1**: colocar atualizações em pausa (expira após cinco semanas)<br /><br />**Valor predefinido:0**|

### Windows Defender

|Nome da política|Suporta|Detalhes|
|---------------|------------|-----------|
|**AllowRealtimeMonitoring**|Ambiente de Trabalho|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Defender/AllowRealtimeMonitoring<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br /><br />**0** – não permitido<br /><br />**1** – permitido<br /><br />**Valor predefinido:** 1|
|**AllowBehaviorMonitoring**|Ambiente de Trabalho|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Defender/AllowBehaviorMonitoring<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br /><br />**0** – não permitido<br /><br />**1** – permitido<br /><br />**Valor predefinido:** 1|
|**AllowIntrusionPreventionSystem**|Ambiente de Trabalho|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Defender/AllowIntrusionPreventionSystem<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br /><br />**0** – não permitido<br /><br />**1** – permitido<br /><br />**Valor predefinido:** 1|
|**AllowIOAVProtection**|Ambiente de Trabalho|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Defender/AllowIOAVProtection<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br /><br />**0** – não permitido<br /><br />**1** – permitido<br /><br />**Valor predefinido:** 1|
|**AllowScriptScanning**|Ambiente de Trabalho|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Defender/AllowScriptScanning<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br /><br />**0** – não permitido<br /><br />**1** – permitido<br /><br />**Valor predefinido:** 1|
|**AllowOnAccessProtection**|Ambiente de Trabalho|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Defender/AllowOnAccessProtection<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br /><br />**0** – não permitido<br /><br />**1** – permitido<br /><br />**Valor predefinido:** 1|
|**RealTimeScanDirection**|Ambiente de Trabalho|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Defender/RealTimeScanDirection<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br /><br />**0** – monitorizar todos os ficheiros (bidirecional)<br /><br />**1** – monitorizar ficheiros recebidos<br /><br />**2** – monitorizar ficheiros enviados<br /><br />**Valor predefinido:** 0|
|**DaysToRetainCleanedMalware**|Ambiente de Trabalho|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Defender/DaysToRetainCleanedMalware<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:0** - **90** – representa o período de retenção do software maligno<br /><br />**Valor predefinido:** 0 – mantém na pasta de quarentena indefinidamente e não remove automaticamente|
|**AllowUserUIAccess**|Ambiente de Trabalho|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Defender/AllowUserUIAccess<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br /><br />**0** – não permitido<br /><br />**1** – permitido<br /><br />**Valor predefinido:** 1|
|**ScanParameter**|Ambiente de Trabalho|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Defender/ScanParameter<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br /><br />**1** – análise rápida<br /><br />**2** - análise completa<br /><br />**Valor predefinido:** 1|
|**ScheduleScanDay**|Ambiente de Trabalho|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Defender/ScheduleScanDay<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br /><br />**0** - todos os dias<br /><br />**1** - Segunda-feira<br /><br />**2** - Terça-feira<br /><br />**3** - Quarta-feira<br /><br />**4** - Quinta-feira<br /><br />**5** - Sexta-feira<br /><br />**6** - Sábado<br /><br />**7** - Domingo<br /><br />**8** – nenhuma análise agendada<br /><br />**Valor predefinido:** 0|
|**ScheduleScanTime**|Ambiente de Trabalho|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Defender/ScheduleScanTime<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br /><br />**0** - 24:00<br /><br />**60** – 01:00<br /><br />**120** – 02:00<br /><br />**180** – 03:00<br /><br />**240** – 04:00<br /><br />**300** – 05:00<br /><br />**360** – 06:00<br /><br />**420** – 07:00<br /><br />**480** – 08:00<br /><br />**540** – 09:00<br /><br />**600** – 10:00<br /><br />**660** – 11:00<br /><br />**720** – 12:00<br /><br />**780** – 13:00<br /><br />**840** – 14:00<br /><br />**900** – 15:00<br /><br />**960** – 16:00<br /><br />**1020** – 17:00<br /><br />**1080** – 18:00<br /><br />**1140** – 19:00<br /><br />**1200** – 20:00<br /><br />**1260** – 21:00<br /><br />**1320** – 22:00<br /><br />**1381** – janela de manutenção<br /><br />**Valor predefinido:** 120|
|**ScheduleQuickScanTime**|Ambiente de Trabalho|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Defender/ScheduleQuickScanTime<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br /><br />**0** - 24:00<br /><br />**60** – 01:00<br /><br />**120** – 02:00<br /><br />**180** – 03:00<br /><br />**240** – 04:00<br /><br />**300** – 05:00<br /><br />**360** – 06:00<br /><br />**420** – 07:00<br /><br />**480** – 08:00<br /><br />**540** – 09:00<br /><br />**600** – 10:00<br /><br />**660** – 11:00<br /><br />**720** – 12:00<br /><br />**780** – 13:00<br /><br />**840** – 14:00<br /><br />**900** – 15:00<br /><br />**960** – 16:00<br /><br />**1020** – 17:00<br /><br />**1080** – 18:00<br /><br />**1140** – 19:00<br /><br />**1200** – 20:00<br /><br />**1260** – 21:00<br /><br />**1320** – 22:00<br /><br />**1380** – 23:00<br /><br />**Valor predefinido:** 120|
|**AVGCPULoadFactor**|Ambiente de Trabalho|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Defender/AVGCPULoadFactor<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:0** - **100**<br /><br />**Valor predefinido:** 50|
|**AllowArchiveScanning**|Ambiente de Trabalho|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Defender/AllowArchiveScanning<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br /><br />**0** – não permitido<br /><br />**1** – permitido<br /><br />**Valor predefinido:** 1|
|**AllowEmailScanning**|Ambiente de Trabalho|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Defender/AllowEmailScanning<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br /><br />**0** – não permitido<br /><br />**1** – permitido<br /><br />**Valor predefinido:** 0|
|**AllowFullScanRemovableDriveScanning**|Ambiente de Trabalho|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Defender/AllowFullScanRemovableDriveScanning<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br /><br />**0** – não permitido<br /><br />**1** – permitido<br /><br />**Valor predefinido:** 0|
|**AllowFullScanOnMappedNetworkDrives**|Ambiente de Trabalho|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Defender/AllowFullScanOnMappedNetworkDrives<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br /><br />**0** – não permitido<br /><br />**1** – permitido<br /><br />**Valor predefinido:** 1|
|**AllowScanningNetworkFiles**|Ambiente de Trabalho|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Defender/AllowScanningNetworkFiles<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br /><br />**0** – não permitido<br /><br />**1** – permitido<br /><br />**Valor predefinido:** 1 – também é executada quando o RTP está definido como permitido|
|**SignatureUpdateInterval**|Ambiente de Trabalho|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Defender/SignatureUpdateInterval<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br /><br />**0** – não verificar assinaturas num intervalo<br /><br />**1** - verificar assinaturas a cada hora<br /><br />**2** – verificar assinaturas a cada duas horas, etc.<br /><br />**24** – verificar assinaturas todos os dias<br /><br />**Valor predefinido:** 8 – verificar assinaturas a cada oito horas|
|**AllowCloudProtection**|Ambiente de Trabalho|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Defender/AllowCloudProtection<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br /><br />**0** – não permitido<br /><br />**1** – permitido<br /><br />**Valor predefinido:** 1|
|**SubmitSamplesConsent**|Ambiente de Trabalho|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Defender/SubmitSamplesConsent<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:**<br /><br />**0** – perguntar sempre<br /><br />**1** – enviar automaticamente amostras seguras<br /><br />**2** – nunca enviar<br /><br />**1** – enviar automaticamente todas as amostras<br /><br />**Valor predefinido:** 0|
|**ExcludedExtensions**|Ambiente de Trabalho|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Defender/ExcludedExtensions<br /><br />**Tipo de dados:** Cadeia<br /><br />**Valores permitidos:**<br /><br />*&lt;lista de extensões separadas por ponto e vírgula&gt;* Por exemplo, **obj;lib**<br /><br />**Valor predefinido:** Não é excluída nenhuma extensão|
|**ExcludedPaths**|Ambiente de Trabalho|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Defender/ExcludedPaths<br /><br />**Tipo de dados:** Cadeia<br /><br />**Valores permitidos:**<br /><br />*&lt;lista de caminhos separados por ponto e vírgula&gt;*<br /><br />Exemplo: **c:\test;c:\test1.exe**<br /><br />**Valor predefinido:** Não são excluídos caminhos|
|**ExcludedProcesses**|Ambiente de Trabalho|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Defender/ExcludedProcesses<br /><br />**Tipo de dados:** Cadeia<br /><br />**Valores permitidos:**<br /><br />*&lt;lista de caminhos separados por ponto e vírgula&gt;*<br /><br />Exemplo: **c:\test.exe;c:\test1.exe**<br /><br />**Valor predefinido:** Não são excluídos processos|

### Browser Edge

|Nome da política|Suporta|Detalhes|
|---------------|------------|-----------|
|**Permitir Browser**|Móvel|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Browser/AllowBrowser<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:0**: navegação desativada; **1**: navegação ativada.<br /><br />**Valor predefinido:** 1|
|**AllowSearchSuggestionsinAddressBar**|Ambos|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Browser/AllowSearchSuggestionsinAddressBar<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:0**: não mostrar sugestões de pesquisa; **1**: mostrar sugestões de pesquisa.<br /><br />**Valor predefinido:** 1|
|**SendIntranetTraffictoInternetExplorer**|Ambiente de Trabalho|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Browser/SendIntranetTraffictoInternetExplorer<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:0**: desativado (abrir sites da intranet no browser Edge); **1** - ativado (abrir sites da intranet no Internet Explorer).<br /><br />**Valor predefinido:** 0|
|**Permitir Não Controlar**|Ambos|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Browser/AllowDoNotTrack<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:0** – desativado (DNT não enviado);  **1** – ativado (enviar DNT)<br /><br />**Valor predefinido:** 0|
|**Configurar SmartScreen**|Ambos|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Browser/AllowSmartScreen<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:0** – não permitir;  **1** – permitir<br /><br />**Valor predefinido:** 1|
|**Permitir Pop-ups**|Ambiente de Trabalho|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Browser/AllowPopups<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:0** – bloquear janelas de pop-up; **1** – permitir janelas de pop-up<br /><br />**Valor predefinido:** 0|
|**Permitir Cookies**|Ambos|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Browser/AllowCookies<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:0** – não bloquear. Permitir cookies de todos os sites; **1** – bloquear apenas cookies de terceiros; **2** – bloquear todos os cookies<br /><br />**Valor predefinido:** 0|
|**Permitir Guardar Palavra-passe**|Ambos|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Browser/AllowPasswordManager<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:0** – o gestor de palavras-passe está desativado; <br />                        **1** – O gestor de palavras-passe está ativado<br /><br />**Valor predefinido:** 1|
|**Permitir Preenchimento Automático**|Ambiente de Trabalho|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Browser/AllowAutofill<br /><br />**Tipo de dados:** Número inteiro<br /><br />**Valores permitidos:0** – desativado; **1** – ativado<br /><br />**Valor predefinido:** 0|
|**Configurar a Lista de Sites da Empresa**|Ambiente de Trabalho|**Caminho completo do URI:** ./Vendor/MSFT/Policy/Config/Browser/EnterpriseModeSiteList<br /><br />**Tipo de dados:** Cadeia<br /><br />**Valores permitidos:0** – não configurado; **1** – utilizar a lista de sites do modo de empresa do IE, caso esteja configurado; **2** – especificar localização da lista de sites da empresa<br /><br />**Valor predefinido:** 1|

### Consulte também
[Gerir definições e funcionalidades nos seus dispositivos com as políticas do Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)



<!--HONumber=May16_HO1-->



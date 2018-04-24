---
title: Definições de políticas do Windows 10
description: Utilize as definições de política indicadas neste tópico para obter ajuda para configurar definições incorporadas e personalizadas para dispositivos com o Windows 10 e o Windows 10 Mobile inscritos.
keywords: ''
author: vhorne
ms.author: victorh
manager: angrobe
ms.date: 09/05/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 00a602d9-b339-4fd8-ab70-defbf6686855
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 202f15766aa740755669ab246739a5331ea328a4
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/16/2018
---
# <a name="intune-policy-settings-for-windows-10-devices-in-microsoft-intune"></a>Definições de política do Intune para dispositivos com o Windows 10 no Microsoft Intune

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Este tópico contém informações para ajudá-lo a compreender as definições de política do Intune que pode utilizar para gerir dispositivos com o Windows 10. Leia este tópico juntamente com os procedimentos em [Gerir definições e funcionalidades nos seus dispositivos com as políticas do Microsoft Intune](/intune-classic/get-started/windows-pc-management-capabilities-in-microsoft-intune).

Poderá escolher entre dois tipos de política:

- **Política personalizada**: utilize a **política personalizada** do Microsoft Intune para Windows 10 e Windows 10 Mobile para implementar definições OMA-URI (Open Mobile Alliance Uniform Resource Identifier) que podem ser utilizadas para controlar as funcionalidades nos dispositivos. O Windows 10 disponibiliza várias definições CSP, por exemplo, o [Fornecedor de Serviços de Configuração de Políticas (CSP de Políticas)](https://technet.microsoft.com/itpro/windows/manage/how-it-pros-can-use-configuration-service-providers).
- **Política de configuração geral**: utilize este tipo de política quando quiser selecionar definições da lista incorporada disponibilizada com o Microsoft Intune.

## <a name="custom-policy-settings"></a>Definições de política personalizada

Forneça as seguintes definições numa política personalizada.

### <a name="general-settings"></a>Definições gerais

Introduza um nome e uma descrição opcional para esta política para ajudá-lo a identificá-la na consola do Intune.

### <a name="oma-uri-settings"></a>Definições OMA-URI

Para cada definição OMA-URI que pretende adicionar, introduza as informações seguintes:

- **Nome da definição**: introduza um nome exclusivo para a definição OMA-URI para o ajudar a identificá-la na lista de definições. Pode encontrar mais informações sobre as definições URI em [Policy Configuration Service Provider (Policy CSP) (Fornecedor de Serviços de Configuração de Política (CSP de Política))](https://technet.microsoft.com/itpro/windows/manage/how-it-pros-can-use-configuration-service-providers).
- **Descrição da definição**: opcionalmente, introduza uma descrição para a definição.
- **Tipo de dados**: escolha entre os seguintes tipos de dados:
    - **Cadeia**
    - **Cadeia (XML)**
    - **Data e hora**
    - **Número inteiro**
    - **Vírgula flutuante**
    - **Booleano**
- **OMA-URI (sensível às maiúsculas e minúsculas)**: especifique o OMA-URI para o qual pretende proporcionar uma definição.
- **Valor**: indique o valor a associar ao OMA-URI que introduziu.

### <a name="example"></a>Exemplo
Na captura de ecrã seguinte, a definição **Connectivity/AllowVPNOverCellular** foi ativada. Isto permite que um dispositivo com o Windows 10 abra uma ligação VPN quando estiver numa rede celular.

> ![Exemplo de uma política personalizada que contém definições de VPN](./media/custom-policy-example.png)

### <a name="how-to-find-the-policies-you-can-configure"></a>Como encontrar as políticas que pode configurar

Encontrará uma lista completa de todos os fornecedores de serviços de configuração (CSPs) que suportam o Windows 10 na [Configuration service provider reference (Referência do fornecedor de serviços de configuração)](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/configuration-service-provider-reference) na biblioteca de documentação do Windows.

Nem todas as definições são compatíveis com todas as versões do Windows 10. A tabela no tópico Windows indica quais as versões suportadas para cada CSP.

Além disso, o Intune não suporta todas as definições listadas no tópico. Para saber se o Intune suporta a definição que pretende, abra o tópico dessa definição. Cada página de definição mostra a sua operação suportada. Para trabalhar com o Intune, a definição tem de suportar as operações **Adicionar** ou **Substituir**.

## <a name="general-configuration-policy-settings"></a>Definições de política de configuração geral

Utilize a **política de configuração geral** do Microsoft Intune para o Windows 10 para configurar definições incorporadas de dispositivos com o Windows 10 e o Windows 10 Mobile inscritos.

### <a name="password"></a>Palavra-passe

|Nome da definição|Informações adicionais (quando necessário)|
|----------------|----------------------|
|**Pedir uma palavra-passe para desbloquear dispositivos**|-|
|**Tipo obrigatório de palavra-passe**|Especifica se a palavra-passe tem de ser apenas numérica ou alfanumérica|
|**Tipo obrigatório de palavra-passe** - **Número mínimo de conjuntos de carateres**| Especifica o número de conjuntos de carateres (letras minúsculas, letras maiúsculas, números e símbolos) que devem ser incluídos na palavra-passe|
|**Comprimento mínimo da palavra-passe**|Aplica-se apenas ao Windows 10 Mobile|
|**Número de falhas de início de sessão consecutivas a permitir antes de o dispositivo ser apagado**.|Para dispositivos a executar o Windows 10: se o dispositivo tiver o BitLocker ativado, será colocado no modo de recuperação do BitLocker após o início de sessão falhar o número de vezes que especificar. Se o dispositivo não tiver o BitLocker ativado, esta definição não se aplica.<br>Para dispositivos a executar o Windows 10 Mobile: após o início de sessão falhar o número de vezes que especificar, o dispositivo será apagado.|
|**Minutos de inatividade antes de o ecrã se desligar**|Especifica o período de tempo durante o qual o dispositivo tem de estar inativo antes de o ecrã ser bloqueado|
|**Expiração da Palavra-passe (dias)**|Especifica o período de tempo após o qual a palavra-passe do dispositivo tem de ser alterada|
|**Memorizar histórico de palavras-passe**|Especifica se o utilizador final deve ser impedido de criar palavras-passe utilizadas anteriormente|
|**Memorizar histórico de palavras-passe** - **Evita a reutilização de palavras-passe anteriores**|Especifica o número de palavras-passe utilizadas anteriormente que são memorizadas pelo dispositivo|
|**Pedir uma palavra-passe quando o dispositivo regressa de um estado inativo**|Especifica que o utilizador tem de introduzir uma palavra-passe para desbloquear o dispositivo (apenas Windows 10 Mobile)|

### <a name="encryption"></a>Encriptação

|Nome da definição|Informações adicionais (quando necessário)|
|----------------|----------------------|
|**Encriptação obrigatória no dispositivo móvel**|Ativa a encriptação nos dispositivos visados<br>(Apenas Windows 10 Mobile)|

### <a name="system"></a>Sistema

|Nome da definição|Informações adicionais (quando necessário)|
|----------------|----------------------|
|**Permitir captura de ecrã**|Permite que o utilizador capture o ecrã do dispositivo como uma imagem (apenas Windows 10 Mobile)|
|**Permitir anular inscrições manualmente**|Permite que o utilizador elimine manualmente a conta da área de trabalho do dispositivo|
|**Permitir instalação do certificado de raiz manual**|Aplica-se ao Windows 10 Mobile|
|**Permitir que os dados de diagnóstico e de utilização sejam enviados à Microsoft**|Os valores possíveis são:<br><br>**Não** – não são enviados dados à Microsoft<br>**Básico** – são enviadas à Microsoft informações limitadas<br>**Melhorado** – são enviados à Microsoft dados de diagnóstico melhorados<br>**Completo (recomendado)** – Eenvia os mesmos dados que **Melhorado**, juntamente com dados adicionais sobre o estado do dispositivo|


### <a name="account-and-synchronization"></a>Conta e sincronização

|Nome da definição|Informações adicionais (quando necessário)|
|----------------|----------------------|---------------------|
|**Permitir conta Microsoft**|Permite que o utilizador associe uma conta Microsoft ao dispositivo|
|**Permitir adicionar contas de terceiros manualmente**|Permite que o utilizador adicione contas de e-mail ao dispositivo, que não estão associadas a uma conta Microsoft|
|**Permitir a sincronização de definições para contas Microsoft**|Permite que as definições do dispositivo e de aplicações associadas a uma conta Microsoft sejam sincronizadas entre dispositivos|

### <a name="microsoft-edge"></a>Microsoft Edge

|Nome da definição|Informações adicionais (quando necessário)|
|----------------|----------------------|
|**Permitir browser**|Permite a utilização do browser Microsoft Edge no dispositivo<br>(Apenas Windows 10 Mobile)|
|**Permitir sugestões de pesquisa na barra de endereço**|Permite que o motor de busca sugira sites à medida que escreve expressões de pesquisa|
|**Permitir o envio de tráfego da intranet para o Internet Explorer**|Permite que os utilizadores abram sites da intranet no Internet Explorer<br>(apenas para computadores com o Windows 10)|
|**Permitir Do Not Track**|Configura o browser Edge para enviar cabeçalhos Do Not Track para sites que os utilizadores visitam|
|**Ativar SmartScreen**||
|**Permitir scripting ativo**|Permite que scripts, como JavaScript, sejam executados no browser Edge|
|**Permitir pop-ups**|Aplica-se apenas ao ambiente de trabalho Windows 10|
|**Permitir cookies**||
|**Permitir Preenchimento Automático**|Permite que os utilizadores alterem as definições de conclusão automática no browser<br>(apenas para computadores com o Windows 10)|
|**Permitir Gestor de Palavras-passe**|Ativa ou desativa a funcionalidade Gestor de Palavras-passe do Microsoft Edge|
|**Localização da lista de sites do Modo Empresarial**|Especifica onde encontrar a lista de sites que abrem no modo Empresarial. Os utilizadores não podem editar esta lista.<br>(apenas para computadores com o Windows 10)|

### <a name="apps"></a>Aplicações

|Nome da definição|Informações adicionais (quando necessário)|
|----------------|----------------------|---------------------|
|**Permitir loja de aplicações**|Aplica-se apenas ao Windows 10 Mobile|



### <a name="cellular"></a>Rede móvel

|Nome da definição|Informações adicionais (quando necessário)|
|----------------|----------------------|---------------------|
|**Permite roaming de dados**|Permitir roaming entre redes ao aceder a dados|
|**Permitir VPN pela rede móvel**|Controla se o dispositivo pode aceder a ligações VPN quando ligado a uma rede celular|
|**Permitir roaming de VPN pela rede móvel**|Controla se o dispositivo pode aceder a ligações VPN quando está em roaming numa rede celular|

### <a name="hardware"></a>Hardware

|Nome da definição|Informações adicionais (quando necessário)|
|----------------|----------------------|
|**Permitir câmara**|-|
|**Permitir armazenamento amovível**|Especifica se os dispositivos de armazenamento externo, como um cartão SD, podem ser utilizados com o dispositivo|
|**Permitir Wi-Fi**|Aplica-se apenas ao Windows 10 Mobile|
|**Permitir partilha da Internet**|Permite a utilização da partilha de ligação à Internet no dispositivo|
|**Permitir configuração de Wi-Fi manual**|Controla se o utilizador pode configurar as suas próprias ligações Wi-F ou se este pode utilizar apenas as ligações configuradas por um perfil Wi-Fi<br>(Apenas Windows 10 Mobile)|
|**Permitir ligação automática a hotspots Wi-Fi**|Permite que o dispositivo ligue automaticamente a hotspots Wi-Fi gratuitos e aceite automaticamente os termos e condições da ligação|
|**Permitir geolocalização**|Especifica se o dispositivo pode utilizar informações de serviços de localização|
|**Permitir NFC**|Permite que o dispositivo utilize as capacidades de Comunicação de Proximidade|
|**Permitir Bluetooth**|-|
|**Permitir modo detetável do Bluetooth**|Permite que este dispositivo seja detetado por outros dispositivos com Bluetooth ativado|
|**Permitir publicidade do Bluetooth**|Permite que os dispositivos recebam anúncios por Bluetooth|
|**Permitir reposição do telefone**|Controla se o utilizador pode fazer uma reposição de fábrica do dispositivo|
|**Permitir ligação USB**|Controla se os dispositivos podem aceder a dispositivos de armazenamento externo através de uma ligação USB|
|**Permitir modo Anti-roubo**|Configurar se o modo Antirroubo do Windows está ativado|

### <a name="features"></a>Funcionalidades

|Nome da definição|Informações adicionais (quando necessário)|
|----------------|----------------------|---------------------|
|**Permitir copiar e colar**|Aplica-se apenas ao Windows 10 Mobile|
|**Permitir gravação de voz**|Aplica-se apenas ao Windows 10 Mobile|
|**Permitir Cortana**|Ativar ou desativar o assistente de voz Cortana|
|**Permitir notificações do centro de ação**|Ativar ou desativar notificações do centro de ação no ecrã de bloqueio do dispositivo<br>(Apenas Windows 10 Mobile)|

### <a name="windows-defender"></a>Windows Defender

Todas as definições são apenas para computadores com o Windows 10.

|Nome da definição|Informações adicionais (quando necessário)|
|----------------|----------------------|---------------------|
|**Permitir monitorização em tempo real**|Permite a análise em tempo real de software maligno, spyware e outro software indesejável|
|**Permitir monitorização de comportamento**|Permite que o Defender verifique a existência de determinados padrões conhecidos de atividade suspeita nos dispositivos|
|**Ativar o Sistema de Inspeção de Rede**|O Sistema de Inspeção de Rede (NIS) ajuda a proteger os dispositivos contra exploits baseados na rede, com as assinaturas de vulnerabilidades conhecidas do Microsoft Endpoint Protection Center para ajudar a detetar e a bloquear tráfego malicioso|
|**Analisar todas as transferências**|Controla se o Defender analisa todos os ficheiros transferidos da Internet|
|**Permitir análise de scripts**|Permite que o Defender analise os scripts que são utilizados no Internet Explorer|
|**Monitorizar a atividade dos ficheiros e programas**|Permite que o Defender monitorize a atividade de ficheiros e programas nos dispositivos|
|**Dias para controlar o software maligno resolvido**|Permite que o Defender continue a controlar o software maligno resolvido durante o número de dias que especificar, para que possa verificar manualmente os dispositivos afetados anteriormente. Se definir o número de dias como **0**, o software maligno permanece na pasta Quarentena e não é removido automaticamente. |
|**Permitir o acesso à IU de cliente**|Controla se a interface de utilizador do Windows Defender está ocultada dos utilizadores.<br>Quando esta definição é alterada, será aplicada da próxima vez que o PC do utilizador for reiniciado.|
|**Agendar uma análise rápida diária**|Permite agendar uma análise rápida que ocorre diariamente à hora que selecionar|
|**Agendar uma análise do sistema**|Permite agendar uma análise completa ou rápida do sistema, que ocorre regularmente no dia e na hora que selecionar|
|**Limitar a utilização da CPU durante a análise**|Permite limitar a quantidade de CPU que as análises estão autorizadas a utilizar (de **1** a **100**)|
|**Analisar ficheiros de arquivo**|Permite que o Defender analise ficheiros arquivados, tais como ficheiros .zip ou .cab.|
|**Analisar mensagens de e-mail**|Permite que o Defender analise mensagens de e-mail quando chegam ao dispositivo|
|**Analisar unidades amovíveis**|Permite que o Defender analise unidades amovíveis, como pens USB|
|**Analisar unidades de rede mapeadas**|Permite que o Defender analise ficheiros em unidades de rede mapeadas.<br>Se os ficheiros na unidade forem só de leitura, o Defender não conseguirá remover qualquer software maligno encontrado nos mesmos.|
|**Analisar ficheiros abertos a partir de pastas partilhadas na rede**|Permite que o Defender analise ficheiros em unidades de rede partilhadas (por exemplo, as unidades acedidas a partir de um caminho UNC).<br>Se os ficheiros na unidade forem só de leitura, o Defender não conseguirá remover qualquer software maligno encontrado nos mesmos.|
|**Intervalo de atualização de assinatura**|Especifica o intervalo no qual o Defender verifica a existência de novos ficheiros de assinatura.|
|**Permitir proteção da cloud**|Permite ou impede que o Serviço de Proteção Ativa Microsoft receba informações sobre a atividade de software maligno nos dispositivos geridos por si. Estas informações são utilizadas para melhorar o serviço no futuro.|
|**Pedir aos utilizadores o envio de amostras**|Controla se os ficheiros que possam exigir análise adicional pela Microsoft para determinar se são maliciosos são automaticamente enviados à Microsoft|
|**Deteção de Aplicação Potencialmente Indesejável**|Protege os dispositivos de ambiente de trabalho Windows inscritos contra software em execução classificado pelo Windows Defender como potencialmente indesejável. Pode proteger contra estas aplicações em execução ou utilizar o modo de auditoria para relatar quando uma aplicação potencialmente indesejável é instalada.|
|**Ficheiros e pastas a excluir quando executa uma análise ou utiliza a proteção em tempo real**|Adiciona um ou mais ficheiros e pastas, como **C:\Path** ou **%ProgramFiles%\Path\filename.exe**, à lista de exclusões. Estes ficheiros e pastas não são incluídos em análises em tempo real ou agendadas.|
|**Extensões de ficheiro a excluir quando executa uma análise ou utiliza a proteção em tempo real**|Adicione uma ou mais extensões de ficheiro, como **jpg** ou **txt**, à lista de exclusões. Os ficheiros com estas extensões não são incluídos em análises em tempo real ou agendadas.|
|**Processos a excluir quando executa uma análise ou utiliza a proteção em tempo real**|Adiciona um ou mais processos do tipo **.exe**, **.com** ou **.scr** à lista de exclusões. Estes processos não são incluídos em análises em tempo real ou agendadas.|


### <a name="updates"></a>Updates

|Nome da definição|Informações adicionais (quando necessário)|
|----------------|---------------|
|**Permitir atualizações automáticas**|Permite atualizações automáticas. Configure uma das seguintes definições para controlar o comportamento da atualização:<br />**Notificar carregamento**<br />**Instalação automática ao tempo de manutenção**<br />**Instalação automática e reinicio ao tempo de manutenção**<br />**Instalação automática e reinício à hora agendada**: Tenha em atenção que quando esta opção está selecionada, também pode configurar as seguintes definições: **Suprimir a notificação para o utilizador final** e **Definir o dia da instalação de atualizações agendadas**.<br>(apenas para computadores com o Windows 10)|
|**Permitir funcionalidades de pré-lançamento**|Permite à Microsoft implementar funcionalidades e definições de pré-lançamento em dispositivos com o Windows 10. Pode selecionar para permitir as definições apenas, ou todas as definições de versão de pré-lançamento e funcionalidades para a instalação.|

### <a name="see-also"></a>Consulte também
[Gerir definições e funcionalidades nos seus dispositivos com as políticas do Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)

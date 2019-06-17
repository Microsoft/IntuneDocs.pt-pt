---
title: Definições de restrição de dispositivos para Android no Microsoft Intune – Azure | Microsoft Docs
description: Veja uma lista de todas as definições de dispositivos Android que pode controlar e restringir no Microsoft Intune. Utilize estas definições para controlar a palavra-passe, aceder ao Google Play, permitir ou proibir aplicações, controlar as definições do browser, bloquear aplicações, criar cópias de segurança na cloud do Google e controlar as opções de mensagens, voz, roaming de dados, Wi-Fi e ligação Bluetooth.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/13/2018
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.reviewer: ayesham, chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: f13b78e05b9f0b94d98677004c7059f1acaa80f9
ms.sourcegitcommit: 4b83697de8add3b90675c576202ef2ecb49d80b2
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/13/2019
ms.locfileid: "67045717"
---
# <a name="android-and-samsung-knox-standard-device-restriction-settings-lists-in-intune"></a>Android e Samsung Knox Standard listas de definições de restrição de dispositivos no Intune

Este artigo mostra-lhe todas as definições de restrições de dispositivos do Microsoft Intune que pode configurar para dispositivos a executar o Android.

>[!TIP]
>Se as definições que pretende não estiverem disponíveis, poderá conseguir configurá-las nos seus dispositivos através de um [perfil personalizado](custom-settings-android.md).

## <a name="general"></a>Geral

- **Câmara**: Escolher **bloco** para impedir o acesso à câmara. **Não configurado** permite o acesso à câmara do dispositivo.
- **Copiar e colar (apenas no Samsung Knox)**: Escolher **bloco** para impedir a copiar e colar. **Não configurado** permite as funções de copiar e colar no dispositivo.
- **Área de transferência entre aplicações (apenas no Samsung Knox) de partilha**: Escolher **bloco** para impedir a utilização da área de transferência para copiar e colar entre aplicações. **Não configurado** permite o uso de área de transferência para copiar e colar entre aplicações.
- **Submissão de dados de diagnóstico (apenas no Samsung Knox)**: Escolher **bloco** para parar o utilizador de submeter dados de diagnóstico do dispositivo. **Não configurado** permite ao usuário enviar os dados.
- **Eliminação de dados (apenas no Samsung Knox)**: Permite que o utilizador executar uma [apagar](devices-wipe.md) ação no dispositivo.
- **Geolocalização (apenas no Samsung Knox)**: Escolher **bloco** para desativar o dispositivo de utilizar as informações de localização. **Não configurado** permite que o dispositivo utilize as informações de localização.
- **Desligar (apenas no Samsung Knox)**: Escolher **bloco** para impedir que o utilizador de desligar o dispositivo. Se esta definição estiver desativada, o **número de falhas de início de sessão antes de limpar o dispositivo** definição não pode ser definida e não funciona. **Não configurado** permite ao utilizador desligar o dispositivo.
- **Captura de ecrã (apenas no Samsung Knox)**: Escolher **bloco** para impedir capturas de ecrã. **Não configurado** permite ao utilizador capturar o conteúdo do ecrã como uma imagem.
- **Assistente de voz (apenas no Samsung Knox)**: Escolher **bloco** para desativar o serviço de voz de S. **Não configurado** permite a utilização do serviço de voz de S e a aplicação no dispositivo. Esta definição não se aplica a Bixby ou o Assistente de voz para acessibilidade, que lê em voz alta o conteúdo do ecrã.
- **YouTube (apenas no Samsung Knox)**: Escolher **bloco** para impedir que os utilizadores a utilizar a aplicação do YouTube. **Não configurado** permite o uso de aplicação YouTube no dispositivo.
- **Dispositivos partilhados (apenas no Samsung Knox)**: Configure um dispositivo Samsung Knox Standard gerido como partilhado. Quando definido como **permitir**, os utilizadores finais podem iniciar sessão dentro e fora do dispositivo com as credenciais do Azure AD. O dispositivo permanece gerido, se está a ser utilizado ou não.</br>Quando utilizado com um perfil de certificado SCEP, esta funcionalidade permite que os utilizadores finais partilhem um dispositivo com as aplicações mesmo para todos os utilizadores. No entanto, cada utilizador tem seu próprio certificado de utilizador SCEP. Quando os utilizadores terminam sessão, todos os dados das aplicações são limpos. Esta funcionalidade é limitada a aplicações LOB. </br>**Não configurado** impede os utilizadores vários de iniciar sessão na aplicação Portal da empresa no dispositivo com as credenciais do Azure AD.
- **Bloquear alterações de data e hora (Samsung Knox)**: Escolher **bloco** impedir que o usuário alterar a data e hora definições no dispositivo. **Não configurado** permite aos utilizadores alterar a data e hora de definições.

## <a name="password"></a>Palavra-passe

- **Palavra-passe**: **Exigir** que o utilizador final introduza uma palavra-passe para aceder ao dispositivo. **Não configurado** permite que os utilizadores acedam ao dispositivo sem introduzir uma palavra-passe.

    > [!NOTE]
    > Os dispositivos Samsung Knox exigem automaticamente um PIN de 4 dígitos durante a inscrição na MDM. Dispositivos Android nativos automaticamente podem exigir um PIN para ficarem em conformidade com acesso condicional.

- **Comprimento mínimo da palavra-passe**: Introduza o comprimento mínimo da palavra-passe de que um utilizador tem de introduzir (entre 4 e 16 carateres).
- **Máximo de minutos de inatividade até o ecrã ser bloqueado**: introduza o número máximo de minutos de inatividade permitidos no dispositivo até o ecrã bloquear. Num dispositivo, um utilizador final não pode definir um valor de tempo superior ao tempo configurado no perfil. Um utilizador final pode definir um valor de tempo inferior. Por exemplo, se o perfil estiver definido para 15 minutos, um utilizador final poderá definir o valor para 5 minutos. Um utilizador final não pode definir o valor para 30 minutos. 
- **Número de falhas de início de sessão antes de apagar o dispositivo**: Introduza o número de falhas de início de sessão consecutivas a permitir antes do dispositivo ser apagado.
- **Expiração da palavra-passe (dias)**: introduza o número de dias antes de ser necessário alterar a palavra-passe do dispositivo.
- **Tipo obrigatório de palavra-passe**: Introduza o nível de complexidade de palavra-passe exigido e se podem ser utilizados dispositivos biométricos. As opções são:
  - **Predefinição do dispositivo**
  - **Biométrica de segurança baixa**
  - **Pelo menos numérica**
  - **Complexo numérico**: Repetido ou números consecutivos, como "1111" ou "1234", não são permitidos. <sup>1</sup>
  - **Pelo menos alfabética**
  - **Pelo menos alfanumérica**
  - **Pelo menos alfanumérica com símbolos**
- **Impedir a reutilização de palavras-passe anteriores**: Impede que o utilizador final crie uma palavra-passe que tenham utilizado antes.
- **(Apenas no Samsung Knox) de desbloqueio por impressão digital**: escolha **Bloquear** para impedir a utilização de uma impressão digital para desbloquear o dispositivo. **Não configurado** permite ao utilizador desbloquear o dispositivo através de uma impressão digital.
- **Smart Lock e outros agentes de fidedignidade**: Escolher **bloco** para impedir que o Smart Lock ou outros agentes de fidedignidade de ajustarem as definições de ecrã de bloqueio (Samsung KNOX Standard 5.0 +). Esta funcionalidade de telefone, por vezes conhecida como agente de confiança, permite desativar ou ignorar a palavra-passe de ecrã do bloqueio de dispositivo se o dispositivo estiver numa localização fidedigna. Por exemplo, esta funcionalidade pode ser utilizada quando o dispositivo está ligado a um dispositivo Bluetooth específico ou quando está próximo de uma etiqueta NFC. Pode utilizar esta definição para impedir que os utilizadores configurem o Smart Lock.
- **Encriptação**: Escolher **requerem** para que os ficheiros no dispositivo estejam encriptados. Nem todos os dispositivos suportam encriptação. Para utilizar esta funcionalidade, também: 
  1. Definir **palavra-passe** ao **exigir**.
  2. Definir **tipo de palavra-passe obrigatório** ao **pelo menos numérico**.
  3. Definir **comprimento mínimo da palavra-passe** para, pelo menos, 4 para reportar corretamente a conformidade para esta definição.

  > [!NOTE]
  > Se for imposta uma política de encriptação, os dispositivos Samsung Knox exigem que os utilizadores definam uma palavra-passe complexa de 6 carateres como o código de acesso do dispositivo.

<sup>1</sup> antes de atribuir esta definição aos dispositivos, certifique-se de que atualizar a aplicação Portal da empresa para a versão mais recente nesses dispositivos.

Se definir **tipo de palavra-passe obrigatório** ao **numérica complexa**e, em seguida, atribuí-lo num dispositivo com uma versão do Android anteriores à 5.0, em seguida, o seguinte comportamento aplica-se:

- Se a aplicação Portal da empresa estiver a executar uma versão anterior à 1704, é aplicada nenhuma política de PIN ao dispositivo e um erro é apresentado no portal do Azure.
- Se a aplicação Portal da Empresa executar a versão 1704 ou posterior, apenas pode ser aplicado um PIN simples. As versões do Android anteriores à 5.0 não suportam esta definição. Nenhum erro é apresentado no portal do Azure.

## <a name="google-play-store"></a>Google Play Store

- **Google Play store (apenas no Samsung Knox)**: Escolher **bloco** para impedir que os utilizadores através da Google Play store. **Não configurado** permite ao utilizador aceder à loja do Google Play no dispositivo.

## <a name="restricted-apps"></a>Aplicações restritas

Utilize estas definições para permitir ou impedir que aplicações específicas no dispositivo. Esta funcionalidade é suportada em dispositivos Android e Samsung Knox Standard:

- **Aplicações proibidas**: uma lista de aplicações não geridas pelo Intune que não quer que sejam instaladas no dispositivo. Se um utilizador instalar uma aplicação desta lista, receberá uma notificação do Intune.
- **Aplicações aprovadas**: uma lista de aplicações que os utilizadores têm permissão para instalar. Para permanecerem compatíveis, os utilizadores não podem instalar outras aplicações. As aplicações geridas pelo Intune são automaticamente permitidas.

Para adicionar aplicações a estas listas, pode:

- **Adicionar** o Google Play Store URL da aplicação que pretende. Por exemplo, para adicionar a aplicação de ambiente de trabalho remoto para Android, introduza `https://play.google.com/store/apps/details?id=com.microsoft.rdc.android`. Para localizar o URL de uma aplicação, abra a [Google Play store](https://play.google.com/store/apps)e procure a aplicação. Por exemplo, procure `Microsoft Remote Desktop Play Store` ou `Microsoft Planner`. Selecione a aplicação e copie o URL.
- Importe um ficheiro CSV com detalhes sobre a aplicação, incluindo o URL. Utilize o <*url de aplicação*>, <*nome da aplicação*>, <*publicador da aplicação*> formato. Ou, **exportar** uma lista existente, que inclui a lista de aplicações restritas no mesmo formato.

> [!IMPORTANT]
> Os perfis de dispositivo que utilizam as definições de aplicações restritas têm de ser atribuídos a grupos de utilizadores.

## <a name="browser"></a>Browser

- **Navegador da Web (apenas no Samsung Knox)**: Escolher **bloco** para impedir que o browser predefinido a ser utilizado no dispositivo. **Não configurado** permite que o navegador da web padrão do dispositivo a ser utilizado.
- **Preenchimento automático (apenas no Samsung Knox)**: Escolher **bloco** para impedir o preenchimento automático de texto no navegador. **Não configurado** permite que a função de preenchimento automático do browser para ser utilizado.
- **Cookies (apenas no Samsung Knox)**: Escolha como pretende processar os cookies do Web sites no dispositivo. As opções são:
  - Permitir
  - Bloquear todos os cookies
  - Permitir cookies dos sites visitados
  - Permitir cookies do site atual
- **JavaScript (apenas no Samsung Knox)**: Escolher **bloco** para impedir que o navegador da web em execução de scripts de Java. **Não configurado** permite que o browser do dispositivo execute scripts em Java.
- **Pop-ups (apenas no Samsung Knox)**: Escolher **bloco** para impedir que os pop-ups do browser. **Não configurado** permite que os pop-ups do browser.

## <a name="allow-or-block-apps"></a>Permitir ou Bloquear aplicações

Utilize estas definições para permitir, bloquear ou ocultar aplicações específicas em dispositivos Samsung Knox Standard. Aplicações que estão ocultos não não possível abrir ou foi executada pelo usuário.

As opções são:

- **Aplicações com permissão para serem instaladas (apenas no Samsung Knox Standard)**
- **Aplicações com início bloqueado (apenas no Samsung Knox Standard)**
- **Aplicações ocultadas do utilizador (apenas no Samsung Knox Standard)**

Para cada definição, adicione uma lista de aplicações. As opções são:

- **Adicionar aplicações pelo nome do pacote**: Usada principalmente para aplicações de linha de negócio. Introduza o nome da aplicação e o nome do pacote de aplicação.
- **Adicionar aplicações por URL**: Introduza o nome da aplicação e o URL na Google Play store.
- **Adicionar aplicação da loja**: Selecione uma aplicação a partir da lista existente de aplicações geridas por que si no Intune.

## <a name="cloud-and-storage"></a>Cloud e Armazenamento

- **Cópia de segurança do Google (apenas no Samsung Knox)**: Escolher **bloco** para impedir que o dispositivo a sincronizar a cópia de segurança do Google. **Não configurado** permite a utilização da cópia de segurança do Google.
- **Sincronização automática da conta Google (apenas no Samsung Knox)**: Escolher **bloco** para impedir que a funcionalidade de sincronização do automática de conta Google no dispositivo. **Não configurado** permite que as definições de conta Google sejam sincronizadas automaticamente.
- **Armazenamento amovível (apenas no Samsung Knox)**: Escolher **bloco** para impedir que o dispositivo utilize armazenamento amovível. **Não configurado** permite que o dispositivo utilize armazenamento amovível, como um cartão SD.
- **Encriptação em cartões de armazenamento (apenas no Samsung Knox)**: **Exigir** impõe que cartões de armazenamento tem de estar encriptados. **Não configurado** permite que cartões de armazenamento não encriptada ser utilizado. Nem todos os dispositivos suportam encriptação do cartão de armazenamento. Para confirmar, contacte o fabricante do dispositivo.

## <a name="cellular-and-connectivity"></a>Rede Móvel e Conectividade

- **Roaming de dados (apenas no Samsung Knox)**: escolha **Bloquear** para impedir o roaming de dados na rede móvel. **Não configurado** permite dados em roaming quando o dispositivo estiver numa rede celular.
- **Mensagens de SMS/MMS (apenas no Samsung Knox)**: Escolher **bloco** para impedir que o texto de mensagens no dispositivo. **Não configurado** permite a utilização de SMS e MMS no dispositivo de mensagens.
- **Marcação por voz (apenas no Samsung Knox)**: escolha **Bloquear** para impedir que os utilizadores utilizem a funcionalidade de marcação por voz no dispositivo. **Não configurado** permite as chamadas discar no dispositivo.
- **Roaming (apenas Samsung Knox) de voz**: escolha **Bloquear** para impedir as chamadas em roaming na rede móvel. **Não configurado** permite chamadas em roaming quando o dispositivo estiver numa rede celular.
- **Bluetooth (apenas no Samsung Knox)**: Escolher **bloco** para impedir a utilização de Bluetooth no dispositivo. **Não configurado** permite a utilização de Bluetooth no dispositivo.
- **NFC (apenas no Samsung Knox)**: Escolher **bloco** para parar a tecnologia de junto ao campo comunicação (NFC). **Não configurado** permite operações que utilizam comunicação de proximidade nos dispositivos suportados.
- **Wi-Fi (apenas no Samsung Knox)**: Escolher **bloco** para impedir a utilização de Wi-Fi no dispositivo. **Não configurado** permite utilizar as funcionalidades de Wi-Fi do dispositivo.
- **Tethering de Wi-Fi (apenas no Samsung Knox)**: Escolher **bloco** para impedir a utilização de tethering Wi-Fi no dispositivo. **Não configurado** permite a utilização de tethering Wi-Fi no dispositivo.

## <a name="kiosk"></a>Modo de Local Público

As definições de modo de local público aplicam-se apenas a dispositivos Samsung Knox Standard e apenas a aplicações que gere com o Intune.

- Adicione aplicações que pretende executar quando o dispositivo estiver no modo de local público. No modo de local público, executam apenas as aplicações que adicionar; aplicações não adicionadas não são executados. Browsers pré-instalados não são executados como uma aplicação quando o dispositivo estiver no modo de local público. Se for necessário utilizar um browser, considere a utilização do [Managed Browser](app-configuration-managed-browser.md).

  As opções de aplicação:

  - **Adicionar aplicações pelo nome do pacote**: Usada principalmente para aplicações de linha de negócio. Introduza o nome da aplicação e o nome do pacote de aplicação.
  - **Adicionar aplicações por URL**: Introduza o nome da aplicação e o URL na Google Play store.
  - **Adicionar aplicação da loja**: Selecione uma aplicação a partir da lista existente de aplicações geridas por que si no Intune.

- **Botão de suspensão do ecrã**: Escolher **bloco** para impedir ou ocultar o botão de suspensão do ecrã. **Não configurado** permite que o botão de reativação de suspensão do ecrã no dispositivo.
- **Botões de volume**: Escolher **bloco** para impedir que o usuário ajustar o volume ao desativar os botões de volume. **Não configurado** permite o uso de botões de volume no dispositivo.

## <a name="next-steps"></a>Passos Seguintes

[Atribua o perfil](device-profile-assign.md) e [monitorize o respetivo estado](device-profile-monitor.md).

Também pode criar perfis de local público para [Android Enterprise](device-restrictions-android-for-work.md#dedicated-device-settings) e [com o Windows 10](kiosk-settings.md) dispositivos.

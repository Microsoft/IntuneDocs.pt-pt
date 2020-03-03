---
title: Definições de restrição de dispositivos para Android no Microsoft Intune – Azure | Microsoft Docs
description: Veja uma lista de todas as definições de dispositivos Android que pode controlar e restringir no Microsoft Intune. Utilize estas definições para controlar a palavra-passe, aceder ao Google Play, permitir ou proibir aplicações, controlar as definições do browser, bloquear aplicações, criar cópias de segurança na cloud do Google e controlar as opções de mensagens, voz, roaming de dados, Wi-Fi e ligação Bluetooth.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/19/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.reviewer: ayesham, chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: cd05547d4699888f5fade58fb5a50557604d81ea
ms.sourcegitcommit: fab685b22a010fe231b27a0c5eda34a6f22f4c8d
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/02/2020
ms.locfileid: "78216042"
---
# <a name="android-and-samsung-knox-standard-device-restriction-settings-lists-in-intune"></a>Listas de configurações de restrições de dispositivos Android e Samsung Knox Standard em Intune

Este artigo mostra-lhe todas as definições de restrições de dispositivos do Microsoft Intune que pode configurar para dispositivos a executar o Android.

>[!TIP]
>Se as definições que pretende não estiverem disponíveis, poderá conseguir configurá-las nos seus dispositivos através de um [perfil personalizado](../custom-settings-android.md).

## <a name="general"></a>Geral

- **Câmara**: Escolha **o Bloco** para impedir o acesso à câmara. **Não configurado** permite o acesso à câmara do dispositivo.
- **Cópia e pasta (apenas Samsung Knox)**: Escolha **o Bloco** para evitar a cópia e a pasta. **Não configurado** permite funções de cópia e pasta no dispositivo.
- **Partilha de clipboard entre apps (apenas Samsung Knox)**: Escolha **o Bloco** para evitar a utilização da pasta para copiar e colar entre apps. **Não configurado** permite usar a pasta para copiar e colar entre aplicações.
- **Submissão de dados de diagnóstico (apenas Samsung Knox)**: Escolha o **Bloco** para impedir que o utilizador envie relatórios de bugs do dispositivo. **Não configurado** permite ao utilizador submeter os dados.
- **Wipe (apenas Samsung Knox)**: Permite ao utilizador executar uma ação de [limpeza](../remote-actions/devices-wipe.md) no dispositivo.
- **Geolocalização (apenas Samsung Knox)**: Escolha o **Bloco** para desativar o dispositivo de utilizar informações de localização. **Não configurado** permite que o dispositivo utilize as informações de localização.
- **Desligar (apenas Samsung Knox)**: Escolha o **Bloco** para evitar que o utilizador desligue o dispositivo. Se esta definição estiver desativada, o **número de falhas de início de sessão antes** de limpar a regulação do dispositivo não pode ser definido e não funciona. **Não configurado** permite ao utilizador desligar o dispositivo.
- **Captura de ecrã (apenas Samsung Knox)**: Escolha **o Bloco** para evitar imagens. **Não configurado** permite ao utilizador capturar o conteúdo do ecrã como uma imagem.
- **Assistente de voz (apenas Samsung Knox)**: Escolha **o Bloco** para desativar o serviço S Voice. **Não configurado** permite a utilização do serviço S Voice e da aplicação no dispositivo. Esta definição não se aplica a Bixby ou ao assistente de voz para acessibilidade que lê o conteúdo do ecrã em voz alta.
- **YouTube (apenas Samsung Knox)**: Escolha **o Bloco** para impedir que os utilizadores utilizem a aplicação do YouTube. **Não configurado** permite usar a aplicação do YouTube no dispositivo.
- **Dispositivos partilhados (apenas Samsung Knox)**: Configure um dispositivo Samsung Knox Standard gerido como partilhado. Quando definido para **Permitir**, os utilizadores finais podem iniciar sessão e sair do dispositivo com as suas credenciais De AD Azure. O dispositivo mantém-se gerido, quer esteja a ser utilizado ou não.</br>Quando utilizada com um perfil de certificado SCEP, esta funcionalidade permite que os utilizadores finais partilhem um dispositivo com as mesmas aplicações para todos os utilizadores. Mas cada utilizador tem o seu próprio certificado de utilizador SCEP. Quando os utilizadores terminam sessão, todos os dados das aplicações são limpos. Esta funcionalidade é limitada a aplicações LOB. </br>**Não configurado** impede que vários utilizadores finais se inscrevam na aplicação Portal da Empresa no dispositivo utilizando as suas credenciais De AD Azure.
- **Alterações na data e hora do bloco (Samsung Knox)**: Escolha o **Bloco** para evitar que o utilizador mude as definições de data e hora no dispositivo. **Não configurado** permite que os utilizadores alterem as definições de data e hora.

## <a name="password"></a>Palavra-passe

- **Palavra-passe**: **Exija** que o utilizador final introduza uma senha para aceder ao dispositivo. **Não configurado** permite que os utilizadores acedam ao dispositivo sem introduzir uma palavra-passe.

    > [!NOTE]
    > Os dispositivos Samsung Knox exigem automaticamente um PIN de 4 dígitos durante a inscrição na MDM. Os dispositivos Android nativos podem exigir automaticamente que um PIN se torne compatível com o Acesso Condicional.

- Comprimento mínimo da **palavra-passe**: Introduza o comprimento mínimo da palavra-passe que um utilizador deve introduzir (entre 4 e 16 caracteres).
- **Minutos máximos de inatividade até que o ecrã bloqueie**: Introduza o número máximo de minutos de inatividade permitidos no aparelho até que o ecrã bloqueie. Num dispositivo, um utilizador final não pode definir um valor de tempo superior ao tempo configurado no perfil. Um utilizador final pode definir um valor de tempo inferior. Por exemplo, se o perfil estiver definido para 15 minutos, um utilizador final poderá definir o valor para 5 minutos. Um utilizador final não pode definir o valor para 30 minutos. 
- **Número de falhas de entrada antes de limpar o dispositivo**: Introduza o número de falhas de entrada para permitir antes de o dispositivo ser limpo.
- **Expiração da palavra-passe (dias)**: Introduza o número de dias antes de a palavra-passe do dispositivo ser alterada.
- Tipo de **palavra-passe necessário**: Introduza o nível de complexidade da palavra-passe exigido e se podem ser utilizados dispositivos biométricos. As opções são:
  - **Predefinição do dispositivo**
  - **Biométrica de segurança baixa**
  - **Pelo menos numérica**
  - **Complexo numérico**: Números repetidos ou consecutivos, como "1111" ou "1234", não são permitidos. <sup>1</sup>
  - **Pelo menos alfabética**
  - **Pelo menos alfanumérica**
  - **Pelo menos alfanumérica com símbolos**
- **Evite a reutilização de senhas anteriores**: Impede o utilizador final de criar uma palavra-passe que já utilizou anteriormente.
- **Desbloqueio de impressões digitais (apenas Samsung Knox)**: Escolha **o Bloco** para evitar a utilização de uma impressão digital para desbloquear o dispositivo. **Não configurado** permite ao utilizador desbloquear o dispositivo através de uma impressão digital.
- **Smart Lock e outros agentes fidedignos**: Escolha **o Bloco** para evitar que o Smart Lock ou outros agentes fiduciários ajustem as definições do ecrã de bloqueio (Samsung KNOX Standard 5.0+). Esta funcionalidade de telefone, por vezes conhecida como agente fiduciário, permite-lhe desativar ou contornar a palavra-passe do ecrã de bloqueio do dispositivo se o dispositivo estiver num local de confiança. Por exemplo, esta funcionalidade pode ser utilizada quando o dispositivo está ligado a um dispositivo Bluetooth específico, ou quando está perto de uma etiqueta NFC. Pode utilizar esta definição para impedir que os utilizadores configurem o Smart Lock.
- **Encriptação**: Escolha **Exigir para** que os ficheiros do dispositivo sejam encriptados. Nem todos os dispositivos suportam encriptação. Para utilizar esta funcionalidade, também: 
  1. Definir **palavra-passe** para **requerer**.
  2. Definir **o tipo de palavra-passe exigido** para pelo menos **numérico**.
  3. Defina o comprimento mínimo da **palavra-passe** para pelo menos 4 para reportar corretamente a conformidade com esta definição.

  > [!NOTE]
  > Se for imposta uma política de encriptação, os dispositivos Samsung Knox exigem que os utilizadores definam uma palavra-passe complexa de 6 carateres como o código de acesso do dispositivo.

<sup>1</sup> Antes de atribuir esta definição aos dispositivos, certifique-se de atualizar a aplicação Portal da Empresa para a versão mais recente desses dispositivos.

Se definir o tipo de **palavra-passe exigido** para **o complexo numérico,** e depois atribuí-lo a um dispositivo que executa uma versão do Android antes de 5.0, então o comportamento seguinte aplica-se:

- Se a aplicação Do Portal da Empresa estiver a executar uma versão antes de 1704, nenhuma política PIN é aplicada ao dispositivo, e um erro é mostrado no centro de administração do Microsoft Endpoint Manager.
- Se a aplicação Portal da Empresa executar a versão 1704 ou posterior, apenas pode ser aplicado um PIN simples. As versões do Android anteriores a 5.0 não suportam esta configuração. Não é mostrado nenhum erro no centro de administração do Microsoft Endpoint Manager.

## <a name="google-play-store"></a>Google Play Store

- **Google Play store (apenas Samsung Knox)**: Escolha **o Bloco** para impedir que os utilizadores utilizem a loja Google Play. **O utilizador não configurado** permite ao utilizador aceder à loja Google Play no dispositivo.

## <a name="restricted-apps"></a>Aplicações restritas

Utilize estas definições para permitir ou prevenir aplicações específicas no dispositivo. Esta funcionalidade é suportada em dispositivos Android e Samsung Knox Standard:

- **Aplicações proibidas**: Uma lista de aplicações não geridas pela Intune que não quer instaladas no dispositivo. Se um utilizador instalar uma aplicação desta lista, receberá uma notificação do Intune.
- **Aplicações aprovadas**: Uma lista de aplicações que os utilizadores estão autorizados a instalar. Para permanecerem compatíveis, os utilizadores não podem instalar outras aplicações. As aplicações geridas pelo Intune são automaticamente permitidas.

Para adicionar app a estas listas, pode:

- **Adicione** o URL da Google Play Store da aplicação que deseja. Por exemplo, para adicionar a aplicação Microsoft Remote Desktop para Android, introduza `https://play.google.com/store/apps/details?id=com.microsoft.rdc.android`. Para encontrar o URL de uma aplicação, abra a [loja Google Play](https://play.google.com/store/apps)e procure a app. Por exemplo, procure `Microsoft Remote Desktop Play Store` ou `Microsoft Planner`. Selecione a aplicação e copie o URL.
- Importe um ficheiro CSV com detalhes sobre a aplicação, incluindo o URL. Use o url de*aplicativo*<, < nome de*app*>, <*app publisher*> formato. Ou, **Exportar** uma lista existente que inclui a lista de aplicações restritas no mesmo formato.

> [!IMPORTANT]
> Os perfis de dispositivo que utilizam as definições de aplicações restritas têm de ser atribuídos a grupos de utilizadores.

## <a name="browser"></a>Browser

- **Navegador web (apenas Samsung Knox)**: Escolha o **Bloco** para evitar que o navegador predefinido seja utilizado no dispositivo. **Não configurado** permite que o navegador padrão do dispositivo seja utilizado.
- **Autofill (apenas Samsung Knox)**: Escolha **o Bloco** para evitar o enchimento automático de texto no navegador. **Não configurado** permite a função de auto-enchimento do navegador web ser utilizada.
- **Cookies (apenas Samsung Knox)**: Escolha como pretende lidar com cookies a partir de websites do dispositivo. As opções são:
  - Permitir
  - Bloquear todos os cookies
  - Permitir cookies dos sites visitados
  - Permitir cookies do site atual
- **Javascript (apenas Samsung Knox)**: Escolha o **Bloco** para evitar que o navegador web execute scripts Java. **Não configurado** permite que o navegador web do dispositivo execute scripts Java.
- **Pop-ups (apenas Samsung Knox)**: Escolha **o Bloco** para evitar pop-ups no navegador web. **Não configurado** permite pop-ups no navegador web.

## <a name="allow-or-block-apps"></a>Permitir ou Bloquear aplicações

Utilize estas definições para permitir, bloquear ou ocultar aplicações específicas em dispositivos Samsung Knox Standard. As aplicações ocultas não podem ser abertas ou ser percorreu pelo utilizador.

As opções são:

- **Aplicações com permissão para serem instaladas (apenas no Samsung Knox Standard)**
- **Aplicações com início bloqueado (apenas no Samsung Knox Standard)**
- **Aplicações ocultadas do utilizador (apenas no Samsung Knox Standard)**

Para cada definição, adicione uma lista de aplicações. As opções são:

- **Adicione aplicativos por nome de pacote**: Usado principalmente para aplicações de linha de negócio. Introduza o nome da aplicação e o nome do pacote de aplicação.
- **Adicione aplicativos por URL**: Introduza o nome da aplicação e o seu URL na loja Google Play.
- **Adicionar aplicativo de loja**: Selecione uma aplicação da lista existente de aplicações que gere no Intune.

## <a name="cloud-and-storage"></a>Cloud e Armazenamento

- **Backup da Google (apenas Samsung Knox)**: Escolha o **Bloco** para evitar que o dispositivo se sincronize com a cópia de segurança da Google. **Não configurado** permite a utilização de backup do Google.
- **Sincronização automática da conta google (apenas Samsung Knox)**: Escolha o **Bloco** para evitar a funcionalidade de sincronização automática da conta da Google no dispositivo. **Não configurado** permite que as definições da conta do Google sejam automaticamente sincronizadas.
- **Armazenamento amovível (apenas Samsung Knox)**: Escolha **o Bloco** para evitar que o dispositivo utilize armazenamento amovível. **Não configurado** permite que o dispositivo utilize armazenamento amovível, como um cartão SD.
- **Encriptação em cartões de armazenamento (apenas Samsung Knox)**: **Exigir** que os cartões de armazenamento sejam encriptados. **Não configurado** permite a sua aplicação de cartões de armazenamento não encriptados. Nem todos os dispositivos suportam encriptação de cartões de armazenamento. Para confirmar, consulte o fabricante do dispositivo.

## <a name="cellular-and-connectivity"></a>Rede Móvel e Conectividade

- **Roaming de dados (apenas Samsung Knox)**: Escolha **o Bloco** para evitar que os dados perloquem a rede celular. **Não configurado** permite o roaming de dados quando o dispositivo está numa rede celular.
- **SMS/MMS mensagens (apenas Samsung Knox)**: Escolha **o Bloco** para evitar mensagens de texto no dispositivo. **Não configurado** permite a utilização de mensagens SMS e MMS no dispositivo.
- **Marcação por voz (apenas Samsung Knox)**: Escolha o **Bloco** para evitar que os utilizadores utilizem a função de marcação de voz no dispositivo. **Não configurado** permite a marcação de voz no dispositivo.
- **Roaming de voz (apenas Samsung Knox)**: Escolha **o Bloco** para evitar que a voz vagueie pela rede celular. **Não configurado** permite o roaming de voz quando o dispositivo está numa rede celular.
- **Bluetooth (apenas Samsung Knox)**: Escolha **o Bloco** para evitar a utilização de Bluetooth no dispositivo. **Não configurado** permite a utilização de Bluetooth no dispositivo.
- **NFC (apenas Samsung Knox)**: Escolha **o Bloco** para parar a tecnologia Near Field Communication (NFC). **Não configurado** permite operações que utilizam comunicações de campo próximas em dispositivos suportados.
- **Wi-Fi (apenas Samsung Knox)**: Escolha **o bloco** para evitar a utilização de Wi-Fi no dispositivo. **Não configurado** permite utilizar as funcionalidades Wi-Fi do dispositivo.
- **Wi-Fi tethering (apenas Samsung Knox)**: Escolha o **bloco** para evitar a utilização de wi-fi no dispositivo. **Não configurado** permite a utilização de tetering Wi-Fi no dispositivo.

## <a name="kiosk"></a>Modo de Local Público

As definições de modo de local público aplicam-se apenas a dispositivos Samsung Knox Standard e apenas a aplicações que gere com o Intune.

- Adicione aplicações que pretende executar quando o dispositivo estiver no modo quiosque. No modo quiosque, apenas as aplicações que adiciona executar; apps não adicionadas não executar. Os navegadores pré-instalados não funcionam como uma aplicação quando o dispositivo está em modo quiosque. Se for necessário utilizar um browser, considere a utilização do [Managed Browser](../apps/app-configuration-managed-browser.md).

  As opções das suas aplicações:

  - **Adicione aplicativos por nome de pacote**: Usado principalmente para aplicações de linha de negócio. Introduza o nome da aplicação e o nome do pacote de aplicação.
  - **Adicione aplicativos por URL**: Introduza o nome da aplicação e o seu URL na loja Google Play.
  - **Adicionar aplicativo de loja**: Selecione uma aplicação da lista existente de aplicações que gere no Intune.

- **Botão de sono de ecrã**: Escolha o **Bloco** para prevenir ou esconder o botão de sono do ecrã. **Não configurado** permite o botão de despertar do sono do ecrã no dispositivo.
- **Botões de volume**: Escolha o **Bloco** para evitar que o utilizador ajuste o volume desativando os botões de volume. **Não configurado** permite utilizar os botões de volume do dispositivo.

## <a name="next-steps"></a>Próximos passos

[Atribua o perfil](../device-profile-assign.md) e [monitorize o respetivo estado](../device-profile-monitor.md).

Também pode criar perfis de quiosque para dispositivos [Android Enterprise](device-restrictions-android-for-work.md#dedicated-device-settings) e [Windows 10.](kiosk-settings.md)

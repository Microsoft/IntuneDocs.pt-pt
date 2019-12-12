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
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.reviewer: ayesham, chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: dfc791450eec9f17be68228bb291ca89fd7d88ce
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72506820"
---
# <a name="android-and-samsung-knox-standard-device-restriction-settings-lists-in-intune"></a>Listas de configurações de restrição de dispositivo Android e Samsung Knox Standard no Intune

Este artigo mostra-lhe todas as definições de restrições de dispositivos do Microsoft Intune que pode configurar para dispositivos a executar o Android.

>[!TIP]
>Se as definições que pretende não estiverem disponíveis, poderá conseguir configurá-las nos seus dispositivos através de um [perfil personalizado](../custom-settings-android.md).

## <a name="general"></a>Geral

- **Câmera**: escolha o **bloco** para impedir o acesso à câmera. **Não configurado** permite o acesso à câmara do dispositivo.
- **Copiar e colar (somente Samsung Knox)** : escolha **Bloquear** para evitar copiar e colar. **Não configurado** permite que as funções copiar e colar no dispositivo.
- **Compartilhamento de área de transferência entre aplicativos (somente Samsung Knox)** : escolha **Bloquear** para impedir o uso da área de transferência para copiar e colar entre aplicativos. **Não configurado** permite usar a área de transferência para copiar e colar entre aplicativos.
- **Envio de dados de diagnóstico (somente Samsung Knox)** : escolha **Bloquear** para impedir que o usuário envie dados de diagnóstico do dispositivo. **Não configurado** permite que o usuário envie os dados.
- **Apagar (somente Samsung Knox)** : permite que o usuário execute uma ação de [apagamento](../remote-actions/devices-wipe.md) no dispositivo.
- **Geolocalização (somente Samsung Knox)** : escolha **Bloquear** para desabilitar o uso de informações de localização pelo dispositivo. **Não configurado** permite que o dispositivo use as informações de local.
- Desligar **(somente Samsung Knox)** : escolha **Bloquear** para impedir que o usuário desligue o dispositivo. Se essa configuração estiver desabilitada, o **número de falhas de entrada antes de apagar a** configuração do dispositivo não poderá ser definido e não funcionará. **Não configurado** permite que o usuário desligue o dispositivo.
- **Captura de tela (somente Samsung Knox)** : escolha **Bloquear** para evitar capturas de telas. **Não configurado** permite ao utilizador capturar o conteúdo do ecrã como uma imagem.
- **Assistente de voz (somente Samsung Knox)** : escolha o **bloco** para desabilitar o serviço de voz S. **Não configurado** permite o uso do serviço de voz S e do aplicativo no dispositivo. Essa configuração não se aplica a Bixby ou ao assistente de voz para acessibilidade que lê o conteúdo da tela em voz alta.
- **YouTube (somente Samsung Knox)** : escolha **Bloquear** para impedir que os usuários usem o aplicativo YouTube. **Não configurado** permite usar o aplicativo YouTube no dispositivo.
- **Dispositivos compartilhados (somente Samsung Knox)** : Configure um dispositivo Samsung Knox Standard gerenciado como compartilhado. Quando definido como **permitir**, os usuários finais podem entrar e sair do dispositivo com suas credenciais do Azure AD. O dispositivo permanece gerenciado, independentemente de estar em uso ou não.</br>Quando usado em com um perfil de certificado SCEP, esse recurso permite que os usuários finais compartilhem um dispositivo com os mesmos aplicativos para todos os usuários. Mas, cada usuário tem seu próprio certificado de usuário SCEP. Quando os utilizadores terminam sessão, todos os dados das aplicações são limpos. Esta funcionalidade é limitada a aplicações LOB. </br>**Não configurado** impede que vários usuários finais entrem no aplicativo portal da empresa no dispositivo usando suas credenciais do Azure AD.
- **Bloquear alterações de data e hora (Samsung Knox)** : escolha **Bloquear** para impedir que o usuário altere as configurações de data e hora no dispositivo. **Não configurado** permite que os usuários alterem as configurações de data e hora.

## <a name="password"></a>Palavra-passe

- **Senha**: **exige** que o usuário final Insira uma senha para acessar o dispositivo. **Não configurado** permite que os utilizadores acedam ao dispositivo sem introduzir uma palavra-passe.

    > [!NOTE]
    > Os dispositivos Samsung Knox exigem automaticamente um PIN de 4 dígitos durante a inscrição na MDM. Dispositivos Android nativos podem exigir automaticamente um PIN para se tornarem compatíveis com o acesso condicional.

- **Comprimento mínimo da palavra-passe**: introduza o comprimento mínimo da palavra-passe de um utilizador tem de introduzir (entre 4 e 16 carateres).
- **Máximo de minutos de inatividade até a tela ser bloqueada**: Insira o número máximo de minutos de inatividade permitido no dispositivo até que a tela seja bloqueada. Num dispositivo, um utilizador final não pode definir um valor de tempo superior ao tempo configurado no perfil. Um utilizador final pode definir um valor de tempo inferior. Por exemplo, se o perfil estiver definido para 15 minutos, um utilizador final poderá definir o valor para 5 minutos. Um utilizador final não pode definir o valor para 30 minutos. 
- **Número de falhas de entrada antes de apagar o dispositivo**: Insira o número de falhas de entrada a serem permitidas antes que o dispositivo seja apagado.
- **Expiração da senha (dias)** : Insira o número de dias antes que a senha do dispositivo deva ser alterada.
- **Tipo de senha necessária**: Insira o nível de complexidade de senha necessário e se os dispositivos biométricos podem ser usados. As opções são:
  - **Predefinição do dispositivo**
  - **Biométrica de segurança baixa**
  - **Pelo menos numérica**
  - **Numérico complexo**: números repetidos ou consecutivos, como "1111" ou "1234", não são permitidos. <sup>1</sup>
  - **Pelo menos alfabética**
  - **Pelo menos alfanumérica**
  - **Pelo menos alfanumérica com símbolos**
- **Evitar a reutilização de senhas anteriores**: impede que o usuário final crie uma senha que usou antes.
- **Desbloqueio de impressão digital (somente Samsung Knox)** : escolha **Bloquear** para impedir o uso de uma impressão digital para desbloquear o dispositivo. **Não configurado** permite ao utilizador desbloquear o dispositivo através de uma impressão digital.
- **Smart Lock e outros agentes de confiança**: escolha **Bloquear** para impedir que Smart Lock ou outros agentes de confiança ajustem as configurações da tela de bloqueio (Samsung Knox Standard 5.0 +). Esse recurso de telefone, às vezes conhecido como agente de confiança, permite desabilitar ou ignorar a senha da tela de bloqueio do dispositivo se o dispositivo estiver em um local confiável. Por exemplo, esse recurso pode ser usado quando o dispositivo está conectado a um dispositivo Bluetooth específico ou quando está próximo de uma marca NFC. Pode utilizar esta definição para impedir que os utilizadores configurem o Smart Lock.
- **Criptografia**: escolha **exigir** para que os arquivos no dispositivo sejam criptografados. Nem todos os dispositivos dão suporte à criptografia. Para usar esse recurso, também: 
  1. Defina a **senha** como **necessária**.
  2. Defina o **tipo de senha necessária** como **, pelo menos, numérico**.
  3. Defina o **comprimento mínimo da senha** para pelo menos 4 para relatar corretamente a conformidade para essa configuração.

  > [!NOTE]
  > Se for imposta uma política de encriptação, os dispositivos Samsung Knox exigem que os utilizadores definam uma palavra-passe complexa de 6 carateres como o código de acesso do dispositivo.

<sup>1</sup> antes de atribuir essa configuração a dispositivos, certifique-se de atualizar o aplicativo portal da empresa para a versão mais recente nesses dispositivos.

Se você definir o **tipo de senha necessária** para **numérico complexo**e, em seguida, atribuí-lo a um dispositivo que executa uma versão do Android anterior a 5,0, o comportamento a seguir se aplicará:

- Se o aplicativo Portal da Empresa estiver executando uma versão anterior à 1704, nenhuma política de PIN será aplicada ao dispositivo e um erro será mostrado na portal do Azure.
- Se a aplicação Portal da Empresa executar a versão 1704 ou posterior, apenas pode ser aplicado um PIN simples. As versões do Android anteriores a 5,0 não dão suporte a essa configuração. Nenhum erro é mostrado na portal do Azure.

## <a name="google-play-store"></a>Google Play Store

- **Google Play Store (somente Samsung Knox)** : escolha **Bloquear** para impedir que os usuários usem o armazenamento Google Play. **Não configurado** permite que o usuário acesse o repositório de Google Play no dispositivo.

## <a name="restricted-apps"></a>Aplicações restritas

Use essas configurações para permitir ou impedir aplicativos específicos no dispositivo. Esse recurso tem suporte em dispositivos Android e Samsung Knox Standard:

- **Aplicativos proibidos**: uma lista de aplicativos não gerenciados pelo Intune que você não deseja que estejam instalados no dispositivo. Se um utilizador instalar uma aplicação desta lista, receberá uma notificação do Intune.
- **Aplicativos aprovados**: uma lista de aplicativos que os usuários têm permissão para instalar. Para permanecerem compatíveis, os utilizadores não podem instalar outras aplicações. As aplicações geridas pelo Intune são automaticamente permitidas.

Para adicionar o aplicativo a essas listas, você pode:

- **Adicione** a URL de Google Play Store do aplicativo que você deseja. Por exemplo, para adicionar o aplicativo Área de Trabalho Remota da Microsoft para Android, insira `https://play.google.com/store/apps/details?id=com.microsoft.rdc.android`. Para localizar a URL de um aplicativo, abra o [Google Play Store](https://play.google.com/store/apps)e procure o aplicativo. Por exemplo, procure `Microsoft Remote Desktop Play Store` ou `Microsoft Planner`. Selecione a aplicação e copie o URL.
- Importe um ficheiro CSV com detalhes sobre a aplicação, incluindo o URL. Use a*URL do aplicativo*< >, <*nome do aplicativo*>, < formato do editor do*aplicativo*>. Ou então, **exporte** uma lista existente que inclui a lista de aplicativos restritos no mesmo formato.

> [!IMPORTANT]
> Os perfis de dispositivo que utilizam as definições de aplicações restritas têm de ser atribuídos a grupos de utilizadores.

## <a name="browser"></a>Browser

- **Navegador da Web (somente Samsung Knox)** : escolha **Bloquear** para impedir que o navegador da Web padrão seja usado no dispositivo. **Não configurado** permite que o navegador da Web padrão do dispositivo seja usado.
- **Preenchimento automático (somente Samsung Knox)** : escolha **Bloquear** para evitar o preenchimento automático do texto no navegador. **Não configurado** permite que a função de preenchimento automático do navegador da Web seja usada.
- **Cookies (somente Samsung Knox)** : escolha como você deseja manipular cookies de sites no dispositivo. As opções são:
  - Allow
  - Bloquear todos os cookies
  - Permitir cookies dos sites visitados
  - Permitir cookies do site atual
- **JavaScript (somente Samsung Knox)** : escolha **Bloquear** para impedir que o navegador da Web execute scripts java. **Não configurado** permite que o navegador da Web do dispositivo execute scripts java.
- **Pop-ups (somente Samsung Knox)** : escolha **Bloquear** para impedir pop-ups no navegador da Web. **Não configurado** permite pop-ups no navegador da Web.

## <a name="allow-or-block-apps"></a>Permitir ou Bloquear aplicações

Use essas configurações para permitir, bloquear ou ocultar aplicativos específicos em dispositivos Samsung Knox Standard. Os aplicativos ocultos não podem ser abertos ou executados pelo usuário.

As opções são:

- **Aplicações com permissão para serem instaladas (apenas no Samsung Knox Standard)**
- **Aplicações com início bloqueado (apenas no Samsung Knox Standard)**
- **Aplicações ocultadas do utilizador (apenas no Samsung Knox Standard)**

Para cada configuração, adicione uma lista de aplicativos. As opções são:

- **Adicionar aplicativos pelo nome do pacote**: usado principalmente para aplicativos de linha de negócios. Introduza o nome da aplicação e o nome do pacote de aplicação.
- **Adicionar aplicativos por URL**: Insira o nome do aplicativo e sua URL no repositório de Google Play.
- **Adicionar aplicativo da loja**: selecione um aplicativo na lista existente de aplicativos que você gerencia no Intune.

## <a name="cloud-and-storage"></a>Cloud e Armazenamento

- **Backup do Google (somente Samsung Knox)** : escolha o **bloco** para impedir que o dispositivo seja sincronizado com o backup do Google. **Não configurado** permite o uso do backup do Google.
- **Sincronização automática da conta do Google (somente Samsung Knox)** : escolha **Bloquear** para impedir o recurso de sincronização automática da conta do Google no dispositivo. **Não configurado** permite que as configurações de conta do Google sejam sincronizadas automaticamente.
- **Armazenamento removível (somente Samsung Knox)** : escolha **Bloquear** para impedir que o dispositivo use o armazenamento removível. **Não configurado** permite que o dispositivo use o armazenamento removível, como um cartão SD.
- **Criptografia em cartões de memória (somente Samsung Knox)** : **exigir** impõe que os cartões de memória devem ser criptografados. **Não configurado** permite que cartões de armazenamento não criptografados sejam usados. Nem todos os dispositivos dão suporte à criptografia de cartão de memória. Para confirmar, verifique com o fabricante do dispositivo.

## <a name="cellular-and-connectivity"></a>Rede Móvel e Conectividade

- **Roaming de dados (somente Samsung Knox)** : escolha **Bloquear** para impedir o roaming de dados na rede celular. **Não configurado** permite dados em roaming quando o dispositivo estiver numa rede celular.
- **Mensagens SMS/MMS (somente Samsung Knox)** : escolha **Bloquear** para impedir mensagens de texto no dispositivo. **Não configurado** permite o uso de mensagens SMS e MMS no dispositivo.
- **Discagem por voz (somente Samsung Knox)** : escolha **Bloquear** para impedir que os usuários usem o recurso de discagem por voz no dispositivo. **Não configurado** permite a discagem por voz no dispositivo.
- **Roaming de voz (somente Samsung Knox)** : escolha **Bloquear** para impedir o roaming de voz na rede celular. **Não configurado** permite o roaming de voz quando o dispositivo está em uma rede de celular.
- **Bluetooth (somente Samsung Knox)** : escolha **Bloquear** para impedir o uso de Bluetooth no dispositivo. **Não configurado** permite o uso do Bluetooth no dispositivo.
- **NFC (somente Samsung Knox)** : escolha **Bloquear** para interromper a tecnologia NFC (comunicação a curta distância). **Não configurado** permite operações que usam comunicação a curta distância em dispositivos com suporte.
- **Wi-Fi (somente Samsung Knox)** : escolha **Bloquear** para impedir o uso de Wi-Fi no dispositivo. **Não configurado** permite usar os recursos de Wi-Fi do dispositivo.
- **Compartilhamento de Internet por Wi-Fi (somente Samsung Knox)** : escolha **Bloquear** para impedir o uso do compartilhamento de Internet por Wi-Fi no dispositivo. **Não configurado** permite o uso de compartilhamento de Internet por Wi-Fi no dispositivo.

## <a name="kiosk"></a>Modo de Local Público

As definições de modo de local público aplicam-se apenas a dispositivos Samsung Knox Standard e apenas a aplicações que gere com o Intune.

- Adicione aplicativos que você deseja executar quando o dispositivo estiver no modo de quiosque. No modo de quiosque, somente os aplicativos que você adicionar executarão; os aplicativos não adicionados não são executados. Os navegadores pré-instalados não são executados como um aplicativo quando o dispositivo está no modo de quiosque. Se for necessário utilizar um browser, considere a utilização do [Managed Browser](../apps/app-configuration-managed-browser.md).

  Suas opções de aplicativo:

  - **Adicionar aplicativos pelo nome do pacote**: usado principalmente para aplicativos de linha de negócios. Introduza o nome da aplicação e o nome do pacote de aplicação.
  - **Adicionar aplicativos por URL**: Insira o nome do aplicativo e sua URL no repositório de Google Play.
  - **Adicionar aplicativo da loja**: selecione um aplicativo na lista existente de aplicativos que você gerencia no Intune.

- **Botão de suspensão da tela**: escolha **Bloquear** para impedir ou ocultar o botão de suspensão da tela. **Não configurado** permite o botão de ativação de suspensão de tela no dispositivo.
- **Botões de volume**: escolha **Bloquear** para impedir que o usuário ajuste o volume desabilitando os botões de volume. **Não configurado** permite usar os botões de volume no dispositivo.

## <a name="next-steps"></a>Próximos passos

[Atribua o perfil](../device-profile-assign.md) e [monitorize o respetivo estado](../device-profile-monitor.md).

Você também pode criar perfis de quiosque para dispositivos [Android Enterprise](device-restrictions-android-for-work.md#dedicated-device-settings) e [Windows 10](kiosk-settings.md) .

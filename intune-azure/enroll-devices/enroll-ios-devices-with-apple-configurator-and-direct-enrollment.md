---
title: "Inscrever dispositivos iOS com o Apple Configurator e a inscrição direta"
titleSuffix: Intune Azure preview
description: "Pré-visualização do Azure no Intune: saiba como utilizar o Apple Configurator para inscrever dispositivos iOS pertencentes à empresa com a inscrição direta."
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e6c0a430-1851-4108-812a-87e0fc2623b5
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 3758df744311392528be01c826527c2a9d879975
ms.openlocfilehash: 02675b6fe9872cb634d0515172f696cedc7e6463
ms.contentlocale: pt-pt
ms.lasthandoff: 05/10/2017


---

# <a name="enroll-ios-devices-with-apple-configurator-and-direct-enrollment"></a>Inscrever dispositivos iOS com o Apple Configurator e a inscrição direta 

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

O Intune suporta a inscrição de dispositivos iOS pertencentes à empresa com o [Apple Configurator](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12) em execução num computador Mac. Este processo não efetua a reposição de fábrica do dispositivo e inscreve o dispositivo com uma política predefinida. Este método destina-se a dispositivos **sem afinidade de utilizadores** e requer que ligue o dispositivo iOS através de USB a um computador Mac para configurar a inscrição empresarial.

>[!NOTE]
>Este método de inscrição não pode ser utilizado com o método do [gestor de inscrição de dispositivos](enroll-devices-using-device-enrollment-manager.md).

Quando estiver a inscrever diretamente dispositivos iOS, pode inscrever um dispositivo sem adquirir o número de série do mesmo. Também pode dar um nome ao dispositivo para fins de identificação antes de o Intune capturar o nome do dispositivo durante a inscrição. A aplicação Portal da Empresa não é suportada para os dispositivos inscritos diretamente. Esta instrução parte do princípio de que está a utilizar o Apple Configurator 2.0 no computador Mac.

Para obter outros métodos para inscrever dispositivos iOS estão descritos em [Escolher como inscrever dispositivos iOS no Intune](choose-ios-enrollment-method.md).


## <a name="prerequisites"></a>Pré-requisitos

Antes de configurar a inscrição de dispositivos iOS, tem de cumprir os seguintes pré-requisitos:

- [Configurar domínios](https://docs.microsoft.com/intune/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-2)
- [Definir a Autoridade de MDM](set-mdm-authority.md)
- [Criar grupos](https://docs.microsoft.com/intune/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-5)
- [Configurar o Portal da Empresa](../manage-apps/company-portal-app.md)
- Atribuir licenças de utilizador no [portal do Office 365](http://go.microsoft.com/fwlink/p/?LinkId=698854)
- [Obter um certificado push de MDM da Apple](get-an-apple-mdm-push-certificate.md)
- Confirmar que tem acesso físico aos dispositivos iOS
- Ter os números de série dos dispositivos (veja [Como obter um número de série iOS](https://support.apple.com//HT204308))
- Ter cabos de ligação USB disponíveis
- Confirmar que tem um PC Mac com o [Apple Configurator 2.0](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12) instalado

## <a name="create-an-apple-configurator-profile-for-devices"></a>Criar um perfil do Apple Configurator para dispositivos

Um perfil de inscrição de dispositivos especifica as definições aplicadas a um grupo de dispositivos. Os seguintes passos mostram como criar um perfil de inscrição de dispositivos para os dispositivos iOS inscritos através do Apple Configurator.

1. No portal do Azure, selecione **Mais Serviços** > **Monitorização + Gestão** > **Intune**.

2. No painel Intune, escolha **Inscrever dispositivos** e, em seguida, escolha **Inscrição da Apple**.

3. Em **Gerir Definições de Inscrição do Apple Configurator**, selecione **Perfis do AC**.

4. No painel **Perfis de Inscrição do Apple Configurator**, selecione **Criar**.

5. No painel **Criar Perfil de Inscrição**, introduza um nome e uma descrição para o perfil.

6. Para **Afinidade de Utilizador**, escolha **Inscrever sem afinidade do utilizador** para garantir que o dispositivo não é afiliado a um utilizador. Utilize esta afiliação em dispositivos que efetuem tarefas sem aceder aos dados de utilizador locais. As aplicações que requerem afiliação de utilizadores (incluindo a aplicação Portal da Empresa utilizada para instalar aplicações de linha de negócio) não irão funcionar.

7. Selecione **Criar** para guardar o perfil.

## <a name="export-the-profile-as-mobileconfig-to-ios-devices"></a>Exportar o perfil como .mobileconfig para dispositivos iOS

1. No painel **Exportar Perfil**, transfira o perfil de inscrição para [Apple Configurator](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12) para emitir diretamente como um perfil de gestão para um dispositivo iOS ligado. Este método não faz uma reposição de fábrica do dispositivo.

2. Prepare o dispositivo com o Apple Configurator ao realizar os seguintes passos.

   a. Num computador Mac, abra o Apple Configurator 2.0.

   b. Ligue o dispositivo iOS ao computador Mac com um cabo USB. Feche Fotografias, o iTunes e outras aplicações que são abertas para o dispositivo quando o dispositivo é detetado.

   c. No Apple Configurator, selecione o dispositivo iOS ligado e, em seguida, selecione o botão **Adicionar**. As opções que podem ser adicionadas ao dispositivo aparecem na lista pendente. Selecione **Perfis**.

   d. Utilize o seletor de ficheiros para selecionar o ficheiro .mobileconfig que exportou a partir do Intune e, em seguida, selecione **Adicionar**. O perfil é adicionado ao dispositivo. Se o dispositivo for Não supervisionado, a instalação vai exigir a aceitação no dispositivo.

3. Realize os seguintes passos para instalar o perfil no dispositivo iOS. O dispositivo já tem de ter concluído o Assistente de Configuração e estar pronto a utilizar. Se o registo implicar implementações de aplicações, o dispositivo deve ter um ID Apple configurado porque as implementações de aplicações irão exigir que tenha um ID Apple registado na App Store.

   a. Desbloqueie o dispositivo iOS.

   b. Na caixa de diálogo **Instalar perfil** de **Perfil de gestão**, escolha **Instalar**.

   c. Indique o Código de Acesso do Dispositivo ou o ID Apple, se for preciso.

   d. Aceite o **Aviso** e selecione **Instalar**.

   e. Aceite o **Aviso Remoto** e selecione **Confiar**.

   f. Quando a caixa **Perfil instalado** confirmar que o perfil foi Instalado, escolha **Concluído**.

4. No dispositivo iOS, abra as **Definições** e aceda a **Geral** > **Gestão de Dispositivos** > **Perfil de Gestão**. Confirme que a instalação do perfil se encontra na lista e verifique as restrições de política do iOS e as aplicações instaladas. As restrições de política e as aplicações poderão demorar até 10 minutos a aparecer no dispositivo.

5. Distribua os dispositivos. O dispositivo iOS está agora inscrito no Intune e gerido.


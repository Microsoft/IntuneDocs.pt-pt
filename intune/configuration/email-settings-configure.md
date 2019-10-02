---
title: Configurar definições de e-mail no Microsoft Intune – Azure | Microsoft Docs
titleSuffix: ''
description: Crie um perfil de e-mail no Microsoft Intune e implemente-o em dispositivos Android Enterprise, iOS e Windows. Utilize um perfil de e-mail para configurar definições de e-mail comuns, incluindo um servidor de e-mail e um método de autenticação para ligar ao e-mail empresarial em dispositivos que gere.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 09/04/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 41eb282767e6699d9286c6867ff51e4c1a2e00ec
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/02/2019
ms.locfileid: "71730648"
---
# <a name="add-email-settings-to-devices-using-intune"></a>Adicionar definições de e-mail a dispositivos com o Intune

O Microsoft Intune inclui várias definições de e-mail que pode implementar em dispositivos da sua organização. Um administrador de ti cria perfis de email com configurações específicas para se conectar a um servidor de email, como o Office 365 e o gmail. Em seguida, os usuários finais se conectam, autenticam e sincronizam suas contas de email organizacionais em seus dispositivos móveis. Ao criar e implantar um perfil de email, você pode confirmar se as configurações são padrão em vários dispositivos. Além disso, pode ajudar a reduzir os pedidos de suporte de utilizadores finais que não sabem quais são as definições de e-mail corretas.

Pode utilizar os perfis de e-mail para configurar as definições de e-mail incorporadas dos seguintes dispositivos:

- Android Samsung Knox Standard 4.0 e posterior
- Android Enterprise
- iOS 8.0 e posterior
- Windows Phone 8.1 e posterior
- Windows 10 (desktop) e Windows 10 Mobile

Este artigo mostra-lhe como criar um perfil de e-mail no Microsoft Intune. Também inclui ligações para definições mais específicas das diferentes plataformas.

## <a name="create-a-device-profile"></a>Criar um perfil de dispositivo

1. Entre no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Selecione **Configuração do dispositivo** > **Perfis** > **Criar perfil**.
3. Introduza as seguintes propriedades:

    - **Nome**: introduza um nome descritivo para a política. Atribua nomes às políticas de forma que possa identificá-las facilmente mais tarde. Por exemplo, um bom nome de política é **as configurações de email para todos os dispositivos Windows**.
    - **Descrição**: introduza uma descrição para o perfil. Esta definição é opcional, mas recomendada.
    - **Plataforma**: escolha a plataforma dos dispositivos. As opções são:

        - **Android** (apenas Samsung Android Knox Standard)
        - **Android Enterprise**
        - **iOS/iPadOS**
        - **Windows Phone 8.1**
        - **Windows 10 e posterior**

    - **Tipo de perfil**: Selecione **email**.

4. Consoante a plataforma que escolheu, as definições que pode configurar variam. Escolha sua plataforma para configurações detalhadas:

    - [Configurações do Android Samsung Knox Standard](../email-settings-android.md)
    - [Configurações do Android Enterprise](../email-settings-android-enterprise.md)
    - [configurações do iOS/iPadOS](email-settings-ios.md)
    - [Definições do Windows Phone 8.1](email-settings-windows-phone-8-1.md)
    - [Definições do Windows 10](email-settings-windows-10.md)

5. Assim que terminar, selecione **OK** > **Criar** para guardar as alterações.

Após introduzir as suas definições e criar o perfil, este será apresentado na lista de perfis. Em seguida, [atribua este perfil a alguns grupos](../device-profile-assign.md).

## <a name="remove-an-email-profile"></a>Remover um perfil de e-mail

Os perfis de e-mail são atribuídos a grupos de dispositivos e não a grupos de utilizadores. Existem diferentes formas de remover um perfil de e-mail de um dispositivo, mesmo quando existe apenas um perfil de e-mail no dispositivo:

- **Opção 1**: Abra o perfil de email (**perfis**de**configuração** > do dispositivo) e escolha **atribuições**. O separador **Incluir** apresenta os grupos atribuídos ao perfil. Clique com o botão direito do rato no grupo e selecione **Remover**. Não se esqueça de **Guardar** as alterações.

- **Opção 2**: [Apagar ou desativar o dispositivo](../remote-actions/devices-wipe.md). Pode utilizar estas ações para remover dados e definições de forma seletiva ou na totalidade.

## <a name="secure-email-access"></a>Proteger o acesso ao e-mail

Pode ajudar a proteger os perfis de e-mail através das seguintes opções:

- **Certificados**: Ao criar o perfil de email, você escolhe um perfil de certificado criado anteriormente no Intune. Este certificado é conhecido como certificado de identidade. A sua função é autenticar em relação a um certificado fidedigno ou um certificado de raiz para confirmar que o dispositivo de um utilizador tem permissões para se ligar. O certificado fidedigno é atribuído ao computador que autentica a ligação de e-mail. Normalmente, este computador é o servidor de e-mail nativo.

  Para obter mais informações sobre como criar e utilizar perfis de certificado no Intune, veja [How to configure certificates with Intune (Como configurar certificados com o Intune)](../protect/certificates-configure.md).

- **Nome de usuário e senha**: O usuário final é autenticado no servidor de email nativo digitando um nome de usuário e senha. A palavra-passe não existe no perfil de e-mail. Portanto, o usuário final insere a senha ao se conectar ao email.

## <a name="how-intune-handles-existing-email-accounts"></a>Como o Intune processa as contas de e-mail existentes

Se o utilizador já tiver configurado uma conta de e-mail, o perfil de e-mail será atribuído de forma diferente consoante a plataforma.

- **iOS**: Um perfil de e-mail duplicado existente é detetado com base no nome de anfitrião e no endereço de e-mail. O perfil de e-mail duplicado impede a atribuição de um perfil do Intune. Nesse caso, o aplicativo Portal da Empresa notifica o usuário de que eles não estão em conformidade e solicita que o usuário final remova manualmente o perfil configurado. Para ajudar a evitar esse cenário, peça aos usuários finais que registrem *antes* de instalar um perfil de email, o que permite ao Intune configurar o perfil.

- **Windows:** Um perfil de e-mail duplicado existente é detetado com base no nome de anfitrião e no endereço de e-mail. O Intune substitui o perfil de email existente criado pelo usuário final.

- **Android Samsung Knox Standard**: Um perfil de e-mail duplicado existente é detetado com base no endereço de e-mail e é substituído pelo perfil do Intune. O Android não utiliza o nome do anfitrião para identificar o perfil. Não crie múltiplos perfis de e-mail com o mesmo endereço de e-mail em diferentes anfitriões. Os perfis substituem uns aos outros.

- **Perfis de trabalho do Android**: O Intune fornece dois perfis de email do Android Work: um para o aplicativo Gmail e um para o nove aplicativos de trabalho. Estas aplicações estão disponíveis na Google Play Store e são instaladas no perfil de trabalho do dispositivo. Esses aplicativos não criam perfis duplicados. Ambas as aplicações suportam ligações ao Exchange. Para utilizar a conectividade de e-mail, implemente uma destas aplicações de e-mail nos dispositivos dos seus utilizadores. Em seguida, crie e implemente o perfil de e-mail adequado. As aplicações de e-mail como o Nine Work podem não ser gratuitas. Reveja os detalhes de licenciamento da aplicação ou contacte a empresa da aplicação para colocar as suas questões.

## <a name="changes-to-assigned-email-profiles"></a>Alterações a perfis de e-mail atribuídos

Se fizer alterações a um perfil de e-mail atribuído anteriormente, os utilizadores finais poderão ver uma mensagem a pedir que aprovem a reconfiguração das definições de e-mail.

## <a name="next-steps"></a>Passos seguintes

O perfil não estará ativo assim que for criado. Em seguida, [atribua o perfil a alguns dispositivos](../device-profile-assign.md).

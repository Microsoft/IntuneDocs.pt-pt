---
title: Configurar definições de e-mail no Microsoft Intune – Azure | Microsoft Docs
titleSuffix: ''
description: Crie um perfil de e-mail no Microsoft Intune e implemente este perfil para dispositivos Android Enterprise, iOS, iPadOS e Windows. Utilize um perfil de e-mail para configurar definições de e-mail comuns, incluindo um servidor de e-mail e um método de autenticação para ligar ao e-mail empresarial em dispositivos que gere.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/18/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 908a20098917540e6f823d94c6643d15f13ecf68
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/20/2020
ms.locfileid: "77511090"
---
# <a name="add-email-settings-to-devices-using-intune"></a>Adicionar definições de e-mail a dispositivos com o Intune

O Microsoft Intune inclui várias definições de e-mail que pode implementar em dispositivos da sua organização. Um administrador de TI cria perfis de e-mail com configurações específicas para ligar a um servidor de correio, como o Office 365 e o Gmail. Os utilizadores finais conectam-se, autenticam e sincronizam as suas contas de email organizacionais nos seus dispositivos móveis. Ao criar e implementar um perfil de e-mail, pode confirmar que as definições são padrão em muitos dispositivos. Além disso, pode ajudar a reduzir os pedidos de suporte de utilizadores finais que não sabem quais são as definições de e-mail corretas.

Pode utilizar os perfis de e-mail para configurar as definições de e-mail incorporadas dos seguintes dispositivos:

- Android Samsung Knox Standard 4.0 e mais recente
- Android Enterprise
- iOS 8.0 e mais recente
- iPadOS 13.0 e mais recente
- Windows Phone 8.1 e mais recente
- Windows 10 (desktop) e Windows 10 Mobile

Este artigo mostra-lhe como criar um perfil de e-mail no Microsoft Intune. Também inclui ligações para definições mais específicas das diferentes plataformas.

## <a name="create-a-device-profile"></a>Criar um perfil de dispositivo

1. Inscreva-se no centro de administração do [Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Selecione **Dispositivos** > Perfis de **Configuração** > **Criar perfil**.
3. Introduza as seguintes propriedades:

    - **Nome**: Introduza um nome descritivo para a apólice. Atribua nomes às políticas de forma que possa identificá-las facilmente mais tarde. Por exemplo, um bom nome de política é **definições de e-mail para todos os dispositivos Windows**.
    - **Descrição:** introduza uma descrição para o perfil. Esta definição é opcional, mas recomendada.
    - **Plataforma**: Escolha a plataforma dos seus dispositivos. As opções são:

        - **Android** (apenas Samsung Android Knox Standard)
        - **Android Enterprise**
        - **iOS/iPadOS**
        - **Windows Phone 8.1**
        - **Windows 10 e posterior**

    - **Tipo de perfil**: Selecione **E-mail**.

4. Consoante a plataforma que escolheu, as definições que pode configurar variam. Escolha a sua plataforma para configurações detalhadas:

    - [Configurações padrão Android Samsung Knox](../email-settings-android.md)
    - [Configurações do Android Enterprise](../email-settings-android-enterprise.md)
    - [definições iOS/iPadOS](email-settings-ios.md)
    - [Definições do Windows Phone 8.1](email-settings-windows-phone-8-1.md)
    - [Definições do Windows 10](email-settings-windows-10.md)

5. Assim que terminar, selecione **OK** > **Criar** para guardar as alterações.

Após introduzir as suas definições e criar o perfil, este será apresentado na lista de perfis. Em seguida, [atribua este perfil a alguns grupos](../device-profile-assign.md).

## <a name="remove-an-email-profile"></a>Remover um perfil de e-mail

Os perfis de e-mail são atribuídos a grupos de dispositivos e não a grupos de utilizadores. Existem diferentes formas de remover um perfil de e-mail de um dispositivo, mesmo quando existe apenas um perfil de e-mail no dispositivo:

- **Opção 1**: Abra o perfil de e-mail **(Dispositivos** > perfis de **configuração** > selecione o seu perfil) e escolha **Atribuições**. O separador **Incluir** apresenta os grupos atribuídos ao perfil. Clique com o botão direito do rato no grupo e selecione **Remover**. Não se esqueça de **Guardar** as alterações.

- **Opção 2**: [elimine ou extinga o dispositivo](../remote-actions/devices-wipe.md). Pode utilizar estas ações para remover dados e definições de forma seletiva ou na totalidade.

## <a name="secure-email-access"></a>Proteger o acesso ao e-mail

Pode ajudar a proteger os perfis de e-mail através das seguintes opções:

- **Certificados**: quando cria o perfil de e-mail, seleciona um perfil de certificado criado anteriormente no Intune. Este certificado é conhecido como certificado de identidade. A sua função é autenticar em relação a um certificado fidedigno ou um certificado de raiz para confirmar que o dispositivo de um utilizador tem permissões para se ligar. O certificado fidedigno é atribuído ao computador que autentica a ligação de e-mail. Normalmente, este computador é o servidor de e-mail nativo.

  Para obter mais informações sobre como criar e utilizar perfis de certificado no Intune, veja [How to configure certificates with Intune (Como configurar certificados com o Intune)](../protect/certificates-configure.md).

- **Nome e palavra-passe**do utilizador : O utilizador final autentica-se no servidor de correio nativo, inserindo um nome de utilizador e uma palavra-passe. A palavra-passe não existe no perfil de e-mail. Assim, o utilizador final introduz a palavra-passe ao ligar-se ao e-mail.

## <a name="how-intune-handles-existing-email-accounts"></a>Como o Intune processa as contas de e-mail existentes

Se o utilizador já tiver configurado uma conta de e-mail, o perfil de e-mail será atribuído de forma diferente consoante a plataforma.

- **iOS/iPadOS**: É detetado um perfil de e-mail duplicado existente com base no nome do anfitrião e no endereço de e-mail. O perfil de e-mail duplicado impede a atribuição de um perfil do Intune. Neste caso, a aplicação Portal da Empresa notifica o utilizador de que não está em conformidade e solicita ao utilizador final que remova manualmente o perfil configurado. Para ajudar a prevenir este cenário, informe os utilizadores finais para se inscreverem *antes* de instalarem um perfil de e-mail, o que permite ao Intune configurar o perfil.

- **Windows**: um perfil de e-mail duplicado existente é detetado com base no nome de anfitrião e no endereço de e-mail. Intune substitui o perfil de e-mail existente criado pelo utilizador final.

- **Android Samsung Knox Standard**: é detetado um perfil de e-mail duplicado existente com base no endereço de e-mail e é substituído pelo perfil do Intune. O Android não utiliza o nome do anfitrião para identificar o perfil. Não crie múltiplos perfis de e-mail com o mesmo endereço de e-mail em diferentes anfitriões. Os perfis sobressaem uns aos outros.

- **Perfis**de trabalho android : Intune fornece dois perfis de email de trabalho Android: um para a aplicação Gmail e outro para a aplicação Nine Work. Estas aplicações estão disponíveis na Google Play Store e são instaladas no perfil de trabalho do dispositivo. Estas aplicações não criam perfis duplicados. Ambas as aplicações suportam ligações ao Exchange. Para utilizar a conectividade de e-mail, implemente uma destas aplicações de e-mail nos dispositivos dos seus utilizadores. Em seguida, crie e implemente o perfil de e-mail adequado. As aplicações de e-mail como o Nine Work podem não ser gratuitas. Reveja os detalhes de licenciamento da aplicação ou contacte a empresa da aplicação para colocar as suas questões.

## <a name="changes-to-assigned-email-profiles"></a>Alterações a perfis de e-mail atribuídos

Se fizer alterações a um perfil de e-mail atribuído anteriormente, os utilizadores finais poderão ver uma mensagem a pedir que aprovem a reconfiguração das definições de e-mail.

## <a name="next-steps"></a>Próximos passos

O perfil não estará ativo assim que for criado. Em seguida, [atribua o perfil](../device-profile-assign.md).

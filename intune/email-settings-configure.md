---
title: Configurar definições de e-mail no Microsoft Intune – Azure | Microsoft Docs
titleSuffix: ''
description: Crie um perfil de e-mail no Microsoft Intune e implemente-o em dispositivos Android Enterprise, iOS e Windows. Utilize um perfil de e-mail para configurar definições de e-mail comuns, incluindo um servidor de e-mail e um método de autenticação para ligar ao e-mail empresarial em dispositivos que gere.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/22/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 33a7593adcab7df76020b8bfe520cf6cbd3c6455
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/20/2018
ms.locfileid: "52186159"
---
# <a name="add-email-settings-to-devices-using-intune"></a>Adicionar definições de e-mail a dispositivos com o Intune

O Microsoft Intune inclui várias definições de e-mail que pode implementar em dispositivos da sua organização. Um administrador de TI pode criar perfis de e-mail com definições específicas para ligar a um servidor de e-mail, como o Office 365 e o Gmail. Depois, os utilizadores podem ligar, autenticar e sincronizar as suas contas de e-mail organizacionais nos dispositivos móveis. Ao criar e implementar um perfil de e-mail, pode verificar que as definições são padrão em muitos dispositivos. Além disso, pode ajudar a reduzir os pedidos de suporte de utilizadores finais que não sabem quais são as definições de e-mail corretas.

Pode utilizar os perfis de e-mail para configurar as definições de e-mail incorporadas dos seguintes dispositivos:

- Android Samsung Knox Standard 4.0 e posterior
- Dispositivos com perfil de trabalho do Android
- iOS 8.0 e posterior
- Windows Phone 8.1 e posterior
- Windows 10 (desktop) e Windows 10 Mobile

Este artigo mostra-lhe como criar um perfil de e-mail no Microsoft Intune. Também inclui ligações para definições mais específicas das diferentes plataformas.

## <a name="create-a-device-profile"></a>Criar um perfil de dispositivo

1. No [portal do Azure](https://portal.azure.com), selecione **Todos os serviços**, filtre o **Intune** e selecione **Microsoft Intune**.
2. Selecione **Configuração do dispositivo** > **Perfis** > **Criar perfil**.
3. Introduza um **Nome** e uma **Descrição** para o perfil de e-mail.
4. Selecione a **Plataforma** da lista pendente. As opções são:

    - **Android** (apenas Samsung Android Knox Standard)
    - **Android Enterprise**
    - **iOS**
    - **macOS**
    - **Windows Phone 8.1**
    - **Windows 8.1 e posterior**
    - **Windows 10 e posterior**

5. Na lista pendente **Tipo de perfil**, selecione **E-mail**.
6. As definições que pode configurar podem variar em cada plataforma. Para ver definições específicas, selecione a sua plataforma:

    - [Definições do Samsung Knox Standard e do perfil de trabalho do Android](email-settings-android.md)
    - [Definições do iOS](email-settings-ios.md)
    - [Definições do Windows Phone 8.1](email-settings-windows-phone-8-1.md)
    - [Definições do Windows 10](email-settings-windows-10.md)

Após introduzir as suas definições e criar o perfil, este será apresentado na lista de perfis. Em seguida, [atribua este perfil a alguns grupos](device-profile-assign.md).

## <a name="remove-an-email-profile"></a>Remover um perfil de e-mail

Os perfis de e-mail são atribuídos a grupos de dispositivos e não a grupos de utilizadores. Existem diferentes formas de remover um perfil de e-mail de um dispositivo, mesmo quando existe apenas um perfil de e-mail no dispositivo:

- **Opção 1**: abra o perfil de e-mail (**Configuração do dispositivo** > **Perfis**) e selecione **Atribuições**. O separador **Incluir** apresenta os grupos atribuídos ao perfil. Clique com o botão direito do rato no grupo e selecione **Remover**. Não se esqueça de **Guardar** as alterações.

- **Opção 2**: [elimine ou extinga o dispositivo](devices-wipe.md). Pode utilizar estas ações para remover dados e definições de forma seletiva ou na totalidade.

## <a name="secure-email-access"></a>Proteger o acesso ao e-mail

Pode ajudar a proteger os perfis de e-mail através das seguintes opções:

- **Certificados**: quando cria o perfil de e-mail, seleciona um perfil de certificado criado anteriormente no Intune. Este certificado é conhecido como certificado de identidade. A sua função é autenticar em relação a um certificado fidedigno ou um certificado de raiz para confirmar que o dispositivo de um utilizador tem permissões para se ligar. O certificado fidedigno é atribuído ao computador que autentica a ligação de e-mail. Normalmente, este computador é o servidor de e-mail nativo.

  Para obter mais informações sobre como criar e utilizar perfis de certificado no Intune, veja [How to configure certificates with Intune (Como configurar certificados com o Intune)](certificates-configure.md).

- **Nome de utilizador e palavra-passe**: o utilizador é autenticado no servidor de e-mail nativo ao introduzir um nome de utilizador e uma palavra-passe. A palavra-passe não existe no perfil de e-mail. Assim, o utilizador tem de introduzir a palavra-passe ao ligar ao e-mail.

## <a name="how-intune-handles-existing-email-accounts"></a>Como o Intune processa as contas de e-mail existentes

Se o utilizador já tiver configurado uma conta de e-mail, o perfil de e-mail será atribuído de forma diferente consoante a plataforma.

- **iOS**: um perfil de e-mail duplicado existente é detetado com base no nome de anfitrião e no endereço de e-mail. O perfil de e-mail duplicado impede a atribuição de um perfil do Intune. Neste caso, a aplicação Portal da Empresa notifica o utilizador de que não está em conformidade e pede-lhe para remover manualmente o perfil configurado. Para ajudar a evitar esta situação, diga aos seus utilizadores para realizarem a inscrição *antes* da instalação de um perfil de e-mail, o que permite que o Intune configure o perfil.

- **Windows**: um perfil de e-mail duplicado existente é detetado com base no nome de anfitrião e no endereço de e-mail. O Intune substitui o perfil de e-mail existente criado pelo utilizador.

- **Android Samsung Knox Standard**: é detetado um perfil de e-mail duplicado existente com base no endereço de e-mail e é substituído pelo perfil do Intune. O Android não utiliza o nome do anfitrião para identificar o perfil. Não crie múltiplos perfis de e-mail com o mesmo endereço de e-mail em diferentes anfitriões. Os perfis irão substituir-se um ao outro.

- **Perfis de trabalho do Android**: o Intune fornece dois perfis de e-mail de trabalho do Android, um para a aplicação Gmail e outro para a aplicação Nine Work. Estas aplicações estão disponíveis na Google Play Store e são instaladas no perfil de trabalho do dispositivo. Estas aplicações não irão criar perfis duplicados. Ambas as aplicações suportam ligações ao Exchange. Para utilizar a conectividade de e-mail, implemente uma destas aplicações de e-mail nos dispositivos dos seus utilizadores. Em seguida, crie e implemente o perfil de e-mail adequado. As aplicações de e-mail como o Nine Work podem não ser gratuitas. Reveja os detalhes de licenciamento da aplicação ou contacte a empresa da aplicação para colocar as suas questões.

## <a name="changes-to-assigned-email-profiles"></a>Alterações a perfis de e-mail atribuídos

Se fizer alterações a um perfil de e-mail atribuído anteriormente, os utilizadores finais poderão ver uma mensagem a pedir que aprovem a reconfiguração das definições de e-mail.

## <a name="next-steps"></a>Passos Seguintes
O perfil não estará ativo assim que for criado. Em seguida, [atribua o perfil a alguns dispositivos](device-profile-assign.md).
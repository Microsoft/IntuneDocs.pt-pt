---
title: "Como configurar definições de e-mail do Intune | Pré-visualização do Azure no Intune | Documentos da Microsoft"
description: "Pré-visualização do Azure no Intune: saiba como configurar o Intune para criar ligações a e-mail empresarial nos dispositivos que gere."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/08/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 484bd9b0-fbf1-4f4f-940c-6b12fa07e228
ms.reviewer: heenamac
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 3ee87c8f6104b06c8a9492566ff160540624f17e
ms.openlocfilehash: 79faa771a9af0761703ca3e72b937fab1a83a81f


---

# <a name="how-to-configure-email-settings"></a>Como configurar as definições de e-mail 

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Pode utilizar definições de perfil de e-mail para configurar dispositivos que gere com as definições que são precisas para ligar e sincronizar com o e-mail da empresa. Esta funcionalidade pode ajudar a assegurar que as definições são padronizadas em todos os seus dispositivos e também pode ajudar a reduzir as chamadas de suporte dos utilizadores finais que não saibam as definições de e-mail corretas.

O cliente de correio incorporado é suportado na maioria das plataformas. Atualmente, a maioria das aplicações de e-mail de terceiros não são suportadas.

Pode utilizar os perfis de e-mail para configurar o cliente de e-mail nativo nos seguintes tipos de dispositivos:

- Android 4.0 e posterior
- iOS 8.0 e posterior
- Windows Phone 8.1 e posterior
- Windows 10 (desktop) e Windows 10 Mobile

Utilize as informações deste tópico para conhecer as noções básicas sobre como configurar um perfil de e-mail e, em seguida, leia os tópicos de cada plataforma para saber mais sobre as especificações dos dispositivos.

## <a name="create-a-device-profile-containing-email-settings"></a>Criar um perfil de dispositivo com as definições de e-mail

1. Inicie sessão no portal do Azure.
2. Escolha **Mais Serviços** > **Outros** > **Intune**.
3. No painel **Intune**, escolha **Configurar dispositivos**.
2. No painel **Configuração do Dispositivo**, escolha **Gerir** > **Perfis**.
3. No painel de perfis, escolha **Criar Perfil**.
4. No painel **Criar Perfil**, introduza um **Nome** e **Descrição** para o perfil de e-mail.
5. Na lista pendente **Plataforma**, selecione a plataforma do dispositivo à qual pretende aplicar as definições de e-mail. Atualmente, pode escolher uma das seguintes plataformas para definições de dispositivos de e-mail:
    - **Android**
    - **iOS**
    - **Windows Phone 8.1**
    - **Windows 10 e posterior**
6. Na lista pendente **Tipo de perfil**, escolha **E-mail**.
7. As definições que pode configurar diferem consoante a plataforma que escolheu. Aceda a um dos seguintes tópicos para definições detalhadas para cada plataforma:
    - [Definições do Android](email-profile-settings-for-android.md)
    - [Definições do iOS](email-profile-settings-for-ios.md)
    - [Definições do Windows Phone 8.1](email-profile-settings-for-windows-phone-8-1.md)
    - [Definições do Windows 10](email-profile-settings-for-windows-10.md)
8. Quando tiver terminado, volte ao painel **Criar Perfil** e clique em **Criar**.

O perfil será criado e é apresentado no painel da lista de perfis.
Se quiser continuar e atribuir este perfil a grupos, veja [Como atribuir perfis de dispositivo](how-to-assign-device-profiles.md).

## <a name="further-information"></a>Informações adicionais

### <a name="remove-an-email-profile"></a>Remover um perfil de e-mail

Se pretende remover um perfil de e-mail de um dispositivo, edite a atribuição e remova todos os grupos dos quais o dispositivo é membro. Tenha em atenção que não pode remover um perfil de e-mail desta forma se este for o único num dispositivo.

### <a name="securing-email-access"></a>Proteger o acesso ao e-mail

Pode ajudar a proteger os perfis de e-mail através de um de dois métodos:

1. **Certificados** – Quando cria o perfil de e-mail, escolhe um perfil de certificado que tenha criado anteriormente no Intune. Este é conhecido como o certificado de identidade e é utilizado para autenticar um perfil de certificado fidedigno (ou um certificado de raiz) para determinar que o dispositivo do utilizador tem permissões para se ligar. O certificado fidedigno é implementado no computador que autentica a ligação de e-mail, normalmente, o servidor de e-mail nativo.
Para obter mais informações sobre como criar e utilizar perfis de certificado no Intune, veja [How to configure certificates with Intune (Como configurar certificados com o Intune)](/intune-azure/configure-devices/how-to-configure-certificates).
2. **Nome de utilizador e palavra-passe** – O utilizador é autenticado no servidor de e-mail nativo ao indicar o nome de utilizador e a palavra-passe dele.
A palavra-passe não se encontra no perfil de e-mail, por isso, o utilizador tem de fornecer estas informações ao ligar-se ao e-mail.


### <a name="how-intune-handles-existing-email-accounts"></a>Como o Intune processa as contas de e-mail existentes

Se o utilizador já tiver configurado uma conta de e-mail, o resultado da atribuição de perfil de e-mail do Intune depende da plataforma do dispositivo:

- **iOS**: um perfil de e-mail duplicado existente é detetado com base no nome de anfitrião e no endereço de e-mail. O perfil de e-mail duplicado vai bloquear a atribuição de um perfil do Intune. Neste caso, o Portal da Empresa informa o utilizador que não está em conformidade e pede-lhe para remover o perfil manualmente configurado. Para ajudar a evitar este problema, indique aos seus utilizadores para realizarem a inscrição antes da instalação de um perfil de e-mail, o que permite que o Intune configure o perfil.
- **Windows**: um perfil de e-mail duplicado existente é detetado com base no nome de anfitrião e no endereço de e-mail. O Intune substitui o perfil de e-mail existente criado pelo utilizador.
- **Android**: um perfil de e-mail duplicado existente é detetado com base no endereço de e-mail e é substituído pelo perfil do Intune.
Dado que o Android não utiliza o nome de anfitrião para identificar o perfil, recomendamos que não crie múltiplos perfis de e-mail a utilizar no mesmo endereço de e-mail em diferentes anfitriões, uma vez que estes substituem-se uns aos outros.



<!--HONumber=Feb17_HO2-->


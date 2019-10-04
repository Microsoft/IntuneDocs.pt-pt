---
title: Registrar dispositivos iOS – registro de usuário
titleSuffix: Microsoft Intune
description: Saiba como configurar o registro de usuário do iOS e do iPadOS.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/2/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: tisilver
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 57162664d6ca3a35696e56088c4e86acadf45371
ms.sourcegitcommit: 223d64a72ec85fe222f5bb10639da729368e6d57
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/04/2019
ms.locfileid: "71955459"
---
# <a name="set-up-ios-and-ipados-user-enrollment-preview"></a>Configurar o registro de usuário do iOS e iPadOS (visualização)

Você pode configurar o Intune para registrar dispositivos iOS e iPadOS usando o processo de registro de usuário da Apple. O registro de usuário fornece aos administradores um subconjunto simplificado de opções de gerenciamento em comparação com outros métodos de registro.

Para obter mais informações sobre as opções disponíveis com o registro de usuário, consulte [ações com suporte para registro de usuário, senhas e outras opções](ios-user-enrollment-supported-actions.md).

> [!NOTE]
> O suporte para o registro de usuário da Apple no Intune está atualmente em versão prévia.

## <a name="prerequisites"></a>Pré-requisitos
- [Autoridade de Gestão de Dispositivos Móveis (MDM)](../fundamentals/mdm-authority-set.md)
- [Certificado Push de MDM da Apple](apple-mdm-push-certificate-get.md)
- [IDs da Apple gerenciadas](https://support.apple.com/guide/apple-business-manager/mdm1c9622977/web).

## <a name="create-a-user-enrollment-profile-in-intune"></a>Criar um perfil de registro de usuário no Intune

Um perfil de registro define as configurações aplicadas a um grupo de dispositivos durante o registro. 

1. No portal do Intune, escolha **registro de dispositivo** > **registro da Apple** >  tipos de**registro (versão prévia)**  > **Criar perfil** > **Ios**. Esse perfil é onde você indicará qual experiência de registro seus usuários finais do iOS e iPadOS terão em dispositivos não registrados por meio de um método corporativo da Apple. Se você quiser fazer alterações, poderá editar esse perfil depois de criá-lo.

    ![Criar perfil de registro da Apple](./media/ios-user-enrollment/create-profile.png)

2. Na página **noções básicas** , insira um **nome** e uma **Descrição** para o perfil para fins administrativos. Os utilizadores não verão estes detalhes. Pode utilizar este campo **Nome** para criar um grupo dinâmico no Azure Active Directory. Utilize o nome de perfil para definir o parâmetro enrollmentProfileName para atribuir dispositivos com este perfil de inscrição. Saiba mais sobre os [grupos dinâmicos do Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-groups-dynamic-membership-azure-portal#rules-for-devices).

    ![Página de noções básicas](./media/ios-user-enrollment/basics-page.png)


3. Selecione **Seguinte**.

4. Na página **configurações** , você pode optar por fornecer aos usuários a opção de qual tipo de registro eles usarão. Como alternativa, você pode definir um padrão.

    ![Página de definições](./media/ios-user-enrollment/settings-page.png)

    - Se você quiser que todos os usuários neste perfil usem o registro de usuário, siga estas etapas:
        1. Para **exigir que o usuário selecione o tipo de dispositivo**, selecione **não configurado**.
        2. Para **tipo de registro padrão**, selecione **registro de usuário**.
    - Se você quiser que todos os usuários neste perfil usem o registro de dispositivo, siga estas etapas:
        1. Para **exigir que o usuário selecione o tipo de dispositivo**, selecione **não configurado**.
        2. Para **tipo de registro padrão**, selecione **registro de dispositivo**.
    - Se você quiser dar a todos os usuários desse grupo a opção de qual tipo de registro usar, selecione **obrigatório** para **exigir que o usuário selecione o tipo de dispositivo**. Quando os usuários registram seus dispositivos, eles terão a opção de escolher entre **eu ter este dispositivo** e **(empresa) proprietário deste dispositivo**. Se eles escolherem o primeiro, o dispositivo será registrado usando o registro do usuário. Se eles escolherem o segundo, o dispositivo será registrado usando o registro de dispositivo. Se o usuário escolher o **proprietário deste dispositivo**, ele obterá outra opção para proteger todo o dispositivo ou somente aplicativos e dados relacionados ao trabalho. A seleção do usuário final se ele é proprietário do dispositivo determina apenas qual tipo de registro é implementado em seu dispositivo. Essa opção de usuário não é refletida no atributo de propriedade de dispositivo no Intune. Para saber mais sobre a experiência do usuário, consulte [Configurar o acesso do dispositivo Ios aos recursos da empresa](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-ios).
    
    > [!NOTE]
    > O aviso a seguir é impreciso e será removido da interface do usuário.
    > "Para que o acesso condicional funcione em dispositivos direcionados ao registro de usuário, você precisará enviar por push o aplicativo Azure Authenticator como um aplicativo necessário para esse grupo de usuários para habilitar o logon único e Workplace Join."
    > Como administrador, você não precisa realizar nenhuma ação para enviar por push o aplicativo autenticador para seus usuários. Os usuários serão instruídos dentro do Portal da Empresa para instalar o aplicativo autenticador a fim de concluir o processo de registro do usuário para garantir que esses cenários funcionem corretamente.

5. Selecione **Seguinte**.

6. Na página **atribuições** , escolha os grupos de usuários que contêm os usuários aos quais você deseja atribuir esse perfil. Você pode optar por atribuir o perfil a todos os usuários ou grupos específicos. Todos os usuários nos grupos selecionados usarão o tipo de registro escolhido acima. Os grupos de dispositivos não têm suporte para cenários de registro de usuário porque o recurso é baseado em identidades de usuário, em vez de dispositivos. Você pode optar por atribuir o perfil a todos os usuários ou grupos específicos.

    ![Página de atribuições](./media/ios-user-enrollment/assignments-page.png)

7. Selecione **Seguinte**.

8. Na página **revisar e criar** , examine suas escolhas e, em seguida, selecione **criar** para atribuir o perfil aos usuários.

    ![Página de atribuições](./media/ios-user-enrollment/assignments-page.png)


## <a name="profile-priority"></a>Prioridade do perfil

Depois de criar mais de um perfil de tipo de registro, você pode alterar a ordem de prioridade na qual eles são aplicados.

1. No Intune na portal do Azure, escolha **registro de dispositivo** > **registro da Apple** >  tipos de**registro (versão prévia)** .
2. Arraste e solte os perfis na lista na ordem em que você deseja aplicá-los.

No caso de conflitos entre os perfis de qualquer usuário, o perfil de prioridade mais alta é aplicado ao usuário.



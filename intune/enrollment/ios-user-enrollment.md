---
title: Inscreva dispositivos iOS/iPadOS - Inscrição do Utilizador
titleSuffix: Microsoft Intune
description: Saiba como configurar a inscrição do utilizador iOS/iPadOS e iPadOS.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/2/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: tisilver
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: d22d8d4772754fddbd366610402d64acc28ffc65
ms.sourcegitcommit: 25e4847ead0f56c269cfefe1e01c1b9106a28cf1
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/05/2020
ms.locfileid: "78369832"
---
# <a name="set-up-iosipados-and-ipados-user-enrollment-preview"></a>Configurar iOS/iPadOS e iPadOS User Registration (pré-visualização)

Pode configurar o Intune para inscrever dispositivos iOS/iPadOS e iPadOS utilizando o processo de inscrição do utilizador da Apple. A Inscrição do Utilizador confere aos administradores um subconjunto simplificado de opções de gestão em comparação com outros métodos de inscrição.

Para obter mais informações sobre as opções disponíveis com a Inscrição do Utilizador, consulte [as ações suportadas pelo Utilizador, palavras-passe e outras opções.](ios-user-enrollment-supported-actions.md)

> [!NOTE]
> O suporte para a inscrição de utilizadores da Apple em Intune está atualmente em pré-visualização.

## <a name="prerequisites"></a>Pré-requisitos
- [Autoridade de Gestão de Dispositivos Móveis (MDM)](../fundamentals/mdm-authority-set.md)
- [Certificado Push de MDM da Apple](apple-mdm-push-certificate-get.md)
- [IDs apple geridos](https://support.apple.com/guide/apple-business-manager/mdm1c9622977/web).

## <a name="create-a-user-enrollment-profile-in-intune"></a>Criar um perfil de inscrição do utilizador em Intune

Um perfil de inscrição define as definições aplicadas a um grupo de dispositivos durante a inscrição. 

1. No [Microsoft Endpoint Manager Admin Center,](https://go.microsoft.com/fwlink/?linkid=2109431)escolha **dispositivos** > **iOS** > **ioS matricular** > tipos de **inscrição (pré-visualização)**  > **Criar perfil** > **iOS/iPadOS**. Este perfil é onde irá indicar qual a experiência de inscrição que os seus iOS/iPadOS e iPadOS terão em dispositivos não matriculados através de um método corporativo da Apple. Se quiser fazer alterações, pode editar este perfil depois de o ter criado.

    ![Criar perfil de inscrição da Apple](./media/ios-user-enrollment/create-profile.png)

2. Na página **Basics,** introduza um **Nome** e **Descrição** para o perfil para fins administrativos. Os utilizadores não verão estes detalhes. Pode utilizar este campo **Nome** para criar um grupo dinâmico no Azure Active Directory. Utilize o nome de perfil para definir o parâmetro enrollmentProfileName para atribuir dispositivos com este perfil de inscrição. Saiba mais sobre os [grupos dinâmicos do Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-groups-dynamic-membership-azure-portal#rules-for-devices).

    ![Página de noções básicas](./media/ios-user-enrollment/basics-page.png)


3. Selecione **Seguinte**.

4. Na página **Definições,** selecione uma das seguintes opções para o **tipo de inscrição:**

    ![Página de definições](./media/ios-user-enrollment/settings-page.png)

    - **Inscrição**do dispositivo : Todos os utilizadores deste perfil utilizarão a Inscrição do Dispositivo.
    - **Inscrição**do utilizador : Todos os utilizadores deste perfil utilizarão a Inscrição do Utilizador.
    - **Determine com base na escolha**do utilizador : Todos os utilizadores deste grupo terão a escolha do tipo de inscrição a utilizar. Quando os utilizadores matriculam os seus dispositivos, verão uma opção para escolher entre **eu ser dono deste dispositivo** e **(Empresa) possuir este dispositivo**. Se escolherem este último, o dispositivo será matriculado utilizando a Inscrição do Dispositivo. Se o utilizador escolher **que sou dono deste dispositivo,** terá outra opção para proteger todo o dispositivo ou apenas proteger aplicações e dados relacionados com o trabalho. A seleção do utilizador final de se possuir o dispositivo determina que tipo de inscrição é implementado no seu dispositivo. Esta escolha do utilizador também se reflete no atributo de Propriedade do Dispositivo em Intune. Para saber mais sobre a experiência do utilizador, consulte [Configurar o acesso do dispositivo iOS/iPadOS aos recursos da sua empresa.](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-ios)
    
5. Selecione **Seguinte**.

6. Na página **de Atribuição,** escolha os grupos de utilizadores que contêm os utilizadores aos quais pretende que este perfil seja atribuído. Pode optar por atribuir o perfil a todos os utilizadores ou grupos específicos. Todos os utilizadores dos grupos selecionados utilizarão o tipo de inscrição acima indicado. Os grupos de dispositivos não são suportados para cenários de inscrição de utilizadores porque a funcionalidade baseia-se nas identidades dos utilizadores e não nos dispositivos. Pode optar por atribuir o perfil a todos os utilizadores ou grupos específicos.

    ![Página de atribuições](./media/ios-user-enrollment/assignments-page.png)

7. Selecione **Seguinte**.

8. Na página **Review and Create,** reveja as suas escolhas e, em seguida, selecione **Criar** para atribuir o perfil aos utilizadores.

    ![Página de atribuições](./media/ios-user-enrollment/assignments-page.png)


## <a name="profile-priority"></a>Prioridade do perfil

Depois de ter criado mais do que um perfil de tipo de inscrição, pode alterar a ordem prioritária na qual são aplicadas.

1. No [Microsoft Endpoint Manager Admin Center,](https://go.microsoft.com/fwlink/?linkid=2109431)escolha **dispositivos** > **iOS** > **iOS de matrícula** > Tipos de **inscrição (pré-visualização)** .
2. Arraste e deixe cair os perfis na lista na ordem que pretende que sejam aplicados.

Em caso de conflitos entre perfis para qualquer utilizador, o perfil prioritário mais elevado é aplicado ao utilizador.



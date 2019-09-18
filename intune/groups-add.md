---
title: Adicionar grupos para organizar utilizadores e dispositivos
titleSuffix: Microsoft Intune
description: Adicione grupos para organizar utilizadores e dispositivos por geografia, departamento ou hardware específico.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 06/13/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f0a2b858-a824-4598-ab81-bdd8e62ac3b3
ms.reviewer: altsou
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: bab0a33eee5f4d4856fb9d01d822236d1927a4e3
ms.sourcegitcommit: 74911a263944f2dbd9b754415ccda6c68dae0759
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/17/2019
ms.locfileid: "71071734"
---
# <a name="add-groups-to-organize-users-and-devices"></a>Adicionar grupos para organizar utilizadores e dispositivos
O Intune utiliza grupos do Azure Active Directory (AD) para gerir dispositivos e utilizadores. Como administrador do Intune, pode configurar grupos para se adaptarem às suas necessidades organizacionais. Crie grupos para organizar utilizadores ou dispositivos por localização geográfica, departamento ou características de hardware. Utilize grupos para gerir tarefas em escala. Por exemplo, pode definir políticas para vários utilizadores ou implementar aplicações num conjunto de dispositivos.

Pode adicionar os seguintes tipos de grupos:
- **Grupos atribuídos** – adicione manualmente utilizadores ou dispositivos num grupo estático
- **Grupos dinâmicos** – (através do Azure Active Directory Premium) permite-lhe criar dinamicamente grupos de utilizadores ou dispositivos definidos com regras simples ou avançadas

## <a name="add-a-new-group"></a>Adicionar um novo grupo

Utilize os seguintes passos para criar um novo grupo.
1. Entre no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
3. No painel **Intune**, selecione **Grupos** e, em seguida, selecione **Novo grupo** no painel **Todos os grupos**.
   ![Captura de ecrã do portal do Azure com a opção Novo Grupo selecionada](./media/groups-add-new.png)
4. Para **tipo de grupo**, escolha uma das seguintes opções:
    - **Segurança**: Os grupos de segurança são um ótimo recurso para preencher os grupos de utilizadores. Uma vez que os grupos de segurança definem quem tem acesso a que recursos, estes podem ser transferidos com êxito para grupos de utilizadores do Intune. Os grupos de segurança que são sincronizados de Active Directory para Azure Active Directory ou que você cria diretamente no Azure Active Directory por meio do centro de administração Microsoft 365 ou do portal do Azure estão disponíveis para uso quando você cria grupos de usuários no Intune.
    - **Office 365**

5. Digite um **nome** e uma **Descrição** para o novo grupo. Estas propriedades só são apresentadas no portal de gestão e não são apresentadas aos utilizadores.

6. Selecione o **Tipo de associação**:
   - **Atribuído** para criar um grupo com membros atribuídos manualmente. Saiba mais sobre os [grupos atribuídos do Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-groups-create-azure-portal).
   - **Utilizador Dinâmico** para criar um grupo de utilizadores definido com uma **Consulta dinâmica**.
   - **Dispositivo Dinâmico** para criar um grupo de dispositivos definido com uma **Consulta dinâmica**.

   ![Captura de ecrã das propriedades de grupos do Intune](./media/groups-add-properties.png)

   O Azure AD permite-lhe criar grupos dinâmicos com base em regras que definem a associação. Saiba como [criar grupos dinâmicos baseados em atributos](https://docs.microsoft.com/azure/active-directory/active-directory-groups-dynamic-membership-azure-portal).

7. Pode selecionar **Ativar funcionalidades do Office** para conceder aos membros do grupo de utilizadores acesso a aplicações partilhadas do Office 365. Saiba mais sobre os [Grupos do Office 365](https://support.office.com/article/Learn-about-Office-365-groups-b565caa1-5c40-40ef-9915-60fdb2d97fa2).
8. Selecione **Criar** para adicionar o novo grupo.

## <a name="groups-and-policies"></a>Grupos e políticas

Ao criar grupos, considere como você aplicará [as políticas](device-compliance-get-started.md). Por exemplo, pode ter políticas específicas para sistemas operativos de dispositivos e políticas específicas para diferentes funções na sua organização ou para unidades organizacionais que já definiu no Active Directory. Poderá ser útil ter grupos de dispositivos específicos para iOS, Android e Windows, bem como grupos de utilizadores para cada função organizacional.

Também poderá querer criar uma política predefinida que se aplique a todos os grupos e dispositivos e para estabelecer os requisitos de conformidade básicos da sua organização. Em seguida, pode criar políticas mais específicas para as categorias mais amplas de utilizadores e dispositivos. Por exemplo, pode criar políticas de e-mail para cada um dos sistemas operativos do dispositivo.



## <a name="see-also"></a>Consulte também
- [Gerir o acesso aos recursos com grupos do Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-manage-groups)
- [Grupos clássicos do Intune no portal do Azure](groups-get-started.md)

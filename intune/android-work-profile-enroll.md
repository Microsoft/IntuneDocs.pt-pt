---
title: Inscrever dispositivos com perfil de trabalho do Android Enterprise no Intune
titleSuffix: Microsoft Intune
description: Saiba como inscrever dispositivos com perfil de trabalho do Android Enterprise no Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 5/13/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: chmaguir
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 67dc325951ad334a30d9bac8a121d364183fd413
ms.sourcegitcommit: 74911a263944f2dbd9b754415ccda6c68dae0759
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/17/2019
ms.locfileid: "71304587"
---
# <a name="set-up-enrollment-of-android-enterprise-work-profile-devices"></a>Configurar a inscrição de dispositivos com perfil de trabalho do Android Enterprise

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

O Intune ajuda você a implantar aplicativos e configurações em dispositivos Android Enterprise de perfil de trabalho para garantir que as informações pessoais e de trabalho sejam separadas. Para obter detalhes específicos sobre o Android Enterprise, veja [Android Enterprise requirements](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012) (Requisitos empresariais do Android).

Para configurar a gestão de perfis de trabalho do Android Enterprise, siga estes passos:

1. [Ligue a sua conta do inquilino do Intune à sua conta do Android Enterprise](connect-intune-android-enterprise.md).
2. Especifique as definições de inscrição dos perfis de trabalho do Android Enterprise. Os perfis de trabalho do Android Enterprise [só são suportados em determinados dispositivos Android](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012%20style=%22target=new_window%22). Qualquer dispositivo que dê suporte a perfis de trabalho Android Enterprise também dá suporte ao gerenciamento de administrador de dispositivos Android. O Intune permite-lhe especificar a forma como os dispositivos que suportam os perfis de trabalho do Android Enterprise devem ser geridos a partir das [Restrições de Inscrição](enrollment-restrictions-set.md).
    - **Bloquear**:  Todos os dispositivos Android, incluindo dispositivos que dão suporte a perfis de trabalho Android Enterprise, serão registrados como dispositivos de administrador de dispositivo Android, a menos que o registro de administrador do dispositivo Android também seja bloqueado. 
    - **Permitir (definido por padrão)** : todos os dispositivos que suportem os perfis de trabalho do Android Enterprise são inscritos como dispositivos com perfil de trabalho do Android. Qualquer dispositivo Android que não dê suporte a perfis de trabalho do Android Enterprise é registrado como um dispositivo de administrador de dispositivo Android, a menos que o registro de administrador do dispositivo Android seja bloqueado. 
> [!NOTE]
> O padrão definido como **permitir** é verdadeiro para novos locatários a partir de julho de 2019. Todos os locatários anteriores não terão nenhuma alteração nas restrições de registro e verão quaisquer políticas definidas nas restrições de registro. Para locatários anteriores que nunca tiveram alterações de restrições de registro, o **bloqueio** ainda será o padrão para perfis de trabalho do Android Enterprise.

3. [Indique aos seus utilizadores como devem inscrever os dispositivos](/intune-user-help/create-a-work-profile-and-enroll-your-device-in-intune-android).  

Se você deseja registrar dispositivos usando perfis de trabalho do Android Enterprise, mas esses dispositivos já foram registrados com o administrador do dispositivo Android, esses dispositivos devem primeiro cancelar o registro e, em seguida, registrar novamente.
> [!NOTE]
> Como administrador, você pode fazer isso remotamente usando a função **desativar** . Essa função pode ser encontrada no menu ações depois de selecionar o dispositivo na folha **todos os dispositivos** .

Se estiver a inscrever dispositivos com perfil de trabalho do Android Enterprise com uma conta de [Gestor de Inscrições de Dispositivos](device-enrollment-manager-enroll.md), existirá um limite de 10 dispositivos para inscrição por conta.

Para obter mais informações, veja [Dados que o Intune envia para a Google](data-intune-sends-to-google.md).

## <a name="next-steps-for-android-enterprise-work-profiles"></a>Passos seguintes para os perfis de trabalho do Android Enterprise
- [Implementar aplicações do perfil de trabalho do Android Enterprise](apps-add-android-for-work.md)
- [Adicionar políticas de configuração de perfis de trabalho do Android Enterprise](device-profiles.md)

## <a name="see-also"></a>Consulte também

[Configurando e Solucionando problemas de dispositivos Android Enterprise no Microsoft Intune](https://support.microsoft.com/help/4476974)

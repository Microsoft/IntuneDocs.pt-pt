---
title: Registro de administrador do dispositivo Android no Microsoft Intune
titleSuffix: ''
description: Registrar dispositivos Android no Intune usando o registro de administrador do dispositivo.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 07/23/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: chmaguir
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 678eb92bb6f5f23756092cd5d9cc1a645e1e8db3
ms.sourcegitcommit: 73b362173929f59e9df57e54e76d19834f155433
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/27/2019
ms.locfileid: "74562361"
---
# <a name="android-device-administrator-enrollment"></a>Inscrição de administrador de dispositivos Android

O administrador do dispositivo Android (às vezes chamado de gerenciamento do Android "herdado" e lançado com o Android 2,2) é uma maneira de gerenciar dispositivos Android. No entanto, a funcionalidade de gerenciamento aprimorada agora está disponível com o [Android Enterprise](https://www.android.com/enterprise/management/) (lançado com Android 5,0). Em um esforço para migrar para o gerenciamento de dispositivos moderno, mais avançado e seguro, o Google está diminuindo o suporte ao administrador de dispositivos em novas versões do Android.

Portanto, para evitar essa funcionalidade reduzida, aconselhamos o registro de novos dispositivos usando o processo de administrador do dispositivo descrito abaixo.

Pelos mesmos motivos, também recomendamos que você migre dispositivos fora do gerenciamento de administradores de dispositivos se os dispositivos forem atualizados para Android 10. 

Para obter mais informações sobre o suporte do Intune para o suporte do administrador de dispositivo Android, consulte a [seção avisos](../fundamentals/whats-new.md#decreasing-support-for-android-device-administrator).

Se você ainda decidir fazer com que os usuários registrem seus dispositivos Android com o gerenciamento de administrador do dispositivo, continue na próxima seção.  


> [!Note]  
> Android 10 e superior não terão suporte no gerenciamento de dispositivo móvel híbrido (MDM híbrido; O Intune é gerenciado com o console do System Center Configuration Manager) porque o MDM híbrido está fora de serviço em 1º de setembro de 2019. Se você ainda estiver usando o MDM híbrido, deverá migrar para o Intune autônomo assim que possível. Contate o suporte se precisar de ajuda para a migração. Para obter mais informações, veja [Move from Hybrid Mobile Device Management to Intune on Azure](https://aka.ms/hybrid_notification) (Mover da Gestão de Dispositivos Móveis Híbrida para o Intune no Azure).

Para obter mais informações sobre os recursos do Android Enterprise do Google, consulte estes artigos:
- [Diretrizes do Google para migração do administrador do dispositivo para Android Enterprise](http://static.googleusercontent.com/media/android.com/en/enterprise/static/2016/pdfs/enterprise/Android-Enterprise-Migration-Bluebook_2019.pdf)
- [Documentação do Google no plano para substituir a API de administrador do dispositivo](https://developers.google.com/android/work/device-admin-deprecation)


## <a name="set-up-device-administrator-enrollment"></a>Configurar o registro de administrador do dispositivo

1. Para se preparar para gerir dispositivos móveis, tem de definir a autoridade de gestão de dispositivos móveis (MDM) para o **Microsoft Intune**. Veja [Set the MDM authority (Definir a autoridade de MDM)](../fundamentals/mdm-authority-set.md) para obter instruções. Este item só é definido uma vez, quando está a configurar pela primeira vez o Intune para a gestão de dispositivos móveis.
2. Entre no centro de [Administração do Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) e escolha > **dispositivos** > **android** > **registro do Android** > **dispositivos pessoais e corporativos com privilégios de administração de dispositivo** > usar o administrador do **dispositivo para gerenciar dispositivos**.
3. [Indique aos seus utilizadores como devem inscrever os dispositivos](/intune-user-help/enroll-your-device-in-intune-android).  

Depois de um utilizador concluir a inscrição, pode começar a gerir os respetivos dispositivos no Intune, incluindo [atribuir políticas de conformidade](../protect/compliance-policy-create-android.md), [gerir aplicações](../apps/app-management.md) e mais.

Para obter informações sobre outras tarefas do utilizador, veja estes artigos:
- [Recursos sobre a experiência do utilizador final com o Microsoft Intune](../fundamentals/end-user-educate.md)
- [Utilizar o dispositivo Android com o Intune](https://docs.microsoft.com/intune-user-help/using-your-android-device-with-intune)


## <a name="block-device-administrator-enrollment"></a>Bloquear o registro de administrador do dispositivo
Para bloquear dispositivos Android de administrador de dispositivo ou bloquear somente dispositivos de administrador de dispositivo Android pessoais do registro, consulte [definir restrições de tipo de dispositivo](enrollment-restrictions-set.md).



## <a name="next-steps"></a>Próximos passos
- [Atribuir políticas de conformidade](../protect/compliance-policy-create-android.md)
- [Gerenciando aplicativos](../apps/app-management.md)

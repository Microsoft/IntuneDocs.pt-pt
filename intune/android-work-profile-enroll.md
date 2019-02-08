---
title: Inscrever dispositivos com perfil de trabalho do Android no Intune
titlesuffix: Microsoft Intune
description: Saiba como inscrever dispositivos com perfil de trabalho do Android no Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 6/21/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: f39e9b5f8ecd49ba84f4e9614e2a63a6cfbfef7a
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/07/2019
ms.locfileid: "55837941"
---
# <a name="set-up-enrollment-of-android-work-profile-devices"></a>Configurar a inscrição de dispositivos com perfil de trabalho do Android

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

O Intune ajuda-o a implementar aplicações e definições em dispositivos com perfil de trabalho do Android, de modo a garantir a separação de informações pessoais e profissionais. Para obter detalhes específicos sobre o Android Enterprise, veja [Android enterprise requirements (Requisitos empresariais do Android)](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012).

Para configurar a gestão de perfis de trabalho do Android, siga estes passos:

1. [Ligue a sua conta do inquilino do Intune à sua conta do Android Enterprise](connect-intune-android-enterprise.md).
2. Especificar as definições de inscrição de perfis de trabalho do Android. Os perfis de trabalho do Android [só são suportados em determinados dispositivos Android](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012%20style=%22target=new_window%22). Qualquer dispositivo que suporte os perfis de trabalho do Android também suporta a gestão Android convencional. O Intune permite-lhe especificar a forma como os dispositivos que suportam os perfis de trabalho do Android devem ser geridos a partir das [Restrições de Inscrição](enrollment-restrictions-set.md).
    - **Bloquear (especificado por predefinição)**:  Todos os dispositivos Android, incluindo os dispositivos que suportem perfis de trabalho Android, serão inscritos como dispositivos Android convencionais.
    - **Permitir**: Todos os dispositivos que suportem perfis de trabalho Android são inscritos como dispositivos de perfil de trabalho Android. Qualquer dispositivo Android que não suporte os perfis de trabalho do Android é inscrito como um dispositivo Android convencional.
3. [Indique aos seus utilizadores como devem inscrever os dispositivos](/intune-user-help/enroll-your-device-in-intune-android).


Se quiser inscrever dispositivos nos perfis de trabalho do Android, mas os mesmos já tiverem sido inscritos como dispositivos Android normais, terá de anular a inscrição dos mesmos e voltar a inscrevê-los.

Se estiver a inscrever dispositivos com perfil de trabalho do Android através de uma conta de [Gestor de Inscrições de Dispositivos](device-enrollment-manager-enroll.md), existe um limite de 10 dispositivos que pode inscrever por conta.

Para obter mais informações, veja [Dados que o Intune envia para a Google](data-intune-sends-to-google.md).

## <a name="approve-the-company-portal-app-in-the-managed-google-play-store"></a>Aprovar a aplicação Portal da Empresa na Google Play Store gerida

Para garantir que os utilizadores têm sempre acesso à versão mais recente da aplicação Portal da Empresa, terá de aprovar a aplicação Portal da Empresa para Android na Google Play Store Gerida. Ao aprová-la, garante que todos os utilizadores recebem atualizações automáticas. Se não a aprovar, a aplicação Portal da Empresa irá eventualmente ficar desatualizada e poderá não receber correções importantes ou novas funcionalidades quando forem lançadas pela Microsoft.

Siga estes passos para aprovar o Portal da Empresa do Intune:

1.  Navegue até à aplicação Portal da Empresa na [Google Play Store gerida](https://play.google.com/work/apps/details?id=com.microsoft.windowsintune.companyportal).
2.  Inicie sessão na Google Play Store Gerida com a mesma conta Google que utilizou para configurar o enlace do Android Enterprise.
3.  Clique em **Aprovar** e será aberta uma nova caixa de diálogo.
4.  Reveja as permissões nesta caixa de diálogo e, em seguida, clique em **Aprovar**. Terá de dar estas permissões para permitir que a aplicação Portal da Empresa faça a gestão do perfil de trabalho no dispositivo.
5.  Selecione **Manter aprovado quando as aplicações pedirem novas permissões** e, em seguida, clique em **Guardar**.

## <a name="next-steps-for-android-work-profiles"></a>Passos seguintes para os perfis de trabalho do Android
- [Implementar aplicações do perfil de trabalho do Android](apps-add-android-for-work.md)
- [Adicionar políticas de configuração de perfis de trabalho do Android](device-profiles.md)

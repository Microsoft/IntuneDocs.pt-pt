---
title: Inscrever dispositivos com perfil de trabalho do Android Enterprise no Intune
titleSuffix: Microsoft Intune
description: Saiba como inscrever dispositivos com perfil de trabalho do Android Enterprise no Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 6/21/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1a86eaece208d1c8ea1737acde74c74ef633eea0
ms.sourcegitcommit: 1cae690ca2ac6cc97bbcdf656f54b31878297ae8
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/22/2019
ms.locfileid: "59901136"
---
# <a name="set-up-enrollment-of-android-enterprise-work-profile-devices"></a>Configurar a inscrição de dispositivos com perfil de trabalho do Android Enterprise

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

O Intune ajuda-o a implementar aplicações e definições em dispositivos com perfil de trabalho do Android Enterprise, de modo a garantir a separação das informações pessoais das profissionais. Para obter detalhes específicos sobre o Android Enterprise, veja [Android Enterprise requirements](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012) (Requisitos empresariais do Android).

Para configurar a gestão de perfis de trabalho do Android Enterprise, siga estes passos:

1. [Ligue a sua conta do inquilino do Intune à sua conta do Android Enterprise](connect-intune-android-enterprise.md).
2. Especifique as definições de inscrição dos perfis de trabalho do Android Enterprise. Os perfis de trabalho do Android Enterprise [só são suportados em determinados dispositivos Android](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012%20style=%22target=new_window%22). Qualquer dispositivo que suporte os perfis de trabalho do Android Enterprise também suporta a gestão convencional do Android. O Intune permite-lhe especificar a forma como os dispositivos que suportam os perfis de trabalho do Android Enterprise devem ser geridos a partir das [Restrições de Inscrição](enrollment-restrictions-set.md).
    - **Bloquear (definido por predefinição)**:  todos os dispositivos Android, incluindo os dispositivos que suportem os perfis de trabalho do Android Enterprise, serão inscritos como dispositivos Android convencionais.
    - **Permitir**: todos os dispositivos que suportem os perfis de trabalho do Android Enterprise são inscritos como dispositivos com perfil de trabalho do Android. Qualquer dispositivo Android que não suporte os perfis de trabalho do Android Enterprise é inscrito como um dispositivo Android convencional.
3. [Indique aos seus utilizadores como devem inscrever os dispositivos](/intune-user-help/create-a-work-profile-and-enroll-your-device-in-intune-android).  


Se quiser inscrever dispositivos com perfis de trabalho do Android Enterprise, mas os mesmos já tiverem sido inscritos como dispositivos Android normais, terá de anular a inscrição e voltar a inscrevê-los.

Se estiver a inscrever dispositivos com perfil de trabalho do Android Enterprise com uma conta de [Gestor de Inscrições de Dispositivos](device-enrollment-manager-enroll.md), existirá um limite de 10 dispositivos para inscrição por conta.

Para obter mais informações, veja [Dados que o Intune envia para a Google](data-intune-sends-to-google.md).

## <a name="approve-the-company-portal-app-in-the-managed-google-play-store"></a>Aprovar a aplicação do Portal da Empresa na loja do Managed Google Play

Para garantir que os utilizadores têm sempre acesso à versão mais recente da aplicação do Portal da Empresa, terá de aprovar a aplicação do Portal da Empresa para Android na loja do Managed Google Play. Ao aprová-la, garante que todos os utilizadores recebem atualizações automáticas. Se não a aprovar, a aplicação Portal da Empresa irá eventualmente ficar desatualizada e poderá não receber correções importantes ou novas funcionalidades quando forem lançadas pela Microsoft.

Siga estes passos para aprovar o Portal da Empresa do Intune:

1.  Navegue até à aplicação do Portal da Empresa na [loja do Managed Google Play](https://play.google.com/work/apps/details?id=com.microsoft.windowsintune.companyportal).
2.  Inicie sessão na loja do Managed Google Play com a mesma conta Google que utilizou para configurar o enlace do Android Enterprise.
3.  Clique em **Aprovar** e será aberta uma nova caixa de diálogo.
4.  Reveja as permissões nesta caixa de diálogo e, em seguida, clique em **Aprovar**. Terá de dar estas permissões para permitir que a aplicação Portal da Empresa faça a gestão do perfil de trabalho no dispositivo.
5.  Selecione **Manter aprovado quando as aplicações pedirem novas permissões** e, em seguida, clique em **Guardar**.

## <a name="next-steps-for-android-enterprise-work-profiles"></a>Passos seguintes para os perfis de trabalho do Android Enterprise
- [Implementar aplicações do perfil de trabalho do Android Enterprise](apps-add-android-for-work.md)
- [Adicionar políticas de configuração de perfis de trabalho do Android Enterprise](device-profiles.md)

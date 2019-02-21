---
title: Inscrever dispositivos de perfil de trabalho empresariais Android no Intune
titlesuffix: Microsoft Intune
description: Saiba como inscrever dispositivos de perfil de trabalho empresariais Android no Intune.
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
ms.openlocfilehash: 6522c3572db715e21b85050cd0c82b4cfb9b9deb
ms.sourcegitcommit: f1681554ad842c22ad3f82f0e6d44d5966e4aa3d
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/21/2019
ms.locfileid: "56458778"
---
# <a name="set-up-enrollment-of-android-enterprise-work-profile-devices"></a>Configurar a inscrição de dispositivos de perfil de trabalho do Android Enterprise

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

O Intune ajuda-o a implementar aplicações e definições para dispositivos de perfil de trabalho do Android Enterprise para garantir que informações pessoais e de trabalho são separadas. Para obter detalhes específicos sobre o Android Enterprise, consulte [requisitos do Android Enterprise](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012).

Para configurar a gestão de perfis de trabalho do Android Enterprise, siga estes passos:

1. [Ligue a sua conta de inquilino do Intune à sua conta do Android Enterprise](connect-intune-android-enterprise.md).
2. Especifica definições de inscrição do perfil de trabalho do Android Enterprise. Os perfis de trabalho do Android Enterprise são [suportado em apenas determinados dispositivos Android](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012%20style=%22target=new_window%22). Qualquer dispositivo que suporte perfis de trabalho do Android Enterprise também suporta a gestão Android convencional. O Intune permite-lhe especificar como os dispositivos que suportam perfis de trabalho do Android Enterprise devem ser geridos de dentro [restrições de inscrição](enrollment-restrictions-set.md).
    - **Bloquear (especificado por predefinição)**:  Todos os dispositivos Android, incluindo os dispositivos que suportem perfis de trabalho do Android Enterprise, serão inscritos como dispositivos Android convencionais.
    - **Permitir**: Dispositivos de perfil de trabalho de todos os dispositivos que suportam o Android Enterprise perfis de trabalho são inscritos como Android Enterprise. Todos os dispositivos Android que não suporta perfis de trabalho do Android Enterprise é inscrito como um dispositivo Android convencional.
3. [Indique aos seus utilizadores como devem inscrever os dispositivos](/intune-user-help/enroll-your-device-in-intune-android).


Se quiser inscrever dispositivos com perfis de trabalho do Android Enterprise, mas esses dispositivos já foram inscritos como dispositivos Android normais, esses dispositivos devem primeiro anular a inscrição e, em seguida, voltar a inscrever.

Se estiver a inscrever dispositivos de perfil de trabalho do Android Enterprise utilizando um [Gestor de inscrição de dispositivos](device-enrollment-manager-enroll.md) de contas, existe um limite de 10 dispositivos que podem ser inscritos por conta.

Para obter mais informações, veja [Dados que o Intune envia para a Google](data-intune-sends-to-google.md).

## <a name="approve-the-company-portal-app-in-the-managed-google-play-store"></a>Aprovar a aplicação Portal da empresa na loja Google Play gerido

Para garantir que os utilizadores tenham sempre acesso para a versão mais recente da aplicação portal da empresa, terá de aprovar a aplicação Portal da empresa para Android na loja Google Play gerido. Ao aprová-la, garante que todos os utilizadores recebem atualizações automáticas. Se não a aprovar, a aplicação Portal da Empresa irá eventualmente ficar desatualizada e poderá não receber correções importantes ou novas funcionalidades quando forem lançadas pela Microsoft.

Siga estes passos para aprovar o Portal da Empresa do Intune:

1.  Navegue para a aplicação Portal da empresa no [loja Google Play gerido](https://play.google.com/work/apps/details?id=com.microsoft.windowsintune.companyportal).
2.  Inicie sessão na loja Google Play gerido com a mesma conta Google que utilizou para configurar o enlace do Android Enterprise.
3.  Clique em **Aprovar** e será aberta uma nova caixa de diálogo.
4.  Reveja as permissões nesta caixa de diálogo e, em seguida, clique em **Aprovar**. Terá de dar estas permissões para permitir que a aplicação Portal da Empresa faça a gestão do perfil de trabalho no dispositivo.
5.  Selecione **Manter aprovado quando as aplicações pedirem novas permissões** e, em seguida, clique em **Guardar**.

## <a name="next-steps-for-android-enterprise-work-profiles"></a>Próximas etapas com o Android Enterprise perfis de trabalho
- [Implementar aplicações de perfil de trabalho do Android Enterprise](apps-add-android-for-work.md)
- [Adicionar políticas de configuração de perfil de trabalho Android Enterprise](device-profiles.md)

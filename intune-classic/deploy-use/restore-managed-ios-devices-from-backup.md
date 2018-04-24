---
title: Restaurar dispositivos iOS geridos pelo Intune a partir da cópia de segurança
description: Forneça orientações aos utilizadores finais acerca de como voltarem a inscrever os respetivos dispositivos depois de os restaurarem a partir da cópia de segurança.
keywords: restaurar, geridos, iOS
author: lenewsad
ms.author: lanewsad
manager: angrobe
ms.date: 10/18/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: a19e5612-8805-4bd7-a86a-b734bde293ae
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: esmich
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 2c2a35a7faa022ab2b9b095d4a08075e1c338c70
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/16/2018
---
# <a name="restore-intune-managed-ios-devices-from-backup"></a>Restaurar dispositivos iOS geridos pelo Intune a partir da cópia de segurança

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Existirão casos em que você ou os seus utilizadores irão precisar de restaurar um dispositivo iOS a partir de uma cópia de segurança, como quando um utilizador tem um dispositivo novo. Este tópico explica-lhe os passos adicionais que pode ter de efetuar para configurar a gestão do Intune após restaurar o dispositivo.

## <a name="restoring-backups-onto-the-same-device"></a>Restaurar cópias de segurança no mesmo dispositivo

Caso a cópia de segurança esteja a ser restaurada para o mesmo dispositivo, o estado de inscrição desse dispositivo também será restaurado. Não é necessária qualquer ação adicional.

## <a name="restoring-backups-onto-different-devices"></a>Restaurar cópias de segurança em dispositivos diferentes

Caso a cópia de segurança esteja a ser restaurada num dispositivo diferente, o estado da inscrição não é automaticamente restaurado no novo dispositivo. Os utilizadores têm de seguir os passos de inscrição padrão na versão 2.1.22 ou posterior da aplicação Portal da Empresa para [inscreverem o respetivo dispositivo iOS no Intune](/intune-user-help/enroll-your-device-in-intune-ios).

> [!NOTE]
> Caso esteja a aplicar políticas de acesso condicional aos seus utilizadores finais, estes não conseguirão aceder ao e-mail empresarial até se voltarem a inscrever.

> [!TIP]
> Um exemplo de comunicação dos seus utilizadores pode ser o seguinte: para inscrever o seu novo dispositivo, certifique-se de que a versão da aplicação Portal da Empresa é a 2.1.22 ou posterior. Para verificar a versão, abra a aplicação Portal da Empresa, toque no botão Menu no canto superior direito e, em seguida, toque em Sobre. Se estiver a utilizar uma versão anterior, saia da aplicação Portal da Empresa e abra a App Store. Toque no botão Atualizações no canto inferior direito e, em seguida, toque no botão Atualizar junto ao item Portal da Empresa na lista. Quando a atualização for concluída, inicie a aplicação Portal da Empresa e [inscreva o seu dispositivo iOS no Intune](/intune-user-help/enroll-your-device-in-intune-ios).

## <a name="resolving-known-issues-with-restores"></a>Resolver problemas de restauro conhecidos

Os utilizadores poderão deparar-se com algumas dificuldades se tiverem restaurado o respetivo dispositivo e iniciado a aplicação Portal da Empresa com a versão 2.1.21 ou posterior da mesma. É possível resolver estas dificuldades ao seguir os passos adequados à situação concreta do utilizador.

### <a name="for-users-who-will-only-use-their-new-device"></a>Para os utilizadores que apenas utilizam o seu novo dispositivo
Inicie a aplicação Portal da Empresa e anule a sua inscrição ao selecionar o mosaico do dispositivo atual e ao tocar no botão __Remover__. Após a remoção, siga os passos de inscrição padrão para [inscrever um dispositivo iOS no Intune](/intune-user-help/enroll-your-device-in-intune-ios).

### <a name="for-users-who-will-use-both-their-old-and-new-devices"></a>Para os utilizadores que vão utilizar dispositivos novos e antigos
Limpe os cookies do Safari ao tocar em __Definições__ > __Safari__ > __Limpar Dados do Histórico e de Sites__. Ao concluir a limpeza, desinstale e volte a instalar a aplicação Portal da Empresa e, em seguida, siga os passos de inscrição padrão para [inscrever um dispositivo iOS no Intune](/intune-user-help/enroll-your-device-in-intune-ios).

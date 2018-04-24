---
title: Impedir fugas de dados da empresa a partir das aplicações móveis do Office 365
description: Utilize o Intune para proteger os dados da organização com políticas de gestão de aplicações móveis (MAM) que ajudam a evitar fugas de dados da empresa, a partir de aplicações móveis do Office 365 ou de outras aplicações de linha de negócio (LOB).
keywords: ''
author: jeffgilb
ms.author: jeffgilb
manager: dougeby
ms.date: 11/22/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 19be3de7-539c-49f5-8c46-5363b987fef9
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: pchacon
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 85233c06d9cbbc697aecabc75ba538612c0fa5fa
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/16/2018
---
# <a name="quick-start-guide-prevent-company-data-leaks-from-office-365-mobile-apps"></a>Guia de Iniciação Rápido: impedir fugas de dados da empresa a partir das aplicações móveis do Office 365

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

O Microsoft Intune pode ajudá-lo a proteger os dados da organização utilizando políticas de gestão (MAM) de aplicações móveis que ajudam a evitar fugas de dados da empresa, a partir de aplicações móveis do Office 365 ou outras aplicações de linha de negócio (LOB). As políticas MAM do Intune podem ser utilizadas sem que os utilizadores finais tenham necessidade de inscrever os respetivos dispositivos na gestão de dispositivos móveis (MDM) do Intune. Portanto, se tiver utilizadores que não pretenda inscrever os respetivos dispositivos móveis BYOD iOS ou Android para uma solução Microsoft MDM (do Intune, do Configuration Manager ou do EAS), pretende proteger dados empresariais sem gestão de dispositivos de utilizadores finais ou já estiver a utilizar uma solução de MDM que não seja da Microsoft, o Intune pode ajudar a aumentar a segurança dos dados da empresa.   

## <a name="is-this-quick-start-guide-right-for-me"></a>Este guia de introdução é indicado para mim?
Gostaria de permitir que os utilizadores finais acedem ao Office 365 e aos dados de aplicação LOB nos respetivos dispositivos iOS e Android, sem necessidade de inscrição de dispositivos numa solução de gestão de dispositivos móveis (MDM), mas ainda assim controlar o que é possível ou o não fazer com os dados, como copiá-los e colá-los em aplicações pessoais?

Se sim, o Microsoft Intune permite-lhe definir políticas MAM para as aplicações móveis do Office 365 no iOS e no Android, incluindo restrições de cortar/copiar/colar, impedir "Guardar como", definição de requisição de PIN e a capacidade de apagar remotamente dados protegidos MAM.  Esta ação protege os dados da empresa sem necessidade de que utilizadores inscrevam os respetivos dispositivos numa solução MDM, mantendo, ao mesmo tempo, uma excelente experiência de utilizador final com aplicações do Office mobile.

## <a name="how-do-i-do-it"></a>Como fazê-lo?
1.  Obter uma compreensão básica sobre [como funciona a gestão de aplicações móveis do Intune (MAM)](/intune-classic/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune).
2.  Descura [o que tem de fazer antes de poder criar políticas MAM](/intune-classic/deploy-use/get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune) no portal do Azure.
3.  [Criar e implementar políticas de MAM](/intune-classic/deploy-use/get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune) com o Intune.

### <a name="additional-information"></a>Informações adicionais:
- [Experiência de utilizador final](/intune-classic/deploy-use/end-user-experience-for-mam-enabled-apps-with-microsoft-intune) utilizando aplicações com MAM ativada.
- [Preparar aplicações LOB para MAM com o Intune](/intune/apps-prepare-mobile-application-management)
- <a href="https://www.microsoft.com/cloud-platform/microsoft-intune-partners" target="_blank"> Lista de parceiros de aplicações do Microsoft Intune &rarr;</a> que proporcionam aplicações com MAM ativada.

## <a name="what-should-i-do-next"></a>O que devo fazer em seguida?
[Migrar de uma solução de MDM não Microsoft para o Microsoft Intune](/intune-classic/deploy-use/migrate-to-intune)

[Inscrever dispositivos no MDM do Intune](/intune-classic/deploy-use/enroll-devices-in-microsoft-intune)

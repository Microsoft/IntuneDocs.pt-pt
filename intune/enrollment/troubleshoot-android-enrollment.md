---
title: Problemas de resolução de dispositivos empresariais Android em Microsoft Intune
description: Sugestões para resolver problemas quando se matriculam dispositivos Android em Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/25/2020
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.reviewer: mghadial
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 04c726c1dc6af7e92b75335d105de605ef00e712
ms.sourcegitcommit: 8b716db3c0fdbb7dff62497ec283902a5069a343
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/27/2020
ms.locfileid: "77652373"
---
# <a name="troubleshoot-android-enterprise-device-problems-in-microsoft-intune"></a>Problemas problemas com dispositivos Android Enterprise na Microsoft Intune

Este artigo ajuda os administradores intune a compreender e a resolver problemas quando os dispositivos Android Enterprise em Intune.

## <a name="apps-on-android-enterprise-devices"></a>Aplicativos em dispositivos Android Enterprise

### <a name="managed-google-play-apps-that-arent-deployed-through-intune-are-displayed-in-the-work-profile"></a>As aplicações geridas do Google Play que não são implementadas através do Intune são exibidas no perfil de trabalho
As aplicações do sistema podem ser ativadas no perfil de trabalho pelo dispositivo OEM no momento em que o perfil de trabalho é criado. Isto não é controlado pelo fornecedor de MDM.

Para resolver problemas, siga estes passos:

  1. Colete registos do Portal da Empresa.
  2. Note as aplicações que aparecem inesperadamente no perfil de trabalho.
  3. Desinscreva o dispositivo a partir de Intune e desinstale o Portal da Empresa.
  4. Instale a aplicação [Test DPC,](https://play.google.com/store/apps/details?id=com.afwsamples.testdpc) que permite a criação de um perfil de trabalho sem um EMM para testes.
  5. Siga as instruções no [Teste DPC](https://play.google.com/store/apps/details?id=com.afwsamples.testdpc) para criar um perfil de trabalho no dispositivo.
  6. Reveja as aplicações que aparecem no perfil de trabalho. 
  7. Se as mesmas aplicações aparecerem na aplicação Test DPC, as aplicações são esperadas pelo OEM para esse dispositivo.

### <a name="unapproved-managed-google-play-for-work-store-apps-arent-being-removed-from-the-client-apps-page-in-intune"></a>Aplicações não aprovadas geridas do Google Play for Work store não estão a ser removidas da página de Aplicações de Clientes em Intune
Este comportamento está previsto.

### <a name="managed-google-play-apps-arent-being-reported-under-the-discovered-apps-blade-in-the-intune-portal"></a>As aplicações geridas do Google Play não estão a ser reportadas sob a lâmina das Aplicações Descobertas no portal Intune
Este comportamento está previsto. Apenas as aplicações do sistema instaladas no Perfil de Trabalho são inventariadas na lâmina das Aplicações Descobertas. Para ver as aplicações instaladas geridas do Google Play, utilize a lâmina **de Aplicações Geridas.**

### <a name="are-web-applications-supported-for-work-profile-enrolled-devices"></a>As Aplicações Web são suportadas para dispositivos matriculados no perfil de trabalho?
Sim. Para mais informações, consulte [Links web geridos do Google Play](../apps/apps-add-android-for-work.md#managed-google-play-web-links)

## <a name="device-management"></a>Gestão de dispositivos

### <a name="file-path-internal-storageandroiddatacommicrosoftwindowsintunecompanyportalfiles-missing-on-work-profile-enrolled-devices"></a>Caminho de arquivoArmazenamento interno/Android/Data.com.microsoft.windowsintune.companyportal/ficheiros em falta em dispositivos matriculados no perfil de trabalho

  **Resposta**: Este comportamento é esperado. Este caminho só é criado para o cenário de Administrador de Dispositivos (Legacy Android Registration).

  Para recolher registos do Portal da Empresa, siga estes passos:

  1. Na aplicação Portal da Empresa com o crachá, toque no **Menu** > **Ajude** > Suporte de **E-mail,** e depois toque em enviar registos de **e-mail e upload**. 
  2. Quando for solicitado **Envie um pedido**de ajuda com , selecione uma das aplicações de e-mail.
  3. Um e-mail é gerado para o seu administrador de TI com um ID incidente que pode ser fornecido para o suporte do produto da Microsoft.

### <a name="managed-google-play-last-sync-time--hasnt-been-updated-in-days"></a>O tempo gerido do Google Play Last Sync não é atualizado há dias
Este comportamento está previsto. A sincronização só é acionada quando o faz manualmente.

### <a name="encryption-is-required-when-a-device-is-enrolled-can-it-be-turned-off"></a>A encriptação é necessária quando um dispositivo está matriculado. Pode ser desligado?
Não, a Google exige que o dispositivo seja encriptado para criar um perfil de trabalho. 

### <a name="samsung-devices-are-blocking-the-use-of-third-party-keyboards-like-swiftkey"></a>Dispositivos da Samsung estão a bloquear o uso de teclados de terceiros como o SwiftKey
A Samsung começou a impor esta restrição aos dispositivos Android 8.0+. A Microsoft está neste momento a trabalhar com a Samsung neste problema e publicará novas informações quando estiver disponível.

## <a name="remote-actions"></a>Ações remotas

### <a name="wipe-factory-reset-option-isnt-available-for-work-profile-enrolled-device"></a>A opção Wipe (Reset de Fábrica) não está disponível para dispositivo matriculado no perfil de trabalho
Este comportamento está previsto. No cenário de perfil de trabalho, o fornecedor de MDM não tem controlo total sobre o dispositivo. A única opção disponível é a Retire (Remover dados da empresa) que remove todo o perfil de trabalho e todo o seu conteúdo.

### <a name="is-device-passcode-reset-supported"></a>A redefinição da código de acesso do dispositivo é suportada?
Para dispositivos matriculados no perfil de trabalho, só é possível redefinir a senha de perfil de trabalho no Android 8.0 ou dispositivos posteriores quando:
- a senha de perfil de trabalho é gerida
- o utilizador final permitiu-lhe redefini-lo.

Para dispositivos dedicados (COSU) e Totalmente Geridos, é suportado o reset da código de acesso do dispositivo.


## <a name="next-steps"></a>Próximos passos

- [Resolução de problemas de inscrição de dispositivos no Intune](../troubleshoot-device-enrollment-in-intune.md)
- [Faça uma pergunta sobre o fórum Intune](https://social.technet.microsoft.com/Forums/%7Blang-locale%7D/home?category=microsoftintune&filter=alltypes&sort=lastpostdesc)
- [Consulte o Blog da Equipa de Suporte Intune da Microsoft](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/bg-p/IntuneCustomerSuccess)
- [Consulte o Microsoft Enterprise Mobility and Security Blog](https://techcommunity.microsoft.com/t5/Azure-Active-Directory-Identity/Announcing-the-public-preview-of-Azure-AD-group-based-license/ba-p/245210)
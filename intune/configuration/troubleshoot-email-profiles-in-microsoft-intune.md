---
title: Troubleshoot perfis de e-mail no Microsoft Intune - Azure Microsoft Docs
description: Consulte questões e soluções comuns com perfis de e-mail no Microsoft Intune, incluindo perfis de email duplicados e erros em dispositivos Android Padrão Samsung KNOX.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/18/2020
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: f5c944ea-32a6-48af-bb57-16d5f1f3c588
ROBOTS: ''
ms.reviewer: tscott
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: a19830130f992a002b73402f5e13a8f062539917
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/20/2020
ms.locfileid: "77512675"
---
# <a name="common-issues-and-resolutions-with-email-profiles-in-microsoft-intune"></a>Questões e resoluções comuns com perfis de e-mail no Microsoft Intune

Reveja alguns problemas comuns de perfil de e-mail e como resolvê-los e resolvê-los.

## <a name="what-you-need-to-know"></a>O que tem de saber

- Os perfis de e-mail são implementados para o utilizador que inscreveu o dispositivo. Para configurar o perfil de e-mail, intune utiliza as propriedades do Azure Ative Directory (AD) no perfil de e-mail do utilizador durante a inscrição. [Adicionar definições de e-mail aos dispositivos](email-settings-configure.md) pode ser um bom recurso.
- Para android enterprise, implemente o Gmail ou O No no trabalho utilizando a gerida Google Play Store. [Adicionar aplicações geridas do Google Play](../apps/apps-add-android-for-work.md) lista os passos.
- O Microsoft Outlook para iOS/iPadOS e Android não suporta perfis de email. Em vez disso, implemente uma política de configuração de aplicações. Para mais informações, consulte a definição de [Configuração do Outlook](../apps/app-configuration-policies-outlook.md).
- Os perfis de e-mail direcionados para grupos de dispositivos (não grupos de utilizadores) não podem ser entregues no dispositivo. Quando o dispositivo tem um utilizador primário, então o alvo do dispositivo deve funcionar. Se o perfil de e-mail incluir certificados de utilizador, certifique-se de que tem como alvo grupos de utilizadores.
- Os utilizadores podem ser repetidamente solicitados a introduzir a sua palavra-passe para o perfil de e-mail. Neste cenário, verifique todos os certificados referenciados no perfil de e-mail. Se um dos certificados não for direcionado para um utilizador, então insinte novamente a implementação do perfil de e-mail.

## <a name="device-already-has-an-email-profile-installed"></a>O dispositivo já tem um perfil de email instalado

Se os utilizadores criarem um perfil de e-mail antes de se inscreverem no Intune ou no Office 365 MDM, o perfil de e-mail implementado pela Intune pode não funcionar como esperado:

- **iOS/iPadOS**: Intune deteta um perfil de e-mail duplicado existente com base no nome de anfitrião e endereço de e-mail. O perfil de e-mail criado pelo utilizador bloqueia a implementação do perfil criado pelo Intune. Este é um problema comum, uma vez que os utilizadores de iOS/iPadOS normalmente criam um perfil de e-mail e depois matriculam-se. A aplicação Portal da Empresa afirma que o utilizador não está em conformidade e pode levar o utilizador a remover o perfil de e-mail.

  O utilizador deve remover o seu perfil de e-mail para que o perfil Intune possa ser implementado. Para evitar este problema, instrua os seus utilizadores a inscreverem-se e a permitir que a Intune implemente o perfil de e-mail. Em seguida, os utilizadores podem criar o seu perfil de e-mail.

- **Windows**: o Intune deteta um perfil de e-mail existente, duplicado com base no nome de anfitrião e no endereço de e-mail. O Intune substitui o perfil de e-mail existente criado pelo utilizador.

- **Samsung KNOX Standard**: Intune identifica uma conta de e-mail duplicada com base no endereço de e-mail, e substitui-a com o perfil Intune. Se o utilizador configurar essa conta, é substituído novamente pelo perfil Intune. Isto pode causar alguma confusão ao utilizador cuja configuração da conta é substituída.

A Samsung KNOX não usa o nome de anfitrião para identificar o perfil. Recomendamos que não crie múltiplos perfis de e-mail para implementar para o mesmo endereço de e-mail em diferentes anfitriões, uma vez que eles se sobreescrevem uns aos outros.

## <a name="error-0x87d1fde8-for-knox-standard-device"></a>Erro 0x87D1FDE8 para dispositivo knox Standard

**Problema**: Após a criação e implementação de um perfil de e-mail Exchange Ative Sync para o Samsung KNOX Standard para diferentes dispositivos Android, o erro falhado **0x87D1FDE8** ou **remediação falha** nos erros do dispositivo .

Reveja a configuração do seu perfil EAS para Samsung KNOX e a política de origem. A opção de sincronização de Notas Samsung já não é suportada e essa opção não deve ser selecionada no seu perfil. Certifique-se de que os dispositivos têm tempo suficiente para processar a apólice, até 24 horas.

## <a name="unable-to-send-images-from--email-account"></a>Não é possível enviar imagens a partir da conta de e-mail

Os utilizadores que tenham contas de e-mail configuradas automaticamente não podem enviar imagens ou imagens dos seus dispositivos. Este cenário pode acontecer se permitir que o **e-mail seja enviado a partir de aplicações de terceiros** não está ativado.

1. Inscreva-se no centro de administração do [Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Selecione **Dispositivos** > perfis de **configuração**.
3. Selecione o seu perfil de e-mail > **Propriedades** > **Definições**.
4. Defina o **e-mail permitir que o e-mail seja enviado a partir da** definição de aplicações de terceiros para **ativar**.

## <a name="next-steps"></a>Próximos passos

Obtenha [ajuda de suporte da Microsoft](../fundamentals/get-support.md), ou use os [fóruns comunitários](https://social.technet.microsoft.com/Forums/en-US/home?category=microsoftintune).

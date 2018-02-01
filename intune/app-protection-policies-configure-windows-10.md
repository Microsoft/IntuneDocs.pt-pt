---
title: "Preparar-se para configurar políticas de proteção de aplicações para o Windows 10"
titlesuffix: Azure portal
description: "Configurar o fornecedor de gestão de aplicações móveis (MAM) no Azure AD"
keywords: 
author: erikre
ms.author: erikre
manager: dougeby
ms.date: 10/25/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 949fddec-5318-4c9a-957e-ea260e6e05be
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 3254adc66c5fd5dc991364c3a33aabef8ac2030b
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/25/2018
---
# <a name="get-ready-to-configure-app-protection-policies-for-windows-10"></a>Preparar-se para configurar políticas de proteção de aplicações para o Windows 10

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Ative a gestão de aplicações móveis (MAM) para o Windows 10 ao definir o fornecedor de MAM no Azure AD. Definir um fornecedor de MAM no Azure AD permite-lhe definir o estado de inscrição ao criar uma nova política do Windows Information Protection (WIP) com o Intune. O estado de inscrição pode ser MAM ou gestão de dispositivos móveis (MDM).

> [!NOTE]
> Os dispositivos com um estado de inscrição MAM têm de estar associados ao Azure AD.

## <a name="to-configure-the-mam-provider"></a>Para configurar o fornecedor de MAM

1. Inicie sessão no portal do Azure e selecione **Azure Active Directory.**

2. Selecione **Mobilidade (MDM e MAM)** no grupo **Gerir**.

3. Clique em **Microsoft Intune**.

4. Configure as definições no grupo **Restaurar URLs MAM predefinidos** no painel **Configurar**.

    **Âmbito de utilizador MAM**  
      Utilize a inscrição automática MAM para gerir dados empresariais nos dispositivos Windows dos seus funcionários. A inscrição automática MAM será configurada para cenários de Bring Your Own Device.<ul><li>**Nenhum**<br>Selecione se todos os utilizadores podem ser inscritos na MAM.</li><li>**Alguns**<br>Selecione grupos do Azure AD que contenham utilizadores que serão inscritos na MAM.</li><li>**Todos**<br>Selecione se todos os utilizadores podem ser inscritos na MAM.</li></ul>

    **URL dos termos de utilização da MAM**  
     O URL do ponto final dos termos de utilização da MAM. O ponto final dos termos de utilização é utilizado para apresentar os termos de serviço aos utilizadores finais antes de inscrever os respetivos dispositivos para gestão. O texto dos termos de utilização informa os utilizadores sobre as políticas impostas ao dispositivo móvel.

    **URL de deteção da MAM**  
    O URL do ponto final de inscrição da MAM. O ponto final de inscrição é utilizado para inscrever dispositivos para gestão com a MAM.

    **URL de conformidade da MAM**  
      O URL do ponto final de conformidade da MAM. Se um utilizador de um dispositivo não conforme for impedido de aceder a um recurso, é apresentada uma ligação para o URL de conformidade ao mesmo. Os utilizadores podem aceder a este URL alojado pela MAM para saberem o motivo do dispositivo ser considerado não conforme. Os utilizadores também podem iniciar a remediação de gestão personalizada para tornarem o dispositivo conforme e assim continuarem a aceder a recursos.

5.  Clique em **Guardar**.

## <a name="next-steps"></a>Próximos passos

[Criar uma política de proteção de aplicações WIP](windows-information-protection-policy-create.md)

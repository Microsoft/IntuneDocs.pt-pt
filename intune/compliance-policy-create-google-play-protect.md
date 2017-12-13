---
title: Ativar a conformidade do Google Play Protect com o Intune
titleSuffix: Azure portal
description: "Saiba como criar uma política de conformidade para dispositivos Android para ativar o Google Play Protect."
keywords: 
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 11/20/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: E9810BEB-000A-4DFB-B5C7-A22A92082B22
ms.reviewer: muhosabe
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: d610bc338c1bcf81ed3bc71f1357e001914c5877
ms.sourcegitcommit: 71e6e80b7370024624ce2e5fad1ca5b372975748
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-device-compliance-policy-to-enable-google-play-protect"></a>Como criar uma política de conformidade de dispositivos para ativar o Google Play Protect

Pode criar uma nova política de conformidade para a plataforma Android verificar a conformidade com o Google Play Protect (GPP).

A política de conformidade que exige estas definições pode então ser destinada a um grupo de utilizadores ou de dispositivos Android. Se um dispositivo não tiver estas definições ativadas, deixa de estar em conformidade.

## <a name="create-a-compliance-policy"></a>Criar uma política de conformidade

1. Inicie sessão no portal do Azure. Escolha **Mais Serviços** > **Monitorização + Gestão** + **Intune**.
2. Escolha **Conformidade do dispositivo** no grupo **Gerir**. 
3. Escolha **Políticas** e, em seguida, **Criar Política**.
4. Escreva o **Nome** e a **Descrição** da política.
5. Selecione **Android** para a Plataforma.
6. Escolha **Definições** > **Estado de Funcionamento do Dispositivo**.
7. Configure as definições do **Google Play Protect**.
8. Quando tiver configurado as definições do Google Play Protect, especifique as definições **Segurança** e **Propriedade do dispositivo**. Quando tiver terminado, escolha **OK**.

## <a name="configure-the-google-play-protect-settings"></a>Configurar as definições do Google Play Protect

 - **Os Serviços Google Play estão configurados**  
   Solicite que a aplicação de Serviços do Google Play esteja instalada e ativada. Os Serviços do Google Play permitem efetuar atualizações de segurança, que são uma dependência de nível base de várias funcionalidades de segurança dos dispositivos Google certificados.
 - **Fornecedor de segurança atualizado**  
   Solicite que um fornecedor de segurança atualizado proteja um dispositivo contra vulnerabilidades conhecidas.
 - **Análise de ameaças nas aplicações**  
   Solicite que a funcionalidade do Android **Verificar Aplicações** esteja ativada.
    > [!Note]  
    > Na plataforma Android legada, esta funcionalidade é uma definição de conformidade. O Intune só consegue verificar se esta definição está ativada ao nível do dispositivo. Em dispositivos com perfis de trabalho, anteriormente Android for Work, esta definição pode ser encontrada como uma definição de política de configuração, permitindo que os administradores ativem a definição para um dispositivo.

    Se a sua empresa utilizar perfis de trabalho Android, pode ativar a **Análise de ameaças nas aplicações** para os dispositivos inscritos. Estabeleça um perfil de dispositivo e solicite a definição de segurança do sistema. Para obter mais informações, veja [Definições de restrição de dispositivos Android for Work no Microsoft Intune](device-restrictions-android-for-work.md).

 - **Atestado de dispositivo SafetyNet**  
   Defina o nível de integridade do atestado de dispositivo SafetyNet que tem de ser cumprido. Os níveis incluem **Não configurado**, **Verificação de integridade básica** e **Verificação de integridade básica e de dispositivos certificados**.




## <a name="next-steps"></a>Próximos passos

Para saber mais sobre como trabalhar com as políticas de conformidade de dispositivos do Intune, veja [Introdução às políticas de conformidade de dispositivos do Intune](device-compliance-get-started.md).
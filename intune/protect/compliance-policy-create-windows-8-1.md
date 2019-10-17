---
title: Definições de conformidade do Windows 8.1 no Microsoft Intune – Azure | Microsoft Docs
description: Veja uma lista de todas as definições que pode utilizar quando define a conformidade para os seus dispositivos Windows 8.1 e Windows Phone 8.1 no Microsoft Intune. Verifique a conformidade da versão mínima e máxima do sistema operativo, defina o comprimento e as restrições das palavras-passe, ative a encriptação no armazenamento de dados e muito mais.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/04/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 322d6f1e23464f1f75cc79346d839a9ccdbd7bc7
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/16/2019
ms.locfileid: "72504650"
---
# <a name="windows-81-settings-to-mark-devices-as-compliant-or-not-compliant-using-intune"></a>Definições do Windows 8.1 para marcar dispositivos como conformes ou não conformes com o Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Este artigo apresenta e descreve as definições de conformidade diferentes que pode configurar em dispositivos Windows 8.1 no Intune. Como parte da solução de gestão de dispositivos móveis (MDM), utilize estas definições para bloquear palavras-passe simples, definir uma versão mínima e máxima do SO e muito mais.

Esta funcionalidade aplica-se a:

- Wnodows Phone 8.1
- Windows 8.1 e posterior

Enquanto administrador do Intune, utilize estas definições de conformidade para ajudar a proteger os recursos da sua organização. Para saber mais sobre as políticas de conformidade e para o que servem, veja a [introdução à conformidade de dispositivos](device-compliance-get-started.md).

## <a name="before-you-begin"></a>Antes de começar

[Criar uma política de conformidade](create-compliance-policy.md#create-the-policy). Em **Plataforma**, selecione **Windows Phone 8.1**, **Windows 8.1 e posterior**.

## <a name="device-properties"></a>Propriedades do dispositivo

- **Sistema operacional mínimo necessário**: Insira a versão mínima permitida. quando um dispositivo não cumpre o requisito de versão mínima do SO, será reportado como não conforme. É apresentada uma ligação com informações sobre como atualizar. O utilizador final pode optar por atualizar o dispositivo e, em seguida, obter acesso aos recursos da empresa.
- **Versão máxima do sistema operacional permitida**: Insira a versão máxima permitida. Quando um dispositivo utiliza uma versão do SO posterior à versão introduzida na regra, o acesso aos recursos da empresa é bloqueado. O usuário é solicitado a entrar em contato com o administrador de ti. O dispositivo não pode acessar os recursos organizacionais até que você altere a regra para permitir a versão do sistema operacional.

Os PCs Windows 8.1 devolvem a versão **3**. Se a regra da versão do SO estiver definida como Windows 8.1 para o Windows, o dispositivo será reportado como não conforme, mesmo que tenha o sistema operativo Windows 8.1.

## <a name="system-security"></a>Segurança do sistema

### <a name="password"></a>Palavra-passe

- **Exigir uma palavra-passe para desbloquear os dispositivos móveis**: **exige** que os utilizadores introduzam uma palavra-passe para poderem aceder aos dispositivos.
- **Palavras-passe simples**: defina como **Bloquear** para que os utilizadores não possam criar palavras-passe simples, como **1234** ou **1111**. Defina como **Não configurado** para permitir aos utilizadores criar palavras-passe como **1234** ou **1111**.
- **Comprimento mínimo da palavra-passe**: introduza o número mínimo de dígitos ou carateres que a palavra-passe tem de ter.

  Para dispositivos que executam o Windows e são acedidos com uma conta Microsoft, a política de conformidade não consegue avaliar corretamente:
  - Se o comprimento mínimo da palavra-passe é superior a oito carateres
  - Ou, se o número mínimo de conjuntos de carateres é superior a dois

- **Tipo de palavra-passe**: escolha se uma palavra-passe deve ter apenas carateres **Numéricos** ou se deve existir uma combinação de números e de outros carateres (**Alfanuméricos**).
  
  - **Número de carateres não alfanuméricos na palavra-passe**: se o **Tipo obrigatório de palavra-passe** estiver definido como **Alfanumérico**, esta definição especificará o número mínimo de conjuntos de carateres que a palavra-passe tem de conter. Os quatro conjuntos de carateres são:
    - Letras minúsculas
    - Letras maiúsculas
    - Símbolos
    - Números

    Definir um número mais relevado exige que o utilizador crie uma palavra-passe mais complexa. Para dispositivos que são acedidos com uma conta Microsoft, a política de conformidade não consegue avaliar corretamente:

    - Se o comprimento mínimo da palavra-passe é superior a oito carateres
    - Ou, se o número mínimo de conjuntos de carateres é superior a dois

- **Máximo de minutos de inatividade antes de ser exigida a palavra-passe**: introduza o tempo de inatividade antes de o utilizador ter de reintroduzir a palavra-passe.
- **Expiração da palavra-passe (dias)** : selecione o número de dias antes de a palavra-passe expirar e ser preciso criar uma nova.
- **Número de senhas anteriores para evitar a reutilização**: Insira o número de senhas usadas anteriormente que não podem ser usadas.

### <a name="encryption"></a>Encriptação

- **Encriptação obrigatória no dispositivo móvel**: **exija** que o dispositivo seja encriptado para ligar a recursos de armazenamento de dados.

Selecione **OK** > **Criar** para guardar as alterações.

## <a name="next-steps"></a>Próximos passos

- [Adicionar ações para dispositivos não conformes](actions-for-noncompliance.md) e [utilizar etiquetas de âmbito para filtrar políticas](../fundamentals/scope-tags.md).
- [Monitorizar as políticas de conformidade](compliance-policy-monitor.md).
- Veja as [definições de política de conformidade para dispositivos Windows 10 e mais recentes](compliance-policy-create-windows.md).
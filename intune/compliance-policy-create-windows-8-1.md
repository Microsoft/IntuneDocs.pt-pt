---
title: Definições de compatibilidade do Windows 8.1 no Microsoft Intune – Azure | Documentos da Microsoft
description: Ver uma lista de todas as definições que pode utilizar quando a definição de conformidade para os seus dispositivos Windows 8.1 e Windows Phone 8.1 no Microsoft Intune. Verificar a conformidade, no mínimo e máximo sistema operacional, definir restrições de palavra-passe e de comprimento, ativar a encriptação em armazenamento de dados e muito mais.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/04/2019
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4ed863378616f8001beab89177c642404287e7d3
ms.sourcegitcommit: 02803863eba37ecf3d8823a7f1cd7c4f8e3bb42c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2019
ms.locfileid: "59425331"
---
# <a name="windows-81-settings-to-mark-devices-as-compliant-or-not-compliant-using-intune"></a>Definições do Windows 8.1 para marcar dispositivos como compatíveis ou não compatíveis com o Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Este artigo apresenta e descreve as definições de conformidade diferentes que pode configurar em dispositivos Windows 8.1 no Intune. Como parte da sua solução de gestão (MDM) de dispositivos móveis, utilize estas definições para bloquear palavras-passe simples, defina um mínimo e versão do SO máxima e muito mais.

Esta funcionalidade aplica-se a:

- Windows Phone 8.1
- Windows 8.1 e posterior

Enquanto administrador do Intune, utilize estas definições de conformidade para ajudar a proteger recursos da sua organização. Para saber mais sobre as políticas de conformidade e o que fazer, consulte [introdução à conformidade de dispositivo](device-compliance-get-started.md).

## <a name="before-you-begin"></a>Antes de começar

[Criar uma política de conformidade](create-compliance-policy.md#create-the-policy). Para **plataforma**, selecione **Windows Phone 8.1** ou **Windows 8.1 e posterior**.

## <a name="device-properties"></a>Propriedades do dispositivo

- **SO mínimo obrigatório**: Introduza a versão mínima permitida. Quando um dispositivo não cumpre o requisito de versão mínima do SO, será comunicado como não conforme. É apresentada uma ligação com informações sobre como atualizar. O utilizador final pode optar por atualizar o dispositivo e, em seguida, obter acesso aos recursos da empresa.
- **Versão do SO máxima permitida**: Introduza o máximo permitido de versão. Quando um dispositivo utiliza uma versão do SO posterior à versão introduzida na regra, o acesso aos recursos da empresa é bloqueado. É pedido ao utilizador para contactar o administrador de TI. O dispositivo não é possível aceder a recursos organizacionais até que alterar a regra para permitir que a versão do SO.

Os PCs Windows 8.1 devolvem a versão **3**. Se a regra de versão do SO estiver definida como Windows 8.1 para Windows, o dispositivo é considerado como não conforme mesmo que o dispositivo tiver o Windows 8.1.

## <a name="system-security"></a>Segurança do sistema

### <a name="password"></a>Palavra-passe

- **Exigir uma palavra-passe para desbloquear dispositivos móveis**: **Exigir** que os utilizadores introduzam uma palavra-passe antes de poderem aceder ao respetivo dispositivo.
- **Palavras-passe simples**: Defina como **bloco** para que os utilizadores não é possível criar palavras-passe simples, tal como **1234** ou **1111**. Defina como **Não configurado** para permitir aos utilizadores criar palavras-passe como **1234** ou **1111**.
- **Comprimento mínimo da palavra-passe**: Introduza o número mínimo de dígitos ou carateres que a palavra-passe tem de ter.

  Para dispositivos que executam o Windows e são acedidos com uma conta Microsoft, a política de conformidade não consegue avaliar corretamente:
  - Se o comprimento mínimo da palavra-passe é superior a oito carateres
  - Ou, se o número mínimo de conjuntos de carateres é superior a dois

- **Tipo de palavra-passe**: Escolha se uma palavra-passe deve ter apenas **numérico** carateres, ou se deve existir uma combinação de números e outros carateres (**alfanumérico**).
  
  - **Número de carateres não alfanuméricos na palavra-passe**: Se **Tipo obrigatório de palavra-passe** estiver definido como **Alfanumérico**, esta definição especifica o número mínimo de conjuntos de carateres que a palavra-passe tem de ter. Os quatro conjuntos de carateres são:
    - Letras minúsculas
    - Letras maiúsculas
    - Símbolos
    - Números

    Definir um número mais relevado exige que o utilizador crie uma palavra-passe mais complexa. Para dispositivos que são acedidos com uma conta Microsoft, a política de conformidade não avalia corretamente:

    - Se o comprimento mínimo da palavra-passe é superior a oito carateres
    - Ou, se definir o número mínimo de carateres é superior a dois

- **Máximo de minutos de inatividade antes da palavra-passe é necessária**: Introduza o tempo de inatividade antes do utilizador ter de reintroduzir a palavra-passe.
- **Expiração de palavra-passe (dias)**: Selecione o número de dias antes da palavra-passe expirar e ser necessário criar um novo.
- **Número de palavras-passe anteriores cuja reutilização está**: Introduza o número de palavras-passe utilizadas anteriormente que não pode ser utilizado.

### <a name="encryption"></a>Encriptação

- **Exigir encriptação no dispositivo móvel**: **Exigir** o dispositivo sejam encriptados para ligar a recursos de armazenamento de dados.

Selecione **OK** > **Criar** para guardar as alterações.

## <a name="next-steps"></a>Passos Seguintes

- [Adicionar ações para dispositivos não conformes](actions-for-noncompliance.md) e [utilizar etiquetas de âmbito para políticas de filtro](scope-tags.md).
- [Monitorizar as suas políticas de conformidade](compliance-policy-monitor.md).
- Consulte a [definições de política de conformidade para Windows 10 e posterior](compliance-policy-create-windows.md) dispositivos.
---
title: "Criar uma política de conformidade de dispositivo"
description: "Crie uma política de conformidade para ajudar a proteger dispositivos móveis e PCs utilizados para aceder aos dados da sua empresa."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 10/12/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5336dac0-a2cc-4cd4-8511-67e4f95bd700
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 3dcafbd3cfdbccdfa851e8d21572d834d629564b
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/01/2017
---
# <a name="create-a-device-compliance-policy-in-microsoft-intune"></a>Criar uma política de conformidade de dispositivos no Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Este tópico descreve os passos que pode utilizar para criar uma política de conformidade que um dispositivo tem de seguir para ser considerado conforme.

##  <a name="step-1-add-a-new-policy"></a>Passo 1: Adicionar uma nova política
  Na [consola de administração do Microsoft Intune](https://manage.microsoft.com), selecione **Política** &gt; **Políticas de Conformidade** &gt; **Adicionar**.

  ![Captura de ecrã da página de política de conformidade na consola de administração do Intune, que mostra a opção de adicionar no menu na parte superior da página](./media/intune-sa-3a-add-compliance-policy.png)

##  <a name="step-2--configure-settings"></a>Passo 2: Configurar as definições
Na página **Criar Política**, ative as definições necessárias:
  -   As definições de segurança do sistema, como palavra-passe e encriptação.
  -   As definições de estado de funcionamento do dispositivo, como se o dispositivo tem ou não jailbrake ou se é considerado como estando em bom estado de funcionamento pelo serviço de atestado de estado de funcionamento de dispositivos do Windows.
  -   Definições de propriedades do dispositivo, como a versão mínima do sistema operativo necessária ou a versão máxima do sistema operativo permitida.
![Separador Geral da página Criar Política ](./media/intune-sa-3b-create-policy.png)


##  <a name="step-3-save-the-policy"></a>Passo 3: Guardar a política
Quando terminar, selecione **Guardar Política**.

Tem a opção de implementar a política logo após guardá-la ou pode optar por implementá-la mais tarde. A nova política é apresentada no nó **Políticas de Conformidade** da área de trabalho **Política**.

##  <a name="step-4-set-the-compliance-status-validity-period"></a>Passo 4: Definir o período de validade do Estado de conformidade
Para especificar o tempo que o dispositivo tem para se registar antes de ser considerado como não estando em conformidade, aceda às definições da política de conformidade e atualize esse período. A predefinição são 30 dias.

![Opção de definições da política de conformidade na barra de menus da política](../media/mdm-compliance-policy-settings.png)

![Caixa de diálogo da política de conformidade](../media/mdm-ca-compliance-status-validity-period.png)

## <a name="supported-policy-settings"></a>Definições de política suportadas
A tabela seguinte lista as definições de política de conformidade e as plataformas em que são suportadas.

-------------
|Definição|iOS|Android|Windows|
|-----|----|-----|-----|
|Palavra-passe obrigatória para desbloquear os dispositivos móveis|iOS 6 e posterior|Android 4.0 e posterior <br>Samsung KNOX Standard 4.0 e posterior|Windows Phone 8.1 e posterior|
|Permitir palavras-passe simples|iOS 6 e posterior|Não suportado|Windows Phone 8.1 e posterior|
|Comprimento mínimo da palavra-passe|iOS 6 e posterior| Android 4.0 e posterior<br>Samsung KNOX Standard 4.0 e posterior| Windows Phone 8.1 e posterior<br>Windows 8.1|
|Tipo obrigatório de palavra-passe|iOS 6 e posterior|Não disponível|Windows Phone 8.1 e posterior <br>Windows RT<br> Windows RT 8.1 <br>Windows 8.1|
|Número mínimo de conjuntos de carateres|iOS 6 e posterior|Não disponível|Windows Phone 8.1 e posterior <br>Windows RT<br> Windows RT 8.1 <br>Windows 8.1|
|Qualidade da palavra-passe|Não disponível|Android 4.0 e posterior <br>Samsung KNOX Standard 4.0 e posterior|Não disponível|
|Minutos de inatividade antes da palavra-passe ser exigida|iOS 6 e posterior|Android 4.0 e posterior<br>Samsung KNOX Standard 4.0 e posterior|Windows Phone 8.1 e posterior<br>Windows RT e Windows RT 8.1<br>Windows 8.1|
|Expiração da Palavra-passe (dias)|iOS 6 e posterior|Android 4.0 e posterior<br>Samsung KNOX Standard 4.0 e posterior|Windows Phone 8.1 e posterior<br>Windows RT e Windows RT 8.1<br>Windows 8.1|
|Memorizar histórico de palavras-passe|iOS 6 e posterior|Android 4.0 e posterior<br>Samsung KNOX Standard 4.0 e posterior|Windows Phone 8.1 e posterior<br>Windows RT e Windows RT 8.1<br>Windows 8.1|
|Impedir a reutilização de palavras-passe anteriores|iOS 6 e posterior|Android 4.0 e posterior<br>Samsung KNOX Standard 4.0 e posterior|Windows Phone 8.1 e posterior<br>Windows RT e Windows RT 8.1<br>Windows 8.1|
|Exigir uma palavra-passe quando o dispositivo regressa de um estado inativo| Não disponível| Não disponível|Windows 10 Mobile|
|Encriptação obrigatória no dispositivo móvel|Não aplicável|Android 4.0 e posterior<br>Samsung KNOX Standard 4.0 e posterior|Windows Phone 8.1 e posterior<br> Windows 8.1|
|Exigir que os dispositivos sejam comunicados como estando em bom estado de funcionamento| Não disponível| Não disponível|Windows <br>Windows 10 Mobile|
|O dispositivo não pode ter jailbreak nem root|iOS 6 e posterior|Android 4.0 e posterior<br>Samsung KNOX Standard 4.0 e posterior|Não disponível|
|A conta de e-mail tem de ser gerida pelo Intune|iOS 6 e posterior|Não disponível| Não disponível|
|Selecionar o perfil de e-mail que deve ser gerido pelo Intune|iOS 6 e posterior|Não disponível| Não disponível|
|SO Mínimo obrigatório|iOS 6 e posterior|Android 4.0 e posterior<br>Samsung KNOX Standard 4.0 e posterior| Windows Phone 8.1 e posterior<br>Windows 8.1|
|Versão máxima de SO permitida|iOS 6 e posterior|Android 4.0 e posterior<br>Samsung KNOX Standard 4.0 e posterior|Windows Phone 8.1 e posterior<br>Windows 8.1|

Selecione um dos seguintes passos para obter mais informações sobre as definições de conformidade suportadas em cada plataforma:
> [!div class="op_single_selector"]
- [Definições de política de conformidade para dispositivos iOS](ios-compliance-policy-settings-in-microsoft-intune.md)
- [Definições de política de conformidade para dispositivos Android](android-compliance-policy-settings-in-microsoft-intune.md)
- [Definições de política de conformidade para dispositivos Windows Phone ](windows-compliance-policy-settings-in-microsoft-intune.md)


## <a name="next-steps"></a>Passos seguintes
[Implementar e monitorizar políticas de conformidade](deploy-and-monitor-a-device-compliance-policy-in-microsoft-intune.md)

### <a name="see-also"></a>Consulte também
[Introdução às políticas de conformidade de dispositivos](introduction-to-device-compliance-policies-in-microsoft-intune.md)

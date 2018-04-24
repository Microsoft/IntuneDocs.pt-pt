---
title: Políticas de conformidade de dispositivo
description: Este tópico explica o que são as políticas de conformidade do dispositivo e como funcionam.
keywords: ''
author: andredm7
ms.author: andredm
manager: dougeby
ms.date: 11/14/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 0775107a-6662-41c8-9404-be14bbb599f3
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 4c9c93d29ddee6d01e057c01a44c81950b857213
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/16/2018
---
# <a name="device-compliance-policies-in-microsoft-intune"></a>Políticas de conformidade de dispositivos no Microsoft Intune

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

## <a name="what-is-a-compliance-policy"></a>O que é uma política de conformidade?
Para ajudar a proteger dados da empresa, tem de garantir que os dispositivos utilizados para aceder às aplicações e aos dados da empresa cumprem determinadas regras. As regras incluem a utilização de um PIN para aceder a dispositivos e encriptar dados armazenados em dispositivos. Um conjunto dessas regras denomina-se política de conformidade.

## <a name="how-should-i-use-compliance-policies"></a>Como devo utilizar as políticas de conformidade?
Pode utilizar as políticas de conformidade com políticas de acesso condicional para permitir que apenas os dispositivos que estejam em conformidade com as regras de política de conformidade acedam a e-mail e outros serviços. Para compreender como as duas políticas podem ser utilizadas em conjunto, consulte o artigo [Restringir o acesso ao e-mail e aos serviços do O365](restrict-access-to-email-and-o365-services-with-microsoft-intune.md).

Também pode utilizar as políticas de conformidade independentemente do acesso condicional. Quando utilizar políticas de conformidade de forma independente, os dispositivos visados são avaliados e reportados com o respetivo estado de conformidade. Por exemplo, pode pretender reportar o número de dispositivos que não estão encriptados ou quais os dispositivos que têm jailbreak ou root. No entanto, quando utilizar políticas de conformidade de forma independente, não existem restrições de acesso aos recursos da empresa.

Pode implementar políticas de conformidade em utilizadores. Quando uma política de conformidade é implementada num utilizador, os dispositivos do utilizador são verificados relativamente à conformidade.
Para saber quanto tempo os dispositivos móveis demoram a obter uma política após a mesma ser implementada, consulte [Gerir definições e funcionalidades nos seus dispositivos](/intune-classic/deploy-use/manage-settings-and-features-on-your-devices-with-microsoft-intune-policies#frequently-asked-questions-about-intune-policies).

A seguinte tabela lista os tipos de dispositivo suportados pelas políticas de conformidade. A tabela também descreve como as definições não conformes são geridas quando uma política de conformidade é utilizada com uma política de acesso condicional.

-----------------------------

|Definição de política| Windows 8.1 e posterior| Windows Phone 8.1 e posterior| iOS 8.0 e posterior|Android 4.0 e posterior<br/>Samsung Knox Standard 4.0 e posterior|
|-----|----|----|----|----|
|**Configuração do PIN ou da palavra-passe** |Corrigido|Corrigido|Corrigido|Em quarentena|
|**Encriptação do dispositivo**|Não aplicável|Corrigido|Corrigido (ao definir um PIN)|Em quarentena|
|**Dispositivo desbloqueado por jailbreak ou obtenção de controlo de raiz**|Não aplicável|Não aplicável|Em quarentena (não é uma definição)|Em quarentena (não é uma definição)|
|**Perfil de e-mail**|Não aplicável|Não aplicável|Em quarentena|Não aplicável|
|**Versão mínima do SO**|Em quarentena|Em quarentena|Em quarentena|Em quarentena|
|**Versão máxima do SO**|Em quarentena|Em quarentena|Em quarentena|Em quarentena|
|**Atestado do estado de funcionamento do Windows**|Em Quarentena: Windows 10 e Windows 10 Mobile<br /><br />Não aplicável: Windows 8.1|Não aplicável|Não aplicável|Não aplicável|

------------------------------

**Remediado** = O sistema operativo do dispositivo impõe a conformidade. (Por exemplo, forçar o utilizador a definir um PIN.)

**Em Quarentena** = O sistema operativo do dispositivo não impõe a conformidade. (Por exemplo, os dispositivos Android não forçam o utilizador a encriptar o dispositivo.) Quando os dispositivos não são conformes, são efetuadas as seguintes ações:

-   O dispositivo é bloqueado se uma política de acesso condicional se aplicar ao utilizador.

-   O portal da empresa notifica o utilizador sobre eventuais problemas de conformidade.

## <a name="next-steps"></a>Próximos passos
[Criar uma política de conformidade de dispositivo](create-a-device-compliance-policy-in-microsoft-intune.md)

[Implementar e monitorizar políticas de conformidade de dispositivos](deploy-and-monitor-a-device-compliance-policy-in-microsoft-intune.md)

### <a name="see-also"></a>Consulte também
[Restringir o acesso ao e-mail e aos serviços do O365](restrict-access-to-email-and-o365-services-with-microsoft-intune.md)

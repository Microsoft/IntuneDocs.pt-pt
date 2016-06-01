---
# required metadata

title: Políticas de conformidade de dispositivos | Microsoft Intune
description:
keywords:
author: karthikaraman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 0775107a-6662-41c8-9404-be14bbb599f3

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Políticas de conformidade de dispositivos no Microsoft Intune
## O que é uma política de conformidade?
Para proteger os dados da empresa, tem de assegurar que os dispositivos utilizados para aceder às aplicações e aos dados da empresa estão em conformidade com determinadas regras, como a utilização de um PIN para aceder ao dispositivo e a encriptação dos dados armazenados no dispositivo. Um conjunto dessas regras é referido como política de conformidade.

## Como devo utilizar as políticas de conformidade?
Pode utilizar as políticas de conformidade com políticas de acesso condicional para restringir o acesso aos dispositivos que estejam em conformidade com as regras de política de conformidade. Leia o artigo [Restringir o acesso ao e-mail e aos serviços do O365](restrict-access-to-email-and-o365-services-with-microsoft-intune.md) para compreender como as duas políticas podem ser utilizadas em conjunto.

Também pode utilizar as políticas de conformidade independentemente do acesso condicional. Quando utilizadas independentemente, os dispositivos visados são avaliados e reportados com o respetivo estado de conformidade. Por exemplo, pode pretender reportar o número de dispositivos que não estão encriptados ou quais os dispositivos que têm jailbreak ou root. No entanto, quando utilizadas independentemente, não existem restrições de acesso aos recursos da empresa.

Pode implementar políticas de conformidade em utilizadores. Quando uma política de conformidade é implementada num utilizador, os dispositivos do utilizador são verificados relativamente à conformidade.

A tabela seguinte lista os tipos de dispositivos suportados pelas políticas de conformidade e como são geridas as definições não conformes quando as políticas são utilizadas com uma política de acesso condicional.

--------------

|Definição da Política| Windows 8.1 e posterior| Windows Phone 8.1 e posterior| iOS 6.0 e posterior|Android 4.0 e posterior<br/>Samsung KNOX Standard 4.0 e posterior|
|-----|----|----|----|
|**Configuração do PIN ou da Palavra-passe** |Corrigido|Corrigido|Corrigido|Em quarentena|
|**Encriptação do dispositivo**|N/D|Corrigido|Corrigido (ao definir um PIN)|Em quarentena|
|**Dispositivo desbloqueado por jailbreak ou obtenção de controlo de raiz**|N/D|N/D|Em quarentena (não é uma definição)|Em quarentena (não é uma definição)|
|**Perfil de e-mail**|N/D|N/D|Em quarentena|N/D|
|**Versão mínima do SO**|Em quarentena|Em quarentena|Em quarentena|Em quarentena|
|**Versão máxima do SO**|Em quarentena| Em quarentena| Em quarentena| Em quarentena|
|**Atestado do estado de funcionamento do Windows**|Windows 10 e Windows 10 Mobile são colocados em Quarentena.<br /><br />A definição não é aplicável ao Windows 8.1|N/D|N/D|N/D|
--------------
**Remediado** = a conformidade é imposta pelo sistema operativo do dispositivo (por exemplo, o utilizador é forçado a definir um PIN).  Nunca se dá o caso de a definição não ser conforme.

**Em quarentena** = o sistema operativo do dispositivo não impõe a conformidade (por exemplo, os dispositivos Android não forçam o utilizador a encriptar o dispositivo). Quando os dispositivos não são conformes, são efetuadas as seguintes ações:

-   O dispositivo será bloqueado se for aplicada uma política de acesso condicional ao utilizador.

-   O portal da empresa notificará o utilizador sobre eventuais problemas de conformidade.

## Passos seguintes
[Criar uma política de conformidade de dispositivo](create-a-device-compliance-policy-in-microsoft-intune.md)

[Implementar e monitorizar políticas de conformidade de dispositivos](deploy-and-monitor-a-device-compliance-policy-in-microsoft-intune.md)

### Consulte também
[Restringir o acesso ao e-mail e aos serviços do O365](restrict-access-to-email-and-o365-services-with-microsoft-intune.md)


<!--HONumber=May16_HO2-->



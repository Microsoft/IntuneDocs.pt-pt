---
title: "Definições de política de conformidade para dispositivos iOS | Documentos da Microsoft"
description: "Este tópico descreve as regras e definições que pode configurar numa política de conformidade para dispositivos iOS."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 12/15/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4a59d24f-ed58-49b1-b874-b2d4aea3ec76
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: 9f05e516723976dcf6862475dbb78f9dce2913be
ms.openlocfilehash: f4867d18634add8cb6ffc61a4413618b1bea5a4b


---


# <a name="compliance-policy-settings-for-ios-devices-in-microsoft-intune"></a>Definições de política de conformidade para dispositivos iOS no Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

As definições de política descritas neste tópico aplicam-se a dispositivos com o iOS 8.0 e posterior.

Se estiver à procura de informações sobre outras plataformas, selecione uma das seguintes opções:
> [!div class="op_single_selector"]
- [Definições de política de conformidade para dispositivos Android](android-compliance-policy-settings-in-microsoft-intune.md)
- [Definições de política de conformidade para Android for Work](afw-compliance-policy-settings-in-microsoft-intune.md)
- [Definições de política de conformidade para dispositivos Windows](windows-compliance-policy-settings-in-microsoft-intune.md)

## <a name="system-security-settings"></a>Definições de segurança do sistema
### <a name="password"></a>Palavra-passe
- **Exigir uma palavra-passe para desbloquear dispositivos móveis:** defina esta opção como **Sim** para exigir que o utilizador introduza uma palavra-passe para que possa aceder ao respetivo dispositivo. Os dispositivos iOS que utilizam uma palavra-passe são encriptados.

- **Permitir palavras-passe simples**: defina esta opção para **Sim** para permitir que o utilizador crie uma palavra-passe simples, como **1234** ou **1111**.

-  **Comprimento mínimo da palavra-passe**: especifique o número mínimo de dígitos ou carateres que a palavra-passe do utilizador tem de ter.

- **Solicitar tipo de palavra-passe:** especifique se o utilizador tem de criar uma palavra-passe **Alfanumérica** ou **Numérica**.

- **Número mínimo de conjuntos de carateres:** se definir **Tipo de palavra-passe necessária** como **Alfanumérico**, utilize esta definição para especificar o número mínimo de conjuntos de carateres que a palavra-passe deve ter. Os quatro conjuntos de carateres são:
  -   Letras minúsculas
  -   Letras maiúsculas
  -   Símbolos
  -   Números

  Definir um número mais relevado requer que o utilizador crie uma palavra-passe mais complexa.

  Para dispositivos iOS, esta definição refere-se ao número de carateres especiais (por exemplo, **!**, **#**, **&amp;**) que têm de ser incluídos na palavra-passe.

- **Minutos de inatividade antes de a palavra-passe ser exigida**: especifique o tempo de inatividade antes de o utilizador ter de reintroduzir a palavra-passe.

- **Expiração da Palavra-passe (dias)**: selecione o número de dias antes de a palavra-passe do utilizador expirar e ser necessário criar uma nova.

- **Memorizar histórico de palavras-passe:** utilize esta definição juntamente com **Impedir a reutilização de palavras-passe anteriores** para impedir o utilizador de criar palavras-passe utilizadas anteriormente.

- **Impedir a reutilização de palavras-passe anteriores**: se tiver selecionado **Memorizar histórico de palavras-passe**, especifique o número de palavras-passe utilizadas anteriormente que não podem ser reutilizadas.

- **Exigir uma palavra-passe quando o dispositivo regressa de um estado inativo**: utilize esta definição em conjunto com a definição em **Minutos de inatividade antes de a palavra-passe ser exigida**. Será pedido ao utilizador que introduza uma palavra-passe para aceder a dispositivos que tenham estado inativos durante o período de tempo especificado na definição **Minutos de inatividade antes de a palavra-passe ser exigida**.

### <a name="email-profile"></a>Perfil de e-mail
- **A conta de e-mail tem de ser gerida pelo Intune:** quando esta opção está definida como **Sim**, o dispositivo tem de utilizar o perfil de e-mail implementado no dispositivo. O dispositivo é considerado não conforme nas seguintes situações:
  - O perfil de e-mail é implementado para um grupo de utilizadores que não o grupo de utilizadores visado pela política de conformidade.
  - O utilizador já configurou uma conta de e-mail no dispositivo que corresponde ao perfil de e-mail do Intune implementado no dispositivo. O Intune não pode substituir o perfil aprovisionado pelo utilizador, pelo que não o consegue gerir. Para garantir a conformidade, o utilizador tem de remover as definições de e-mail existentes. Em seguida, o Intune pode instalar o perfil de e-mail gerido.

- **Selecionar o perfil de e-mail que deve ser gerido pelo Intune:** se a definição **A conta de e-mail tem de ser gerida pelo Intune** estiver selecionada, selecione a opção **Selecionar** para especificar o perfil de e-mail do Intune. O perfil de e-mail tem de estar presente no dispositivo.

     Para obter informações sobre os perfis de e-mail, consulte [Configurar o acesso a e-mail empresarial através de perfis de e-mail com o Microsoft Intune](configure-access-to-corporate-email-using-email-profiles-with-microsoft-intune.md).

## <a name="device-health-settings"></a>Definições de estado de funcionamento do dispositivo

- **O dispositivo não pode ter jailbreak ou root:** se ativar esta definição, os dispositivos com jailbreak não serão conformes.

##  <a name="device-properties"></a>Propriedades do dispositivo
- **SO mínimo necessário:** quando um dispositivo não cumpre o requisito de versão mínima do SO, será reportado como não conforme.
É apresentada uma hiperligação com informações sobre como atualizar. O utilizador pode optar por atualizar o dispositivo. Depois, pode aceder aos recursos da empresa.

- **Versão do SO máxima permitida**: quando um dispositivo utiliza uma versão do SO posterior à especificada na regra, o acesso aos recursos da empresa é bloqueado e é pedido ao utilizador que contacte o administrador de TI. Até a regra ser alterada para permitir a versão do SO, este dispositivo não pode ser utilizado no acesso aos recursos da empresa.



<!--HONumber=Jan17_HO4-->



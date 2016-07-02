---
title: "Definições de política de conformidade para dispositivos Android | Microsoft Intune"
description: 
keywords: 
author: karthikaraman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e721c5c7-9678-4f3b-81d4-564da5efd337
ms.reviewer: chrisgre
ms.suite: ems
ms.sourcegitcommit: e736d688032dd2ddee5be9edf2a33d5e7ba5257b
ms.openlocfilehash: dd3369cf59ea972f1ecc4953881ddbbede9a99c8


---


# Definições de política de conformidade para dispositivos Android no Microsoft Intune

As definições de política descritas neste tópico aplicam-se a dispositivos com o Android 4.0 e posterior, ou Samsung KNOX 4.0 e posterior.

Se estiver à procura de informações sobre outras plataformas, selecione uma das seguintes opções:
> [!div class="op_single_selector"]
- [Definições de política de conformidade para dispositivos iOS](ios-compliance-policy-settings-in-microsoft-intune.md)
- [Definições de política de conformidade para dispositivos Windows](windows-compliance-policy-settings-in-microsoft-intune.md)

## Definições de segurança do sistema
### Palavra-passe
- **Palavra-passe obrigatória para desbloquear dispositivos móveis:** defina esta opção como **Sim** para exigir que os utilizadores introduzam uma palavra-passe para que possam aceder ao respetivo dispositivo.

-  **Comprimento mínimo da palavra-passe:** especifique o número mínimo de dígitos ou carateres que a palavra-passe do utilizador tem de ter.

- **Qualidade da palavra-passe:** ative esta definição para configurar os requisitos de palavra-passe para dispositivos Android. Escolha entre:
  -   **Biométrica de segurança baixa**
  - **Necessário**
  -   **Pelo menos numérica**
  -   **Pelo menos alfabética**
  -   **Pelo menos alfanumérica**
  -   **Alfanumérica com símbolos**

- **Minutos de inatividade antes de a palavra-passe ser exigida:** especifica o tempo de inatividade antes de o utilizador ter de reintroduzir a palavra-passe.

- **Expiração da Palavra-passe (dias):** selecione o número de dias antes de a palavra-passe do utilizador expirar e ser necessário criar uma nova.

- **Memorizar histórico de palavras-passe:** utilize esta definição juntamente com **Impedir a reutilização de palavras-passe anteriores** para impedir o utilizador de criar palavras-passe utilizadas anteriormente.

- **Impedir a reutilização de palavras-passe anteriores:** se a opção **Memorizar histórico de palavras-passe** estiver selecionada, especifique o número de palavras-passe utilizadas anteriormente que não podem ser reutilizadas.

- **Exigir uma palavra-passe quando o dispositivo regressa de um estado inativo:** esta definição deve ser utilizada em conjunto com a definição **Minutos de inatividade antes de a palavra-passe ser exigida**. Será pedido aos utilizadores finais que introduzam uma palavra-passe para aceder a dispositivos que tenham estado inativos durante o período de tempo especificado na definição **Minutos de inatividade antes de a palavra-passe ser exigida**.

### Encriptação
- **Exigir encriptação no dispositivo móvel:** configure esta opção como **Sim** para exigir que os dispositivos sejam encriptados para ligar aos recursos. Os dispositivos são encriptados quando é configurada a definição **Palavra-passe obrigatória para desbloquear os dispositivos móveis**.

## Definições de estado de funcionamento do dispositivo

- **O dispositivo não pode ter jailbreak ou root:** se ativar esta definição, os dispositivos com jailbreak serão avaliados como não conformes.

## Definições de propriedade do dispositivo
- **SO mínimo necessário:** quando um dispositivo não cumpre o requisito de versão mínima do SO, será comunicado como não conforme.
  É apresentada uma ligação com informações sobre como atualizar. O utilizador final pode optar por atualizar o dispositivo para poder aceder aos recursos da empresa.

- **Versão do SO máxima permitida:** quando um dispositivo utiliza uma versão do SO posterior à especificada na regra, o acesso aos recursos da empresa é bloqueado e é pedido ao utilizador que contacte o administrador de TI. Até a regra ser alterada para permitir a versão do SO, este dispositivo não pode ser utilizado no acesso aos recursos da empresa.



<!--HONumber=Jun16_HO4-->



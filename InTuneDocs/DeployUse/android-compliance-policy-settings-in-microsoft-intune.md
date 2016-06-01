---
# required metadata

title: Definições de política de conformidade para dispositivos Android | Microsoft Intune
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

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---


# Definições de política de conformidade para dispositivos Android no Microsoft Intune

As definições de política descritas neste tópico aplicam-se a dispositivos com o Android 4.0 e posterior, ou Samsung KNOX 4.0 e posterior.

Se estiver à procura de informações sobre outras plataformas, selecione uma das seguintes opções:
> [!div class="op_single_selector"]
- [Definições de política de conformidade para dispositivos iOS](ios-compliance-policy-settings-in-microsoft-intune.md)
- [Definições de política de conformidade para dispositivos Windows](windows-compliance-policy-settings-in-microsoft-intune.md)

## Definições de segurança do sistema
### Palavra-passe
- **Exigir uma palavra-passe para desbloquear dispositivos móveis:** defina esta opção como **Sim** para exigir que os utilizadores introduzam uma palavra-passe para que

-  possam aceder ao seu dispositivo.

- **Comprimento mínimo da palavra-passe:** especifique o número mínimo de dígitos ou carateres que a palavra-passe do utilizador tem de ter. **Qualidade da palavra-passe:** ative esta definição para configurar os requisitos de palavra-passe para dispositivos Android.
  -   **Escolha entre:**
  - **Biométrica de segurança baixa**
  -   **Necessário**
  -   **Pelo menos numérica**
  -   **Pelo menos alfabética**
  -   **Pelo menos alfanumérica**

- Alfanumérica com símbolos

- **Minutos de inatividade antes de a palavra-passe ser exigida:** especifica o tempo de inatividade antes de o utilizador ter de reintroduzir a palavra-passe.

- **Expiração da palavra-passe (dias):** selecione o número de dias antes de a palavra-passe do utilizador expirar

- e ser necessário criar uma nova.

- **Memorizar histórico de palavras-passe:** utilize esta definição juntamente com a definição **Impedir a reutilização de palavras-passe anteriores** para impedir o utilizador de criar palavras-passe utilizadas anteriormente.

### **Impedir a reutilização de palavras-passe anteriores:** se a opção **Memorizar histórico de palavras-passe** estiver selecionada, especifique o
- número de palavras-passe utilizadas anteriormente que não podem ser reutilizadas. Exigir uma palavra-passe quando o dispositivo regressa de um estado inativo:

## Esta definição deve ser utilizada em conjunto com a definição **Minutos de inatividade antes de a palavra-passe ser exigida**.

- Será pedido aos utilizadores finais que introduzam uma palavra-passe para aceder a dispositivos que tenham estado inativos durante o período de tempo especificado na definição

## **Minutos de inatividade antes de a palavra-passe ser exigida**.
- Encriptação
  **Exigir encriptação no dispositivo móvel:** configure esta opção como **Sim** para exigir que os dispositivos sejam encriptados para se ligarem aos recursos.

- Os dispositivos são encriptados quando é configurada a definição **Exigir uma palavra-passe para
  desbloquear os dispositivos móveis**


<!--HONumber=May16_HO2-->



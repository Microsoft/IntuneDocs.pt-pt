---
# required metadata

title: Definições de política de conformidade para dispositivos iOS | Microsoft Intune
description:
keywords:
author: karthikaraman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 4a59d24f-ed58-49b1-b874-b2d4aea3ec76

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---


# Definições de política de conformidade para dispositivos iOS no Microsoft Intune

As definições de política descritas neste tópico aplicam-se a dispositivos com o iOS 6 e posterior.

Se estiver à procura de informações sobre outras plataformas, selecione uma das seguintes opções:
> [!div class="op_single_selector"]
- [Definições de política de conformidade para dispositivos Android](android-compliance-policy-settings-in-microsoft-intune.md)
- [Definições de política de conformidade para dispositivos Windows](windows-compliance-policy-settings-in-microsoft-intune.md)

## Definições de segurança do sistema
### Palavra-passe
- **Exigir uma palavra-passe para desbloquear dispositivos móveis:**    defina esta opção como **Sim** para exigir que os utilizadores introduzam uma palavra-passe para que possam aceder ao seu dispositivo.

- Os dispositivos iOS que utilizam a palavra-passe são encriptados.

-  **Permitir palavras-passe simples:**    defina esta opção
- como **Sim** para permitir que os utilizadores criem palavras-passe simples,

- como ’‘**1234**’’ ou ’‘**1111**’’. Comprimento mínimo da palavra-passe:
  -   Especifique o número mínimo de dígitos ou carateres que
  -   a palavra-passe do utilizador tem de conter.
  -   **Tipo obrigatório de palavra-passe:** especifique se os utilizadores têm de criar
  -   uma palavra-passe **Alfanumérica** ou **Numérica**.

  **Número mínimo de conjuntos de carateres:** se definir **Tipo obrigatório de palavra-passe** como

  **Alfanumérico**, esta definição especifica o número mínimo de
- conjuntos de carateres que a palavra-passe tem de conter.

- Os quatro conjuntos de carateres são:

- Letras minúsculas

- Letras maiúsculas

- Símbolos Números

### A definição de um número mais alto nesta definição obrigará os utilizadores a criarem palavras-passe mais complexas.
- Para dispositivos iOS, esta definição refere-se ao número de carateres especiais (por exemplo, **!**, **#**, **&amp;**) que tem de ser incluído na palavra-passe. **Minutos de inatividade antes da palavra-passe ser exigida:** especifica o tempo de inatividade antes de o utilizador ter de reintroduzir a palavra-passe.
  - **Expiração da palavra-passe (dias):** selecione o número de dias antes de a palavra-passe do utilizador expirar
  - e ser necessário criar uma nova. **Memorizar histórico de palavras-passe:** utilize esta definição juntamente com a definição **Impedir a reutilização de palavras-passe anteriores** para impedir o utilizador de criar palavras-passe utilizadas anteriormente.


- **Impedir a reutilização de palavras-passe anteriores:** se a opção **Memorizar histórico de palavras-passe** estiver selecionada, especifique o número de palavras-passe utilizadas anteriormente que não podem ser reutilizadas.

     Exigir uma palavra-passe quando o dispositivo regressa de um estado inativo:

## Esta definição deve ser utilizada em conjunto com a definição **Minutos de inatividade antes de a palavra-passe ser exigida**.

- Será pedido aos utilizadores finais que introduzam uma palavra-passe para aceder a dispositivos que tenham estado inativos durante o período de tempo especificado na definição

##  **Minutos de inatividade antes de a palavra-passe ser exigida**.
- Perfil de e-mail
**A conta de e-mail tem de ser gerida pelo Intune:** quando esta opção está definida como **Sim**, o dispositivo tem de utilizar o e-mail não conforme implementado no dispositivo. O dispositivo é considerado não conforme nas seguintes situações:

- O perfil de e-mail também tem de ser implementado no mesmo grupo de utilizadores como grupo de utilizadores visado pela política de conformidade, caso contrário os dispositivos dos utilizadores serão considerados não conformes. O dispositivo é considerado como não conforme se o utilizador tiver configurado uma conta de e-mail no dispositivo que corresponda a um perfil de e-mail do Intune que tenha sido implementado no dispositivo.


<!--HONumber=May16_HO2-->



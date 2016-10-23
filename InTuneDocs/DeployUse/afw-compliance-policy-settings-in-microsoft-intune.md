---
title: "Definições de política de conformidade para Android for Work | Microsoft Intune"
description: "Este tópico descreve as definições de política de conformidade do dispositivo para dispositivos Android que são compatíveis com o Android for Work."
keywords: 
author: karthikaraman
manager: angrobe
ms.date: 07/13/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e721c5c7-9678-4f3b-81d4-564da5efd337
ms.reviewer: chrisbal
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 609d3ab2c96d9a3dff7a6bb6aa085f9cda83ba38
ms.openlocfilehash: 845604fb97927abcc267884dbea6096a82eb170c


---


# Definições de política de conformidade para dispositivos Android for Work no Microsoft Intune

As definições de política descritas neste tópico aplicam-se a dispositivos Android for Work.

Se estiver à procura de informações sobre outras plataformas, selecione uma das seguintes opções:
> [!div class="op_single_selector"]
- [Definição de política de conformidade para Android](android-compliance-policy-settings-in-microsoft-intune.md)
- [Definições de política de conformidade para dispositivos iOS](ios-compliance-policy-settings-in-microsoft-intune.md)
- [Definições de política de conformidade para dispositivos Windows](windows-compliance-policy-settings-in-microsoft-intune.md)

## Definições de segurança do sistema
### Palavra-passe
- **Palavra-passe obrigatória para desbloquear dispositivos móveis:** defina esta opção como **Sim** para exigir que os utilizadores introduzam uma palavra-passe para que possam aceder ao respetivo dispositivo.

-  **Comprimento mínimo da palavra-passe:** especifique o número mínimo de dígitos ou carateres que a palavra-passe do utilizador tem de ter.

- **Qualidade da palavra-passe:** esta definição deteta se os requisitos de palavra-passe que especificou estão configurados no dispositivo. Ative esta definição para exigir que os utilizadores configurem determinados requisitos de palavra-passe para dispositivos Android. Escolha entre:
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
- **Exigir encriptação em dispositivos móveis:** uma vez que os dispositivos Android for Work impõem a encriptação, não necessita de configurar esta definição.

## Definições de estado de funcionamento e segurança do dispositivo

- **O dispositivo não pode ter jailbreak ou root:** se ativar esta definição, os dispositivos com jailbreak serão avaliados como não conformes.
- **Exigir que os dispositivos impeçam a instalação de aplicações de origens desconhecidas:** uma vez que os dispositivos Android for Work restringem sempre a instalação de origens desconhecidas, não necessita de configurar esta definição. .  

- **Exigir que a depuração USB esteja desativada**: uma vez que a depuração USB já se encontra desativada em dispositivos Android for Work, não necessita de configurar esta definição.

- **Nível mínimo de correção de segurança Android**: utilize esta definição para especificar o nível mínimo de correção Android.  Os dispositivos que não tenham, pelo menos, este nível de correção não serão conformes. A data tem de ser especificada no formato: AAAA-MM-DD.
- **Exigir que a proteção contra ameaças de dispositivos seja ativada**: utilize esta definição para assumir a avaliação de riscos da solução Lookout MTP como uma condição para conformidade. Selecione o nível de ameaça máximo permitido, que será um dos seguintes:

  - **Nenhum (seguro):** é o nível mais seguro. Isto significa que o dispositivo não pode ter nenhuma ameaça. Se o dispositivo detetar qualquer nível de ameaças, será avaliado como não conforme.
  - **Baixo:** o dispositivo é avaliado como conforme se só estiverem presentes ameaças de nível baixo. Qualquer nível mais alto coloca o dispositivo num estado de não conforme.
  - **Médio:** o dispositivo é avaliado como conforme se só estiverem presentes ameaças de nível baixo ou médio. Se forem detetadas ameaças de nível alto no dispositivo, será determinado como não conforme.
  - **Alto:** este é o nível menos seguro. Essencialmente, este nível permite todos os níveis de ameaças e possivelmente só será útil se utilizar esta solução apenas para a criação de relatórios.

  Para obter mais detalhes, consulte [Ativar a regra de proteção contra ameaças de dispositivo na política de conformidade](enable-device-threat-protection-rule-in-compliance-policy.md).

## Definições de propriedade do dispositivo
- **SO mínimo necessário:** quando um dispositivo não cumpre o requisito de versão mínima do SO, será comunicado como não conforme.
  É apresentada uma ligação com informações sobre como atualizar. O utilizador final pode optar por atualizar o dispositivo para poder aceder aos recursos da empresa.

- **Versão do SO máxima permitida:** quando um dispositivo utiliza uma versão do SO posterior à especificada na regra, o acesso aos recursos da empresa é bloqueado e é pedido ao utilizador que contacte o administrador de TI. Até a regra ser alterada para permitir a versão do SO, este dispositivo não pode ser utilizado no acesso aos recursos da empresa.



<!--HONumber=Oct16_HO2-->



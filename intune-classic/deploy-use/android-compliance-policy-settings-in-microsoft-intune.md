---
title: Definições de políticas de conformidade para Android
description: Este tópico descreve as definições da política de conformidade de dispositivos para dispositivos Android.
keywords: ''
author: andredm7
ms.author: andredm
manager: dougeby
ms.date: 01/23/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: e721c5c7-9678-4f3b-81d4-564da5efd337
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 63618f9af5f2bdb863a19c229c862e446dd4ea7a
ms.sourcegitcommit: df60d03a0ed54964e91879f56c4ef0a7507c17d4
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2018
---
# <a name="compliance-policy-settings-for-android-devices-in-microsoft-intune"></a>Definições de política de conformidade para dispositivos Android no Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

As definições de política descritas neste tópico aplicam-se a dispositivos com o Android 4.0 e posterior ou Samsung KNOX 4.0 e posterior.

Se estiver à procura de informações sobre outras plataformas, selecione uma das seguintes opções:
> [!div class="op_single_selector"]
- [Definições de política de conformidade para dispositivos iOS](ios-compliance-policy-settings-in-microsoft-intune.md)
- [Definições de política de conformidade para dispositivos Windows](windows-compliance-policy-settings-in-microsoft-intune.md)
- [Definições de política de conformidade para dispositivos Android for Work](afw-compliance-policy-settings-in-microsoft-intune.md)

## <a name="system-security-settings"></a>Definições de segurança do sistema
### <a name="password"></a>Palavra-passe
- **Palavra-passe obrigatória para desbloquear dispositivos móveis**: defina esta opção como **Sim** para exigir que os utilizadores introduzam uma palavra-passe para que possam aceder ao respetivo dispositivo.

-  **Comprimento mínimo da palavra-passe**: especifique o número mínimo de dígitos ou carateres que a palavra-passe do utilizador tem de ter.

- **Qualidade da palavra-passe**: esta definição deteta se os requisitos de palavra-passe que especificou estão configurados no dispositivo. Ative esta definição para exigir que os utilizadores cumpram determinados requisitos de palavra-passe para dispositivos Android. Escolha entre:

  -   **Biométrica de segurança baixa**
  -   **Necessário**
  -   **Pelo menos numérica**
  -   **Pelo menos alfabética**
  -   **Pelo menos alfanumérica**
  -   **Alfanumérica com símbolos**

- **Minutos de inatividade antes da palavra-passe ser exigida:** especifica o tempo de inatividade antes de o utilizador ter de reintroduzir a palavra-passe.

- **Expiração da Palavra-passe (dias)**: selecione o número de dias antes de a palavra-passe do utilizador expirar e ser necessário criar uma nova.

- **Memorizar histórico de palavras-passe**: utilize esta definição juntamente com **Impedir a reutilização de palavras-passe anteriores** para impedir o utilizador de criar palavras-passe utilizadas anteriormente.

- **Impedir a reutilização de palavras-passe anteriores:** especifique o número de palavras-passe utilizadas anteriormente que não podem ser reutilizadas (se a opção **Memorizar histórico de palavras-passe** estiver selecionada).

- **Exigir uma palavra-passe quando o dispositivo é ativado de um estado inativo:** utilize esta definição em conjunto com a definição **Minutos de inatividade antes de a palavra-passe ser exigida**. Será pedido aos utilizadores que introduzam uma palavra-passe para aceder a dispositivos que tenham estado inativos durante o período de tempo especificado na definição **Minutos de inatividade antes de a palavra-passe ser exigida**.

### <a name="encryption"></a>Encriptação
- **Exigir encriptação no dispositivo móvel:** defina esta opção como **Sim** para exigir que os dispositivos sejam encriptados para ligar aos recursos. Os dispositivos são encriptados quando é configurada a definição **Palavra-passe obrigatória para desbloquear os dispositivos móveis**.

## <a name="device-health-and-security-settings"></a>Definições de estado de funcionamento e segurança do dispositivo

- **O dispositivo não pode estar desbloqueado por jailbreak ou root:** se ativar esta definição, os dispositivos com jailbreak serão avaliados como não conformes.
- **Exigir que os dispositivos impeçam a instalação de aplicações de origens desconhecidas (Android 4.0 ou posterior)**: para bloquear os dispositivos que tenham a opção **Segurança > Origens desconhecidas** ativada no dispositivo, ative esta definição e defina-a como **Sim**.  

>[!IMPORTANT]
>As aplicações de sideload requerem a ativação da opção **Origens desconhecidas**. Aplique esta política de conformidade apenas se não tiver aplicações Android de sideload nos dispositivos.

- **Exigir que a depuração USB esteja desativada (Android 4.2 ou posterior)**: especifique se a opção de deteção de depuração USB no dispositivo está ativada.
- **Exigir que os dispositivos tenham ativado o dispositivo de Análise para ameaças de segurança (Android 4.2 a 4.4)**: especifique que a funcionalidade **Verificar aplicações** está ativada no dispositivo.
- **Nível mínimo de correção de segurança Android (Android 6.0 ou posterior)**: especifique o nível mínimo de correção Android.  Os dispositivos que não tenham, pelo menos, este nível de correção não serão conformes. A data tem de ser especificada no formato AAAA-MM-DD.
- **Exigir que a proteção contra ameaças de dispositivos seja ativada**: utilize esta definição para assumir a avaliação de riscos da solução Lookout MTP como uma condição para conformidade. Selecione o nível de ameaça máximo permitido, que será um dos seguintes:

  - **Nenhum (seguro):** é o nível mais seguro. Isto significa que o dispositivo não pode ter nenhuma ameaça. Se forem detetadas ameaças no dispositivo, o mesmo será avaliado como não conforme.
  - **Baixo**: o dispositivo é avaliado como conforme se só estiverem presentes ameaças de nível baixo. Qualquer nível mais alto coloca o dispositivo num estado não conforme.
  - **Médio**: o dispositivo é avaliado como conforme se só estiverem presentes ameaças de nível baixo ou médio. Se forem detetadas ameaças de nível alto no dispositivo, este será determinado como não conforme.
  - **Alto:** este é o nível menos seguro. Essencialmente, este nível permite todos os níveis de ameaças e possivelmente só será útil se utilizar esta solução apenas para a criação de relatórios.

  Para obter mais detalhes, veja [Criar política de conformidade de dispositivos do Lookout](create-lookout-device-compliance-policy.md).

## <a name="device-property-settings"></a>Definições de propriedade do dispositivo

- **SO mínimo necessário**: quando um dispositivo não cumpre o requisito de versão mínima do SO, será comunicado como não conforme.
  É apresentada uma ligação com informações sobre como atualizar. O utilizador pode optar por atualizar o dispositivo para poder aceder aos recursos da empresa.

- **Versão do SO máxima permitida**: quando um dispositivo utiliza uma versão do SO posterior à especificada na regra, o acesso aos recursos da empresa é bloqueado e é pedido ao utilizador que contacte o administrador de TI. Até a regra ser alterada para permitir a versão do SO, este dispositivo não pode ser utilizado no acesso aos recursos da empresa.

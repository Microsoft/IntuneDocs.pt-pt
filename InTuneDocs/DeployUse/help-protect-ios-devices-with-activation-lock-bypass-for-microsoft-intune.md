---
title: "Ajudar a proteger dispositivos iOS desativando o Bloqueio de Ativação | Microsoft Intune"
description: 
keywords: 
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: bb49e926-15c4-4f01-b6eb-cee6f7ee1984
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 496679a196dc3e84c6b16ad0d3b830c81f12631b
ms.openlocfilehash: 7bbd761b13f110297959a036ec15cafe1396377e


---

# Ajudar a proteger dispositivos iOS desativando o Bloqueio de Ativação para o Microsoft Intune
O Microsoft Intune pode ajudá-lo a gerir o Bloqueio de Ativação de iOS, uma funcionalidade da aplicação Encontrar o Meu iPhone para iOS 7.1 ou dispositivos posteriores. O Bloqueio de Ativação é ativado automaticamente ao utilizar a aplicação Encontrar o Meu iPhone num dispositivo. Depois de estar ativado, o Apple ID e a palavra-passe do utilizador têm de ser introduzidos primeiro para que qualquer pessoa possa:

-   Desativar a aplicação Encontrar o Meu iPhone

-   Apagar o dispositivo

-   Reativar o dispositivo

## Como o Bloqueio de Ativação o afeta
Embora o Bloqueio de Ativação ajude a proteger os dispositivos iOS e melhore as possibilidades de recuperação em caso de roubo ou perda, esta funcionalidade pode apresentar-lhe, na qualidade de administrador de TI, vários desafios. Por exemplo:

-   Um dos seus utilizadores configura o Bloqueio de Ativação num dispositivo. O utilizador sai da empresa e devolve o dispositivo. Sem o Apple ID e a palavra-passe do utilizador, não existe nenhuma forma de reativar o dispositivo.

-   É necessário um relatório de todos os dispositivos que têm o Bloqueio de Ativação ativado.

-   Durante a atualização do dispositivo na sua organização, deve reatribuir alguns dispositivos para outro departamento. Apenas pode reatribuir dispositivos que não têm o Bloqueio de Ativação ativado.

Para ajudar a resolver estes problemas, a Apple introduziu a desativação do Bloqueio de Ativação no iOS 7.1. Isto permite-lhe remover o Bloqueio de Ativação a partir de dispositivos supervisionados sem o Apple ID e a palavra-passe do utilizador. Os dispositivos supervisionados podem gerar um código de desativação do Bloqueio de Ativação específico para o dispositivo, que é armazenado no servidor de ativação da Apple.

> [!TIP]
> O modo supervisionado para dispositivos iOS permite-lhe utilizar a Ferramenta de Configuração da Apple para bloquear um dispositivo, de forma a limitar a funcionalidade para fins empresariais específicos. O modo supervisionado destina-se, geralmente, apenas para dispositivos dos utilizadores da empresa.

## De que forma o Intune o ajuda a gerir o Bloqueio de Ativação
O Intune pode pedir o estado de Bloqueio de Ativação de dispositivos supervisionados e não supervisionados com o iOS 7.1 e posterior. Apenas para dispositivos supervisionados, o Intune pode obter o código de desativação do Bloqueio de Ativação e enviá-lo diretamente para o dispositivo. Se o dispositivo tiver sido eliminado, pode aceder diretamente ao mesmo, utilizando o código como o nome de utilizador e uma palavra-passe em branco).

**Os benefícios empresariais desta funcionalidade são**:

-   O utilizador obtém as vantagens de segurança da aplicação Encontrar o Meu iPhone.

-   Pode permitir que o utilizador trabalhe sabendo que quando o dispositivo tiver de ser reaproveitado, pode extinguí-lo ou desbloqueá-lo.

## Como utilizar a desativação de Bloqueio de Ativação a partir da consola de administração do Intune
> [!IMPORTANT]
> Depois de desativar o Bloqueio de Ativação num dispositivo, será aplicado automaticamente um novo Bloqueio de Ativação se abrir a aplicação Encontrar o Meu iPhone. Por este motivo, **deverá estar na posse física do dispositivo antes de seguir este procedimento**.

1.  Na [consola de administração do Microsoft Intune](https://manage.microsoft.com), escolha **Grupos** &gt; **Todos os Dispositivos** &gt; **Todos os Dispositivos Pertencentes à Empresa**.

2.  Selecione o dispositivo cujo Bloqueio de Ativação pretende desativar. Escolha **Desativar Bloqueio de Ativação**.

3.  Leia a mensagem de aviso. Escolha **Sim** para continuar.

Pode determinar o estado do pedido de desbloqueio na página de detalhes do dispositivo.

## Como ver os dispositivos que estão a utilizar o Bloqueio de Ativação
Pode ver os dispositivos que estão a utilizar o Bloqueio de Ativação de duas formas:

-   Execute os **Relatórios de Inventário de Dispositivos Móveis**. Este relatório apresenta as colunas **Estado do Bloqueio de Ativação** e **Supervisionado** para indicar o estado dos dispositivos. Os valores para **Supervisionado** são **Sim** ou **Não**e os valores para **Estado do Bloqueio de Ativação** são:

    -   Ativado com código de desativação

    -   Ativado sem o código de desativação (o dispositivo não é supervisionado)

    -   Ativado sem o código de desativação (o dispositivo não é alcançado)

    -   Não ativado

    O campo **Estado do Bloqueio de Ativação** está em branco para dispositivos que não executem o iOS 7.1 ou posterior.

-   Selecione um dispositivo numa vista de grupos, pode ver o estado de Bloqueio de Ativação no painel de detalhes do dispositivo.

    Se selecionar um dispositivo no nó **Todos os Dispositivos Pertencentes à Empresa** e o Bloqueio de Ativação estiver ativado para o dispositivo, também pode ver o código de desativação. Este código pode ser utilizado para emitir manualmente uma desativação do Bloqueio de Ativação.

### Consulte também
[Extinguir dispositivos](retire-devices-from-microsoft-intune-management.md)
[Ajudar a proteger os seus dispositivos através do bloqueio remoto e da reposição do código de acesso](use-remote-lock-and-passcode-reset-in-microsoft-intune.md)



<!--HONumber=Jun16_HO4-->



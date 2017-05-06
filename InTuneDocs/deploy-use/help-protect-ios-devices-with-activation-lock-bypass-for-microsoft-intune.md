---
title: "Gerir o Bloqueio de Ativação do iOS em dispositivos | Documentos da Microsoft"
description: "O Microsoft Intune pode ajudá-lo a gerir o Bloqueio de Ativação de iOS, uma funcionalidade da aplicação Encontrar o Meu iPhone para iOS 7.1 ou dispositivos posteriores."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 04/24/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: bb49e926-15c4-4f01-b6eb-cee6f7ee1984
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: 8b2bd3ecba0b597bc742ea08872ffe8fc58155cf
ms.openlocfilehash: 742fac9c401c24bfc0f2500a238c41fa00c47fd3
ms.lasthandoff: 04/24/2017


---

# <a name="help-protect-ios-devices-with-activation-lock-bypass-for-microsoft-intune"></a>Ajudar a proteger dispositivos iOS desativando o Bloqueio de Ativação para o Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

O Microsoft Intune pode ajudá-lo a gerir o Bloqueio de Ativação de iOS, uma funcionalidade da aplicação Encontrar o Meu iPhone para iOS 8.0 ou dispositivos posteriores. O Bloqueio de Ativação é ativado automaticamente quando um utilizador abre a aplicação Encontrar o Meu iPhone num dispositivo. Depois de estar ativado, o Apple ID e a palavra-passe do utilizador têm de ser introduzidos primeiro para que qualquer pessoa possa: 

-   Desativar a aplicação Encontrar o Meu iPhone

-   Apagar o dispositivo

-   Reativar o dispositivo

## <a name="how-activation-lock-affects-you"></a>Como o Bloqueio de Ativação o afeta
Embora o Bloqueio de Ativação ajude a proteger os dispositivos iOS e melhore as possibilidades de recuperação em caso de roubo ou perda do dispositivo, esta funcionalidade pode apresentar-lhe, na qualidade de administrador de TI, vários desafios. Por exemplo:

-   Um utilizador configura o Bloqueio de Ativação num dispositivo. O utilizador sai da empresa e devolve o dispositivo. Sem o Apple ID e a palavra-passe do utilizador, não existe nenhuma forma de reativar o dispositivo.

-   É necessário um relatório de todos os dispositivos que têm o Bloqueio de Ativação ativado.

-   Deve reatribuir alguns dispositivos para outro departamento, durante a atualização do dispositivo na sua organização. Apenas pode reatribuir dispositivos que não têm o Bloqueio de Ativação ativado.

Para ajudar a resolver estes problemas, a Apple introduziu a desativação do Bloqueio de Ativação no iOS 7.1. Isto permite-lhe remover o Bloqueio de Ativação a partir de dispositivos supervisionados sem o Apple ID e a palavra-passe do utilizador. Os dispositivos supervisionados podem gerar um código de desativação do Bloqueio de Ativação específico para o dispositivo, que é armazenado no servidor de ativação da Apple.

> [!TIP]
> O modo supervisionado para dispositivos iOS permite-lhe utilizar a Configuração da Apple para bloquear um dispositivo e limitar a funcionalidade para fins empresariais específicos. O modo supervisionado destina-se, geralmente, apenas para dispositivos dos utilizadores da empresa.

Pode ler mais sobre o Bloqueio de Ativação [aqui](https://support.apple.com/en-us/HT201365).

## <a name="how-intune-helps-you-manage-activation-lock"></a>De que forma o Intune o ajuda a gerir o Bloqueio de Ativação
O Intune pode pedir o estado de Bloqueio de Ativação de dispositivos supervisionados com o iOS 8.0 e posterior. Apenas para dispositivos supervisionados, o Intune pode obter o código de desativação do Bloqueio de Ativação e enviá-lo diretamente para o dispositivo. Se o dispositivo tiver sido eliminado, pode aceder diretamente ao mesmo com um nome de utilizador em branco e o código como a palavra-passe.

**Os benefícios empresariais desta funcionalidade são**:

-   O utilizador obtém as vantagens de segurança da aplicação Encontrar o Meu iPhone.

-   Pode permitir que os utilizadores trabalhem e saibam que quando um dispositivo tiver de ser reaproveitado, pode extingui-lo ou desbloqueá-lo.

## <a name="before-you-start"></a>Antes de começar

Para poder ignorar o Bloqueio de Ativação nos dispositivos, tem de o ativar primeiro. Para efetuar este procedimento:

1. Utilize as informações no tópico [Gerir definições e funcionalidades nos seus dispositivos com as políticas do Microsoft Intune](/intune/deploy-use/manage-settings-and-features-on-your-devices-with-microsoft-intune-policies) para criar uma [política de configuração de dispositivos](/intune/deploy-use/ios-policy-settings-in-microsoft-intune) iOS.
2. Na secção **Inscrição**, da página de definições, configure a definição **Permitir Bloqueio de Ativação quando o dispositivo estiver no modo supervisionado** como **Sim**.
3. Guarde a política e implemente-a nos dispositivos nos quais pretende ignorar o Bloqueio de Ativação.

## <a name="how-to-use-activation-lock-bypass-from-the-intune-admin-console"></a>Como utilizar a desativação de Bloqueio de Ativação a partir da consola de administração do Intune
> [!IMPORTANT]
> Depois de desativar o Bloqueio de Ativação num dispositivo, é automaticamente aplicada um novo Bloqueio de Ativação se a aplicação Encontrar o meu iPhone for aberta. Por este motivo, **deverá estar na posse física do dispositivo antes de seguir este procedimento**.

1.  Na [consola de administração do Microsoft Intune](https://manage.microsoft.com), escolha **Grupos** &gt; **Todos os Dispositivos** &gt; **Todos os Dispositivos Pertencentes à Empresa**.

2.  Selecione o dispositivo cujo Bloqueio de Ativação pretende desativar. Escolha **Desativar Bloqueio de Ativação**.

3.  Leia a mensagem de aviso. Escolha **Sim** para continuar.

Pode determinar o estado do pedido de desbloqueio na página de detalhes do dispositivo.

## <a name="how-to-see-which-devices-are-using-activation-lock"></a>Como ver os dispositivos que estão a utilizar o Bloqueio de Ativação
Pode ver os dispositivos que estão a utilizar o Bloqueio de Ativação de duas formas:

-   Execute os **Relatórios de Inventário de Dispositivos Móveis**. Este relatório apresenta as colunas **Estado do Bloqueio de Ativação** e **Supervisionado** para indicar o estado dos dispositivos. Os valores para **Supervisionado** são **Sim** ou **Não**e os valores para **Estado do Bloqueio de Ativação** são:

    -   Ativado com código de desativação

    -   Ativado sem o código de desativação (o dispositivo não é supervisionado)

    -   Ativado sem o código de desativação (o dispositivo não é alcançado)

    -   Não ativado

    A caixa **Estado do Bloqueio de Ativação** está em branco para dispositivos que não executem o iOS 8.0 ou posterior.

-   Selecione um dispositivo numa vista de grupos, para ver o estado de Bloqueio de Ativação no painel de detalhes do dispositivo.

    Se selecionar um dispositivo no nó **Todos os Dispositivos Pertencentes à Empresa** e o Bloqueio de Ativação estiver ativado para o dispositivo, também pode ver o código de desativação. Este código pode ser utilizado para emitir manualmente uma desativação do Bloqueio de Ativação.

    > [!IMPORTANT]
    >O Intune retira o inventário dos dispositivos para o Bloqueio de Ativação de sete em sete dias. Por este motivo, dispositivos poderão não ser apresentados imediatamente com o estado do Bloqueio de Ativação na consola do Intune.


### <a name="see-also"></a>Consulte também
[Extinguir dispositivos](retire-devices-from-microsoft-intune-management.md)
[Ajudar a proteger os seus dispositivos através do bloqueio remoto e da reposição do código de acesso](use-remote-lock-and-passcode-reset-in-microsoft-intune.md)


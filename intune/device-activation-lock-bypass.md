---
title: "Ignorar o Bloqueio de Ativação do iOS com o Intune"
titleSuffix: Intune on Azure
description: "Saiba como utilizar o Intune para ignorar o Bloqueio de Ativação do iOS para aceder a dispositivos bloqueados.\""
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 04/27/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9ca3b0ba-e41c-45fb-af28-119dff47c59f
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 0b92949efca2e4dac5836755e2f32b0527d4762d
ms.sourcegitcommit: fd2e8f6f8761fdd65b49f6e4223c2d4a013dd6d9
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/03/2017
---
# <a name="bypass-activation-lock-on-supervised-ios-devices-with-intune"></a>Ignorar o Bloqueio de Ativação em dispositivos iOS supervisionados com o Intune


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

O Microsoft Intune pode ajudá-lo a gerir o Bloqueio de Ativação de iOS, uma funcionalidade da aplicação Encontrar o Meu iPhone para iOS 8.0 ou dispositivos posteriores. O Bloqueio de Ativação é ativado automaticamente quando um utilizador abre a aplicação Encontrar o Meu iPhone num dispositivo. Depois de estar ativado, o Apple ID e a palavra-passe do utilizador têm de ser introduzidos primeiro para que qualquer pessoa possa:

- Desativar a aplicação Encontrar o Meu iPhone
- Apagar o dispositivo
- Reativar o dispositivo

## <a name="how-activation-lock-affects-you"></a>Como o Bloqueio de Ativação o afeta

Embora o Bloqueio de Ativação ajude a proteger os dispositivos iOS e melhore as possibilidades de recuperação em caso de roubo ou perda do dispositivo, esta funcionalidade pode apresentar-lhe, na qualidade de administrador de TI, vários desafios. Por exemplo:

- Um utilizador configura o Bloqueio de Ativação num dispositivo. O utilizador sai da empresa e devolve o dispositivo. Sem o Apple ID e a palavra-passe do utilizador, não existe nenhuma forma de reativar o dispositivo.
- É necessário um relatório de todos os dispositivos que têm o Bloqueio de Ativação ativado.
- Deve reatribuir alguns dispositivos para outro departamento, durante a atualização do dispositivo na sua organização. Apenas pode reatribuir dispositivos que não têm o Bloqueio de Ativação ativado.

Para ajudar a resolver estes problemas, a Apple introduziu a desativação do Bloqueio de Ativação no iOS 7.1. Isto permite-lhe remover o Bloqueio de Ativação a partir de dispositivos supervisionados sem o Apple ID e a palavra-passe do utilizador. Os dispositivos supervisionados podem gerar um código de desativação do Bloqueio de Ativação específico para o dispositivo, que é armazenado no servidor de ativação da Apple.

>[!TIP]
>O modo supervisionado para dispositivos iOS permite-lhe utilizar a Configuração da Apple para bloquear um dispositivo e limitar a funcionalidade para fins empresariais específicos. O modo supervisionado destina-se, geralmente, apenas para dispositivos dos utilizadores da empresa.

Pode ler mais sobre o Bloqueio de Ativação no [site da Apple](https://support.apple.com/HT201365).

## <a name="how-intune-helps-you-manage-activation-lock"></a>De que forma o Intune o ajuda a gerir o Bloqueio de Ativação
O Intune pode pedir o estado de Bloqueio de Ativação de dispositivos supervisionados com o iOS 8.0 e posterior. Apenas para dispositivos supervisionados, o Intune pode obter o código de desativação do Bloqueio de Ativação e enviá-lo diretamente para o dispositivo. Se o dispositivo tiver sido eliminado, pode aceder diretamente ao mesmo com um nome de utilizador em branco e o código como a palavra-passe.

**Os benefícios empresariais desta funcionalidade são:**

- O utilizador obtém as vantagens de segurança da aplicação Encontrar o Meu iPhone.
- Pode permitir que os utilizadores trabalhem e saibam que quando um dispositivo tiver de ser reaproveitado, pode extingui-lo ou desbloqueá-lo.

## <a name="before-you-start"></a>Antes de começar
Para poder ignorar o Bloqueio de Ativação nos dispositivos, tem de o ativar primeiro. Para efetuar este procedimento:

1. Configure um perfil de restrição de dispositivos do Intune para iOS utilizando as informações em [Como configurar as definições de restrição de dispositivos](/intune-azure/configure-devices/how-to-configure-device-restrictions).
2. Ative a definição do modo **Quiosque** em **Bloqueio de Ativação**.
3. Guarde o perfil e, em seguida, atribua o mesmo aos dispositivos nos quais pretende ignorar o Bloqueio de Ativação.


## <a name="how-to-use-activation-lock-bypass"></a>Como ignorar o Bloqueio de Ativação

>[!IMPORTANT]
>Depois de desativar o Bloqueio de Ativação num dispositivo, é automaticamente aplicada um novo Bloqueio de Ativação se a aplicação Encontrar o meu iPhone for aberta. Por este motivo, **deverá estar na posse física do dispositivo antes de seguir este procedimento**.

A ação remota de dispositivos **Ignorar Bloqueio de Ativação** do Intune remove o bloqueio de ativação de um dispositivo iOS sem o Apple ID e a palavra-passe do utilizador. Depois de ignorar o bloqueio de ativação, o dispositivo ativa novamente o bloqueio de ativação quando a aplicação Encontrar o Meu iPhone é iniciada. Ignore o bloqueio de ativação apenas se tiver acesso físico ao dispositivo.

1. Inicie sessão no portal do Azure.
2. Escolha **Mais Serviços** > **Monitorização + Gestão** > **Intune**.
3. No painel **Intune**, escolha **Dispositivos**.
4. No painel **Dispositivos e grupos**, selecione **Todos os dispositivos**.
5. Na lista de dispositivos que gere, escolha um dispositivo iOS supervisionado e, em seguida, escolha a ação remota de dispositivos **Ignorar Bloqueio de Ativação**.

Pode determinar o estado do pedido de desbloqueio na página de detalhes do dispositivo na carga de trabalho **Gerir dispositivos**.

---
title: Ignorar o Bloqueio de Ativação do iOS com o Intune
titlesuffix: Microsoft Intune
description: Saiba como utilizar o Intune para ignorar o Bloqueio de Ativação do iOS para aceder a dispositivos bloqueados.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/22/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 9ca3b0ba-e41c-45fb-af28-119dff47c59f
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8fc349636dc9bccc64782dec2c8d54d6f179bfc3
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/07/2019
ms.locfileid: "55837616"
---
# <a name="bypass-activation-lock-on-supervised-ios-devices-with-intune"></a>Ignorar o Bloqueio de Ativação em dispositivos iOS Supervisionados com o Intune


[!INCLUDE [azure_portal](./includes/azure_portal.md)]

O Microsoft Intune pode ajudá-lo a gerir o Bloqueio de Ativação de iOS, uma funcionalidade da aplicação Encontrar o Meu iPhone para iOS 8.0 ou dispositivos posteriores. O Bloqueio de Ativação é ativado automaticamente quando um utilizador abre a aplicação Encontrar o Meu iPhone num dispositivo. Depois de estar ativado, o Apple ID e a palavra-passe do utilizador têm de ser introduzidos primeiro para que qualquer pessoa possa:

- Desativar a aplicação Encontrar o Meu iPhone
- Apagar o dispositivo
- Reativar o dispositivo

## <a name="how-activation-lock-affects-you"></a>Como o Bloqueio de Ativação o afeta

Embora o Bloqueio de Ativação ajude a proteger os dispositivos iOS e melhore as possibilidades de recuperação em caso de roubo ou perda do dispositivo, esta funcionalidade pode apresentar-lhe, na qualidade de administrador de TI, vários desafios. Por exemplo:

- Um utilizador configura o Bloqueio de Ativação num dispositivo. O utilizador sai da empresa e devolve o dispositivo. Sem o Apple ID e a palavra-passe do utilizador, não existe nenhuma forma de reativar o dispositivo.
- É necessário um relatório de todos os dispositivos que têm o Bloqueio de Ativação ativado.
- Deve reatribuir alguns dispositivos para outro departamento, durante a atualização do dispositivo na sua organização. Apenas pode reatribuir dispositivos que não têm o Bloqueio de Ativação ativado.

Para ajudar a resolver estes problemas, a Apple introduziu a desativação do Bloqueio de Ativação no iOS 7.1. A ação de ignorar o Bloqueio de Ativação permite-lhe remover o Bloqueio de Ativação a partir de dispositivos supervisionados sem o ID Apple e a palavra-passe do utilizador. Os dispositivos supervisionados podem gerar um código de desativação do Bloqueio de Ativação específico para o dispositivo, que é armazenado no servidor de ativação da Apple.

>[!TIP]
>O modo supervisionado para dispositivos iOS permite-lhe utilizar a Configuração da Apple para bloquear um dispositivo e limitar a funcionalidade para fins empresariais específicos. O modo supervisionado é utilizado apenas em dispositivos pertencentes à empresa.

Pode ler mais sobre o Bloqueio de Ativação no [site da Apple](https://support.apple.com/HT201365).

## <a name="how-intune-helps-you-manage-activation-lock"></a>De que forma o Intune o ajuda a gerir o Bloqueio de Ativação
O Intune pode pedir o estado de Bloqueio de Ativação de dispositivos supervisionados com o iOS 8.0 e posterior. Apenas para dispositivos supervisionados, o Intune pode obter o código de desativação do Bloqueio de Ativação e enviá-lo diretamente para o dispositivo. Se o dispositivo tiver sido eliminado, pode aceder diretamente ao mesmo com um nome de utilizador em branco e o código como a palavra-passe.

**As vantagens empresariais da utilização do Intune para gerir o Bloqueio de Ativação são:**

- O utilizador obtém as vantagens de segurança da aplicação Encontrar o Meu iPhone.
- Pode permitir que os utilizadores trabalhem e saibam que quando um dispositivo tiver de ser reaproveitado, pode extingui-lo ou desbloqueá-lo.

## <a name="before-you-start"></a>Antes de começar
Antes de poder ignorar o Bloqueio de Ativação em dispositivos, tem de ativá-lo através destas instruções:

1. Configure um perfil de restrição de dispositivos do Intune para iOS utilizando as informações em [Como configurar as definições de restrição de dispositivos](/intune-azure/configure-devices/how-to-configure-device-restrictions).
2. Nas [definições de restrição de dispositivos para iOS](device-restrictions-ios.md), nas definições **Gerais**, ative a opção **Bloqueio de Ativação**.
3. Guarde o perfil e, em seguida, [atribua-o](device-profile-assign.md) aos dispositivos nos quais pretende ignorar o Bloqueio de Ativação.


## <a name="how-to-use-activation-lock-bypass"></a>Como ignorar o Bloqueio de Ativação

>[!IMPORTANT]
>Depois de ignorar o Bloqueio de Ativação num dispositivo, se a aplicação Encontrar o Meu iPhone for iniciada, será automaticamente aplicado um novo Bloqueio de Ativação. Por este motivo, **deverá estar na posse física do dispositivo antes de seguir este procedimento**.

A ação remota de dispositivos **Ignorar Bloqueio de Ativação** do Intune remove o Bloqueio de Ativação de um dispositivo iOS sem exigir o Apple ID e a palavra-passe do utilizador. Depois de ignorar o Bloqueio de Ativação, o dispositivo ativa novamente o Bloqueio de Ativação quando a aplicação Encontrar o Meu iPhone é iniciada. Ignore o Bloqueio de Ativação apenas se tiver acesso físico ao dispositivo.

1. Inicie sessão no [portal do Azure](https://portal.azure.com).
2. Selecione **Todos os serviços** > **Intune**.
3. No painel do **Intune**, selecione **Dispositivos**.
4. No painel **Dispositivos**, selecione **Todos os dispositivos**.
5. Na lista de dispositivos que gere, selecione a ação remota de dispositivos **Ignorar Bloqueio de Ativação**.
6. Aceda à secção "Hardware" do dispositivo e, em seguida, copie o **Código para ignorar o bloqueio de ativação** em **Acesso condicional**.

    >[!NOTE]
    >Copie o código para ignorar antes de limpar o dispositivo. Se repuser as definições do dispositivo antes de copiar o código, este será removido do Azure.

7.  Aceda ao painel **Descrição geral** do dispositivo e, em seguida, selecione **Limpar**.
8.  Depois de repor o dispositivo, é-lhe pedido o *ID Apple* e a *Palavra-passe*. Deixe o campo *ID* em branco e, em seguida, introduza o **código para ignorar** no campo *palavra-passe*. Esta ação remove a conta do dispositivo. 


## <a name="next-steps"></a>Passos Seguintes

Pode determinar o estado do pedido de desbloqueio na página de detalhes do dispositivo na carga de trabalho **Gerir dispositivos**.

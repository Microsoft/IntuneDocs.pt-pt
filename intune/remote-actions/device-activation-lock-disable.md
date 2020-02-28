---
title: Bypass iOS/iPadOS Activation Lock com Intune
titleSuffix: Microsoft Intune
description: Saiba como utilizar o Intune para contornar o bloqueio de ativação iOS/iPadOS para aceder a dispositivos bloqueados.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/27/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: remote-actions
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 9ca3b0ba-e41c-45fb-af28-119dff47c59f
ms.reviewer: coferro
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: af5bb1c95a15a5c52585278605e2f7a86307cb76
ms.sourcegitcommit: 045ca42cad6f86024af9a38a380535f42a6b4bef
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/28/2020
ms.locfileid: "77782220"
---
# <a name="disable-activation-lock-on-supervised-iosipados-devices-with-intune"></a>Desativar bloqueio de ativação em dispositivos supervisionados iOS/iPadOS com Intune


[!INCLUDE [azure_portal](../includes/azure_portal.md)]

O Microsoft Intune pode ajudá-lo a gerir o iOS/iPadOS Activation Lock, uma funcionalidade da aplicação Find My iPhone para iOS/iPadOS 8.0 e dispositivos posteriores. O Bloqueio de Ativação é ativado automaticamente quando um utilizador abre a aplicação Encontrar o Meu iPhone num dispositivo. Depois de estar ativado, o Apple ID e a palavra-passe do utilizador têm de ser introduzidos primeiro para que qualquer pessoa possa:

- Desativar a aplicação Encontrar o Meu iPhone
- Apagar o dispositivo
- Reativar o dispositivo

## <a name="how-activation-lock-affects-you"></a>Como o Bloqueio de Ativação o afeta

Enquanto o Bloqueio de Ativação ajuda a proteger os dispositivos iOS/iPadOS e melhora as hipóteses de recuperar um dispositivo perdido ou roubado, esta capacidade pode apresentá-lo, como administrador de TI, com uma série de desafios. Por exemplo:

- Um utilizador configura o Bloqueio de Ativação num dispositivo. O utilizador sai da empresa e devolve o dispositivo. Sem o Apple ID e a palavra-passe do utilizador, não existe nenhuma forma de reativar o dispositivo.
- É necessário um relatório de todos os dispositivos que têm o Bloqueio de Ativação ativado.
- Deve reatribuir alguns dispositivos para outro departamento, durante a atualização do dispositivo na sua organização. Apenas pode reatribuir dispositivos que não têm o Bloqueio de Ativação ativado.

Para ajudar a resolver estes problemas, a Apple introduziu o bloqueio de ativação desativação no iOS/iPadOS 7.1. Desativar o bloqueio de ativação permite-lhe remover o bloqueio de ativação de dispositivos supervisionados sem o APPLE ID e a palavra-passe do utilizador. Os dispositivos supervisionados podem gerar um código de desativação do Bloqueio de Ativação específico para o dispositivo, que é armazenado no servidor de ativação da Apple.

>[!TIP]
>O modo supervisionado para dispositivos iOS/iPadOS permite utilizar o Configurator Apple para bloquear um dispositivo e limitar a funcionalidade a fins comerciais específicos. O modo supervisionado é utilizado apenas em dispositivos pertencentes à empresa.

Pode ler mais sobre o Bloqueio de Ativação no [site da Apple](https://support.apple.com/HT201365).

## <a name="how-intune-helps-you-manage-activation-lock"></a>De que forma o Intune o ajuda a gerir o Bloqueio de Ativação
Intune pode solicitar o estado de Bloqueio de Ativação de dispositivos supervisionados que executam iOS/iPadOS 8.0 e posteriormente. Apenas para dispositivos supervisionados, o Intune pode recuperar o código de bloqueio de ativação de sactivação e emiti-lo diretamente para o dispositivo. Se o dispositivo tiver sido eliminado, pode aceder diretamente ao mesmo com um nome de utilizador em branco e o código como a palavra-passe.

**As vantagens empresariais da utilização do Intune para gerir o Bloqueio de Ativação são:**

- O utilizador obtém as vantagens de segurança da aplicação Encontrar o Meu iPhone.
- Pode permitir que os utilizadores trabalhem e saibam que quando um dispositivo tiver de ser reaproveitado, pode extingui-lo ou desbloqueá-lo.

## <a name="before-you-start"></a>Antes de começar
Antes de poder desativar o bloqueio de ativação nos dispositivos, deve activar-o seguindo estas instruções:

1. Configure um perfil de restrição do dispositivo Intune para iOS/iPadOS utilizando as informações em [Como configurar as definições](/intune-azure/configure-devices/how-to-configure-device-restrictions)de restrição do dispositivo .
2. Nas definições de restrição do [dispositivo para iOS/iPadOS,](../configuration/device-restrictions-ios.md)sob as definições **gerais,** ative a fechadura de **ativação**da opção .
3. Guarde o perfil e, em seguida, [atribua-o](../configuration/device-profile-assign.md) aos dispositivos em que pretende gerir o Bloqueio de Ativação de Desativação.


## <a name="how-to-use-disable-activation-lock"></a>Como utilizar o bloqueio de ativação de desativação

>[!IMPORTANT]
>Depois de desativar o Bloqueio de Ativação num dispositivo, se a aplicação Find My iPhone for iniciada, é automaticamente aplicado um novo Bloqueio de Ativação. Por este motivo, **deverá estar na posse física do dispositivo antes de seguir este procedimento**.

A ação do dispositivo remoto de ativação Intune **Desativação** remove o bloqueio de ativação de um dispositivo iOS/iPadOS sem necessitar do APPLE ID e da palavra-passe do utilizador. Depois de desativar o bloqueio de ativação, o dispositivo volta a ligar o Bloqueio de Ativação quando a aplicação Find My iPhone começar. Desative o bloqueio de ativação apenas se tiver acesso físico ao dispositivo.

1. Inscreva-se no [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431).
3. No painel do **Intune**, selecione **Dispositivos**.
4. No painel **Dispositivos**, selecione **Todos os dispositivos**.
5. Na lista de dispositivos que gere, selecione a ação remota do dispositivo **de ativação de ativação desativação.**
6. Aceda à secção "Hardware" do dispositivo e, em seguida, copie o **Código para ignorar o bloqueio de ativação** em **Acesso condicional**.

    >[!NOTE]
    >Copie o código para ignorar antes de limpar o dispositivo. Se repuser as definições do dispositivo antes de copiar o código, este será removido do Azure.

7. Aceda ao painel **Descrição geral** do dispositivo e, em seguida, selecione **Limpar**.
8. Depois de repor o dispositivo, é-lhe pedido o *ID Apple* e a *Palavra-passe*. Deixe o campo *ID* em branco e, em seguida, introduza o **código para ignorar** no campo *palavra-passe*. Esta ação remove a conta do dispositivo. 


## <a name="next-steps"></a>Próximos passos

Pode determinar o estado do pedido de desbloqueio na página de detalhes do dispositivo na carga de trabalho **Gerir dispositivos**.

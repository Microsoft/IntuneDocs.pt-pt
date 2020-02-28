---
title: Enviar notificações personalizadas aos utilizadores com microsoft Intune
titleSuffix: Microsoft Intune
description: Use Intune para criar e enviar notificações push personalizadas para utilizadores de dispositivos iOS/iPadOS e Android
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/27/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: remote-actions
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: jinyoon
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: afcb49447aa044b730d2271603d4966466318193
ms.sourcegitcommit: 045ca42cad6f86024af9a38a380535f42a6b4bef
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/28/2020
ms.locfileid: "77782025"
---
# <a name="send-custom-notifications-in-intune"></a>Enviar notificações personalizadas em Intune

Utilize o Microsoft Intune para enviar notificações personalizadas aos utilizadores de dispositivos geridos iOS/iPadOS e Android. Estas mensagens aparecem como notificações padrão da aplicação Portal da Empresa e da aplicação Microsoft Intune no dispositivo de um utilizador, assim como surgem notificações de outras aplicações no dispositivo. As notificações personalizadas intonizadas não são suportadas por dispositivos macOS e Windows.

As mensagens de notificação personalizadas incluem um título curto e um corpo de mensagem de 500 caracteres ou menos. Estas mensagens podem ser personalizadas para qualquer finalidade de comunicação geral.

### <a name="what-the-notification-looks-like-on-an-iosipados-device"></a>Como é a notificação num dispositivo iOS/iPadOS

Se tiver a aplicação Portal da Empresa aberta num dispositivo iOS/iPadOS, a notificação assemelha-se à seguinte imagem:

> [!div class="mx-imgBorder"]
> ![Portal da Empresa iOS/iPadOS Teste](./media/custom-notifications/105046-1.png)

Se o dispositivo estiver bloqueado, a notificação assemelha-se à seguinte imagem:

> [!div class="mx-imgBorder"]
> ![dispositivo bloqueado iOS/iPadOS Teste](./media/custom-notifications/105046-2.png)

### <a name="what-the-notification-looks-like-on-an-android-device"></a>Como é a notificação num dispositivo Android

Se tem a aplicação Portal da Empresa aberta num dispositivo Android, a notificação assemelha-se à seguinte imagem:

> [!div class="mx-imgBorder"]
> ![](./media/custom-notifications/105046-3.png) de notificação do Teste Android

## <a name="common-scenarios-for-sending-custom-notifications"></a>Cenários comuns para o envio de notificações personalizadas  

- Notifique todos os funcionários de uma mudança de horário, como o encerramento de edifícios devido ao mau tempo.
- Envie uma notificação ao utilizador de um único dispositivo para comunicar um pedido urgente, como reiniciar o dispositivo para concluir a instalação de uma atualização.

## <a name="considerations-for-using-custom-notifications"></a>Considerações para o uso de notificações personalizadas

**Configuração do dispositivo**

- Os dispositivos devem ter a aplicação Portal da Empresa ou a aplicação Microsoft Intune instalada antes de os utilizadores poderem receber notificações personalizadas. Devem também ter permissões configuradas para permitir que a aplicação Portal da Empresa ou a aplicação Microsoft Intune enviem notificações push. Se necessário, a aplicação Portal da Empresa e a aplicação Microsoft Intune podem levar os utilizadores a permitir notificações.
- No Android, o Google Play Services é uma dependência necessária.
- O dispositivo deve estar matriculado em MDM.

**Permissões:**

- Para enviar notificações a grupos, a sua conta deve ter a seguinte permissão RBAC em Intune: *Organização* > **Atualizar**.
- Para enviar notificações para um dispositivo, a sua conta deve ter a seguinte permissão RBAC em Intune: *Tarefas remotas* > **Enviar notificações personalizadas**.

**Criação de notificações:**
 
- Para criar uma mensagem, utilize uma conta que seja atribuída uma função Intune que inclua a permissão correta, conforme descrito na secção *Permissões* anteriores. Para atribuir permissões a um utilizador, consulte [as atribuições](../fundamentals/role-based-access-control.md#role-assignments)de role .
- As notificações personalizadas estão limitadas a títulos de 50 caracteres e mensagens de 500 caracteres.  
- Intune não guarda texto de notificações personalizadas previamente enviadas. Para reenviar uma mensagem, tem de recriar essa mensagem.  
- Só pode enviar até 25 mensagens para grupos por hora. Esta restrição está ao nível dos inquilinos. Esta limitação não se aplica no envio de notificações para dispositivos individuais.
- Só pode enviar até 25 mensagens para grupos por hora. Esta restrição está ao nível dos inquilinos. Esta limitação não se aplica no envio de notificações a indivíduos.
- Ao enviar mensagens para dispositivos individuais, só pode enviar até 10 mensagens por hora para o mesmo dispositivo.
- Pode enviar notificações aos utilizadores em grupos. Ao enviar notificações a grupos, cada notificação pode direcionar diretamente até 25 grupos. Grupos aninhados não contam contra este total. Ao enviar uma notificação a um grupo, as mensagens visam apenas os utilizadores do grupo e são enviadas para cada dispositivo iOS/iPadOS ou Android que o utilizador tenha registado. Os dispositivos do grupo serão ignorados quando visarem a notificação.
- Pode enviar notificações para um único dispositivo. Em vez de utilizar grupos, selecione um dispositivo e, em seguida, utilize uma ação remota do [dispositivo](device-management.md#available-device-actions) para enviar a notificação personalizada.

**Entrega:**

- Intune envia mensagens para a aplicação Portal da Empresa dos utilizadores ou para a aplicação Microsoft Intune, que cria a notificação push. Os utilizadores não precisam de ser inscritos na aplicação para que a notificação seja empurrada para o dispositivo, mas o dispositivo deve ter sido matriculado pelo utilizador visado.
- Intune, a aplicação Portal da Empresa e a aplicação Microsoft Intune não podem garantir a entrega de uma notificação personalizada. As notificações personalizadas podem aparecer após várias horas de atraso, se é que não devem ser usadas para mensagens urgentes.
- As mensagens de notificação personalizadas do Intune aparecem nos dispositivos como notificações padrão de push. Se a aplicação Portal da Empresa estiver aberta num dispositivo iOS/iPadOS quando receber a notificação, a notificação apresenta-se na aplicação em vez de como notificação push do sistema.  
- As notificações personalizadas podem ser visíveis nos ecrãs de bloqueio tanto em dispositivos iOS/iPadOS como Android, dependendo das definições do dispositivo.  
- Em dispositivos Android, outras aplicações podem ter acesso aos dados nas suas notificações personalizadas. Não os use para comunicações sensíveis.  
- Os utilizadores de um dispositivo recentemente não inscrito, ou utilizadores que foram removidos de um grupo, poderão ainda receber uma notificação personalizada que é posteriormente enviada para aquele grupo.  Da mesma forma, se adicionar um utilizador a um grupo após a notificação personalizada ter sido enviada para o grupo, é possível que a nova utilização adicionada receba a mensagem de notificação enviada anteriormente.  

## <a name="send-a-custom-notification-to-groups"></a>Enviar uma notificação personalizada a grupos

1. Inscreva-se no [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) com uma conta que tem permissões para criar e enviar notificações, e ir à **administração do Tenant** > **notificações personalizadas.**  

2. No separador Basics, especifique o seguinte e, em seguida, selecione **Next** para continuar.  
   - **Título** – Especifique um título para esta notificação. Os títulos estão limitados a 50 caracteres.  
   - **Corpo** – Especifique a mensagem. As mensagens estão limitadas a 500 caracteres.

   ![Criar uma notificação personalizada](./media/custom-notifications/custom-notifications.png)  

3. No separador **Demissões,** selecione os grupos para os quais pretende enviar esta notificação personalizada e, em seguida, selecione Next para continuar. O envio de uma notificação a um grupo visará apenas os utilizadores desse grupo; a notificação irá para todos os dispositivos iOS/iPadOS e Android matriculados por esse utilizador.

4. No separador **Review + Criar,** reveja as informações e quando estiver pronto para enviar a notificação, selecione **Criar**.  

Insintoniza as mensagens que cria imediatamente. A única confirmação de que a mensagem foi enviada é a notificação intune que confirma que a notificação personalizada foi enviada.  

![Confirmação de uma notificação enviada](./media/custom-notifications/notification-sent.png)  

Intune não rastreia as notificações personalizadas que envia, e os dispositivos não registam o recibo fora do centro de notificação do dispositivo. A notificação pode ser contida num registo de diagnóstico temporário se um utilizador solicitar apoio dentro do Portal da Empresa ou da aplicação Intune.

## <a name="send-a-custom-notification-to-a-single-device"></a>Envie uma notificação personalizada para um único dispositivo

1. Inscreva-se no [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) com uma conta que tem permissões para criar e enviar notificações e depois ir para **Dispositivos** > **Todos os dispositivos**.

2. Clique duas vezes no nome do dispositivo gerido para o qual pretende enviar uma notificação, para abrir a página *de Visualização geral* dos dispositivos.

3. Na página **'Overview'** dos dispositivos, selecione a ação do dispositivo **de notificação personalizada enviar** para abrir o painel de *notificação personalizado enviar.* Se esta opção não estiver disponível, selecione a opção **...** (elipses) do lado superior direito da página e, em seguida, selecione **Enviar Notificação Personalizada**.

4. No painel **de notificação personalizado enviar,** especifique os seguintes detalhes da mensagem:  

   - **Título** – Especifique um título para esta notificação. Os títulos estão limitados a 50 caracteres.  
   - **Corpo** – Especifique a mensagem. As mensagens estão limitadas a 500 caracteres.  

5. Selecione **Enviar** para enviar a notificação personalizada para o dispositivo. Ao contrário das notificações que envia a grupos, não configura uma atribuição nem revê a mensagem antes de a enviar.  

Insintoniza a mensagem imediatamente. A única confirmação de que a mensagem foi enviada é a notificação intune que receberá na consola, que exibe o texto da mensagem que enviou.  

## <a name="receive-a-custom-notification"></a>Receba uma notificação personalizada

Num dispositivo, os utilizadores vêem as mensagens de notificação personalizadas que são enviadas pela Intune como uma notificação padrão da aplicação Portal da Empresa ou da aplicação Microsoft Intune. Estas notificações são semelhantes às notificações push que os utilizadores recebem de outras aplicações no dispositivo.  

Nos dispositivos iOS/iPadOS, se a aplicação Portal da Empresa estiver aberta quando a notificação for recebida, a notificação apresenta-se na aplicação em vez de ser uma notificação push.  

A notificação permanece até que o utilizador a despeça.  

## <a name="next-steps"></a>Próximos passos

[Gerir dispositivos](device-management.md)

---
title: Enviar notificações personalizadas para usuários com Microsoft Intune
titleSuffix: Microsoft Intune
description: Use o Intune para criar e enviar notificações por push personalizadas para usuários de dispositivos iOS e Android
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 09/19/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: jinyoon
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: d3c21e255db1142ec5ab15c99e8da6bc41de01cf
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/02/2019
ms.locfileid: "71732452"
---
# <a name="send-custom-notifications-in-intune"></a>Enviar notificações personalizadas no Intune  

Use Microsoft Intune para enviar notificações personalizadas aos usuários de dispositivos iOS e Android gerenciados. Essas mensagens aparecem como notificações por push padrão do aplicativo Portal da Empresa e do aplicativo Microsoft Intune no dispositivo de um usuário, assim como as notificações de outros aplicativos no dispositivo são exibidas. As notificações personalizadas do Intune não têm suporte por dispositivos macOS e Windows.   

As mensagens de notificação personalizadas incluem um título curto e um corpo de mensagem de 500 caracteres ou menos. Essas mensagens podem ser personalizadas para qualquer finalidade de comunicação geral.

## <a name="common-scenarios-for-sending-custom-notifications"></a>Cenários comuns para enviar notificações personalizadas  

- Notifique todos os funcionários de uma alteração na agenda, como a criação de fechamentos devido ao clima Inclement.
- Envie uma notificação para o usuário de um único dispositivo para comunicar uma solicitação urgente, como reiniciar o dispositivo para concluir a instalação de uma atualização. 

## <a name="considerations-for-using-custom-notifications"></a>Considerações sobre o uso de notificações personalizadas

**Configuração do dispositivo** 

- Os dispositivos devem ter o aplicativo Portal da Empresa ou o aplicativo Microsoft Intune instalado antes que os usuários possam receber notificações personalizadas. Eles também devem ter configurado permissões para permitir que o aplicativo Portal da Empresa ou o aplicativo Microsoft Intune envie notificações por push. Se necessário, o aplicativo Portal da Empresa e o aplicativo Microsoft Intune podem solicitar que os usuários permitam notificações.  
- No Android, Google Play Services é uma dependência necessária.  
- O dispositivo deve ser registrado como MDM.

**Permissões**:
- Para enviar notificações aos grupos, sua conta deve ter a seguinte permissão de RBAC no Intune: > **Atualização**da organização.
- Para enviar notificações para um dispositivo, sua conta deve ter a seguinte permissão de RBAC no Intune: *As tarefas* > remotas**enviam notificações personalizadas**.

**Criando notificações**:  
- Para criar uma mensagem, use uma conta que seja atribuída a uma função do Intune que inclua a permissão **Atualizar** para a **organização**. Para atribuir permissões a um usuário, consulte [atribuições de função](../fundamentals/role-based-access-control.md#role-assignments)  
- As notificações personalizadas são limitadas a títulos de 50 caracteres e a mensagens de 500 caracteres.  
- O Intune não salva mensagens enviadas. Para reenviar uma mensagem, você deve recriar essa mensagem.  
- Você só pode enviar até 25 mensagens para grupos por hora. Essa restrição está no nível do locatário. Essa limitação não se aplica ao enviar notificações para indivíduos.
- Ao enviar mensagens para dispositivos individuais, você pode enviar até 10 mensagens por hora para o mesmo dispositivo. 
- Você pode enviar notificações para vários usuários ou dispositivos atribuindo a notificação a grupos. Ao usar grupos, cada notificação pode direcionar diretamente até 25 grupos. Grupos aninhados não contam com esse total.  

  Os grupos podem incluir usuários ou dispositivos, mas as mensagens são enviadas somente para os usuários e para cada dispositivo iOS ou Android que o usuário registrou.  
- Você pode enviar notificações para um único dispositivo. Em vez de usar grupos, você seleciona um dispositivo e, em seguida, usa uma [ação de dispositivo](device-management.md#available-device-actions) remoto para enviar a notificação personalizada.  

**Entrega**:  
- O Intune envia mensagens para o aplicativo Portal da Empresa do usuário ou para o aplicativo Microsoft Intune, que, em seguida, cria a notificação por push. Os usuários não precisam estar conectados ao aplicativo para que a notificação seja enviada por push no dispositivo.  
- O Intune, bem como o aplicativo Portal da Empresa e o aplicativo Microsoft Intune, não podem garantir a entrega de uma notificação personalizada. As notificações personalizadas podem aparecer após várias horas de atraso, se, portanto, não devem ser usadas para mensagens urgentes.  
- Mensagens de notificação personalizadas do Intune aparecem em dispositivos como notificações por push padrão. Se o aplicativo Portal da Empresa estiver aberto em um dispositivo iOS quando receber a notificação, a notificação será exibida no aplicativo, em vez de ser uma notificação por push.  
- As notificações personalizadas podem ser visíveis em telas de bloqueio em dispositivos iOS e Android, dependendo das configurações do dispositivo.  
- Em dispositivos Android, outros aplicativos podem ter acesso aos dados em suas notificações personalizadas. Não os use para comunicações confidenciais.  
- Os usuários de um dispositivo que foi recentemente cancelado, ou usuários que foram removidos de um grupo, ainda podem receber uma notificação personalizada que é enviada posteriormente para esse grupo.  Da mesma forma, se você adicionar um usuário a um grupo depois que uma notificação personalizada for enviada ao grupo, será possível que o uso recém-adicionado receba essa mensagem de notificação enviada anteriormente.  

## <a name="send-a-custom-notification-to-groups"></a>Enviar uma notificação personalizada para grupos  

1. Entre no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) com uma conta que tenha permissões para criar e enviar notificações e vá para **dispositivos** > **enviar notificações personalizadas**.  

2. Na guia noções básicas, especifique o seguinte e, em seguida, selecione **Avançar** para continuar.  
   - **Título** – especifique um título para esta notificação. Os títulos são limitados a 50 caracteres.  
   - **Corpo** – especifique a mensagem. As mensagens são limitadas a 500 caracteres.

   ![Criar uma notificação personalizada](./media/custom-notifications/custom-notifications.png)  

3. Na guia **atribuições** , selecione os grupos aos quais você deseja enviar essa notificação personalizada e, em seguida, selecione avançar para continuar.  

4. Na guia **revisar + criar** , examine as informações e, quando estiver pronto para enviar a notificação, selecione **criar**.  

O Intune processa as mensagens que você cria imediatamente. A única confirmação de que a mensagem foi enviada é a notificação do Intune que confirma que a notificação personalizada foi enviada.  

![Confirmação de uma notificação enviada](./media/custom-notifications/notification-sent.png)  

O Intune não rastreia as notificações personalizadas que você envia e os dispositivos não registram o recebimento fora do centro de notificação do dispositivo.  

## <a name="send-a-custom-notification-to-a-single-device"></a>Enviar uma notificação personalizada para um único dispositivo  

1. Entre no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) com uma conta que tenha permissões para criar e enviar notificações e, em seguida, vá para **dispositivos** > **todos os dispositivos**.  

2. Selecione o dispositivo para o qual você deseja enviar uma notificação.  

3. Na página **visão geral** de dispositivos, selecione **... Mais** opções do lado superior esquerdo da página.  

4. Selecione a ação enviar dispositivo de **notificação personalizado** para abrir o painel *enviar notificação personalizada* onde você especifica os seguintes detalhes da mensagem:  

   - **Título** – especifique um título para esta notificação. Os títulos são limitados a 50 caracteres.  
   - **Corpo** – especifique a mensagem. As mensagens são limitadas a 500 caracteres.  

5. Selecione **Enviar** para enviar a notificação personalizada para o dispositivo. Ao contrário das notificações que você envia para os grupos, você não configura uma atribuição ou revisa a mensagem antes de enviá-la.  

O Intune processa a mensagem imediatamente. A única confirmação de que a mensagem foi enviada é a notificação do Intune que você receberá no console do, que exibe o texto da mensagem enviada.  

## <a name="receive-a-custom-notification"></a>Receber uma notificação personalizada  

Em um dispositivo, os usuários veem mensagens de notificação personalizadas que são enviadas pelo Intune como uma notificação por push padrão do aplicativo Portal da Empresa ou do aplicativo Microsoft Intune. Essas notificações são semelhantes às notificações por push que os usuários recebem de outros aplicativos no dispositivo.  

Em dispositivos iOS, se o aplicativo Portal da Empresa estiver aberto quando a notificação for recebida, a notificação será exibida no aplicativo, em vez de ser uma notificação por push.  

A notificação permanece até que o usuário a descarte.  

## <a name="next-steps"></a>Passos seguintes  

[Gerir dispositivos](device-management.md)

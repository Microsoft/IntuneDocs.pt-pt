---
title: Obter um Certificado Push de MDM da Apple para o Intune
titleSuffix: ''
description: Obtenha um Certificado Push de MDM da Apple para gerir dispositivos iOS com o Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/08/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 6f67fcd2-5682-4f9c-8d74-d4ab69dc978c
ms.reviewer: tisilver
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: d15fd73a608c799745c92c4b07df4b9705d00106
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/16/2019
ms.locfileid: "72490314"
---
# <a name="get-an-apple-mdm-push-certificate"></a>Obter um certificado push de MDM da Apple

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

É preciso um certificado Push de MDM da Apple para que o Intune possa gerir dispositivos iOS e macOS. Depois de adicionar o certificado ao Intune, o utilizadores podem inscrever os seus dispositivos com:

- A aplicação Portal da Empresa.

- Os métodos de inscrição em massa da Apple, como o Programa de Registo de Aparelho, o Apple School Manager ou o Apple Configurator.

Para obter mais informações sobre as opções de inscrição, veja [Escolher como inscrever dispositivos iOS](ios-enroll.md).

Quando um certificado push expira, tem de renová-lo. Ao renovar, certifique-se de que utiliza o mesmo ID Apple que utilizou quando criou o certificado push.


## <a name="steps-to-get-your-certificate"></a>Passos para obter o seu certificado
Entre no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973), escolha **registro de dispositivo** > **registro da Apple** > **Apple MDM Push Certificate**e siga estas etapas no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).

### <a name="step-1-grant-microsoft-permission-to-send-user-and-device-information-to-apple"></a>Passo 1. conceder permissão à Microsoft para enviar informações sobre o utilizador e o dispositivo à Apple
Selecione **Concordo** para conceder permissão à Microsoft para enviar dados à Apple.

![O ecrã Configurar Certificado Push de MDM da Apple com o Push de MDM não configurado.](./media/apple-mdm-push-certificate-get/create-mdm-push-certificate.png)

### <a name="step-2-download-the-intune-certificate-signing-request-required-to-create-an-apple-mdm-push-certificate"></a>Passo 2: transferir o pedido de assinatura de certificado do Intune obrigatório para criar um Certificado Push de MDM da Apple
Selecione **Transferir o CSR** para transferir e guardar o ficheiro de pedido localmente. O ficheiro é utilizado para pedir um certificado de relação de confiança do Portal de Certificados Apple Push.

### <a name="step-3-create-an-apple-mdm-push-certificate"></a>Passo 3: criar um certificado push de MDM da Apple
Selecione **Criar o Certificado Push de MDM** para aceder ao Portal de Certificados Push da Apple. Inicie sessão com o seu ID Apple empresarial e, em seguida, clique em **Create a Certificate (Criar um Certificado)** . Selecione **Choose File (Escolher Ficheiro)** e navegue para o ficheiro de pedido de assinatura de certificado. Em seguida, selecione **Upload (Carregar)** . Na página Confirmação, selecione **Download (Transferir)** para transferir o ficheiro de certificado (.pem) e guardá-lo localmente.

> [!NOTE]
> O certificado está associado ao ID Apple utilizado para criar o mesmo. Como melhor prática, utilize um ID Apple da empresa para tarefas de gestão e certifique-se de que a caixa de correio é monitorizada por mais do que uma pessoa, como uma lista de distribuição. Nunca utilize um ID Apple pessoal.

### <a name="step-4-enter-the-apple-id-used-to-create-your-apple-mdm-push-certificate"></a>Passo 4: introduzir o ID Apple que utilizou para criar o seu certificado push de MDM da Apple
Registe este ID como um lembrete para quando precisar de renovar este certificado.

### <a name="step-5-browse-to-your-apple-mdm-push-certificate-to-upload"></a>Passo 5: navegar para o certificado push de MDM da Apple a carregar
Aceda ao ficheiro de certificado (.pem), escolha **Abrir** e, em seguida, escolha **Carregar**. Com o certificado push, o Intune pode inscrever e gerir dispositivos Apple.

## <a name="renew-apple-mdm-push-certificate"></a>Renovar um certificado push de MDM da Apple
O certificado push de MDM da Apple é válido durante um ano e tem de ser renovado anualmente para manter a gestão de dispositivos iOS e macOS. Se o seu certificado expirar, os dispositivos Apple inscritos não podem ser contactados.

O certificado está associado ao ID Apple utilizado para criar o mesmo. Renove o certificado push de MDM com o ID Apple utilizado para criar o mesmo.

1. Entre no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973), escolha **registro de dispositivo** > **registro da Apple**e, em seguida, escolha o bloco **Apple MDM Push Certificate** na área de detalhes.
2. Selecione **Transferir o CSR** para transferir e guardar o ficheiro de pedido localmente. O ficheiro é utilizado para pedir um certificado de relação de confiança do Portal de Certificados Apple Push.
3. Selecione **Criar o Certificado Push de MDM** para aceder ao Portal de Certificados Push da Apple. Encontre o certificado que pretende renovar e selecione **Renovar**.
4. No ecrã **Renovar Certificado Push**, introduza notas para ajudá-lo a identificar o certificado no futuro, selecione **Escolher Ficheiro** para navegar até ao novo ficheiro de pedido que transferiu e selecione **Carregar**.
   > [!TIP]
   > Um Certificado pode ser identificado pelo respetivo UID. Examine o **ID do Requerente** nos detalhes do certificado para encontrar a parte GUID do UID. Em alternativa, num dispositivo iOS inscrito, aceda a **Definições** > **Geral** > **Dispositivo** **Gestão** > **Perfil de Gestão** > **Mais Detalhes** > **Perfil de Gestão**. O item da segunda linha, **Tópico**, contém o GUID exclusivo que pode fazer corresponder ao certificado no portal Apple Push Certificates.
 
6. No ecrã **Confirmação**, selecione **Transferir** e guarde o ficheiro .pem localmente.
7. No [Intune](https://go.microsoft.com/fwlink/?linkid=2090973), selecione o ícone de navegação do **Apple MDM Push Certificate** , selecione o arquivo. pem baixado da Apple e escolha **carregar**.

O seu certificado push de MDM da Apple aparece como **Ativo** e tem 365 dias até expirar.
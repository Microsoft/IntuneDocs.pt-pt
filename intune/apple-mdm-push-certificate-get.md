---
title: Obter um Certificado Push de MDM da Apple
titlesuffix: Azure portal
description: "Saiba quais são os passos para obter um Certificado Push de MDM da Apple para gerir dispositivos iOS com o Intune.\""
keywords: 
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 1/29/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6f67fcd2-5682-4f9c-8d74-d4ab69dc978c
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 8fca2a1f32cd15752758802ee6ae44b8ae33b696
ms.sourcegitcommit: b982f9d50da4f958fb0c48c56ba46c8ef71500c4
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/29/2018
---
# <a name="get-an-apple-mdm-push-certificate"></a>Obter um certificado push de MDM da Apple

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

O Intune ativa a gestão de dispositivos móveis (MDM) de iPads, iPhones e computadores Mac e concede aos utilizadores acesso a aplicações e ao e-mail da empresa. É preciso um certificado Push de MDM para que o Intune possa gerir dispositivos iOS e Mac. Depois de adicionar o certificado ao Intune, os utilizadores podem instalar a aplicação Portal da Empresa para inscreverem os seus dispositivos. Também pode configurar a gestão de dispositivos iOS pertencentes à empresa com o Programa de Inscrição de Dispositivos da Apple ou inscrever os dispositivos através do Apple Configurator, por exemplo. Para obter mais informações sobre as opções de inscrição, veja [Escolher como inscrever dispositivos iOS](enrollment-method-choose-ios.md).

## <a name="steps-to-get-your-certificate"></a>Passos para obter o seu certificado
No portal do Azure, escolha **Inscrição de dispositivos** > **Inscrição Apple** **Certificado Push de MDM da Apple** e, em seguida, realize os seguintes passos no portal do Azure.

**Passo 1. Transfira o pedido de assinatura de certificado do Intune obrigatório para criar um Certificado Push de MDM da Apple.**<br>
Selecione **Transferir o CSR** para transferir e guardar o ficheiro de pedido localmente. O ficheiro é utilizado para pedir um certificado de relação de confiança do Portal de Certificados Apple Push.

  ![Captura de ecrã da janela Configurar Certificado Push de MDM sem o Certificado Push de MDM configurado.](./media/create-mdm-push-certificate.png)

**Passo 2: Crie um Certificado Push de MDM da Apple.**<br>
Selecione **Criar o Certificado Push de MDM** para aceder ao Portal de Certificados Push da Apple. Inicie sessão com o seu ID Apple empresarial e, em seguida, clique em **Create a Certificate (Criar um Certificado)**. Selecione **Choose File (Escolher Ficheiro)** e navegue para o ficheiro de pedido de assinatura de certificado. Em seguida, selecione **Upload (Carregar)**. Na página Confirmação, selecione **Download (Transferir)** para transferir o ficheiro de certificado (.pem) e guardá-lo localmente.

> [!NOTE]
> O certificado está associado ao ID Apple utilizado para criar o mesmo. Como melhor prática, utilize um ID Apple empresarial para a gestão de tarefas. Nunca utilize um ID Apple pessoal.

**Passo 3: Introduza o ID Apple que serviu para criar o seu Certificado Push de MDM da Apple.**<br>
Registe este ID como um lembrete para quando precisar de renovar este certificado.

**Passo 4: Navegue para o Certificado Push de MDM da Apple para carregar.**<br>
Aceda ao ficheiro de certificado (.pem), escolha **Abrir** e, em seguida, escolha **Carregar**. Com o certificado push, o Intune pode inscrever e gerir dispositivos Apple.

## <a name="renew-apple-mdm-push-certificate"></a>Renovar um certificado push de MDM da Apple
O certificado push de MDM da Apple é válido durante um ano e tem de ser renovado anualmente para manter a gestão de dispositivos iOS e macOS. Se o seu certificado expirar, os dispositivos Apple inscritos não podem ser contactados.

O certificado está associado ao ID Apple utilizado para criar o mesmo. Renove o certificado push de MDM com o ID Apple utilizado para criar o mesmo.

1. No portal do Azure, escolha **Inscrição de dispositivos** > **Inscrição da Apple** e, em seguida, escolha **Certificado Push de MDM da Apple**.
2. Selecione **Transferir o CSR** para transferir e guardar o ficheiro de pedido localmente. O ficheiro é utilizado para pedir um certificado de relação de confiança do Portal de Certificados Apple Push.
3. Encontre o certificado que pretende renovar e selecione **Renovar**.
4. No ecrã **Renovar Certificado Push**, introduza notas para ajudá-lo a identificar o certificado no futuro, selecione **Selecionar Ficheiro** para navegar até ao novo ficheiro de pedido que transferiu e selecione **Carregar**.
   > [!TIP]
   > Um Certificado pode ser identificado pelo respetivo UID. Examine o **ID do Requerente** nos detalhes do certificado para encontrar a parte GUID do UID. Em alternativa, num dispositivo iOS inscrito, aceda a **Definições** > **Geral** > **Dispositivo** **Gestão** > **Perfil de Gestão** > **Mais Detalhes** > **Perfil de Gestão**. O item da segunda linha, **Tópico**, contém o GUID exclusivo que pode fazer corresponder ao certificado no portal Apple Push Certificates.
 
6. No ecrã **Confirmação**, selecione **Transferir** e guarde o ficheiro .pem localmente.
7. No portal do Azure, selecione o ícone de pesquisa do **certificado push de MDM da Apple**, selecione o ficheiro .pem transferido da Apple e escolha **Carregar**.

O seu certificado push de MDM da Apple aparece como **Ativo** e tem 365 dias até expirar.

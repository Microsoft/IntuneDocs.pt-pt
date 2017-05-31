---
title: Obter um Certificado Push de MDM da Apple
titleSuffix: Intune Azure preview
description: "Pré-visualização do Azure no Intune: saiba os passos para obter um Certificado Push de MDM da Apple para gerir dispositivos iOS com o Intune."
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 03/14/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6f67fcd2-5682-4f9c-8d74-d4ab69dc978c
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: e3ff50fa65eff897147081f2ec9ab366dbf50140
ms.contentlocale: pt-pt
ms.lasthandoff: 05/23/2017


---

# <a name="get-an-apple-mdm-push-certificate"></a>Obter um certificado push de MDM da Apple

[!INCLUDE[azure_preview](./includes/azure_preview.md)]

O Intune ativa a gestão de dispositivos móveis (MDM) de iPads, iPhones e computadores Mac e concede aos utilizadores acesso a aplicações e ao e-mail da empresa. É preciso um certificado Push de MDM para que o Intune possa gerir dispositivos iOS e Mac. Depois de adicionar o certificado ao Intune, os utilizadores podem instalar a aplicação Portal da Empresa para inscreverem os seus dispositivos. Também pode configurar a gestão de dispositivos iOS pertencentes à empresa com o Programa de Inscrição de Dispositivos da Apple ou inscrever os dispositivos através do Apple Configurator, por exemplo. Para obter mais informações sobre as opções de inscrição, veja [Escolher como inscrever dispositivos iOS](enrollment-method-choose-ios.md).

## <a name="steps-to-get-your-certificate"></a>Passos para obter o seu certificado
No portal do Azure, selecione **Mais Serviços** > **Monitorização + Gestão** > **Intune**. No painel Intune, escolha **Inscrever dispositivos** > **Inscrição Apple** **Certificado Push de MDM da Apple**e, em seguida, siga os passos numerados no portal do Azure, que são apresentados abaixo.

**Passo 1. Transfira o pedido de assinatura de certificado do Intune obrigatório para criar um Certificado Push de MDM da Apple.**<br>
Selecione **Transferir o CSR** para transferir e guardar o ficheiro .csr localmente. O ficheiro .csr é utilizado para pedir um certificado de relação de confiança do Portal de Certificados Apple Push.

**Passo 2: Crie um Certificado Push de MDM da Apple.**<br>
Selecione **Criar o Certificado Push de MDM** para aceder ao Portal de Certificados Push da Apple. Inicie sessão com o ID Apple da sua empresa para criar o certificado push através do ficheiro .csr. Após selecionar **Carregar** no Portal do Certificado Push da Apple, receberá um ficheiro .json. Utilize este ficheiro para o certificado push. Conclua a transferência, regresse ao Portal de Certificados Push da Apple para obter Certificados para Servidores de Terceiros e, em seguida, escolha **Transferir**. Transfira o certificado push (ficheiro .pem) e guarde o ficheiro localmente.

> [!NOTE]
> O certificado está associado ao ID Apple utilizado para criar o mesmo. Como melhor prática, utilize um ID Apple empresarial para a gestão de tarefas. Nunca utilize um ID Apple pessoal.

**Passo 3: Introduza o ID Apple que serviu para criar o seu Certificado Push de MDM da Apple.**

**Passo 4: Navegue para o Certificado Push de MDM da Apple para carregar.**<br>
Aceda ao ficheiro de certificado (.pem), escolha **Abrir** e, em seguida, escolha **Carregar**. Com o certificado push, o Intune pode inscrever e gerir dispositivos iOS ao enviar políticas para dispositivos móveis inscritos.

## <a name="renew-apple-mdm-push-certificate"></a>Renovar um certificado push de MDM da Apple
O certificado push de MDM da Apple é válido durante um ano e tem de ser renovado anualmente para manter a gestão de dispositivos iOS e macOS. Se o seu certificado expirar, os dispositivos Apple inscritos não podem ser contactados.

O certificado está associado ao ID Apple utilizado para criar o mesmo. Renove o certificado push de MDM com o ID Apple utilizado para criar o mesmo.

> [!NOTE]
> O certificado está associado ao ID Apple utilizado para criar o mesmo. Como melhor prática, utilize um ID Apple empresarial para a gestão de tarefas. Nunca utilize um ID Apple pessoal.

1. No [portal do Intune no Azure](https://portal.azure.com), selecione **Inscrição de dispositivos** > **Inscrição da Apple** e, em seguida, selecione **Certificado Push de MDM da Apple**.
2. Selecione **Transferir o CSR** para transferir e guardar o ficheiro .csr localmente. O ficheiro .csr é utilizado para pedir um certificado de relação de confiança do Portal de Certificados Apple Push.
3. Encontre o certificado que pretende renovar e selecione **Renovar**.
4. No ecrã **Renovar Certificado Push**, introduza notas para ajudá-lo a identificar o certificado no futuro, selecione **Escolher Ficheiro** para navegar até ao novo ficheiro .csr que transferiu e selecione **Carregar**.
5. No ecrã **Confirmação**, selecione **Transferir** e guarde o ficheiro .pem localmente.
6. No portal do Intune no Azure, selecione o ícone de pesquisa do **certificado push de MDM da Apple**, selecione o ficheiro .pem transferido da Apple e selecione **Carregar**.

O seu certificado push de MDM da Apple aparece como **Ativo** e tem 365 dias até expirar.


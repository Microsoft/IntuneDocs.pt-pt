---
title: "Obter um Certificado Push de MDM da Apple | Pré-visualização do Azure no Intune | Documentos da Microsoft"
description: "Pré-visualização do Azure no Intune: saiba os passos para obter um Certificado Push de MDM da Apple para gerir dispositivos iOS com o Intune."
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 12/07/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6f67fcd2-5682-4f9c-8d74-d4ab69dc978c
ms.reviewer: dagerrit
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 990062ecf03a117dad74eb71e3f40abb79f22be6
ms.openlocfilehash: c0884ded1c8c55bb1b7968e483864b42f5bd6bde


---

# <a name="get-an-apple-mdm-push-certificate"></a>Obter um Certificado Push de MDM da Apple 

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

O Intune permite a gestão de dispositivos móveis (MDM), como iPads, iPhones e dispositivos Mac OS X e concede aos utilizadores acesso a aplicações e e-mail empresariais. É necessário um certificado do serviço Apple Push Notification (APNs) para que o Intune possa gerir dispositivos iOS e Mac. Depois de adicionar o certificado ao Intune, os utilizadores podem instalar a aplicação Portal da Empresa para inscrever os dispositivos deles ou pode configurar a gestão de dispositivos iOS pertencentes à empresa.

**Para obter um Certificado Push de MDM:**<br>

No portal do Azure, escolha **Mais Serviços**, introduza **Intune** na caixa de texto e, em seguida, escolha **Outros** > **Intune**. No painel Intune, escolha **Inscrever dispositivos** > **Certificado Push de MDM da Apple** e, em seguida, siga os passos numerados no portal do Azure, que são apresentados abaixo.

**Passo 1. Transfira o pedido de assinatura de certificado do Intune obrigatório para criar um Certificado Push de MDM da Apple.**<br>
Selecione **Transferir o CSR** para transferir e guardar o ficheiro .csr localmente. O ficheiro .csr é utilizado para pedir um certificado de relação de confiança do Portal de Certificados Apple Push.

**Passo 2: Crie um Certificado Push de MDM da Apple.**<br>
Selecione **Criar o Certificado Push de MDM** para aceder ao Portal de Certificados Push da Apple. Inicie sessão com o seu ID Apple da empresa para criar o certificado push através do ficheiro .csr. Após selecionar **Carregar** no Portal do Certificado Push da Apple, receberá um ficheiro .json. Utilize este ficheiro para o certificado push. Conclua a transferência, regresse ao Portal de Certificados Push da Apple para obter Certificados para Servidores de Terceiros e, em seguida, escolha **Transferir**. Transfira o certificado push (ficheiro .pem) e guarde o ficheiro localmente.
Nota

**Passo 3: Introduza o ID Apple que serviu para criar o seu Certificado Push de MDM da Apple.**

**Passo 4: Navegue para o Certificado Push de MDM da Apple para carregar.**<br>
Aceda ao ficheiro de certificado (.pem), escolha **Abrir** e, em seguida, escolha **Carregar**. Com o certificado push, o Intune pode inscrever e gerir dispositivos iOS ao enviar políticas para dispositivos móveis inscritos.



<!--HONumber=Feb17_HO1-->



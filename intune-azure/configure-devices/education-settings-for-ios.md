---
title: "Configurar as definições de educação do Intune para iOS"
titleSuffix: Intune Azure preview
description: "Pré-visualização do Azure no Intune: saiba mais sobre as definições que pode utilizar para controlar as definições de educação em dispositivos iOS."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 01/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 44c427f8-0f22-43c2-8c29-e0f9fa533b1f
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 153cce3809e24303b8f88a833e2fc7bdd9428a4a
ms.openlocfilehash: 8d801c0b264e95348f55b1d4046c00e43ead5d10
ms.lasthandoff: 02/18/2017


---

# <a name="how-to-configure-intune-education-settings-for-ios-devices-in-intune-azure-preview"></a>Como configurar definições de educação do Intune para dispositivos iOS na pré-visualização do Azure no Intune

[!INCLUDE[azure_preview](../includes/azure_preview.md)]


## <a name="create-a-device-profile-containing-ios-education-settings"></a>Criar um perfil de dispositivo com as definições de educação do iOS

1. Inicie sessão no portal do Azure.
2. Escolha **Mais Serviços** > **Outros** > **Intune**.
3. No painel **Intune**, escolha **Configurar dispositivos**.
2. No painel **Configuração do Dispositivo**, selecione **Gerir** > **Perfis**.
3. No painel de perfis, escolha **Criar Perfil**.
4. No painel **Criar Perfil**, introduza um **Nome** e uma **Descrição** para o perfil de atualização da edição.
5. Na lista pendente **Plataforma**, selecione **iOS**.
6. Na lista pendente **Tipo de perfil**, escolha **Educação**.
7. No painel **Educação**, selecione o seguinte:
    - **Ficheiro de certificado de raiz do professor**
    - **Perfil PKCS12/PFX do professor**
    - **Ficheiro de certificado de raiz do estudante**
    - **Perfil PKCS12/PFX do estudante**
8. Quando tiver terminado, volte ao painel **Criar Perfil** e clique em **Criar**.

O perfil será criado e é apresentado no painel da lista de perfis.


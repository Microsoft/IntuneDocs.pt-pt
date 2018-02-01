---
title: "Definições personalizadas do Intune para dispositivos Android"
titleSuffix: Azure portal
description: "Saiba quais são as definições que pode utilizar num perfil personalizado do Android.\""
keywords: 
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 09/18/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 494b3892-916e-4b40-9b67-61adec889bdf
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 293137705fc8d5a37ac0dd7101a7ce80c9f7e917
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/25/2018
---
# <a name="custom-settings-for-android-devices-in-microsoft-intune"></a>Definições personalizadas para dispositivos Android no Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Utilize o perfil **Personalizado** para Android do Microsoft Intune para atribuir as definições OMA-URI que podem servir para controlar as funcionalidades nos dispositivos Android. Tratam-se de definições padrão utilizadas por inúmeros fabricantes de dispositivos móveis para controlar as funcionalidades dos dispositivos.

Esta funcionalidade destina-se a permitir a atribuição das seguintes definições do Android que não são configuráveis com as políticas do Intune:

- [Utilizar um perfil de dispositivo personalizado do Microsoft Intune para criar um perfil Wi-Fi com uma chave pré-partilhada](/intune/wi-fi-profile-shared-key)
- [Utilizar um perfil personalizado do Microsoft Intune para criar um perfil VPN por aplicação para dispositivos Android](/intune/android-pulse-secure-per-app-vpn)
- [Utilizar políticas personalizadas para permitir e bloquear aplicações para dispositivos Samsung Knox Standard no Microsoft Intune](/intune/samsung-knox-apps-allow-block)

>[!IMPORTANT]
>Atualmente, apenas as definições apresentadas acima podem ser configuradas por este tipo de perfil. Os dispositivos Android não expõem uma lista completa das definições OMA-URI que pode configurar. Se quiser que sejam adicionadas mais definições, faça um pedido das mesmas no [site do UserVoice do Intune](https://microsoftintune.uservoice.com/forums/291681-ideas).

## <a name="custom-profile-settings-for-android-devices"></a>Definições de perfil personalizado para dispositivos Android

1. Utilize as instruções em [Como configurar definições personalizadas dos dispositivos no Microsoft Intune](custom-settings-configure.md) para começar.
2. No painel **Criar Perfil**, escolha **Definições** para adicionar uma ou mais definições OMA-URI.
3. No painel **Editar Linha**, configure os seguintes valores para cada definição:
    - **Nome** – Introduza um nome exclusivo para a definição OMA-URI para o ajudar a identificá-la na lista de definições.
    - **Descrição** – Introduza uma descrição geral da definição e outras informações relevantes para o ajudar a localizá-la.
    - **Tipo de dados** – Selecione o tipo de dados em que especificará esta definição OMA-URI. Escolha entre **Cadeia**, **Cadeia (XML)**, **Data e hora**, **Número inteiro**, **Vírgula flutuante** ou **Booleano**.
    - **OMA-URI** – Especifique o OMA-URI para o qual pretende fornecer uma definição.
    - **Valor** – Introduza o valor que quer associar ao OMA-URI que introduziu.
4. Clique em **OK** quando tiver terminado e, em seguida, continue a adicionar mais definições, conforme necessário.

## <a name="next-steps"></a>Próximos passos

Quando concluir as definições, o perfil será criado e apresentado no painel da lista de perfis. Se quiser continuar e atribuir este perfil a grupos, veja [Como atribuir perfis de dispositivo](device-profile-assign.md).





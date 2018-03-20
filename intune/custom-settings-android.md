---
title: "Adicionar definições personalizadas para dispositivos Android no Microsoft Intune – Azure | Microsoft Docs"
description: "Adicionar ou criar um perfil personalizado para dispositivos Android para criar um perfil Wi-Fi com uma chave pré-partilhada, criar um perfil de VPN por aplicação ou permitir/bloquear aplicações para dispositivos Samsung Knox Standard no Microsoft Intune"
keywords: 
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/07/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 494b3892-916e-4b40-9b67-61adec889bdf
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: aa105cc96cd0fa7d8c6beb32cdb80b7782d9828c
ms.sourcegitcommit: 9cf05d3cb8099e4a238dae9b561920801ad5cdc6
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/09/2018
---
# <a name="custom-settings-for-android-devices---intune"></a>Definições personalizadas para dispositivos Android – Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Os perfis personalizados utilizam as definições Open Mobile Alliance Uniform Resource Identifier (OMA-URI) para configurar diferentes funcionalidades em dispositivos Android. Estas definições são normalmente utilizadas por fabricantes de dispositivos móveis para controlar as funcionalidades no dispositivo.

A utilização de um perfil personalizado permite configurar e atribuir as seguintes definições do Android. Estas definições não estão incorporadas nas políticas do Intune:

- [Criar um perfil Wi-Fi com uma chave pré-partilhada](/intune/wi-fi-profile-shared-key)
- [Criar um perfil de VPN por aplicação](/intune/android-pulse-secure-per-app-vpn)
- [Permitir e bloquear aplicações para dispositivos Samsung Knox Standard](/intune/samsung-knox-apps-allow-block)

>[!IMPORTANT]
> Este tipo de perfil só pode configurar as definições listadas. Os dispositivos Android não expõem uma lista completa das definições OMA-URI que pode configurar. Se quiser ver mais definições, contribua com o seu voto para a adição de mais definições no [site do UserVoice do Intune](https://microsoftintune.uservoice.com/forums/291681-ideas).

## <a name="custom-profile-settings-for-android-devices"></a>Definições de perfil personalizado para dispositivos Android

1. Inicie sessão no [portal do Azure](https://portal.azure.com). 
2. Selecione **Todos os Serviços**, filtre por **Intune** e selecione **Microsoft Intune**.
3. Crie um perfil personalizado com a plataforma Android. O tópico [Configurar as definições personalizadas dos dispositivos no Microsoft Intune](custom-settings-configure.md) apresenta a lista de passos.
4. Em **Definições personalizadas de OMA-URI**, selecione **Adicionar** e, em seguida, selecione **Adicionar Linha**.
5. Introduza as seguintes propriedades:

  - **Nome** – introduza um nome exclusivo para a definição de OMA-URI para poder encontrá-la facilmente.
  - **Descrição** – introduza uma descrição que lhe permita obter uma descrição geral da definição e outros detalhes importantes.
  - **Tipo de dados** – introduza o tipo de dados que utiliza para esta definição de OMA-URI. Escolha entre **Cadeia**, **Cadeia (XML)**, **Data e hora**, **Número inteiro**, **Vírgula flutuante** ou **Booleano**.
  - **OMA-URI** – introduza o OMA-URI que pretende.
  - **Valor** – Introduza o valor que quer associar ao OMA-URI que introduziu.

6. Selecione **OK** para guardar as alterações. Continue a adicionar mais definições conforme necessário.

## <a name="next-steps"></a>Próximos passos

Quando concluir as definições, o perfil será criado e apresentado na lista. Para atribuir este perfil a grupos, veja [Como atribuir perfis de dispositivo](device-profile-assign.md).

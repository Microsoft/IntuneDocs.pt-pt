---
title: Adicionar definições personalizadas a dispositivos Android no Microsoft Intune – Azure | Microsoft Docs
description: Adicionar ou criar um perfil personalizado para dispositivos Android para criar um perfil Wi-Fi com uma chave pré-partilhada, criar um perfil de VPN por aplicação ou permitir/bloquear aplicações para dispositivos Samsung Knox Standard no Microsoft Intune
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/24/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 494b3892-916e-4b40-9b67-61adec889bdf
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 74d23c8433c741927f28bb1d6b9f55393e38f7db
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/20/2018
ms.locfileid: "52182980"
---
# <a name="use-custom-settings-for-android-devices-in-microsoft-intune"></a>Utilizar definições personalizadas para dispositivos Android no Microsoft Intune

Ao utilizar o Microsoft Intune, pode adicionar ou criar definições personalizadas para os seus dispositivos Android com um "perfil personalizado". Os perfis personalizados são uma funcionalidade do Intune. Foram concebidos para adicionar definições e funcionalidades de dispositivos que não estão incorporadas Intune.

Os perfis personalizados do Android utilizam as definições Open Mobile Alliance Uniform Resource Identifier (OMA-URI) para configurar diferentes funcionalidades em dispositivos Android. Estas definições são normalmente utilizadas por fabricantes de dispositivos móveis para controlar essas funcionalidades.

A utilização de um perfil personalizado permite configurar e atribuir as seguintes definições do Android. As seguintes definições não estão incorporadas no Intune:

- [Criar um perfil Wi-Fi com uma chave pré-partilhada](/intune/wi-fi-profile-shared-key)
- [Criar um perfil de VPN por aplicação](/intune/android-pulse-secure-per-app-vpn)
- [Permitir e bloquear aplicações para dispositivos Samsung Knox Standard](/intune/samsung-knox-apps-allow-block)

>[!IMPORTANT]
> Apenas as definições apresentadas podem ser configuradas por um perfil personalizado. Os dispositivos Android não expõem uma lista completa das definições OMA-URI que pode configurar. Se quiser ver mais definições, contribua com o seu voto para a adição de mais definições no [site do UserVoice do Intune](https://microsoftintune.uservoice.com/forums/291681-ideas).

Este artigo mostra-lhe como criar um perfil personalizado para dispositivos Android.

## <a name="create-the-profile"></a>Criar o perfil

1. No [portal do Azure](https://portal.azure.com), selecione **Todos os serviços**, filtre o **Intune** e selecione **Microsoft Intune**.
2. Selecione **Configuração do dispositivo** > **Perfis** > **Criar perfil**.
3. Introduza as seguintes definições:

    - **Nome**: introduza um nome para o perfil, como `android custom profile`.
    - **Descrição:** introduza uma descrição para o perfil.
    - **Plataforma**: selecione **Android**.
    - **Tipo de perfil**: selecione **Personalizado**.

4. Em **Definições OMA-URI Personalizadas**, selecione **Adicionar**. Introduza as seguintes definições:

    - **Nome**: introduza um nome exclusivo para a definição OMA-URI, para poder encontrá-la facilmente.
    - **Descrição**: introduza uma descrição que lhe permita obter uma descrição geral da definição e outros detalhes importantes.
    - **OMA-URI**: introduza o OMA-URI que quer utilizar como uma definição.
    - **Tipo de dados**: selecione o tipo de dados que irá utilizar para esta definição OMA-URI. As opções são:

      - Cadeia
      - Cadeia (ficheiro XML)
      - Data e Hora
      - Número inteiro
      - Vírgula flutuante
      - Booleano
      - Base64 (ficheiro)

    - **Valor**: introduza o valor de dados que pretende associar à definição OMA-URI que introduziu. O valor depende do tipo de dados que selecionou. Por exemplo, se optar por **Data e hora**, selecione o valor num seletor de datas.

    Depois de adicionar algumas definições, pode selecionar **Exportar**. A opção **Exportar** cria uma lista de todos os valores que adicionou num ficheiro de valores separados por vírgulas (.csv).

5. Selecione **OK** para guardar as alterações. Continue a adicionar mais definições conforme necessário. 
6. Quanto terminar, selecione **OK** > **Criar** para criar o perfil do Intune. Depois de criado, o perfil é apresentado na lista **Configuração do dispositivo – Perfis**.

## <a name="next-steps"></a>Passos Seguintes

O perfil está criado, mas ainda não está ativo. Em seguida, [atribua o perfil](device-profile-assign.md).

Saiba como [criar o perfil em dispositivos Android Enterprise](custom-settings-android-for-work.md).

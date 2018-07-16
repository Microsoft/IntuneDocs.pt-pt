---
title: Definições de perfil personalizado do Intune para perfis de trabalho do Android
titlesuffix: Microsoft Intune
description: Saiba como criar definições de perfil personalizado do Microsoft Intune para dispositivos com perfil de trabalho do Android.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/12/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 4724d6e5-05e5-496c-9af3-b74f083141f8
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 109c50acf194598017aa507a0979ad3b9298de9e
ms.sourcegitcommit: 98b444468df3fb2a6e8977ce5eb9d238610d4398
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/07/2018
ms.locfileid: "37905296"
---
# <a name="create-intune-custom-profile-settings-for-android-work-profile-devices"></a>Criar definições de perfil personalizado do Intune para dispositivos com perfil de trabalho do Android

Utilize a política de configuração personalizada de perfis de trabalho do Android do Intune para atribuir as definições OMA-URI que podem ser utilizadas para controlar as funcionalidades nos dispositivos com perfil de trabalho do Android. Tratam-se de definições padrão utilizadas por inúmeros fabricantes de dispositivos móveis para controlar as funcionalidades dos dispositivos.

Esta capacidade destina-se a permitir a atribuição de definições do Android que não são configuráveis com as políticas do Intune. Atualmente, o Intune suporta um número limitado de políticas personalizadas do Android. Veja os exemplos neste artigo para saber quais as políticas que pode configurar.

## <a name="create-a-custom-profile"></a>Criar um perfil personalizado

1. Utilize as instruções em [Como configurar as definições personalizadas dos dispositivos](custom-settings-configure.md) para começar. Em **Plataforma**, selecione **Android Enterprise** e, em **Tipo de perfil**, selecione **Personalizado**.
2. No painel **Definições de OMA-URI Personalizadas**, escolha **Adicionar** para adicionar uma nova definição.
3. No painel **Adicionar Linha**, configure o seguinte:
    - **Nome** – introduza um nome exclusivo para as definições personalizadas do perfil de trabalho do Android para o ajudar a identificá-lo no portal do Azure.
    - **Descrição** – indique uma descrição geral da política personalizada do Android e outras informações relevantes que o ajudem a localizá-la.
    - **OMA-URI** – introduza o OMA-URI para o qual pretende indicar uma definição.
    - **Tipo de dados** – Selecione o tipo de dados em que especificará esta definição OMA-URI. Escolha entre **Cadeia**, **Cadeia (ficheiro XML)**, **Data e hora**, **Número inteiro**, **Vírgula flutuante**, **Booleano** ou **Base64 (ficheiro)**.
    - **Valor** – especifique o valor a associar ao OMA-URI especificado anteriormente. O método que utilizar para indicar este valor irá variar de acordo com o tipo de dados que selecionou. Por exemplo, se optou por **Data e hora**, deverá selecionar o valor num seletor de datas.
4. Quando tiver terminado, escolha OK para regressar às **Definições de OMA-URI Personalizadas** e, em seguida, adicione mais definições ou escolha **Criar** para criar o perfil personalizado.


## <a name="example"></a>Exemplo

Neste exemplo, irá criar um perfil personalizado que pode ser utilizado para restringir se são permitidas ações de copiar e colar entre as aplicações de trabalho e pessoais em dispositivos com perfil de trabalho do Android.

1. Utilize o procedimento neste artigo para criar um perfil personalizado para dispositivos com perfil de trabalho do Android com os seguintes valores:
    - **Nome** – introduza “Bloquear copiar e colar” ou texto à sua escolha.
    - **Descrição** – introduza “Bloqueia copiar/colar entre as aplicações de trabalho e pessoais” ou texto à sua escolha.
    - **OMA-URI** – introduza **./Vendor/MSFT/WorkProfile/DisallowCrossProfileCopyPaste**.
    - **Tipo de dados** – selecione **Booleano** para indicar que o valor deste OMA-URI é **Verdadeiro** ou **Falso**.
    - **Valor** – selecione **Verdadeiro**.
2. Deverá resultar numa definição com um aspeto semelhante a esta imagem.
![Bloquear ações de copiar e colar para perfis de trabalho do Android.](./media/custom-policy-afw-copy-paste.png)
3. Agora, quando atribuir este perfil personalizado aos dispositivos com perfil de trabalho do Android que gerir, as ações de copiar e colar serão bloqueadas entre as aplicações nos perfis de trabalho e pessoais.
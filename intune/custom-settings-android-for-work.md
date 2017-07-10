---
title: "Definições de perfil personalizado do Intune para Android for Work"
titleSuffix: Intune on Azure
description: "Saiba como criar definições de perfil personalizado do Intune para dispositivos Android for Work.\""
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 04/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4724d6e5-05e5-496c-9af3-b74f083141f8
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 1b48fc7bd784b5d6d531ef5bf28fe835e394b106
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/01/2017
---
# <a name="create-intune-custom-profile-settings-for-android-for-work-devices"></a>Criar definições de perfil personalizado do Intune para dispositivos Android for Work

Utilize a política de configuração personalizada para Android for Work do Intune para atribuir as definições OMA-URI que podem ser utilizadas para controlar as funcionalidades nos dispositivos Android for Work. Tratam-se de definições padrão utilizadas por inúmeros fabricantes de dispositivos móveis para controlar as funcionalidades dos dispositivos.

Esta capacidade destina-se a permitir a atribuição de definições do Android que não são configuráveis com as políticas do Intune. Atualmente, o Intune suporta um número limitado de políticas personalizadas do Android. Consulte os exemplos neste tópico para saber quais as políticas que pode configurar.

## <a name="create-a-custom-profile"></a>Criar um perfil personalizado

1. Utilize as instruções em [Como configurar as definições personalizadas dos dispositivos](custom-settings-configure.md) para começar.
2. No painel **Definições de OMA-URI Personalizadas**, escolha **Adicionar** para adicionar uma nova definição.
3. No painel **Adicionar Linha**, configure o seguinte:
    - **Nome** – introduza um nome exclusivo para as definições personalizadas do Android for Work para o ajudar a identificá-lo no portal do Intune.
    - **Descrição** – indique uma descrição geral da política personalizada do Android e outras informações relevantes que o ajudem a localizá-la.
    - **OMA-URI** – introduza o OMA-URI para o qual pretende indicar uma definição.
    - **Tipo de dados** – Selecione o tipo de dados em que especificará esta definição OMA-URI. Escolha entre **Cadeia**, **Cadeia (ficheiro XML)**, **Data e hora**, **Número inteiro**, **Vírgula flutuante**, **Booleano** ou **Base64 (ficheiro)**.
    - **Valor** – especifique o valor a associar ao OMA-URI especificado anteriormente. O método que utilizar para indicar este valor irá variar de acordo com o tipo de dados que selecionou. Por exemplo, se optou por **Data e hora**, deverá selecionar o valor num seletor de datas.
4. Quando tiver terminado, escolha OK para regressar às **Definições de OMA-URI Personalizadas** e, em seguida, adicione mais definições ou escolha **Criar** para criar o perfil personalizado.


## <a name="example"></a>Exemplo

Neste exemplo, vai criar um perfil personalizado que pode servir para restringir se são permitidas ações de copiar e colar entre as aplicações de trabalho e pessoais em dispositivos Android for Work geridos.

1. Utilize o procedimento neste tópico para criar um perfil personalizado para dispositivos Android for Work com os seguintes valores:
    - **Nome** – introduza “Bloquear copiar e colar” ou texto à sua escolha.
    - **Descrição** – introduza “Bloqueia copiar/colar entre as aplicações de trabalho e pessoais” ou texto à sua escolha.
    - **OMA-URI** – introduza **./Vendor/MSFT/WorkProfile/DisallowCrossProfileCopyPaste**.
    - **Tipo de dados** – selecione **Booleano** para indicar que o valor deste OMA-URI é **Verdadeiro** ou **Falso**.
    - **Valor** – selecione **Verdadeiro**.
2. Deverá resultar numa definição com um aspeto semelhante a esta imagem.
![Bloquear copiar e colar para o Android for Work.](./media/custom-policy-afw-copy-paste.png)
3. Agora, quando atribuir este perfil personalizado aos dispositivos Android for Work que gerir, as ações de copiar e colar serão bloqueadas entre as aplicações nos perfis de trabalho e pessoais.
---
title: "Utilizar políticas de configuração da aplicação para dispositivos móveis Android for Work | Microsoft Intune"
description: "Utilize políticas de configuração de aplicações móveis no Intune para disponibilizar definições que poderão ser necessárias quando os utilizadores executarem uma aplicação do Android for Work."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 10/12/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: fc6b645a-e837-4b2a-a10f-144065cbd8dd
ms.reviewer: chrisbal
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 32bded5047b1a08738418e3e36382eeae1a5f3b4
ms.openlocfilehash: a986e859e38e0936f53c57a75872dc86de3ee181


---

# Configurar as aplicações do Android for Work com as políticas de configuração de aplicações móveis no Microsoft Intune
Utilize políticas de configuração de aplicações móveis no Microsoft Intune para disponibilizar definições que poderão ser necessárias quando os utilizadores executarem uma aplicação. Por exemplo, uma aplicação poderá exigir que os utilizadores especifiquem:

-   Um número de porta personalizado.

-   Definições de idioma.

-   Definições de imagem corporativa, como um logótipo de empresa.

Se os utilizadores introduzirem estas definições incorretamente, isso pode aumentar a carga sobre o suporte técnico e tornar mais lenta a adoção de novas aplicações.

As políticas de configuração de aplicações móveis podem ajudar a eliminar estes problemas, permitindo-lhe implementar estas definições aos utilizadores antes de executarem a aplicação. As definições são então fornecidas automaticamente e os utilizadores não têm de executar nenhuma ação.

Para utilizar as políticas de configuração de aplicação, é necessário que o programador da aplicação tenha exposto as configurações empresariais da aplicação quando a criou. Por exemplo, o Google Chrome expõe definições que lhe permitem predefinir marcadores, sites permitidos e não permitidos, entre outras funcionalidades. Contacte o programador da aplicação para saber se estas definições são suportadas e como as especificar na política.

A implementação da política de configuração da aplicação é feita aos mesmos utilizadores a quem implementou a aplicação que quer configurar. As definições de política serão utilizadas sempre que a aplicação for executada.

## Configurar uma política de configuração de aplicações móveis

1.  Na [consola de administração do Microsoft Intune](https://manage.microsoft.com), selecione **Política** &gt; **Descrição Geral** &gt; **Adicionar Política**.

2.  Na lista de políticas, expanda **Android for Work**, selecione **Configuração de Política de Aplicação Móvel(Android for Work)** e, em seguida, selecione **Criar Política**.

    > [!TIP]
    > Apenas pode configurar definições personalizadas para este tipo de política. As definições recomendadas não estão disponíveis.

3.  Na secção **Geral** da página **Criar Política** , forneça um nome e uma descrição opcional para a política de configuração de aplicação móvel.

4. Na secção **Configuração de Política de Aplicação Móvel** da página, especifique as informações seguintes:
    - **ID do pacote da aplicação a que esta configuração se aplica** – pode encontrar o ID do pacote na secção "id=" do URL da aplicação na respetiva página do Google Play. Por exemplo, o ID do pacote da aplicação Microsoft Excel é **com.microsoft.office.excel**.
    - Na caixa de texto, introduza os dados das definições da aplicação que quer configurar. Obtém estas definições do fornecer da aplicação. Nem todas as aplicações suportam estas definições.
5.  Clique em **Validar** para se certificar de que os dados que introduziu estão num formato de lista de propriedades válido.

    > [!IMPORTANT]
    > Quando clica em **Validar**, o Intune verifica se os dados de configuração que introduziu se encontram num formato válido. Verifica se os dados irão funcionar com a aplicação à qual estão associados.

6.  Quando terminar, clique em **Guardar Política**.

A nova política é apresentada no nó **Políticas de Configuração** .


## Implementar a política de configuração da aplicação
Após criar a política de configuração da aplicação, tem de a implementar aos mesmos utilizadores a quem implementou a aplicação à qual as definições serão aplicadas.

Para mais informações sobre como implementar políticas, consulte [implementar uma política de configuração](/intune/deploy-use/manage-settings-and-features-on-your-devices-with-microsoft-intune-policies#deploy-a-configuration-policy)

Para mais informações sobre como implementar aplicações em dispositivos com o Android for Work, consulte [Como implementar aplicações do Android for Work com o Intune](android-for-work-apps.md).

Quando a aplicação implementada for executada num dispositivo, será executada com as definições que configurou na política de configuração de aplicação móvel.

> [!TIP]
> Implemente apenas uma política de configuração de aplicação por cada aplicação para um utilizador.







<!--HONumber=Oct16_HO2-->



---
title: "Utilizar políticas de configuração de aplicações móveis iOS"
description: "Utilize políticas de configuração de aplicações móveis no Intune para disponibilizar definições que poderão ser necessárias quando os utilizadores executarem uma aplicação iOS."
keywords: 
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 12/27/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: fc6b645a-e837-4b2a-a10f-144065cbd8dd
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 7dd73ecbba6c10cbbec92bdf4e856bf15434aea9
ms.sourcegitcommit: 769db6599d5eb0e2cca537d0f60a5df9c9f05079
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/15/2017
---
# <a name="configure-ios-apps-with-mobile-app-configuration-policies-in-microsoft-intune"></a>Configurar aplicações iOS com políticas de configuração de aplicações móveis no Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Utilize políticas de configuração de aplicações móveis no Microsoft Intune para disponibilizar definições que poderão ser necessárias quando os utilizadores executarem uma aplicação. Por exemplo, uma aplicação poderá exigir que os utilizadores especifiquem:

-   Um número de porta personalizado.

-   Definições de idioma.

-   Definições de segurança.

-   Definições de imagem corporativa, como um logótipo de empresa.

Se os utilizadores introduzirem estas definições incorretamente, isso pode aumentar a carga sobre o suporte técnico e tornar mais lenta a adoção de novas aplicações.

As políticas de configuração de aplicações móveis podem ajudar a eliminar estes problemas, permitindo-lhe implementar estas definições aos utilizadores de uma política antes de executarem a aplicação. As definições são então fornecidas automaticamente e os utilizadores não têm de executar nenhuma ação.

Não implemente estas políticas diretamente a utilizadores nem a dispositivos. Em alternativa, associe uma política à aplicação e, em seguida, implemente-a. As definições de política serão utilizadas sempre que a aplicação as verificar (normalmente, a primeira vez for executada).

> [!TIP]
> Este tipo de política está atualmente disponível apenas para dispositivos com o iOS 8.0 e posterior. Suporta os seguintes tipos de instalação de aplicações:
>
> -   **Aplicação iOS gerida da loja de aplicações**
> -   **Pacote de aplicações para iOS**
>
> Para mais informações sobre os tipos de instalação de aplicações, consulte [Implementar aplicações com o Microsoft Intune](deploy-apps.md).

## <a name="configure-a-mobile-app-configuration-policy"></a>Configurar uma política de configuração de aplicações móveis

1.  Na [consola de administração do Microsoft Intune](https://manage.microsoft.com), selecione **Política** &gt; **Descrição Geral** &gt; **Adicionar Política**.

2.  Na lista de políticas, expanda **iOS**, escolha **Configuração de Aplicação Móvel**, e, em seguida, escolha **Criar Política**.

    > [!TIP]
    > Apenas pode configurar definições personalizadas para este tipo de política. As definições recomendadas não estão disponíveis.

3.  Na secção **Geral** da página **Criar Política**, forneça um nome e uma descrição opcional para a política de configuração de aplicação móvel.

4.  Na secção **Política de Configuração de Aplicação Móvel** da página, introduza ou cole uma lista de propriedades XML que contenha as definições de configuração de aplicação que pretende. O formato da lista de propriedades de XML irá variar em função da aplicação que está a configurar. Contacte o fornecedor da aplicação para obter detalhes sobre o formato exato a utilizar.

    > [!TIP]
    > Para saber mais sobre listas de propriedades XML, consulte [Compreender Listas de Propriedades XML](https://developer.apple.com/library/ios/documentation/Cocoa/Conceptual/PropertyLists/UnderstandXMLPlist/UnderstandXMLPlist.html) na iOS Developer Library.

5.  Clique em **Validar** para se certificar de que o XML que introduziu está num formato de lista de propriedades válido.

    > [!IMPORTANT]
    > Quando clica em **Validar**, o Intune verifica se o XML que introduziu está num formato válido. Não verifica se a lista de propriedades do XML irá funcionar com a aplicação à qual está associada.

6.  Quando terminar, clique em **Guardar Política**.

A nova política é apresentada no nó **Políticas de Configuração**.

## <a name="information-about-the-xml-file-format"></a>Informações sobre o formato de ficheiro XML

O Intune suporta os seguintes tipos de dados numa lista de propriedades:
    
- &lt;número inteiro&gt;
- &lt;real&gt;
- &lt;cadeia&gt;
- &lt;matriz&gt;
- &lt;dict&gt;
- &lt;verdadeiro /&gt; ou &lt;falso /&gt;
     
Para obter mais informações sobre tipos de dados, veja [Sobre Listas de Propriedades](https://developer.apple.com/library/ios/documentation/Cocoa/Conceptual/PropertyLists/AboutPropertyLists/AboutPropertyLists.html) na iOS Developer Library.

Além disso, o Intune suporta os seguintes tipos de tokens na lista de propriedades:
- \{\{userprincipalname\}\} - (Exemplo: **John@contoso.com**)
- \{\{mail\}\} - (Exemplo: **John@contoso.com**)
- \{\{partialupn\}\} - (Exemplo: **João**)
- \{\{accountid\}\} - (Exemplo: **fc0dc142-71d8-4b12-bbea-bae2a8514c81**)
- \{\{deviceid\}\} - (Exemplo: **b9841cd9-9843-405f-be28-b2265c59ef97**)
- \{\{userid\}\} - (Exemplo: **3ec2c00f-b125-4519-acf0-302ac3761822**)
- \{\{username\}\} - (Exemplo: **João Teixeira**)
- \{\{serialnumber\}\} - (Exemplo: **F4KN99ZUG5V2**) para dispositivos iOS
- \{\{serialnumberlast4digits\}\} - (Exemplo: **G5V2**) para dispositivos iOS
    
Os carateres \{\{ e \}\} são utilizados apenas por tipos de token e não devem ser utilizados para outros fins.

## <a name="associate-a-mobile-app-configuration-policy-with-an-app"></a>Associar uma política de configuração de aplicação móvel a uma aplicação
Depois de ter criado uma política de configuração de aplicação móvel, tem de a associar à aplicação iOS à qual pretende que as definições da política de configuração sejam aplicadas.

Para tal, siga os passos para criar uma implementação de aplicações em [Adicionar aplicações para dispositivos móveis no Microsoft Intune](add-apps-for-mobile-devices-in-microsoft-intune.md) e em [Implementar aplicações com o Microsoft Intune](deploy-apps-in-microsoft-intune.md). Quando chegar à página **Configuração de Aplicação Móvel** do assistente, selecione a política que pretende associar à aplicação a partir da lista pendente **Política de Configuração de Aplicação**.

Em seguida, continue a implementar e a monitorizar a implementação da aplicação da forma habitual.

Quando a aplicação implementada for executada num dispositivo, será executada com as definições que configurou na política de configuração de aplicação móvel.

> [!TIP]
> Se uma ou mais políticas de configuração de aplicação móvel entrarem em conflito, não é aplicada nenhuma política. O conflito será comunicado no **Dashboard** da consola de administração do Intune.

## <a name="example-format-for-a-mobile-app-configuration-xml-file"></a>Formato de exemplo para o ficheiro XML de configuração de aplicação móvel

Quando criar um ficheiro de configuração de aplicação móvel, pode especificar um ou mais dos seguintes valores utilizando este formato:

```
<dict>
  <key>userprincipalname</key>
  <string>{{userprincipalname}}</string>
  <key>mail</key>
  <string>{{mail}}</string>
  <key>partialupn</key>
  <string>{{partialupn}}</string>
  <key>accountid</key>
  <string>{{accountid}}</string>
  <key>deviceid</key>
  <string>{{deviceid}}</string>
  <key>userid</key>
  <string>{{userid}}</string>
  <key>username</key>
  <string>{{username}}</string>
  <key>serialnumber</key>
  <string>{{serialnumber}}</string>
  <key>serialnumberlast4digits</key>
  <string>{{serialnumberlast4digits}}</string>
  <key>udidlast4digits</key>
  <string>{{udidlast4digits}}</string>
</dict>

```

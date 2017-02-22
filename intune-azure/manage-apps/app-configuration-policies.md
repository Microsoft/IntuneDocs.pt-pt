---
title: "Como utilizar políticas de configuração de aplicação do Intune | Pré-visualização do Azure no Intune | Documentos da Microsoft"
description: "Pré-visualização do Azure no Intune: saiba como utilizar políticas de configuração de aplicação para disponibilizar dados de configuração a uma aplicação iOS quando é executada."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 01/23/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c9163693-d748-46e0-842a-d9ba113ae5a8
ms.reviewer: mghadial
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 424fae862592c1ab5b4221fb5ad40a52c39f6760
ms.openlocfilehash: 75e3f3f62dd392cda1530321b12cd27e9ee8847f

---

# <a name="how-to-use-intune-app-configuration-policies"></a>Como utilizar políticas de configuração de aplicação

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Utilize políticas de configuração de aplicação no Microsoft Intune para disponibilizar definições que poderão ser obrigatórias quando os utilizadores executarem uma aplicação. Por exemplo, uma aplicação poderá exigir que os utilizadores especifiquem:

-   Um número de porta personalizado.

-   Definições de idioma.

-   Definições de segurança.

-   Definições de imagem corporativa, como um logótipo de empresa.

Se os utilizadores introduzirem estas definições incorretamente, isso pode aumentar a carga sobre o suporte técnico e tornar mais lenta a adoção de novas aplicações.

As políticas de configuração de aplicação podem ajudar a eliminar estes problemas, permitindo-lhe atribuir estas definições aos utilizadores de uma política antes de executarem a aplicação. As definições são então fornecidas automaticamente e os utilizadores não têm de executar nenhuma ação.

Não atribua estas políticas diretamente a utilizadores nem a dispositivos. Em alternativa, associe uma política à aplicação e, em seguida, implemente-a. As definições de política serão utilizadas sempre que a aplicação as verificar (normalmente, a primeira vez for executada).

> [!TIP]
> Este tipo de política está atualmente disponível apenas para dispositivos com o iOS 8.0 e posterior. Suporta os seguintes tipos de instalação de aplicações:
>
> -   **Aplicação iOS gerida da loja de aplicações**
> -   **Pacote de aplicações para iOS**
>
> Para obter mais informações sobre os tipos de instalação de aplicações, veja [How to add an app to Microsoft Intune (Como adicionar uma aplicação ao Microsoft Intune)](/intune-azure/manage-apps/add-apps).

## <a name="create-an-app-configuration-policy"></a>Criar uma política de configuração de aplicação

1. Inicie sessão no portal do Azure.
2. Escolha **Mais Serviços** > **Outros** > **Intune**.
3. No painel **Intune**, escolha **Gerir aplicações**.
1.  Na carga de trabalho **Gerir aplicações**, escolha **Gerir** > **Políticas de Configuração de Aplicação**.

2.  No painel da lista de políticas, escolha **Adicionar**.

3.  No painel **Adicionar Política de Configuração**, indique um nome e uma descrição opcional para a política de configuração de aplicação.
4.  Escolha **Aplicação Associada** e, em seguida, no painel **Aplicação Associada**, escolha a aplicação gerida à qual quer aplicar a configuração.
5.  No painel **Adicionar Política de Configuração**, escolha **Definições de configuração** e, em seguida, no painel de Definições de Configuração, escolha como pretende especificar os valores XML que constituem o perfil de configuração em:
    - **Introduzir dados XML** – introduza ou cole uma lista de propriedades XML que contém as definições de configuração de aplicações que quer. O formato da lista de propriedades de XML irá variar em função da aplicação que está a configurar. Contacte o fornecedor da aplicação para obter detalhes sobre o formato exato a utilizar.
    O Intune verifica se o XML que introduziu está num formato válido. Não verifica se a lista de propriedades do XML irá funcionar com a aplicação à qual está associada.
    Para saber mais sobre listas de propriedades XML, consulte [Compreender Listas de Propriedades XML](https://developer.apple.com/library/ios/documentation/Cocoa/Conceptual/PropertyLists/UnderstandXMLPlist/UnderstandXMLPlist.html) na iOS Developer Library.
    - **Utilizar designer de configuração** –Permite-lhe especificar pares de valores e chaves XML diretamente no portal.
8. Quando tiver terminado, volte ao painel **Adicionar Política de Configuração** e clique em **Criar**.

A política será criada e é apresentada no painel da lista de políticas.

Em seguida, continue a [atribuir](deploy-apps.md) e [monitorizar](monitor-apps.md) a aplicação como é habitual.

Quando a aplicação atribuída for executada num dispositivo, será executada com as definições que configurou na política de configuração de aplicação.

> [!TIP]
> Se uma ou mais políticas de configuração de aplicação entrarem em conflito, não será aplicada nenhuma política.

## <a name="information-about-the-xml-file-format"></a>Informações sobre o formato de ficheiro XML

O Intune suporta os seguintes tipos de dados numa lista de propriedades:

- &lt;número inteiro&gt;
- &lt;real&gt;
- &lt;cadeia&gt;
- &lt;matriz&gt;
- &lt;dict&gt;
- &lt;verdadeiro /&gt; ou &lt;falso /&gt;

Para obter mais informações sobre tipos de dados, consulte [Sobre Listas de Propriedades](https://developer.apple.com/library/ios/documentation/Cocoa/Conceptual/PropertyLists/AboutPropertyLists/AboutPropertyLists.html) na iOS Developer Library.

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





## <a name="example-format-for-an-app-configuration-xml-file"></a>Formato de exemplo do ficheiro XML de configuração de aplicação

Quando criar um ficheiro de configuração de aplicação, pode especificar um ou mais dos seguintes valores com este formato:

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



<!--HONumber=Feb17_HO1-->



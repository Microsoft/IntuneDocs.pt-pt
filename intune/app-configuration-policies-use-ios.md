---
title: "Como utilizar políticas de configuração de aplicações do Intune para iOS"
titlesuffix: Azure portal
description: "Saiba como utilizar políticas de configuração de aplicações para disponibilizar dados de configuração a uma aplicação iOS quando é executada.\""
keywords: 
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 07/26/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c9163693-d748-46e0-842a-d9ba113ae5a8
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: bc42f3cafa83b5f7ba053d03dbd066b725bb1fee
ms.sourcegitcommit: e10dfc9c123401fabaaf5b487d459826c1510eae
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/09/2017
---
# <a name="how-to-use-microsoft-intune-app-configuration-policies-for-ios"></a>Como utilizar as políticas de configuração de aplicações do Microsoft Intune para iOS

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Utilize políticas de configuração de aplicações no Microsoft Intune para disponibilizar definições que serão utilizadas quando os utilizadores executarem uma aplicação iOS. Por exemplo, uma aplicação poderá exigir que os utilizadores especifiquem:

-   Um número de porta personalizado.

-   Definições de idioma.

-   Definições de segurança.

-   Definições de imagem corporativa, como um logótipo de empresa.

Se os utilizadores introduzirem estas definições incorretamente, isso pode aumentar a carga sobre o suporte técnico e tornar mais lenta a adoção de novas aplicações.

As políticas de configuração de aplicação podem ajudar a eliminar estes problemas, permitindo-lhe atribuir estas definições aos utilizadores de uma política antes de executarem a aplicação. As definições são então fornecidas automaticamente e os utilizadores não têm de executar nenhuma ação. É necessário que as aplicações tenham sido escritas de forma a suportar a utilização das configurações de aplicação. Consulte o seu fornecedor de aplicações para obter informações adicionais.

Não atribua estas políticas diretamente a utilizadores nem a dispositivos. Em alternativa, associe uma política à aplicação e, em seguida, atribua a aplicação. As definições de política são utilizadas sempre que a aplicação as verificar (normalmente, a primeira vez que for executada).

> [!TIP]
> Este tipo de política está atualmente disponível apenas para dispositivos com o iOS 8.0 e posterior. Suporta os seguintes tipos de instalação de aplicações:
>
> -   **Aplicação iOS gerida da loja de aplicações**
> -   **Pacote de aplicações para iOS**
>
> Para obter mais informações sobre os tipos de instalação de aplicações, veja [How to add an app to Microsoft Intune (Como adicionar uma aplicação ao Microsoft Intune)](apps-add.md).

## <a name="create-an-app-configuration-policy"></a>Criar uma política de configuração de aplicação
1.  Inicie sessão no portal do Azure.
2.  Escolha **Mais Serviços** > **Monitorização + Gestão** > **Intune**.
3.  No painel **Intune**, escolha **Aplicações móveis**.
4.  Na carga de trabalho **Aplicações móveis**, escolha **Gerir** > **Políticas de Configuração da Aplicação**.
5.  No painel da lista de políticas, escolha **Adicionar**.
6.  No painel **Adicionar Política de Configuração**, indique um **Nome** e uma **Descrição** opcional para a política de configuração de aplicações.
7.  Em **Tipo de inscrição de dispositivos**, selecione uma das seguintes opções:
    - **Inscrito com o Intune** – para aplicações que são geridas pelo Intune.
    - **Não inscrito com o Intune** – para aplicações que não são geridas pelo Intune ou que são geridas por outra solução.
8.  Em **Plataforma**, selecione **iOS** (apenas para dispositivos inscritos com o Intune)
9.  Escolha **Aplicação Associada** e, em seguida, no painel **Aplicação Associada**, escolha a aplicação gerida à qual quer aplicar a configuração.
10. No painel **Adicionar Política de Configuração**, selecione **Definições de configuração**
11. No painel **Definições de Configuração**, escolha de que forma pretende especificar os valores XML que constituem o perfil de configuração em:
    - **Introduzir dados XML** (apenas para dispositivos inscritos com o Intune) – introduza ou cole uma lista de propriedades XML que contenha as definições de configuração de aplicações que pretende. O formato da lista de propriedades XML varia em função da aplicação que está a configurar. Contacte o fornecedor da aplicação para obter detalhes sobre o formato exato a utilizar.
O Intune verifica se o XML que introduziu está num formato válido. Não verifica se a lista de propriedades XML funciona com a aplicação à qual está associada.
Para saber mais sobre listas de propriedades XML, veja [Compreender Listas de Propriedades XML](https://developer.apple.com/library/ios/documentation/Cocoa/Conceptual/PropertyLists/UnderstandXMLPlist/UnderstandXMLPlist.html) na iOS Developer Library.
    - **Utilizar designer de configuração** (quer o dispositivo esteja inscrito ou não com o Intune) – permite-lhe especificar pares de valores e chaves XML diretamente no portal.
11. Quando tiver terminado, volte ao painel **Adicionar Política de Configuração** e clique em **Criar**.

A política é criada e apresentada no painel da lista de políticas.



>[!Note]
>Pode utilizar o [SDK da Aplicação Intune](https://docs.microsoft.com/intune/app-sdk-ios) para preparar aplicações de linha de negócios para serem geridas por políticas de proteção de aplicações do Intune e políticas de configuração de aplicações, quer o dispositivo esteja inscrito ou não com o Intune. Por exemplo, pode utilizar uma política de configuração de aplicações para configurar URLs permitidos e bloqueados para o [Intune Managed Browser](app-configuration-managed-browser.md). Assim que uma aplicação for compatível com estas políticas, pode configurá-las com uma política.


Quando a aplicação atribuída é executada num dispositivo, a mesma é executada com as definições que configurou na política de configuração de aplicações.
Veja a documentação relativa à aplicação que está a configurar para obter informações sobre o que acontece se uma ou mais políticas de configuração de aplicações entrarem em conflito.

>[!Tip]
>Além disso, pode utilizar a Graph API para realizar estas tarefas. Para obter mais detalhes, veja [Graph API Reference MAM Targeted Config (Configuração de MAM Direcionada de Referência para Graph API)](https://graph.microsoft.io/docs/api-reference/beta/api/intune_mam_targetedmanagedappconfiguration_create).


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

## <a name="next-steps"></a>Próximos passos

Continue a [atribuir](apps-deploy.md) e [monitorizar](apps-monitor.md) a aplicação como é habitual.
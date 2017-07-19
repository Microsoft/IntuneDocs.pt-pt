---
title: "Como utilizar políticas de configuração de aplicações do Intune para iOS"
titleSuffix: Intune on Azure
description: "Saiba como utilizar políticas de configuração de aplicações para disponibilizar dados de configuração a uma aplicação iOS quando é executada.\""
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 06/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c9163693-d748-46e0-842a-d9ba113ae5a8
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 112f60ff208c27825ddd0f4c812535b255894333
ms.sourcegitcommit: fd2e8f6f8761fdd65b49f6e4223c2d4a013dd6d9
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/03/2017
---
# <a name="how-to-use-microsoft-intune-app-configuration-policies-for-ios"></a>Como utilizar as políticas de configuração de aplicações do Microsoft Intune para iOS

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Utilize políticas de configuração de aplicações no Microsoft Intune para disponibilizar definições que poderão ser obrigatórias quando os utilizadores executarem uma aplicação iOS. Por exemplo, uma aplicação poderá exigir que os utilizadores especifiquem:

-   Um número de porta personalizado.

-   Definições de idioma.

-   Definições de segurança.

-   Definições de imagem corporativa, como um logótipo de empresa.

Se os utilizadores introduzirem estas definições incorretamente, isso pode aumentar a carga sobre o suporte técnico e tornar mais lenta a adoção de novas aplicações.

As políticas de configuração de aplicação podem ajudar a eliminar estes problemas, permitindo-lhe atribuir estas definições aos utilizadores de uma política antes de executarem a aplicação. As definições são então fornecidas automaticamente e os utilizadores não têm de executar nenhuma ação.

Não atribua estas políticas diretamente a utilizadores nem a dispositivos. Em alternativa, associe uma política à aplicação e, em seguida, atribua a aplicação. As definições de política serão utilizadas sempre que a aplicação as verificar (normalmente, a primeira vez for executada).

> [!TIP]
> Este tipo de política está atualmente disponível apenas para dispositivos com o iOS 8.0 e posterior. Suporta os seguintes tipos de instalação de aplicações:
>
> -   **Aplicação iOS gerida da loja de aplicações**
> -   **Pacote de aplicações para iOS**
>
> Para obter mais informações sobre os tipos de instalação de aplicações, veja [How to add an app to Microsoft Intune (Como adicionar uma aplicação ao Microsoft Intune)](apps-add.md).

## <a name="create-an-app-configuration-policy"></a>Criar uma política de configuração de aplicação

1. Inicie sessão no portal do Azure.
2. Escolha **Mais Serviços** > **Monitorização + Gestão** > **Intune**.
3. No painel **Intune**, escolha **Aplicações móveis**.
1.  Na carga de trabalho **Aplicações móveis**, escolha **Gerir** > **Políticas de Configuração da Aplicação**.

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

Em seguida, continue a [atribuir](apps-deploy.md) e [monitorizar](apps-monitor.md) a aplicação como é habitual.

Quando a aplicação atribuída for executada num dispositivo, será executada com as definições que configurou na política de configuração de aplicação.

> [!TIP]
> Se uma ou mais políticas de configuração de aplicação entrarem em conflito, não será aplicada nenhuma política.

## <a name="create-a-mam-targeted-configuration-policy"></a>Criar uma política de configuração de MAM direcionada
A configuração de MAM direcionada permite que uma aplicação receba dados de configuração através do SDK da Aplicação Intune. O formato e as variantes destes dados têm de ser definidos e comunicados aos clientes do Intune pelo proprietário/programador da aplicação. Os administradores do Intune podem direcionar e implementar dados de configuração através da consola do Intune no Azure. Os dados de configuração de MAM direcionada podem ser fornecidos através do Serviço de MAM para aplicações ativadas por MAM-WE. Por exemplo, o [Intune Managed Browser](https://docs.microsoft.com/intune/app-configuration-managed-browser) permitiu/bloqueou a lista de URLs. Os dados de configuração de aplicações são emitidos através do nosso Serviço de MAM diretamente para a aplicação em vez de através do canal de MDM. As [políticas de configuração de aplicações de MDM](https://docs.microsoft.com/intune/app-configuration-policies-use-ios#create-an-app-configuration-policy) são a solução nativa através de MDM. A principal diferença para a configuração de MAM direcionada é que o dispositivo no qual a aplicação é executada não precisa de ser inscrito para MDM. A configuração de MAM direcionada está disponível em iOS e Android. Para iOS, a aplicação tem de ter o SDK da Aplicação Intune para iOS (versão 7.0.1) incorporado e participar nas definições de configuração da aplicação. Os passos para criar uma política de configuração de MAM direcionada são os seguintes: 

1. Inicie sessão no **portal do Azure**.

2. Selecione **Intune > Aplicações móveis – Políticas de configuração de aplicações**.

3. No painel **Políticas de configuração de aplicações**, escolha **Adicionar**.

4. Introduza um **Nome**e uma **Descrição** opcional para as definições de configuração de aplicações e escolha **Não inscrita com o Intune**.

5. Escolha **Selecionar aplicações necessárias** e, em seguida, no painel de aplicações **Direcionadas**, escolha aplicações para as plataformas que pretende. <br>
**Nota:** para aplicações LOB, selecione **Mais aplicações**. Introduza o ID do pacote da sua aplicação.

6. Escolha **OK** para regressar ao painel **Adicionar configuração de aplicações**.

7. Escolha **Definir configuração**. No painel **Configuração**, define os pares de chave e valor para fornecer as configurações.

8. Quando tiver terminado, escolha **OK**.

9. No **painel Adicionar configuração de aplicações**, escolha **Criar**.

A nova configuração é criada e apresentada no painel Configuração de aplicações.

Em seguida, continue a [atribuir](apps-deploy.md) e [monitorizar](apps-monitor.md) a aplicação como é habitual.

Quando a aplicação atribuída (integrada com o SDK da Aplicação do Intune) for executada num dispositivo, será executada com as definições que configurou na política de configuração de MAM direcionada. A aplicação atribuída precisa de ter integrada a versão suportada do SDK da Aplicação do Intune. Para obter mais informações sobre os requisitos de desenvolvimento de aplicações para utilizar políticas de Configuração de MAM Direcionada, veja [Guia de Integração do SDK da Aplicação do Intune para iOS](https://docs.microsoft.com/intune/app-sdk-ios).

Para obter mais informações sobre as capacidades da nossa Graph API em relação aos valores de configuração de MAM direcionada, veja [Configuração de MAM Direcionada de Referência para Graph API](https://graph.microsoft.io/docs/api-reference/beta/api/intune_mam_targetedmanagedappconfiguration_create).

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

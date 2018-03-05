---
title: "Adicionar políticas de configuração da aplicação para dispositivos iOS geridos | Documentos da Microsoft"
titlesuffix: Azure portal
description: "Saiba como utilizar políticas de configuração da aplicação para disponibilizar dados de configuração a uma aplicação iOS quando é executada."
keywords: 
author: erikre
ms.author: erikre
manager: dougeby
ms.date: 01/30/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c9163693-d748-46e0-842a-d9ba113ae5a8
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: b64d8b60a4c577acc2f6ef161f6de37ac529e7ac
ms.sourcegitcommit: a6fd6b3df8e96673bc2ea48a2b9bda0cf0a875ae
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2018
---
# <a name="add-app-configuration-policies-for-managed-ios-devices"></a>Adicionar políticas de configuração da aplicação para dispositivos iOS geridos

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Utilize políticas de configuração da aplicação no Microsoft Intune para disponibilizar definições quando os utilizadores executarem uma aplicação iOS. Não atribua estas políticas diretamente a utilizadores nem a dispositivos. Em alternativa, associe uma política à aplicação e, em seguida, atribua a aplicação. As definições de política são utilizadas quando a aplicação as verificar, normalmente a primeira vez em que for executada.

Pode atribuir uma política de configuração da aplicação a um grupo de utilizadores e dispositivos ao utilizar uma combinação de inclusão e exclusão de atribuições. Depois de adicionar uma política de configuração da aplicação, pode definir as atribuições dessa política. Quando definir as atribuições da política, poderá optar por incluir e excluir os grupos de utilizadores aos quais a políticas será aplicada. Quando escolher incluir um ou mais grupos, poderá optar por selecionar grupos específicos para incluir ou selecionar grupos incorporados. Os grupos incorporados incluem **Todos os Utilizadores**, **Todos os Dispositivos** e **Todos os Utilizadores e Todos os Dispositivos**. 

>[!NOTE]
>O Intune fornece os grupos **Todos os Utilizadores** e **Todos os Dispositivos** pré-criados na consola com otimizações incorporadas para sua comodidade. Recomendamos fortemente que utilize estes grupos para abranger todos os utilizadores e todos os dispositivos em vez dos grupos "Todos os utilizadores" ou "Todos os dispositivos" que possa ter criado.

Depois de selecionar os grupos a incluir na sua política de configuração da aplicação, também poderá escolher os grupos específicos a excluir.

> [!TIP]
> Este tipo de política está atualmente disponível apenas para dispositivos com o iOS 8.0 e posterior. Suporta os seguintes tipos de instalação de aplicações:
>
> -   **Aplicação iOS gerida da loja de aplicações**
> -   **Pacote de aplicações para iOS**
>
> Para obter mais informações sobre os tipos de instalação de aplicações, veja [How to add an app to Microsoft Intune (Como adicionar uma aplicação ao Microsoft Intune)](apps-add.md).

## <a name="create-an-app-configuration-policy"></a>Criar uma política de configuração de aplicação

1. Inicie sessão no portal do Azure.
2. Escolha **Mais Serviços** > **Monitorização + Gestão** + **Intune**.
3. Selecione a carga de trabalho **Aplicações Móveis**.
4. Selecione **Políticas de configuração da aplicação** no grupo **Gerir** e, em seguida, selecione **Adicionar**.
5. Defina os seguintes detalhes:
    - **Nome**<br>
      O nome do perfil que será apresentado no portal do Azure.
    - **Descrição**<br>
      A descrição do perfil que será apresentada no portal do Azure.
    - **Tipo de inscrição do dispositivo**<br>
      Selecione **Dispositivos geridos**.
6. Selecione **iOS** em **Plataforma**.
7.  Selecione **Aplicação Associada**. Em seguida, no painel **Aplicação Associada**, selecione a aplicação gerida à qual pretende aplicar a configuração.
8.  No painel **Adicionar Política de Configuração**, selecione **Definições de configuração**.
9. Selecione **Formato das definições de configuração**. Selecione um dos seguintes procedimentos:
    - **[Utilizar estruturador de configuração](#use-configuration-designer)**
    - **[Introduzir dados XML](#enter-xml-data)**
10. Depois de adicionar as suas informações XML, selecione **OK** e, em seguida, selecione **Adicionar** para adicionar a política de configuração. O painel descrição geral da política de configuração será apresentado.
11. Selecione **Atribuições** para apresentar as opções de inclusão e exclusão. 

    ![Atribuições de política](./media/app-config-policy01.png)
12. Selecione **Todos os Utilizadores** no separador **Incluir**.

    ![Atribuições de política – Todos os Utilizadores](./media/app-config-policy02.png)
13. Selecione o separador **Excluir**. 
14. Clique em **Selecionar grupos para excluir** para apresentar o painel relacionado.

    ![Atribuições de política – selecionar grupos para excluir](./media/app-config-policy03.png)
15. Escolha os grupos que pretende excluir e, em seguida, clique em **Selecionar**.

    >[!NOTE]
    >Ao adicionar um grupo, se outro grupo já tiver sido incluído num determinado tipo de atribuição, o mesmo estará pré-selecionado e inalterável para outras atribuições de inclusão. Por conseguinte, esse grupo que foi utilizado não poderá ser utilizado como um grupo excluído.
16. Clique em **Guardar**.

## <a name="use-configuration-designer"></a>Utilizar o estruturador de configuração

Pode utilizar o estruturador de configuração para as aplicações em dispositivos inscritos ou não inscritos no Intune. O estruturador permite-lhe configurar chaves e valores de configuração específicos. Também tem de especificar o tipo de dados para cada valor. As definições são fornecidas às aplicações automaticamente no momento da instalação.

### <a name="add-a-setting"></a>Adicionar uma definição

1. Para cada chave e valor na configuração, defina:
   - **Chave de configuração**<br>
     A chave que identifica exclusivamente a configuração de definição específica.
   - **Tipo de valor**<br>
     O tipo de dados do valor de configuração. Os tipos incluem Número Inteiro, Real, Cadeia ou Booleano.
   - **Valor de configuração**<br>
     O valor da configuração.
2. Selecione **OK** para definir as definições de configuração.

### <a name="delete-a-setting"></a>Eliminar uma definição

1. Selecione as reticências (**...**) junto à definição.
2. Selecione **Eliminar**.

Os carateres \{\{ e \}\} são utilizados apenas por tipos de token e não devem ser utilizados para outros fins.

## <a name="enter-xml-data"></a>Introduzir dados XML

Pode escrever ou colar uma lista de propriedades XML que contenha as definições de configuração da aplicação para dispositivos inscritos no Intune. O formato da lista de propriedades XML varia em função da aplicação que está a configurar. Contacte o fornecedor da aplicação para obter detalhes sobre o formato exato a utilizar.

O Intune valida o formato XML. No entanto, o Intune não verifica se a lista de propriedades XML (PList) irá funcionar com a aplicação de destino.

Para saber mais sobre listas de propriedades XML:

  -  Leia [Configurar aplicações iOS com políticas de configuração de aplicações móveis no Microsoft Intune](/intune-classic/deploy-use/configure-ios-apps-with-mobile-app-configuration-policies-in-microsoft-intune).
  -  Veja [Understand XML Property Lists (Compreender Listas de Propriedades XML)](https://developer.apple.com/library/ios/documentation/Cocoa/Conceptual/PropertyLists/UnderstandXMLPlist/UnderstandXMLPlist.html) na iOS Developer Library.

### <a name="example-format-for-an-app-configuration-xml-file"></a>Formato de exemplo do ficheiro XML de configuração de aplicação

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
### <a name="supported-xml-plist-data-types"></a>Tipos de dados de Listas de Propriedades XML suportados

O Intune suporta os seguintes tipos de dados numa lista de propriedades:

- &lt;número inteiro&gt;
- &lt;real&gt;
- &lt;cadeia&gt;
- &lt;matriz&gt;
- &lt;dict&gt;
- &lt;verdadeiro /&gt; ou &lt;falso /&gt;

### <a name="tokens-used-in-the-property-list"></a>Tokens utilizados na lista de propriedades

Além disso, o Intune suporta os seguintes tipos de tokens na lista de propriedades:
- \{\{userprincipalname\}\} – por exemplo, **John@contoso.com**
- \{\{mail\}\} – por exemplo, **John@contoso.com**
- \{\{partialupn\}\} – por exemplo, **João**
- \{\{accountid\}\} – por exemplo, **fc0dc142-71d8-4b12-bbea-bae2a8514c81**
- \{\{deviceid\}\} – por exemplo, **b9841cd9-9843-405f-be28-b2265c59ef97**
- \{\{userid\}\} – por exemplo, **3ec2c00f-b125-4519-acf0-302ac3761822**
- \{\{username\}\} – por exemplo, **John Doe**
- \{\{serialnumber\}\} – por exemplo, **F4KN99ZUG5V2** (para dispositivos iOS)
- \{\{serialnumberlast4digits\}\} – por exemplo, **G5V2** (para dispositivos iOS)

## <a name="next-steps"></a>Próximos passos

Continue a [atribuir](apps-deploy.md) e [monitorizar](apps-monitor.md) a aplicação como é habitual.
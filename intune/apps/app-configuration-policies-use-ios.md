---
title: Adicionar políticas de configuração da aplicação para dispositivos iOS geridos
titleSuffix: Microsoft Intune
description: Saiba como utilizar políticas de configuração da aplicação para disponibilizar dados de configuração a uma aplicação iOS quando é executada.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: c9163693-d748-46e0-842a-d9ba113ae5a8
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0ee3ecd64254c0e212ffc86155d677bf18ba647a
ms.sourcegitcommit: f6b82c62af81a2643a1aaec774afa42d02eef352
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/04/2019
ms.locfileid: "73566183"
---
# <a name="add-app-configuration-policies-for-managed-ios-devices"></a>Adicionar políticas de configuração da aplicação para dispositivos iOS geridos

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Utilize políticas de configuração de aplicações no Microsoft Intune para disponibilizar definições de configuração personalizadas para uma aplicação para iOS. Essas definições de configuração permitem que um aplicativo seja personalizado com base na direção dos fornecedores de aplicativos. Pode obter estas definições de configuração (chaves e valores) junto do fornecedor da aplicação. Para configurar a aplicação, terá de especificar as definições como chaves e valores, ou como XML com chaves e valores.

Enquanto administrador do Microsoft Intune, pode controlar as contas de utilizadores que são adicionadas a aplicações do Microsoft Office em dispositivos geridos. Pode limitar o acesso exclusivamente a contas de utilizadores autorizadas e bloquear contas pessoais em dispositivos inscritos. As aplicações de apoio processam a configuração da aplicação e removem e bloqueiam contas não aprovadas. As definições de políticas de configuração são utilizadas quando a aplicação as procura, normalmente quando é executada pela primeira vez.

Depois de adicionar uma política de configuração da aplicação, pode definir as atribuições dessa política. Quando definir as atribuições da política, poderá optar por incluir e excluir os grupos de utilizadores aos quais a política será aplicada. Quando escolher incluir um ou mais grupos, poderá optar por selecionar grupos específicos para incluir ou selecionar grupos incorporados. Os grupos incorporados incluem **Todos os Utilizadores**, **Todos os Dispositivos** e **Todos os Utilizadores e Todos os Dispositivos**. 

> [!NOTE]
> O Intune fornece os grupos **Todos os Utilizadores** e **Todos os Dispositivos** pré-criados na consola com otimizações incorporadas para sua comodidade. Recomendamos fortemente que utilize estes grupos para abranger todos os utilizadores e todos os dispositivos em vez dos grupos "Todos os utilizadores" ou "Todos os dispositivos" que possa ter criado.

Depois de selecionar os grupos a incluir na sua política de configuração da aplicação, também poderá escolher os grupos específicos a excluir. Para obter mais informações, veja [Incluir e excluir atribuições de aplicações no Microsoft Intune](apps-inc-exl-assignments.md).

> [!TIP]
> Este tipo de política está atualmente disponível apenas para dispositivos com o iOS 8.0 e posterior. Suporta os seguintes tipos de instalação de aplicações:
>
> - **Aplicação iOS gerida da loja de aplicações**
> - **Pacote de aplicações para iOS**
>
> Para obter mais informações sobre os tipos de instalação de aplicações, veja [How to add an app to Microsoft Intune (Como adicionar uma aplicação ao Microsoft Intune)](apps-add.md). Para obter mais informações sobre como incorporar a configuração do aplicativo ao pacote do aplicativo. ipa para dispositivos gerenciados, consulte configuração de aplicativo gerenciado na [documentação do desenvolvedor do IOS](https://developer.apple.com/library/archive/samplecode/sc2279/Introduction/Intro.html).

## <a name="create-an-app-configuration-policy"></a>Criar uma política de configuração de aplicação

1. Entre no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
3. Selecione a carga de trabalho **Aplicações do cliente**.
4. Selecione **Políticas de configuração da aplicação** no grupo **Gerir** e, em seguida, selecione **Adicionar**.
5. Defina os seguintes detalhes:
    - **Nome** – o nome do perfil que é apresentado no portal do Azure.
    - **Descrição** – a descrição do perfil que é apresentada no portal do Azure.
    - **Tipo de registro de dispositivo** -escolha **dispositivos gerenciados** para dispositivos que foram registrados no Intune.
6. Selecione **iOS** em **Plataforma**.
7. Selecione **Aplicação associada**. Em seguida, no painel **Aplicação associada**, selecione a aplicação gerida à qual pretende aplicar a configuração e selecione **OK**.
8. No painel **Adicionar política de configuração**, selecione **Definições de configuração**.
9. Selecione **Formato das definições de configuração**. Selecione um dos seguintes métodos para adicionar informações de configuração:
    - **Utilizar estruturador de configuração**
    - **Introduzir dados XML**<br><br>
    Para obter detalhes sobre a utilização do estruturador de configuração, veja [Utilizar estruturador de configuração](#use-configuration-designer). Para obter detalhes sobre a introdução de dados XML, veja [Introduzir dados XML](#enter-xml-data). 
10. Depois de adicionar as informações de configuração, escolha **OK**e, em seguida, escolha **Adicionar** para adicionar a política de configuração. O painel de descrição geral da política de configuração é apresentado.
11. Selecione **Atribuições** para apresentar as opções de inclusão e exclusão. 

    ![Captura de ecrã do separador Atribuições de política – Incluir](./media/app-configuration-policies-use-ios/app-config-policy01.png)
12. Selecione **Todos os Utilizadores** no separador **Incluir**.

    ![Captura de ecrã do menu pendente Atribuições de política – Todos os Utilizadores](./media/app-configuration-policies-use-ios/app-config-policy02.png)
13. Selecione o separador **Excluir**. 
14. Clique em **Selecionar grupos para excluir** para apresentar o painel relacionado.

    ![Captura de ecrã do painel Atribuições de política – Selecionar grupos para excluir](./media/app-configuration-policies-use-ios/app-config-policy03.png)
15. Escolha os grupos que pretende excluir e, em seguida, clique em **Selecionar**.

    >[!NOTE]
    >Ao adicionar um grupo, se outro grupo já tiver sido incluído num determinado tipo de atribuição, o mesmo estará pré-selecionado e inalterável para outras atribuições de inclusão. Por conseguinte, esse grupo que foi utilizado não poderá ser utilizado como um grupo excluído.
16. Clique em **Guardar**.

## <a name="use-configuration-designer"></a>Utilizar o estruturador de configuração

O Microsoft Intune disponibiliza definições de configuração exclusivas para uma aplicação. Pode utilizar o estruturador de configuração para as aplicações em dispositivos inscritos ou não inscritos no Microsoft Intune. O estruturador permite-lhe configurar chaves e valores de configuração específicos que o ajudam a criar o XLM subjacente. Também tem de especificar o tipo de dados para cada valor. Estas definições são fornecidas para aplicações automaticamente quando estas são instaladas.

### <a name="add-a-setting"></a>Adicionar uma definição

1. Para cada chave e valor na configuração, defina:
   - **Chave de configuração** – a chave que identifica exclusivamente a configuração de definição específica.
   - **Tipo de valor** – o tipo de dados do valor de configuração. Os tipos incluem Número Inteiro, Real, Cadeia ou Booleano.
   - **Valor de configuração** – o valor da configuração.
2. Selecione **OK** para definir as definições de configuração.

### <a name="delete-a-setting"></a>Eliminar uma definição

1. Selecione as reticências ( **...** ) junto à definição.
2. Selecione **Eliminar**.

Os carateres \{\{ e \}\} são utilizados apenas por tipos de token e não devem ser utilizados para outros fins.

### <a name="allow-only-configured-organization-accounts-in-multi-identity-apps"></a>Permitir apenas contas de organização configuradas nas aplicações de várias identidades 

Para dispositivos iOS, use os seguintes pares de chave/valor:

| **Chave** | IntuneMAMAllowedAccountsOnly |
|--------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Os** | <ul><li>**Ativada**: a única conta autorizada é a conta de utilizador gerido definida pela chave [IntuneMAMUPN](data-transfer-between-apps-manage-ios.md#configure-user-upn-setting-for-microsoft-intune-or-third-party-emm).</li><li>**Desativado** (ou qualquer valor que não seja sensível a maiúsculas/minúsculas que corresponda a **ativado**): qualquer conta é permitida.</li></ul> |.

   > [!NOTE]
   > Você deve usar o OneDrive para iOS 10,34 ou posterior, o Outlook para iOS 2.99.0 ou posterior ou o Edge para iOS 44.8.7 ou posterior e o aplicativo deve ser direcionado com [políticas de proteção de aplicativo do Intune](app-protection-policy.md) ao permitir apenas contas de organização configuradas com várias identidades.

## <a name="enter-xml-data"></a>Introduzir dados XML

Pode escrever ou colar uma lista de propriedades XML que contenha as definições de configuração da aplicação para dispositivos inscritos no Intune. O formato da lista de propriedades XML varia em função da aplicação que está a configurar. Contacte o fornecedor da aplicação para obter detalhes sobre o formato exato a utilizar.

O Intune valida o formato XML. No entanto, o Intune não verifica se a lista de propriedades XML (PList) funciona com a aplicação de destino.

Para saber mais sobre listas de propriedades XML:

- Veja [Understand XML Property Lists (Compreender Listas de Propriedades XML)](https://developer.apple.com/library/ios/documentation/Cocoa/Conceptual/PropertyLists/UnderstandXMLPlist/UnderstandXMLPlist.html) na iOS Developer Library.

### <a name="example-format-for-an-app-configuration-xml-file"></a>Formato de exemplo do ficheiro XML de configuração de aplicação

Quando criar um ficheiro de configuração de aplicação, pode especificar um ou mais dos seguintes valores com este formato:

```xml
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
  <key>aaddeviceid</key>
  <string>{{aaddeviceid}}</string>
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
- \{\{userPrincipalName\}\}— por exemplo, **John\@contoso.com**
- \}de \{de\}de \{de email — por exemplo, **John\@contoso.com**
- \{\{partialupn\}\} – por exemplo, **João**
- \{\{accountid\}\} – por exemplo, **fc0dc142-71d8-4b12-bbea-bae2a8514c81**
- \{\{deviceid\}\} – por exemplo, **b9841cd9-9843-405f-be28-b2265c59ef97**
- \{\{userid\}\} – por exemplo, **3ec2c00f-b125-4519-acf0-302ac3761822**
- \{\{username\}\} – por exemplo, **John Doe**
- \{\{serialnumber\}\} – por exemplo, **F4KN99ZUG5V2** (para dispositivos iOS)
- \{\{serialnumberlast4digits\}\} – por exemplo, **G5V2** (para dispositivos iOS)
- \{\{aaddeviceid\}\} – por exemplo, **ab0dc123-45d6-7e89-aabb-cde0a1234b56**

## <a name="configure-the-company-portal-app-to-support-ios-dep-devices"></a>Configurar o aplicativo Portal da Empresa para dar suporte a dispositivos DEP com iOS

Os registros de DEP (Programa de registro de dispositivos da Apple) não são compatíveis com a versão da loja de aplicativos do aplicativo Portal da Empresa. No entanto, você pode configurar o aplicativo Portal da Empresa para dar suporte a dispositivos DEP com iOS usando as etapas a seguir.

1. No Intune portal do Azure:
    - Adicione o Portal da Empresa do Intune, se necessário, acessando**aplicativos cliente**do **Intune** >   > **aplicativos** > **Adicionar**.
    - Vá para **aplicativos cliente** > **políticas de configuração de aplicativo**para criar uma política de configuração de aplicativo para o aplicativo portal da empresa.
2. Crie uma política de configuração de aplicativo com o XML abaixo. Mais informações sobre como criar uma política de configuração de aplicativo e inserir dados XML podem ser encontradas em [Adicionar políticas de configuração de aplicativo para dispositivos IOS gerenciados](app-configuration-policies-use-ios.md) ou para MDM híbrido, [aplicar configurações a aplicativos Ios com políticas de configuração de aplicativo no System Center Configuration Manager](https://docs.microsoft.com/sccm/mdm/deploy-use/configure-ios-apps-with-app-configuration-policies).

    ``` xml
    <dict>
        <key>IntuneCompanyPortalEnrollmentAfterUDA</key>
        <dict>
            <key>IntuneDeviceId</key>
            <string>{{deviceid}}</string>
            <key>UserId</key>
            <string>{{userid}}</string>
        </dict>
    </dict>
    ```

3. Implante o Portal da Empresa em dispositivos com a política de configuração de aplicativo direcionada aos grupos desejados. Certifique-se de implantar a política somente em grupos de dispositivos que já estão registrados como DEP.
4. Diga aos usuários finais para entrar no aplicativo Portal da Empresa quando ele é instalado automaticamente.

## <a name="monitor-ios--app-configuration-status-per-device"></a>Monitorizar o estado de configuração da aplicação iOS por dispositivo 
Assim que a política de configuração for atribuída, pode monitorizar o estado da configuração da aplicação iOS para cada dispositivo gerido. No **Microsoft Intune**, no portal do Azure, selecione **Dispositivos** > **Todos os dispositivos**. Na lista de dispositivos geridos, selecione um dispositivo específico para apresentar um painel do dispositivo. No painel do dispositivo, selecione **Configuração da aplicação**.  

## <a name="additional-information"></a>Informações adicionais

- [Implantando definições de configuração de aplicativo do Outlook para iOS e Android](https://docs.microsoft.com/exchange/clients-and-mobile-in-exchange-online/outlook-for-ios-and-android/outlook-for-ios-and-android-configuration-with-microsoft-intune)

## <a name="next-steps"></a>Próximos passos

Continue a [atribuir](apps-deploy.md) e [monitorizar](apps-monitor.md) a aplicação.

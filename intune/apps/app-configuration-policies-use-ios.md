---
title: Adicione políticas de configuração de aplicativos para dispositivos geridos iOS/iPadOS
titleSuffix: Microsoft Intune
description: Saiba como utilizar as políticas de configuração de aplicações para fornecer dados de configuração a uma aplicação iOS/iPadOS quando é executado.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/11/2020
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
ms.openlocfilehash: af3c4e05a47e015384716588a28a6074898e2f6a
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/20/2020
ms.locfileid: "77513967"
---
# <a name="add-app-configuration-policies-for-managed-iosipados-devices"></a>Adicione políticas de configuração de aplicativos para dispositivos geridos iOS/iPadOS

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Utilize as políticas de configuração de aplicações no Microsoft Intune para fornecer configurações de configuração personalizadas para uma aplicação iOS/iPadOS. Estas configurações de configuração permitem que uma aplicação seja personalizada com base na direção dos fornecedores de aplicações. Pode obter estas definições de configuração (chaves e valores) junto do fornecedor da aplicação. Para configurar a aplicação, terá de especificar as definições como chaves e valores, ou como XML com chaves e valores.

Enquanto administrador do Microsoft Intune, pode controlar as contas de utilizadores que são adicionadas a aplicações do Microsoft Office em dispositivos geridos. Pode limitar o acesso exclusivamente a contas de utilizadores autorizadas e bloquear contas pessoais em dispositivos inscritos. As aplicações de apoio processam a configuração da aplicação e removem e bloqueiam contas não aprovadas. As definições de políticas de configuração são utilizadas quando a aplicação as procura, normalmente quando é executada pela primeira vez.

Depois de adicionar uma política de configuração da aplicação, pode definir as atribuições dessa política. Quando definir as atribuições da política, poderá optar por incluir e excluir os grupos de utilizadores aos quais a política será aplicada. Quando escolher incluir um ou mais grupos, poderá optar por selecionar grupos específicos para incluir ou selecionar grupos incorporados. Os grupos incorporados incluem **Todos os Utilizadores**, **Todos os Dispositivos** e **Todos os Utilizadores e Todos os Dispositivos**. 

> [!NOTE]
> O Intune fornece os grupos **Todos os Utilizadores** e **Todos os Dispositivos** pré-criados na consola com otimizações incorporadas para sua comodidade. Recomendamos fortemente que utilize estes grupos para abranger todos os utilizadores e todos os dispositivos em vez dos grupos "Todos os utilizadores" ou "Todos os dispositivos" que possa ter criado.

Depois de selecionar os grupos a incluir na sua política de configuração da aplicação, também poderá escolher os grupos específicos a excluir. Para obter mais informações, veja [Incluir e excluir atribuições de aplicações no Microsoft Intune](apps-inc-exl-assignments.md).

> [!TIP]
> Este tipo de política está atualmente disponível apenas para dispositivos que executam iOS/iPadOS 8.0 e posteriormente. Suporta os seguintes tipos de instalação de aplicações:
>
> - **Aplicativo iOS/iPadOS gerido a partir da loja de aplicações**
> - **Pacote de aplicações para iOS**
>
> Para obter mais informações sobre os tipos de instalação de aplicações, veja [How to add an app to Microsoft Intune (Como adicionar uma aplicação ao Microsoft Intune)](apps-add.md). Para obter mais informações sobre a incorporação de app config no seu pacote de aplicações .ipa para dispositivos geridos, consulte a Configuração de Aplicações Geridas na documentação do [desenvolvedor do iOS](https://developer.apple.com/library/archive/samplecode/sc2279/Introduction/Intro.html).

## <a name="create-an-app-configuration-policy"></a>Criar uma política de configuração de aplicação

1. Inscreva-se no centro de administração do [Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Escolha as **aplicações** > políticas de **configuração** de apps > **adicionar** > **dispositivos geridos**. Note que pode escolher entre **dispositivos geridos** e **aplicações geridas.** Para mais informações consulte apps que suportam a [configuração da aplicação](~/apps/app-configuration-policies-overview.md#apps-that-support-app-configuration).
3. Na página **Basics,** delineie os seguintes detalhes:
    - **Nome** – o nome do perfil que é apresentado no portal do Azure.
    - **Descrição** – a descrição do perfil que é apresentada no portal do Azure.
    - Tipo de **inscrição do dispositivo** - Esta definição está definida para **dispositivos geridos**.
4. Selecione **iOS/iPadOS** como **plataforma**.
5. Clique em **selecionar a aplicação** ao lado da **aplicação Targeted**. O painel de **aplicações Associado** é apresentado. 
6. No painel de **aplicações direcionado,** escolha a aplicação gerida para associar à política de configuração e clique EM **OK**.
7. Clique em **Seguir** para visualizar a página **Definições.**
8. Na caixa de dropdown, selecione o formato de definições de **configuração**. Selecione um dos seguintes métodos para adicionar informações de configuração:
    - **Utilizar estruturador de configuração**
    - **Introduzir dados XML**<br><br>
    Para obter detalhes sobre a utilização do estruturador de configuração, veja [Utilizar estruturador de configuração](#use-configuration-designer). Para obter detalhes sobre a introdução de dados XML, veja [Introduzir dados XML](#enter-xml-data). 
9. Clique em **Seguir** para exibir a página **de Tarefas.**
10. Na caixa de dropdown ao lado da **Atribuição para**, selecione **grupos selecionados,** **Todos os utilizadores,** **Todos os dispositivos,** ou **todos os utilizadores e todas as pessoas se desloquem** para atribuir a política de configuração da aplicação.

    ![Captura de ecrã do separador Atribuições de política – Incluir](./media/app-configuration-policies-use-ios/app-config-policy01.png)

11. Selecione **todos os utilizadores** na caixa de dropdown.

    ![Captura de ecrã do menu pendente Atribuições de política – Todos os Utilizadores](./media/app-configuration-policies-use-ios/app-config-policy02.png)

12. Clique em **Selecionar grupos para excluir** para apresentar o painel relacionado.

    ![Screenshot de atribuições políticas - Selecione grupos para excluir o painel](./media/app-configuration-policies-use-ios/app-config-policy03.png)

13. Escolha os grupos que pretende excluir e, em seguida, clique em **Selecionar**.

    >[!NOTE]
    >Ao adicionar um grupo, se outro grupo já tiver sido incluído num determinado tipo de atribuição, o mesmo estará pré-selecionado e inalterável para outras atribuições de inclusão. Por conseguinte, esse grupo que foi utilizado não poderá ser utilizado como um grupo excluído.

14. Clique em **Seguir** para exibir a página **Review + criar.**
15. Clique **em Criar** para adicionar a política de configuração da aplicação ao Intune.

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

Para dispositivos iOS/iPadOS, utilize os seguintes pares chave/valor:

| **Chave** | **Valores** |
|----|----|
| IntuneMAMAllowedAccountsOnly | <ul><li>**Ativada**: a única conta autorizada é a conta de utilizador gerido definida pela chave [IntuneMAMUPN](data-transfer-between-apps-manage-ios.md#configure-user-upn-setting-for-microsoft-intune-or-third-party-emm).</li><li>**Desativado** (ou qualquer valor que não seja sensível a maiúsculas/minúsculas que corresponda a **ativado**): qualquer conta é permitida.</li></ul> |
| IntuneMAMUPN | <ul><li>UPN da conta permitida para assinar na app.</li><li> Para os dispositivos inscritos no Intune, o token <code>{{userprincipalname}}</code> pode ser utilizado para representar a conta de utilizador inscrito.</li></ul>  |

   > [!NOTE]
   > Deve utilizar o OneDrive para iOS 10.34 ou mais tarde, Outlook para iOS 2.99.0 ou mais tarde ou Edge para iOS 44.8.7 ou posterior e a aplicação deve ser direcionada com políticas de proteção de [aplicações Intune](app-protection-policy.md) ao permitir apenas contas de organização configuradas com identidade múltipla.

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
- \{\{nome principal de utilizador\}\}— por exemplo, **John\@contoso.com**
- \{\{\}de\}correio - por exemplo, **John\@contoso.com**
- \{\{partialupn\}\} – por exemplo, **João**
- \{\{accountid\}\} – por exemplo, **fc0dc142-71d8-4b12-bbea-bae2a8514c81**
- \{\{deviceid\}\} – por exemplo, **b9841cd9-9843-405f-be28-b2265c59ef97**
- \{\{userid\}\} – por exemplo, **3ec2c00f-b125-4519-acf0-302ac3761822**
- \{\{username\}\} – por exemplo, **John Doe**
- \{\{número de série\}\}— por exemplo, **F4KN99ZUG5V2** (para dispositivos iOS/iPadOS)
- \{\{número de sérielast4dígitos\}\}— por exemplo, **G5V2** (para dispositivos iOS/iPadOS)
- \{\{aaddeviceid\}\} – por exemplo, **ab0dc123-45d6-7e89-aabb-cde0a1234b56**

## <a name="configure-the-company-portal-app-to-support-ios-and-ipados-dep-devices"></a>Configure a app Portal da Empresa para apoiar dispositivos iOS e iPadOS DEP

As inscrições do DEP (Programa de Inscrição de Dispositivos da Apple) não são compatíveis com a versão da app store da aplicação Portal da Empresa. No entanto, pode configurar a aplicação Portal da Empresa para suportar dispositivos iOS/iPadOS DEP utilizando os seguintes passos.

1. Intune, adicione a aplicação Intune Company Portal, se necessário, indo para **Intune** > **Apps** > Todas **as aplicações** > **Add.**
2. Vá a **Apps** > políticas de configuração de **Apps,** para criar uma política de configuração de aplicações para a aplicação Portal da Empresa.
3. Crie uma política de configuração de aplicativos com o XML abaixo. Mais informações sobre como criar uma política de configuração de apps e introduzir dados XML podem ser encontradas em Políticas de configuração de [aplicações Add para dispositivos iOS/iPadOS geridos](app-configuration-policies-use-ios.md).

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

3. Implemente o Portal da Empresa para dispositivos com a política de configuração da aplicação direcionada aos grupos pretendidos. Certifique-se de que apenas implementa a política em grupos de dispositivos que já estão inscritos em DEP.
4. Informe os utilizadores finais para assinarem na aplicação Portal da Empresa quando esta for instalada automaticamente.

## <a name="monitor-iosipados--app-configuration-status-per-device"></a>Monitorize o estado de configuração da aplicação iOS/iPadOS por dispositivo 
Uma vez atribuída uma política de configuração, pode monitorizar o estado de configuração da aplicação iOS/iPadOS para cada dispositivo gerido. No **Microsoft Intune**, no portal do Azure, selecione **Dispositivos** > **Todos os dispositivos**. A partir da lista de dispositivos geridos, selecione um dispositivo específico para exibir um painel para o dispositivo. No painel do dispositivo, selecione **a configuração**da Aplicação .  

## <a name="additional-information"></a>Informações adicionais

- [Implementação de Outlook para configurações de configurações de aplicações iOS/iPadOS e Android](https://docs.microsoft.com/exchange/clients-and-mobile-in-exchange-online/outlook-for-ios-and-android/outlook-for-ios-and-android-configuration-with-microsoft-intune)

## <a name="next-steps"></a>Próximos passos

Continue a [atribuir](apps-deploy.md) e [monitorizar](apps-monitor.md) a aplicação.

---
# required metadata

title: Resolver conflitos de políticas de GPO e do Intune | Microsoft Intune
description:
keywords:
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: e76af5b7-e933-442c-a9d3-3b42c5f5868b

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Resolver conflitos de políticas de Objetos de Política de Grupo (GPO) e do Microsoft Intune
O Intune utiliza políticas que o ajudam a gerir definições nos computadores que gere. Por exemplo, poderia utilizar uma política para controlar as definições da Firewall do Windows nos computadores. Muitas das definições do Intune são semelhantes a definições que poderá configurar com a Política de Grupo do Windows. No entanto, é possível que por vezes os dois métodos entrem em conflito um com o outro.

Quando ocorrem conflitos, a Política de Grupo ao nível do domínio tem prioridade sobre a política do Intune, a não ser que o computador não consiga iniciar sessão no domínio. Neste caso, a política do Intune é aplicada ao computador cliente.

## O que fazer se estiver a utilizar a Política de Grupo
Verifique que as políticas que aplicar não estão a ser geridas pela Política de Grupo. Para ajudar a impedir conflitos, pode aplicar um ou mais dos seguintes métodos:

-   Antes de instalar o cliente do Intune, mova os seus computadores para uma unidade organizacional (UO) do Active Directory que não tenha definições de Política de Grupo aplicadas. Também pode bloquear a herança da Política de Grupo em UOs que contenham computadores inscritos no Intune aos quais não pretenda aplicar definições da Política de Grupo.

-   Utilize um filtro WMI ou um filtro de segurança para restringir GPOs apenas a computadores que não são geridos pelo Intune. Para obter informações e exemplos sobre como o fazer, consulte a secção [Como filtrar Objetos de Política de Grupo existentes para evitar Conflitos com políticas do Microsoft Intune](resolve-gpo-and-microsoft-intune-policy-conflicts.md#BKMK_Filter) abaixo.

-   Desative ou remova os Objetos de Política de Grupo que estiverem em conflito com as políticas do Intune.

Para obter mais informações sobre o Active Directory e a Política de Grupo do Windows, consulte a sua Documentação do Windows Server.

## Como filtrar GPOs existentes para evitar conflitos com políticas do Intune
Se detetou GPOs com definições que estão em conflito com políticas do Intune, pode utilizar um dos seguintes métodos de filtragem para restringir esses GPOs apenas a computadores que não são geridos pelo Intune.

### Utilizar filtros WMI
Os filtros WMI aplicam seletivamente GPOs a computadores que cumprem as condições de uma consulta. Para aplicar um filtro WMI, implemente uma instância de classe WMI em todos os computadores da empresa antes de inscrever qualquer computador no serviço Intune.

#### Para aplicar filtros WMI a um GPO

1.  Crie um ficheiro de objeto de gestão ao copiar e colar o seguinte para um ficheiro de texto e, em seguida, guarde-o numa localização conveniente com o nome **WIT.mof**. O ficheiro contém a instância de classe WMI que implementa nos computadores que pretende inscrever no serviço Intune.

    ```
    //Beginning of MOF file.
    #pragma classflags("forceupdate")
    #pragma namespace ("\\\\.\\Root")
    instance of __Namespace
    {
       Name = "WindowsIntune";
    };

    #pragma namespace ("\\\\.\\Root\\WindowsIntune")
    [
       Description("This class defines Microsoft Intune common properties")
    ]
    class WindowsIntune_ManagedNode
    {
       [ read, Description("This defines whether Microsoft Intune Policy is enabled"): DisableOverride ToSubClass ]
       boolean WindowsIntunePolicyEnabled;
       [ read, key, Description("This property defines the version." "Example: 1.0"): ToSubClass ]
       string Version;
    };

    instance of WindowsIntune_ManagedNode
    {
       Version = "1.0";
       WindowsIntunePolicyEnabled = 1;
    };
    ```

2.  Utilize um script de arranque ou Política de Grupo para implementar o ficheiro. O que se segue é o comando de implementação do script de arranque. A instância de classe WMI tem de ser implementada antes de inscrever computadores cliente no serviço Intune.

    **C:/Windows/System32/Wbem/MOFCOMP &lt;caminho para o ficheiro MOF&gt;\wit.mof**

3.  Execute um dos seguintes comandos para criar os filtros WMI, consoante o GPO que pretende filtrar se aplique a computadores que são geridos com o Intune ou a computadores que não são geridos com o Intune.

    -   Para GPOs que se aplicam a computadores que não são geridos com o Intune, utilize o seguinte:

        ```
        Namespace:root\WindowsIntune
        Query:  SELECT WindowsIntunePolicyEnabled FROM WindowsIntune_ManagedNode WHERE WindowsIntunePolicyEnabled=0
        ```

    -   Para GPOs que se aplicam a computadores que são geridos com o Intune, utilize o seguinte:

        ```
        Namespace:root\WindowsIntune
        Query:  SELECT WindowsIntunePolicyEnabled FROM WindowsIntune_ManagedNode WHERE WindowsIntunePolicyEnabled=1
        ```

4.  Edite o GPO na consola de Gestão de Políticas de Grupo para aplicar o filtro WMI que criou no passo anterior.

    -   Para GPOs que se devem aplicar apenas aos computadores que pretende gerir com o Intune, aplique o filtro **WindowsIntunePolicyEnabled=1**

    -   Para GPOs que se devem aplicar apenas aos computadores que não pretende gerir com o Intune, aplique o filtro **WindowsIntunePolicyEnabled=0**

Para mais informações sobre como aplicar filtros WMI na Política de Grupo, consulte a mensagem de blogue [Filtragem de Segurança, Filtragem WMI e Filtragem ao Nível dos Itens nas Preferências das Políticas de Grupo](http://go.microsoft.com/fwlink/?LinkId=177883)

### Utilizar filtros de grupos de segurança
A Política de Grupo permite-lhe aplicar GPOs apenas aos grupos de segurança especificados na área **Filtragem de Segurança** da consola de Gestão de Políticas de Grupo de um GPO selecionado. Por predefinição, todos os GPOs são aplicados aos **Utilizadores Autenticados**

-   No snap-in **Utilizadores e Computadores do Active Directory**, crie um novo grupo de segurança que contenha computadores e contas de utilizador que não pretende gerir com o Intune. Por exemplo, pode dar o nome **Não Pertencentes ao Microsoft Intune**

-   Na consola de Gestão de Políticas de Grupo, no separador **Delegação** do GPO selecionado, clique com o botão direito do rato no novo grupo de segurança para delegar as permissões **Ler** e **Aplicar Política de Grupo** adequadas, tanto aos utilizadores como aos computadores no grupo de segurança. (As permissões**Aplicar Política de Grupo** estão disponíveis na caixa de diálogo **Avançadas** .)

-   Em seguida, aplique o novo filtro de grupo de segurança a um GPO selecionado e remova o filtro predefinido **Utilizadores Autenticados** .

O novo grupo de segurança deve ser mantido à medida que a inscrição no serviço Intune é alterada.

### Consulte também
[Gerir Computadores com Windows com o Microsoft Intune](manage-windows-pcs-with-microsoft-intune.md)


<!--HONumber=May16_HO2-->



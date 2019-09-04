---
title: Usar modelos para dispositivos Windows 10 no Microsoft Intune-Azure | Microsoft Docs
description: Use modelos administrativos no Microsoft Intune para criar grupos de configurações para dispositivos Windows 10. Use essas configurações em um perfil de configuração de dispositivo para controlar programas do Office, Microsoft Edge, recursos seguros no Internet Explorer, controlar o acesso ao OneDrive, usar recursos de área de trabalho remota, habilitar reprodução automática, definir configurações de gerenciamento de energia, usar a impressão HTTP, Use opções de entrada de usuário diferentes e controle o tamanho do log de eventos.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 8/28/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 608f9045d676a756c4ee7440072040075e497605
ms.sourcegitcommit: 7269abaefb2857bc8b343896bb2138bdb01bf8dc
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/03/2019
ms.locfileid: "70214330"
---
# <a name="use-windows-10-templates-to-configure-group-policy-settings-in-microsoft-intune"></a>Use os modelos do Windows 10 para definir as configurações de política de grupo no Microsoft Intune

Ao gerenciar dispositivos em sua organização, você deseja criar grupos de configurações que se aplicam a diferentes grupos de dispositivos. Por exemplo, você tem vários grupos de dispositivos. Para o GroupA, você deseja atribuir um conjunto específico de configurações. Para GroupB, você deseja atribuir um conjunto diferente de configurações. Você também deseja uma exibição simples das configurações que pode configurar.

Você pode concluir essa tarefa usando **modelos administrativos** em Microsoft Intune. Os modelos administrativos incluem centenas de configurações que controlam recursos no Microsoft Edge, Internet Explorer, Microsoft Office programas, área de trabalho remota, OneDrive, senhas e PINs e muito mais. Essas configurações permitem que os administradores de grupo gerenciem políticas de grupo usando a nuvem.

As configurações do Windows são semelhantes às configurações de diretiva de grupo (GPO) no Active Directory (AD). Essas configurações são criadas no Windows e são configurações com [suporte de ADMX](https://docs.microsoft.com/windows/client-management/mdm/understanding-admx-backed-policies) que usam XML. As configurações do Office são ingeridas pelo ADMX e usam as configurações do ADMX nos [arquivos de modelo administrativo do Office](https://www.microsoft.com/download/details.aspx?id=49030). Mas, os modelos do Intune são 100% baseados em nuvem. Eles oferecem uma maneira simples e direta de definir as configurações e localizar as configurações desejadas.

**Modelos administrativos** são criadas no Intune e não exigem personalizações, incluindo o uso de OMA-URI. Como parte da sua solução de MDM (gerenciamento de dispositivo móvel), use essas configurações de modelo como uma loja única para gerenciar seus dispositivos Windows 10.

Este artigo lista as etapas para criar um modelo para dispositivos Windows 10 e mostra como filtrar todas as configurações disponíveis no Intune. Quando você cria o modelo, ele cria um perfil de configuração de dispositivo. Você pode atribuir ou implantar esse perfil em dispositivos Windows 10 em sua organização.

## <a name="before-you-begin"></a>Antes de começar

- Algumas dessas configurações estão disponíveis a partir do Windows 10 versão 1703 (RS2). Para obter a melhor experiência, é recomendável usar o Windows 10 Enterprise versão 1903 (19H1) e mais recente.

- As configurações do Windows usam [CSPs da política do Windows](https://docs.microsoft.com/windows/client-management/mdm/policy-configuration-service-provider#admx-backed-policies). Os CSPs funcionam em diferentes edições do Windows, como Home, Professional, Enterprise e assim por diante. Para ver se um CSP funciona em uma edição específica, vá para [CSPs da política do Windows](https://docs.microsoft.com/windows/client-management/mdm/policy-configuration-service-provider#admx-backed-policies).

## <a name="create-a-template"></a>Criar um modelo

1. Entre no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Selecione **Configuração do dispositivo** > **Perfis** > **Criar perfil**.
3. Introduza as seguintes propriedades:

    - **Nome**: Insira um nome para o perfil.
    - **Descrição**: introduza uma descrição para o perfil. Esta definição é opcional, mas recomendada.
    - **Plataforma**: Selecione **Windows 10 e posterior**.
    - **Tipo de perfil**: Selecione **modelos administrativos**.

4. Selecione **Criar**. Na nova janela, selecione **configurações**. Todas as configurações são listadas e você pode usar as setas antes e próximo para ver mais configurações:

    ![Veja um exemplo de lista de configurações e use os botões anterior e próximo](./media/administrative-templates-windows/administrative-templates-sample-settings-list.png)

    > [!TIP]
    > As configurações do Windows no Intune correlacionam-se ao caminho da política de grupo local que você`gpedit`vê no editor de política de grupo local ().

5. Por padrão, a lista suspensa mostra **todos os produtos**. Na lista, você também pode filtrar as configurações para mostrar apenas as configurações do **Windows** , mostrar apenas as configurações **do Office** ou mostrar apenas as configurações **do Microsoft Edge** :

    ![Filtre a lista para mostrar todas as configurações do Windows ou do Office em modelos administrativos no Intune](./media/administrative-templates-windows/administrative-templates-choose-windows-office-all-products.png)

    > [!NOTE]
    > As configurações do Microsoft Edge se aplicam a:
    >
    > - Windows 10 RS4 e mais recente com [KB 4512509](https://support.microsoft.com/kb/4512509) instalado.
    > - Windows 10 RS5 e mais recente com [KB 4512534](https://support.microsoft.com/kb/4512534) instalado.
    > - Windows 10 19H1 e mais recente com [KB 4512941](https://support.microsoft.com/kb/4512941) instalado.

6. Selecione qualquer configuração. Por exemplo, filtre no **Office**e selecione **Ativar navegação restrita**. Uma descrição detalhada da configuração é mostrada. Escolha **habilitado**, **desabilitado**ou deixe a configuração como **não configurado** (padrão). A descrição detalhada também explica o que acontece quando você escolhe **habilitado**, **desabilitado**ou **não configurado**.
7. Selecione **OK** para guardar as alterações.

Continue a percorrer a lista de configurações e defina as configurações desejadas em seu ambiente. Aqui estão alguns exemplos:

- Use a configuração de **configurações de notificação de macro do VBA** para lidar com macros do VBA em diferentes programas de Microsoft Office, incluindo o Word e o Excel.
- Use a configuração **permitir downloads de arquivos** para permitir ou impedir downloads do Internet Explorer.
- Use **exigir uma senha quando um computador for ativado (conectado)** para solicitar uma senha aos usuários quando os dispositivos forem ativados do modo de suspensão.
- Use a configuração **baixar controles ActiveX não assinados** para impedir que os usuários baixem controles ActiveX não assinados do Internet Explorer.
- Use a configuração **Desativar restauração do sistema** para permitir ou impedir que os usuários executem uma restauração do sistema no dispositivo.
- Use a configuração **permitir importação de favoritos** para permitir ou impedir que os usuários importem favoritos de outro navegador para o Microsoft Edge.
- E muito mais...

## <a name="find-some-settings"></a>Localizar algumas configurações

Há centenas de configurações disponíveis nesses modelos. Para facilitar a localização de configurações específicas, use os recursos internos:

- Em seu modelo, selecione as colunas **configurações**, **estado**, **tipo de configuração**ou **caminho** para classificar a lista. Por exemplo, selecione a coluna **caminho** para ver todas as configurações no `Microsoft Excel` caminho:

  ![Clique em caminho para mostrar todas as configurações agrupadas pela política de grupo ou caminho ADMX em modelos administrativos no Intune](./media/administrative-templates-windows/path-filter-shows-excel-options.png)

- Em seu modelo, use a caixa de **pesquisa** para localizar configurações específicas. Você pode pesquisar definindo o título ou o caminho. Por exemplo, pesquise por `copy`. Todas as configurações com `copy` são mostradas:

  ![Procurar cópia para mostrar todas as configurações do Windows e do Office em modelos administrativos no Intune](./media/administrative-templates-windows/search-copy-settings.png) 

  Em outro exemplo, pesquise `microsoft word`. Você verá todas as configurações que pode definir para o programa Microsoft Word. `explorer` Procure para ver todas as configurações do Internet Explorer que você pode adicionar ao seu modelo.

## <a name="next-steps"></a>Passos seguintes

O modelo é criado, mas não está fazendo nada ainda. Em seguida, [atribua o modelo, também chamado de perfil,](device-profile-assign.md) e [monitore seu status](device-profile-monitor.md).

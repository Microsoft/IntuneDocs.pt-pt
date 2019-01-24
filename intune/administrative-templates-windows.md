---
title: Utilizar modelos para dispositivos Windows 10 no Microsoft Intune – Azure | Documentos da Microsoft
description: Utilize modelos administrativos no Microsoft Intune para criar grupos de definições para dispositivos Windows 10. Utilize estas definições num perfil de configuração do dispositivo para controlar programas do Office, proteger recursos do Internet Explorer, controlar o acesso para o OneDrive, usar recursos de área de trabalho remotos, ativar a reprodução automática, definir as definições de gestão de energia, utilizar a impressão de HTTP, utilize o utilizador diferente Opções de início de sessão e controlar o tamanho do registo de eventos.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/09/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: d0426b63cb4601a73451ec9509ddea8e39271c29
ms.sourcegitcommit: 4a7421470569ce4efe848633bd36d5946f44fc8d
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/10/2019
ms.locfileid: "54203780"
---
# <a name="windows-10-templates-to-configure-group-policy-settings-in-microsoft-intune"></a>Grupo de modelos do Windows 10 para configurar definições de política no Microsoft Intune

Quando gerir dispositivos na sua organização, em que pretende criar um grupo de definições que são aplicadas a diferentes grupos de dispositivos. Por exemplo, tem vários grupos de dispositivos. Para GroupA, que pretende atribuir um conjunto específico de definições. Para GroupB, que pretende atribuir um conjunto diferente de definições. Também deseje uma simples exibição de definições que pode configurar.

Pode concluir esta tarefa com **modelos administrativos** no Microsoft Intune. Os modelos administrativos incluem centenas de configurações que controlam funcionalidades no Internet Explorer, programas do Microsoft Office, ambiente de trabalho remoto, aceder ao OneDrive, utilizam uma palavra-passe de imagem ou PIN para iniciar sessão e muito mais. Estes modelos são semelhantes às definições de política (GPO) do grupo no Active Directory (AD) e são [definições de segurança de ADMX](https://docs.microsoft.com/windows/client-management/mdm/understanding-admx-backed-policies) que utilizam o XML. No entanto, os modelos no Intune são 100% baseado na nuvem. Eles oferecem mais simples e direta para configurar as definições e localizar as definições que pretende.

**Modelos administrativos** incorporados no Intune e não necessitam de quaisquer personalizações, incluindo a utilização de OMA-URI. Como parte da sua solução de gestão (MDM) de dispositivos móveis, utilize estas definições de modelo como um meio único para gerir os dispositivos Windows 10.

Este artigo apresenta os passos para criar um modelo para dispositivos Windows 10 e mostra como filtrar todas as definições disponíveis no Microsoft Intune. Quando criar o modelo, ele cria um perfil de configuração do dispositivo. Em seguida, pode atribuir ou implementar este perfil para dispositivos Windows 10 na sua organização.

> [!NOTE]
> Modelos administrativos são suportados para dispositivos autónomos. Atualmente não são suportados para dispositivos cogeridos do System Center Configuration Manager (SCCM).

## <a name="create-a-template"></a>Criar um modelo

1. Na [portal do Azure](https://portal.azure.com), selecione **todos os serviços** > Filtrar **Intune** > selecione **Intune**.
2. Selecione **Configuração do dispositivo** > **Perfis** > **Criar perfil**.
3. Introduza as seguintes propriedades:

    - **Nome**: Introduza um nome para o perfil.
    - **Descrição**: Introduza uma descrição para o perfil. Esta definição é opcional, mas recomendada.
    - **Plataforma**: Selecione **Windows 10 e posterior**.
    - **Tipo de perfil**: Selecione **modelos administrativos (pré-visualização)**.

4. Selecione **Criar**. Na nova janela, selecione **definições**. Cada definição estiver listada, e pode usar o antes e, em seguida setas para ver mais definições:

    ![Ver uma lista de exemplo de definições e utilize os botões de anteriores e posteriores](./media/administrative-templates-windows/sample-settings-list-next-page.png)

5. Selecione qualquer definição. Por exemplo, seleccione **permitir transferências de ficheiros**. Uma descrição detalhada da definição é apresentada. Optar por **habilitar**, **desativar**, ou deixe o valor como **não configurado** (predefinição). A descrição detalhada também explica o que acontece quando escolher **habilitar**, **desativar**, ou **não configurado**.
6. Selecione **OK** para guardar as alterações.

Continue percorrer a lista de definições e configurar as definições que pretende no seu ambiente. Aqui estão alguns exemplos:

- Utilize o **definições de notificação de Macro do VBA** definição para lidar com macros VBA em diferentes programas do Microsoft Office, inclusive o Word e Excel.
- Utilize o **permitir transferências de ficheiros** definição para permitir ou impedir que transfere a partir do Internet Explorer.
- Utilize o **exigir uma palavra-passe quando um computador a sair (ligado)** definição para pedir aos utilizadores uma palavra-passe quando os dispositivos sair do modo de suspensão.
- Utilize o **Download não controles ActiveX assinados** definição para impedir que os utilizadores a transferência não assinados controles ActiveX do Internet Explorer.
- Utilize o **desativar a restauração do sistema** definição para permitir ou impedir que os utilizadores a executar uma restauração do sistema no dispositivo.
- E muito mais...

## <a name="find-some-settings"></a>Encontrar algumas definições

Centenas de configurações estão disponíveis nestes modelos. Para tornar mais fácil encontrar as definições específicas, utilize as funcionalidades incorporadas:

- No seu modelo, selecione o **configurações**, **estado**, ou **caminho** colunas para ordenar a lista. Por exemplo, selecione o **caminho** coluna para ver todas as definições no `Microsoft Excel` caminho:

  ![Clique em caminho para ordenar alfabeticamente](./media/administrative-templates-windows/path-filter-shows-excel-options.png)

- No seu modelo, utilize o **pesquisa** caixa para encontrar as definições específicas. Por exemplo, procure `copy`. Todas as configurações com `copy` são apresentadas:

  ![Clique em caminho para ordenar alfabeticamente](./media/administrative-templates-windows/search-copy-settings.png)

  Noutro exemplo, procure `microsoft word`. Ver todas as definições que pode definir para o programa do Microsoft Word. Procure `explorer` para ver todas as configurações do Internet Explorer pode adicionar ao seu modelo.

## <a name="next-steps"></a>Passos Seguintes

O modelo é criado, mas ele não faz nada ainda. Em seguida, [atribuir o modelo, também designado por perfil](device-profile-assign.md) e [monitorizar o estado](device-profile-monitor.md).
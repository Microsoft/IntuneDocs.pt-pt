---
title: Configurar o Windows Update para Empresas no Microsoft Intune – Azure | Microsoft Docs
description: Atualize as definições de Atualização de Software num perfil para criar uma cadência de atualização, analise a conformidade e coloque atualizações em pausa nas definições do Windows Update para Empresas através do Microsoft Intune em dispositivos com o Windows 10.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/12/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: coryfe
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 05fd362ff6f068669b85b9b78cb1dfd7d3c8011f
ms.sourcegitcommit: 430b290474b11f9df87785b01edc178e6bae2049
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/05/2019
ms.locfileid: "57397280"
---
# <a name="manage-software-updates-in-intune"></a>Gerir atualizações de software no Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Utilize o Intune para definir os anéis de atualização que especificar como e quando o Windows como um serviço atualiza os dispositivos Windows 10. Cadências de atualização são as políticas que atribuir aos grupos de dispositivos. Ao utilizar anéis de atualização, pode criar uma estratégia de atualização que reflete as necessidades da sua empresa. Para obter mais informações, veja [Manage updates using Windows Update for Business (Gerir atualizações através do Windows Update para Empresas)](https://technet.microsoft.com/itpro/windows/manage/waas-manage-updates-wufb).

Com o Windows 10, as novas Atualizações de Funcionalidades e Atualizações de Qualidade incluem os conteúdos de todas as atualizações anteriores. Desde que instale a atualização mais recente, pode ter a certeza de que os seus dispositivos com o Windows 10 estão atualizados. Ao contrário das versões anteriores do Windows, agora tem de instalar toda a atualização em vez de parte de uma atualização.


Ao utilizar o Windows Update para Empresas, pode simplificar a experiência de gestão de atualizações. Não precisa de aprovar atualizações individuais de grupos de dispositivos. Pode gerir o risco nos seus ambientes ao configurar uma estratégia de implementação de atualizações. O Intune fornece a capacidade de [configurar definições de atualização](windows-update-settings.md) em dispositivos e dá-lhe a capacidade de diferir a instalação da atualização. O Intune não armazena as atualizações, mas apenas a atribuição da política de atualização. Os dispositivos acedem diretamente ao Windows Update para obter as atualizações. Esta coleção de definições que configura quando as atualizações do Windows 10 são instaladas é chamada um *cadência de atualização do Windows 10*.

Suporte de cadências de atualização do Windows 10 [etiquetas de âmbito](scope-tags.md). Pode utilizar etiquetas de âmbito com cadências de atualização para o ajudar a filtrar e gerir conjuntos de configurações que utilizar.

## <a name="prerequisites"></a>Pré-requisitos  

Tem de ser cumpridos os seguintes pré-requisitos para utilizar as atualizações do Windows para dispositivos Windows 10 no Intune.  

- Windows 10 PCs tem de executar, pelo menos, Windows 10 Pro com a atualização de aniversário do Windows ou posterior (versão 1607 ou posterior)
- Windows Update suporta as seguintes edições do Windows 10:
  - Windows 10
  - Windows 10 Team (para dispositivos Surface Hub)
  - Windows Holographic for Business  

    Windows Holographic for Business suporta um subconjunto das definições de atualizações do Windows, incluindo:
    - **Comportamento de atualização automática**
    - **Atualizações de produtos da Microsoft**
    - **Canal de serviço**: Suporta **canal semianual** e **canal semianual (direcionada)** opções  

    Para obter mais informações, consulte [gerir Windows Holographic](windows-holographic-for-business.md)  
  
  Os dispositivos com o Windows 10 Mobile não são suportados.

- Em dispositivos Windows, **comentários e diagnósticos** > **dados de diagnóstico e utilização** tem de ser definido como **básica**, **avançado**, ou **completo**.  

  Pode configurar esta definição manualmente ou utilizar um perfil de restrição de dispositivos Intune para Windows 10 e posterior. Para utilizar o perfil de restrição de dispositivos, configure a definição **gerais** > **submissão de dados de diagnóstico** para, pelo menos, **básica**. Para obter mais informações sobre os perfis de dispositivo, veja [Configurar definições de restrições de dispositivos](device-restrictions-configure.md).  

- Se utilizar o portal clássico do Azure, [migre as suas definições para o portal do Azure](#migrate-update-settings-to-the-azure-portal).  

## <a name="create-and-assign-update-rings"></a>Criar e atribuir cadências de atualização

1. Inicie sessão no [portal do Azure](https://portal.azure.com).
2. Selecione **Todos os serviços**, filtre por **Intune** e, em seguida, selecione **Microsoft Intune**.
3. Selecione **Atualizações de software** > **Cadências de Atualização do Windows 10** > **Criar**.
4. Introduza um nome, uma descrição (opcional) e, em seguida, selecione **Configurar**.
5. Na **definições**, configurar as definições para as suas necessidades de negócio. Para obter informações sobre as definições disponíveis, consulte [Windows atualizar as definições de](windows-update-settings.md).  
6. Quando terminar, selecione **OK**. Em **Criar Cadência de Atualização**, selecione **Criar**. O novo anel de atualização é apresentado na lista de anéis de atualização.
7. Para atribuir o anel, na lista de cadências de atualização, selecione um anel e, em seguida, no \<nome do anel > separador, escolha **atribuições**.
8. Utilize o **inclusão** e **excluir** separadores para definir que agrupa Este anel está atribuído a e, em seguida, selecione **guardar** para concluir a atribuição.

## <a name="manage-your-windows-10-update-rings"></a>Gerir a sua cadência de atualização do Windows 10
No portal, pode selecionar uma cadência de atualização do Windows 10 para abrir o respetivo **descrição geral** painel. Neste painel pode ver o estado de atribuição de anéis e realizar ações adicionais para gerir o anel. 
### <a name="to-view-an-updates-rings-overview-pane"></a>Para ver um painel de descrição geral de cadência de atualizações: 
1. Inicie sessão no Portal do Azure.
2. Navegue para **Intune** > **atualizações de Software** > **Cadências de atualização do Windows 10**.
3. Selecione a cadência de atualização que pretende ver ou gerir.  

Além de visualizar o estado da atribuição, pode selecionar as seguintes ações na parte superior do painel de descrição geral para gerir o anel de atualização:  
- [Eliminar](#delete)  
- [Colocar em pausa](#pause)  
- [Retomar](#resume)  
- [Extend](#extend)  
- [Uninstall](#uninstall)  

![Ações disponíveis](./media/windows-update-for-business-configure/overview-actions.png)

### <a name="delete"></a>Eliminar  
Selecione **eliminar** para parar de impor as definições do anel de atualização do Windows 10 selecionado. A eliminar um anel remove a respetiva configuração do Intune para que o Intune já não se aplica e impõe essas definições.  

A eliminar um anel do Intune não modifica as definições nos dispositivos que foram atribuídos a cadência de atualização.  Em vez disso, o dispositivo mantém as definições atuais. Isso é porque dispositivos não mantêm um registro histórico de quais as definições foram anteriormente no local e uma vez que o dispositivo pode receber definições de cadências de atualização adicionais que permanecem ativas.  

#### <a name="to-delete-a-ring"></a>Para eliminar um anel  
1. Ao visualizar a página de descrição geral para uma cadência de atualização, selecione **eliminar**.  
2. Selecione **OK**.  

### <a name="pause"></a>Colocar em pausa  
Selecione **colocar em pausa** para impedir que os dispositivos atribuídos a receber atualizações de funcionalidades ou atualizações de qualidade até 35 dias desde o momento em que colocar em pausa o anel. Após ter decorrido o número máximo de dias, a funcionalidade de pausa expira automaticamente e o dispositivo procura atualizações aplicáveis nas Atualizações do Windows. Após esta procura, pode colocar as atualizações em pausa novamente. Se retomar uma pausa cadência de atualização e, em seguida, colocar em pausa novamente, esse anel reposições de período de pausa 35 dias.  

 #### <a name="to-pause-a-ring"></a>Para colocar em pausa um anel  
1. Ao visualizar a página de descrição geral para uma cadência de atualização, selecione **pausa**.  
2. Selecione **funcionalidade** ou **qualidade** para colocar em pausa esse tipo de atualização e, em seguida, selecione **OK**.  
3. Depois de colocar em pausa o tipo de uma atualização, pode selecionar a colocar em pausa novamente para colocar em pausa o outro tipo de atualização.  

Quando um tipo de atualização está em pausa, o painel de descrição geral para esse anel mostra quantos dias faltam para essa atualização escreva retoma.

> [!IMPORTANT]  
> Depois de emitir um comando de pausa, dispositivos receberão este comando da próxima vez que se registarem no serviço. É possível que instalem uma atualização agendada antes do registo. Além disso, se um dispositivo de destino for desativado quando emitir o comando de pausa, ao desativá-lo, este poderá transferir e instalar atualizações agendadas antes do registo no Intune.

### <a name="resume"></a>Retomar  
Embora uma cadência de atualização está em pausa, pode selecionar **retomar** para restaurar as atualizações de qualidade e de funcionalidades para esse anel para operação do Active Directory. Após retomar uma cadência de atualização, pode interromper esse anel novamente.  

#### <a name="to-resume-a-ring"></a>Para retomar um anel  
1. Ao visualizar a página de descrição geral para um anel de atualização em pausa, selecione **retomar**.  
2. Selecione entre as opções disponíveis para retomar a qualquer um **funcionalidade** ou **qualidade** atualizações e, em seguida, selecione **OK**.  
3. Após retomar um tipo de atualização, pode selecionar retomar novamente para retomar o outro tipo de atualização.  

### <a name="extend"></a>Expandir  
Embora uma cadência de atualização está em pausa, pode selecionar **expandir** repor o período de pausa de atualizações de qualidade e funcionalidade para esse anel de atualização para 35 dias.  

#### <a name="to-extend-the-pause-period-for-a-ring"></a>Para estender o período de pausa para um anel  
1. Ao visualizar a página de descrição geral para um anel de atualização em pausa, selecione **expandir**. 
2. Selecione entre as opções disponíveis para retomar a qualquer um **funcionalidade** ou **qualidade** atualizações e, em seguida, selecione **OK**.  
3. Depois de expandir a pausa para o tipo de uma atualização, pode selecionar expandir novamente para estender o outro tipo de atualização.  

### <a name="uninstall"></a>Desinstalar  
Um administrador do Intune pode utilizar **desinstalação** desinstalar (reverter) a versão mais recente *funcionalidade* atualização ou a versão mais recente *qualidade* atualização para uma cadência de atualização do Active Directory ou em pausa. Após a desinstalação de um tipo, em seguida, pode desinstalar o outro tipo. Intune não suporta ou gerir a capacidade de utilizadores para desinstalar as atualizações.  

Para desinstalação seja concluída com êxito:  
- Um dispositivo tem de executar o Windows 10 de Abril de 2018 atualização (versão 1803) ou posterior.  

Um dispositivo tem de ter instalado a atualização mais recente. Uma vez que as atualizações são cumulativas, dispositivos que instalam a atualização mais recente terão a atualização mais recente de funcionalidade e qualidade. É um exemplo de quando utilizar esta opção para reverter a última atualização deve detetar um problema de última hora nos seus computadores Windows 10.  

Quando usar a desinstalação, considere o seguinte:  
- A desinstalação de uma atualização da funcionalidade ou qualidade só está disponível para o canal de serviço onde o dispositivo está ativado.  

- Usando desinstalar funcionalidade ou as atualizações de qualidade aciona uma política para restaurar a atualização anterior nas suas máquinas do Windows 10.  

- Num dispositivo Windows 10, após uma atualização de qualidade é revertida com êxito, os utilizadores finais continuam a ver a atualização listada no **definições do Windows** > **atualiza**  >  **Histórico de atualização**.  

- Para atualizações de funcionalidades especificamente, o tempo, pode desinstalar a atualização de funcionalidade é limitado de 2-60 dias, conforme configurado pela definição de atualização de anéis de atualização **período (2 – 60 dias) de desinstalação de atualização de funcionalidades do conjunto**. Não é possível reverter uma atualização de funcionalidade que foi instalada num dispositivo após a atualização de funcionalidade foi instalada para o período de tempo superior configurada período de desinstalação.  

  Por exemplo, considere uma cadência de atualização com uma funcionalidade de desinstalação de atualizações de período de 20 dias. Após 25 dias optar por revertê-lo a atualização mais recente do recurso e utilize a opção de desinstalação.  Dispositivos que instalaram a atualização de funcionalidade há mais de 20 dias não é possível desinstalá-lo como foram removidos os bits necessários como parte da sua manutenção. No entanto, os dispositivos que apenas instalaram a atualização de funcionalidade cópia de segurança para 19 dias atrás podem desinstalar a atualização se eles com êxito der entrada para receber o comando de desinstalação antes de exceder o período de desinstalação de 20 dias.  

Para obter mais informações sobre as políticas de atualização do Windows, consulte [atualizar CSP](https://docs.microsoft.com/windows/client-management/mdm/update-csp) na documentação de gestão de cliente do Windows.  

#### <a name="to-uninstall-the-latest-windows-10-update"></a>Para desinstalar a atualização mais recente do Windows 10  
1. Ao visualizar a página de descrição geral para um anel de atualização em pausa, selecione **desinstalação**.  
2. Selecione entre as opções disponíveis para desinstalar o **funcionalidade** ou **qualidade** atualizações e, em seguida, selecione **OK**.  
3. Depois de acionar a desinstalação para o tipo de uma atualização, pode selecionar desinstalar novamente para desinstalar o tipo de atualização restantes.  

## <a name="migrate-update-settings-to-the-azure-portal"></a>Migrar definições de atualização para o portal do Azure  
O portal clássico do Azure também tem um número limitado de outras definições de atualizações do Windows 10 no perfil de configuração do dispositivo. Se tiver qualquer uma destas definições configuradas quando migrar para o portal do Azure, recomendamos vivamente que siga o seguinte procedimento:  

1. No portal do Azure, crie anéis de atualização do Windows 10 com as definições de que precisa. A definição **Permitir funcionalidades de pré-lançamento** não é suportada no portal do Azure, porque já não é aplicável às compilações do Windows 10 mais recentes. Pode configurar as outras três definições, bem como outras definições de atualizações do Windows 10, quando cria os anéis de atualização.  

   > [!NOTE]  
   > As definições das atualizações do Windows 10 criadas no portal clássico não são apresentadas no portal do Azure após a migração. No entanto, estas definições são aplicadas. Se migrar qualquer uma destas definições e editar a política migrada a partir do portal do Azure, estas definições serão removidas da política.  

2. Elimine as definições de atualização no portal clássico. Depois de migrar para o portal do Azure e adicionar as mesmas definições a uma cadência de atualização, terá de eliminar as definições no portal clássico para evitar potenciais conflitos de políticas. Por exemplo, quando a mesma definição está configurada com valores diferentes, não existe um conflito. Não existem é uma forma fácil de saber por que motivo a definição configurada no portal clássico não apresentada no portal do Azure.  

## <a name="next-steps"></a>Passos Seguintes
[Windows atualizar as definições suportadas pelo Intune](windows-update-settings.md)  

[Relatórios de conformidade do Intune para atualizações](windows-update-compliance-reports.md)


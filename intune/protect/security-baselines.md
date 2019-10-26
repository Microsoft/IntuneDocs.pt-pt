---
title: Usar linhas de base de segurança no Microsoft Intune-Azure | Microsoft Docs
description: Use as configurações de segurança do Windows recomendadas para proteger o usuário e os dados em dispositivos com Microsoft Intune para gerenciamento de dispositivo móvel. Habilitar a criptografia, configurar a proteção avançada contra ameaças do Microsoft defender, controlar o Internet Explorer, definir políticas de segurança locais, exigir uma senha, bloquear downloads da Internet e muito mais.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 09/09/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9df7f5a34313d55b460bf6d8492b0790b1424d2f
ms.sourcegitcommit: 5932da3ed8f52c7b0f0d71c1801f81c85952cf0c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/25/2019
ms.locfileid: "72923369"
---
# <a name="use-security-baselines-to-configure-windows-10-devices-in-intune"></a>Usar linhas de base de segurança para configurar dispositivos Windows 10 no Intune

Use as linhas de base de segurança do Intune para ajudá-lo a proteger e proteger seus usuários e dispositivos. As linhas de base de segurança são grupos pré-configurados de configurações do Windows que ajudam a aplicar um grupo conhecido de configurações e valores padrão que são recomendados pelas equipes de segurança relevantes. Ao criar um perfil de linha de base de segurança no Intune, você está criando um perfil de *configuração de dispositivo* .

Esta funcionalidade aplica-se a:

- Windows 10 versão 1809 e posterior

Você implanta linhas de base de segurança para grupos de usuários ou dispositivos no Intune, e as configurações se aplicam a dispositivos que executam o Windows 10 ou posterior. Por exemplo, a *linha de base de segurança do MDM* habilita automaticamente o BitLocker para unidades removíveis, requer automaticamente uma senha para desbloquear um dispositivo, desabilita automaticamente a autenticação básica e muito mais. Quando um valor padrão não funcionar para o seu ambiente, personalize a linha de base para aplicar as configurações necessárias.  

Tipos de linha de base separados podem incluir as mesmas configurações, mas usam valores padrão diferentes para essas configurações. É importante entender os padrões nas linhas de base que você escolhe usar e, em seguida, modificar cada linha de base para atender às suas necessidades organizacionais.  

> [!NOTE]
> A Microsoft não recomenda o uso de versões prévias de linhas de base de segurança em um ambiente de produção. As configurações em uma linha de base de visualização podem mudar ao longo do curso da versão prévia. 

As linhas de base de segurança podem ajudá-lo a ter um fluxo de trabalho seguro de ponta a ponta ao trabalhar com Microsoft 365. Alguns dos benefícios incluem:

- Uma linha de base de segurança inclui as práticas recomendadas e recomendações sobre configurações que afetam a segurança. Parceiros do Intune com a mesma equipe de segurança do Windows que cria linhas de base de segurança de diretiva de grupo. Essas recomendações são baseadas em orientação e ampla experiência.
- Se você for novo no Intune e não tiver certeza de onde começar, as linhas de base de segurança lhe dão uma vantagem. Você pode criar e implantar rapidamente um perfil seguro, sabendo que está ajudando a proteger os recursos e os dados da sua organização.
- Se você atualmente usa a política de grupo, migrar para o Intune para gerenciamento é muito mais fácil com essas linhas de base. Essas linhas de base são criadas nativamente no Intune e incluem uma experiência de gerenciamento moderna.



As [linhas de base de segurança do Windows](https://docs.microsoft.com/windows/security/threat-protection/windows-security-baselines) são um ótimo recurso para saber mais sobre esse recurso. O MDM ( [Gerenciamento de dispositivo móvel](https://docs.microsoft.com/windows/client-management/mdm/) ) é um excelente recurso sobre o MDM e o que você pode fazer em dispositivos Windows.

## <a name="about-baseline-versions-and-instances"></a>Sobre as versões de linha de base e instâncias

Cada nova instância da versão de uma linha de base pode adicionar ou remover configurações ou introduzir outras alterações. Por exemplo, à medida que novas configurações do Windows 10 se tornam disponíveis com as novas versões do Windows 10, a linha de base de segurança do MDM pode receber uma nova instância de versão que inclui as configurações mais recentes.  

No console do Intune, o bloco de cada linha de base exibe o nome do modelo de linha de base e as informações básicas sobre essa linha de base. As informações incluem quantos perfis você tem que usam esse tipo de linha de base, quantas instâncias separadas (versões) do tipo de linha de base estão disponíveis e uma data da *última publicação* que identifica quando esse modelo de linha de base foi adicionado ao seu locatário. O exemplo a seguir mostra o bloco para uma linha de base de segurança do MDM bem usada:  

![Bloco de linha de base](./media/security-baselines/baseline-tile.png)

Para exibir mais informações sobre as versões de linha de base que você usa, selecione um bloco de linha de base para abrir seu painel de *visão geral* e, em seguida, selecione **versões**. O Intune exibe detalhes sobre as versões da linha de base que estão sendo usadas por seus perfis. No painel versões, você pode selecionar uma única versão para exibir detalhes mais detalhados sobre os perfis que usam essa versão. Você também pode selecionar duas versões diferentes e, em seguida, escolher **comparar linhas de base** para baixar um arquivo CSV que detalha essas diferenças.  

![Comparar linhas de base](./media/security-baselines/compare-baselines.png)

Quando você cria um *perfil*de linha de base de segurança, o perfil usa automaticamente a instância de linha de base de segurança lançada mais recentemente.  Você pode continuar a usar e editar perfis que você criou anteriormente, que usam uma instância de versão de linha de base anterior, incluindo linhas de base criadas usando uma versão de visualização. 

Você pode optar por [alterar a versão](#change-the-baseline-version-for-a-profile) de uma linha de base que está em uso com um determinado perfil. Isso significa que quando uma nova versão sair, você não precisará criar um novo perfil de linha de base para tirar proveito dela. Em vez disso, quando estiver pronto, você poderá selecionar um perfil de linha de base e usar a opção interna para alterar a versão da instância para esse perfil para um novo.  

## <a name="available-security-baselines"></a>Linhas de base de segurança disponíveis 

 Você pode usar uma ou mais das linhas de base disponíveis no ambiente do Intune ao mesmo tempo. Você também pode usar várias instâncias das mesmas linhas de base de segurança que têm personalizações diferentes. 

Ao usar várias linhas de base de segurança, examine as configurações em cada uma para identificar quando linhas de base diferentes apresentam valores conflitantes para a mesma configuração. Como você pode implantar linhas de base de segurança que são projetadas para diferentes intenções e implantar várias instâncias da mesma linha de base que inclui configurações personalizadas, você pode criar [conflitos de configuração para dispositivos que devem ser investigados e resolvido](security-baselines-monitor.md#troubleshoot-using-per-setting-status).  Além disso, lembre-se dos [perfis de configuração do dispositivo](../configuration/device-profiles.md), que podem definir muitas das mesmas configurações como linhas de base de segurança. 



As seguintes instâncias de linha de base de segurança estão disponíveis para uso com o Intune. Use os links para exibir as configurações da instância mais recente de cada linha de base. 

- **Linha de base de segurança do MDM**
  - [Linha de base de segurança do MDM para maio de 2019](security-baseline-settings-mdm-all.md?pivots=mdm-may-2019)
  - [Visualização: linha de base de segurança do MDM para outubro de 2018](security-baseline-settings-mdm-all.md?pivots=mdm-preview)

- **Linha de base do Microsoft defender ATP**  
  *(Para usar essa linha de base, seu ambiente deve atender aos pré-requisitos para usar a [proteção avançada contra ameaças do Microsoft defender](advanced-threat-protection.md#prerequisites))* .
  - [Linha de base do Microsoft defender ATP](security-baseline-settings-defender-atp.md)  

  > [!NOTE]
  > A linha de base de segurança do Microsoft defender ATP foi otimizada para dispositivos físicos e não é recomendada no momento para uso em VMs (máquinas virtuais) ou pontos de extremidade de VDI. Determinadas configurações de linha de base podem afetar sessões interativas remotas em ambientes virtualizados.  Para obter mais informações, consulte [aumentar a conformidade com a linha de base de segurança do Microsoft defender ATP](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/configure-machines-security-baseline) na documentação do Windows.

Você pode continuar a usar e editar perfis criados anteriormente com base em um modelo de visualização, mesmo quando esse modelo de visualização não está mais disponível para a criação de novos perfis. 

## <a name="manage-baselines"></a>Gerenciar linhas de base  

As tarefas comuns quando você trabalha com linhas de base de segurança incluem:
- [Criar um perfil](#create-the-profile) – para definir as configurações que você deseja usar e, em seguida, atribuir a linha de base a grupos.
- [Alterar a versão](#change-the-baseline-version-for-a-profile) – altere a versão de linha de base em uso por um perfil.
- [Remover uma atribuição de linha de base](#remove-a-security-baseline-assignment) – saiba o que acontece quando você interrompe o gerenciamento de configurações com uma linha de base de segurança.


### <a name="prerequisites"></a>Pré-requisitos
- Para gerenciar linhas de base no Intune, sua conta deve ter a função interna do [Gerenciador de políticas e perfis](../fundamentals/role-based-access-control.md#built-in-roles) .

- O uso de algumas linhas de base pode exigir que você tenha uma assinatura ativa para serviços adicionais, como o Microsoft defender ATP.  


### <a name="create-the-profile"></a>Criar o perfil

1. Entre no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) e, em seguida, selecione **segurança do dispositivo** >  linhas de**base de segurança** para exibir a lista de linhas de base disponíveis.


    ![Selecione uma linha de base de segurança para configurar](./media/security-baselines/available-baselines.png)

2. Selecione a linha de base que você deseja usar e, em seguida, selecione **Criar perfil**.  

3. Na guia **noções básicas** , especifique as seguintes propriedades:

    - **Nome**: Insira um nome para seu perfil de linhas de base de segurança. Por exemplo, insira *perfil padrão para o defender ATP*.

    - **Descrição**: Insira algum texto que descreva o que essa linha de base faz. A descrição é para que você insira qualquer texto desejado. É opcional, mas recomendado.  

   Selecione **Avançar** para ir para a próxima guia. Depois de avançado para uma nova guia, você pode selecionar o nome da guia para retornar a uma guia exibida anteriormente.  

4. Na guia definições de configuração, exiba os grupos de **configurações** que estão disponíveis na linha de base selecionada. Você pode expandir um grupo para exibir as configurações nesse grupo e os valores padrão para essas configurações na linha de base. Para localizar configurações específicas:
   - Selecione um grupo para expandir e examine as configurações disponíveis.  
   - Use a barra de *pesquisa* e especifique palavras-chave que filtram a exibição para exibir somente os grupos que contêm seus critérios de pesquisa.  
 
   Cada configuração em uma linha de base tem uma configuração padrão para essa versão de linha de base. Reconfigure as configurações padrão para atender às suas necessidades de negócios. Linhas de base diferentes podem conter a mesma configuração e usar valores padrão diferentes para a configuração, dependendo da intenção da linha de base. 

    ![Expanda um grupo para exibir as configurações para esse grupo](./media/security-baselines/sample-list-of-settings.png)

5. Na guia **marcas de escopo** , selecione **selecionar marcas de escopo** para abrir o painel *selecionar marcas* para atribuir marcas de escopo ao perfil. 

6. Na guia **atribuições** , selecione **Selecionar grupos para incluir** e, em seguida, atribua a linha de base a um ou mais grupos. Use **Selecionar grupos para excluir** para ajustar a atribuição.  

   ![Atribuir um perfil](./media/security-baselines/assignments.png)
  
7. Quando estiver pronto para implantar a linha de base, avance para a guia **revisar + criar** e examine os detalhes da linha de base. Selecione **criar** para salvar e implantar o perfil.  

   Assim que você criar o perfil, ele será enviado por push para o grupo atribuído e poderá ser aplicado imediatamente.

   > [!TIP]  
   > Se você salvar um perfil sem primeiro atribuí-lo a grupos, poderá editar o perfil posteriormente para fazer isso.  

   ![Examinar a linha de base](./media/security-baselines/review.png) 

  
8. Depois de criar um perfil, edite-o indo para **segurança do dispositivo** >  linhas de base de**segurança**, selecione o tipo de linha de base que você configurou e, em seguida, selecione **perfis**. Selecione o perfil na lista de perfis disponíveis e, em seguida, selecione **Propriedades**. Você pode editar as configurações de todas as guias de configuração disponíveis e selecionar **revisar + salvar** para confirmar suas alterações.  

### <a name="change-the-baseline-version-for-a-profile"></a>Alterar a versão de linha de base de um perfil  

Você pode alterar a versão da instância de linha de base que está sendo usada com um perfil.  Ao alterar a versão, você seleciona uma instância disponível da mesma linha de base. Você não pode alterar entre dois tipos de linha de base diferentes, como alterar um perfil de usar uma linha de base para o defender ATP para usar a linha de base de segurança do MDM. 

Ao configurar uma alteração da versão de linha de base, você pode baixar um arquivo CSV que lista as alterações entre as duas versões de linha de base envolvidas. Você também tem a opção de manter todas as suas personalizações da versão de linha de base original ou implementar a nova versão usando todos os seus valores padrão. Você não tem a opção de fazer alterações em configurações individuais quando altera a versão de uma linha de base para um perfil. 

Após a gravação, depois que a conversão for concluída, a linha de base será reimplantada imediatamente em grupos atribuídos.  

**Durante a conversão**:
- Novas configurações que não estavam na versão original que você estava usando são adicionadas e definidas para usar os valores padrão.  

- As configurações que não estão na nova versão de linha de base selecionada são removidas e não são mais impostas por esse perfil de linha de base de segurança.  

  Quando uma configuração não é mais gerenciada por um perfil de linha de base, essa configuração não é redefinida no dispositivo. Em vez disso, a configuração no dispositivo permanece definida para sua última configuração até que algum outro processo gerencie a configuração para alterá-la. Exemplos de processos que podem alterar uma configuração depois de você parar de gerenciá-lo incluem um perfil de linha de base diferente, uma configuração de política de grupo ou uma configuração manual feita no dispositivo. 

#### <a name="to-change-the-baseline-version-for-a-profile"></a>Para alterar a versão de linha de base de um perfil  

1. Entre no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) e, em seguida, selecione **segurança do dispositivo** >  linhas de**base de segurança**e, em seguida, selecione o bloco para o tipo de linha de base que tem o perfil que você deseja alterar.  

2. Em seguida, selecione **perfis**e marque a caixa de seleção do perfil que você deseja editar e, em seguida, selecione **alterar versão**.  

   ![selecionar uma linha de base](./media/security-baselines/select-baseline.png)  

3. No painel **alterar versão** , use a lista suspensa **selecionar uma linha de base de segurança para atualizar** e selecione a instância de versão que você deseja usar.  

   ![selecionar uma versão](./media/security-baselines/select-instance.png)  
   
4. Selecione **examinar atualização** para baixar um arquivo CSV que exibe a diferença entre a versão de instância atual de perfis e a nova versão que você selecionou. Examine esse arquivo para entender quais configurações são novas ou removidas e quais valores padrão para essas configurações estão no perfil atualizado.  

   Quando estiver pronto, continue para a próxima etapa.  

5. Escolha uma das duas opções para **selecionar um método para atualizar o perfil**: 
   - **Aceitar alterações de linha de base, mas manter minhas personalizações de configuração existentes** – essa opção mantém as personalizações feitas no perfil de linha de base e as aplica à nova versão que você selecionou para usar.
   - **Aceitar alterações de linha de base e descartar personalizações de configuração existentes** -essa opção substitui completamente o seu perfil original. O perfil atualizado usará os valores padrão para todas as configurações.  

6. Selecione **Enviar**. As atualizações de perfil para a versão de linha de base selecionada e após a conversão são concluídas, a linha de base é reimplantada imediatamente em grupos atribuídos.

### <a name="remove-a-security-baseline-assignment"></a>Remover uma atribuição de linha de base de segurança
Quando uma configuração de linha de base de segurança não se aplica a um dispositivo ou as configurações em uma linha de base são definidas como *não configuradas*, essas configurações em um dispositivo não são revertidas para uma configuração previamente gerenciada. Em vez disso, as configurações anteriormente gerenciadas no dispositivo mantêm suas últimas configurações como recebidas da linha de base até que algum outro processo atualize essas configurações no dispositivo.  

Outros processos que podem alterar posteriormente as configurações no dispositivo incluem uma linha de base de segurança diferente ou nova, perfil de configuração de dispositivo, configurações de Política de Grupo ou edição manual da configuração no dispositivo.  

## <a name="co-managed-devices"></a>Dispositivos cogerenciados

As linhas de base de segurança em dispositivos gerenciados pelo Intune são semelhantes aos dispositivos cogerenciados com Configuration Manager. Os dispositivos cogerenciados usam System Center Configuration Manager e Microsoft Intune para gerenciar os dispositivos Windows 10 simultaneamente. Ele permite que você anexe a nuvem seu investimento de Configuration Manager existente aos benefícios do Intune. A [visão geral do cogerenciamento](https://docs.microsoft.com/sccm/comanage/overview) é um ótimo recurso se você usar Configuration Manager e também quiser os benefícios da nuvem.

Ao usar dispositivos cogerenciados, você deve alternar a carga de trabalho de **configuração do dispositivo** (suas configurações) para o Intune. As [cargas de trabalho de configuração do dispositivo](https://docs.microsoft.com/sccm/comanage/workloads#device-configuration) fornecem mais informações.  

## <a name="q--a"></a>Perguntas e Respostas

### <a name="why-these-settings"></a>Por que essas configurações?

A equipe de segurança da Microsoft tem anos de experiência trabalhando diretamente com desenvolvedores do Windows e a comunidade de segurança para criar essas recomendações. As configurações nessa linha de base são consideradas as opções de configuração mais relevantes relacionadas à segurança. Em cada nova compilação do Windows, a equipe ajusta suas recomendações com base em recursos recentemente lançados.

### <a name="is-there-a-difference-in-the-recommendations-for-windows-security-baselines-for-group-policy-vs-intune"></a>Há uma diferença nas recomendações para as linhas de base de segurança do Windows para a diretiva de grupo versus o Intune?

A mesma equipe de segurança da Microsoft escolheu e organizou as configurações para cada linha de base. O Intune inclui todas as configurações relevantes na linha de base de segurança do Intune. Há algumas configurações na linha de base da diretiva de grupo que são específicas para um controlador de domínio local. Essas configurações são excluídas das recomendações do Intune. Todas as outras configurações são as mesmas.

### <a name="are-the-intune-security-baselines-cis-or-nsit-compliant"></a>As linhas de base de segurança do Intune estão em conformidade com o CIS ou o NSIT?

Estritamente falando, não. A equipe de segurança da Microsoft consulta as organizações, como CIS, para compilar suas recomendações. No entanto, não há um mapeamento de um para um entre "conformidade com o CIS" e linhas de base da Microsoft.

### <a name="what-certifications-does-microsofts-security-baselines-have"></a>Quais certificações as linhas de base de segurança da Microsoft têm? 

- A Microsoft continua a publicar linhas de base de segurança para políticas de grupo (GPOs) e o [Security Compliance Toolkit](https://docs.microsoft.com/windows/security/threat-protection/security-compliance-toolkit-10), como há muitos anos. Essas linhas de base são usadas por muitas organizações. As recomendações nessas linhas de base são do envolvimento da equipe de segurança da Microsoft com clientes corporativos e agências externas, incluindo o departamento de defesa (DoD), National Institute of Standards and Technology (NIST) e muito mais. Compartilhamos nossas recomendações e linhas de base com essas organizações. Essas organizações também têm suas próprias recomendações que espelham de forma minuciosa as recomendações da Microsoft. Como o MDM (gerenciamento de dispositivo móvel) continua crescendo na nuvem, a Microsoft criou recomendações de MDM equivalentes dessas linhas de base de diretiva de grupo. Essas linhas de base adicionais são internas para Microsoft Intune e incluem relatórios de conformidade em usuários, grupos e dispositivos que seguem (ou não seguem) a linha de base.

- Muitos clientes estão usando as recomendações de linha de base do Intune como um ponto de partida e, em seguida, personalizando-o para atender às suas demandas de segurança e ti. A linha de base de **segurança do MDM** RS5 do Windows 10 da Microsoft é a primeira linha de base a ser lançada. Essa linha de base é criada como uma infraestrutura genérica que permite aos clientes eventualmente importar outras linhas de base de segurança com base em CIS, NIST e outros padrões. Atualmente, ele está disponível para o Windows e, eventualmente, inclui iOS e Android.

- A migração do local Active Directory políticas de grupo para uma solução de nuvem pura usando Azure Active Directory (AD) com Microsoft Intune é uma jornada. Para ajudar, há modelos de política de grupo incluídos no [Security Compliance Toolkit](https://docs.microsoft.com/windows/security/threat-protection/security-compliance-toolkit-10) que podem ajudar a gerenciar dispositivos ingressados no AD híbrido e no Azure AD. Esses dispositivos podem obter as configurações de MDM da nuvem (Intune) e as configurações de política de grupo de controladores de domínio locais, conforme necessário.

## <a name="next-steps"></a>Próximos passos
- Exiba as configurações nas versões mais recentes das linhas de base disponíveis:  
  - [Linha de base de segurança do MDM](security-baseline-settings-mdm-all.md)  
  - [Linha de base do Microsoft defender ATP](security-baseline-settings-defender-atp.md)  

- Verificar o status e monitorar a [linha de base e o perfil](security-baselines-monitor.md)


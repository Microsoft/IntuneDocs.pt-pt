---
title: Verificar o êxito ou falha de linhas de base de segurança no Microsoft Intune – Azure | Documentos da Microsoft
description: Verificar o estado de erro, o conflito e o sucesso ao implementar linhas de base de segurança a utilizadores e dispositivos no Microsoft Intune MDM. Veja como resolver problemas com registos de cliente e as funcionalidades de relatório no Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 06/20/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e3bf59f75d41d50cfd9280251e20964a35a149a8
ms.sourcegitcommit: 256952cac44bc6289156489b6622fdc1a3c9c889
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/26/2019
ms.locfileid: "67403582"
---
# <a name="monitor-security-baseline-and-profiles-in-microsoft-intune"></a>Monitorizar a base de segurança e perfis no Microsoft Intune  

O Intune fornece várias opções para monitorizar as linhas de base de segurança. Pode monitorizar o perfil de linhas de base de segurança que se aplica aos seus utilizadores e dispositivos. Também pode monitorizar a linha de base real e todos os dispositivos que corresponde ao (ou não correspondem) os valores recomendados.

Este artigo orienta-o por meio de ambas as opções de monitorização.

[Linhas de base de segurança no Intune](security-baselines.md) fornece mais detalhes sobre a funcionalidade de linhas de base de segurança no Microsoft Intune.

## <a name="monitor-the-baseline-and-your-devices"></a>Monitorizar a linha de base e seus dispositivos  

Ao monitorizar uma linha de base, obtenha informações sobre o estado de segurança dos seus dispositivos com base nas recomendações da Microsoft. Pode ver estas informações a partir do painel de descrição geral da linha de base de segurança na consola do Intune.  Demora até 24 horas para os dados são apresentados depois do primeiro de atribuir uma linha de base. Alterações posteriores demorar até seis horas a aparecer.  

Para ver dados de monitorização para a linha de base e dispositivos, inicie sessão para o [portal do Intune](https://go.microsoft.com/fwlink/?linkid=2090973). Em seguida, selecione **segurança de dispositivos** > **linhas de base de segurança**, selecione uma linha de base e veja o **descrição geral** painel.

O **descrição geral** painel fornece dois métodos para monitorizar o estado:
- **Vista do dispositivo** – um resumo de quantos dispositivos estão em cada categoria de estado da linha de base.  
- **Por categoria** -uma vista que apresenta cada categoria na linha de base e inclui a percentagem de dispositivos para cada grupo de estado para cada categoria de linha de base. 

Cada dispositivo é representado por um dos seguintes Estados, o que são utilizados em ambos os *dispositivo* modo de exibição e o *por categoria* vistas:  
- **Linha de base de correspondências** -todas as definições na linha de base correspondem as definições recomendadas.
- **Não corresponde à linha de base** -pelo menos uma definição na linha de base não corresponde as definições recomendadas.
- **Configurado incorretamente** -pelo menos uma definição não está corretamente configurada. Este estado significa que a definição está num conflito, erro ou o estado pendente.
- **Não aplicável** -pelo menos uma definição não é aplicável e não é aplicada.


### <a name="device-view"></a>Vista do dispositivo
Painel de descrição geral apresenta um resumo de baseado em gráfico de mensagens em fila de quantos dispositivos têm um estado específico da linha de base; **Postura de linha de base de segurança para dispositivos do Windows 10 atribuídos**.  

![Verificar o estado dos dispositivos](./media/security-baselines-monitor/overview.png)

Quando um dispositivo tiver estado diferente de categorias diferentes na linha de base, o dispositivo é representado por um único de estado. O estado que representa o dispositivo foi obtido da seguinte ordem de precedência de: **Configurado incorretamente**, **não corresponde à linha de base**, **não aplicável**, **linha de base de correspondências**.  

Por exemplo, se um dispositivo tem uma definição classificado como *mal configurados* e uma ou mais definições classificadas como *não corresponde à linha de base*, o dispositivo será classificado como *configurado incorretamente*.  

Pode clicar no gráfico para explorar e visualizar uma lista de dispositivos com vários Estados. Em seguida, pode selecionar dispositivos individuais nessa lista para ver detalhes sobre dispositivos individuais. Por exemplo:
- Selecione **configuração do dispositivo** > selecione o perfil com um Estado de erro:

  ![Verificar o estado dos dispositivos](./media/security-baselines-monitor/device-configuration-profile-list.png)

- Selecione o perfil de erro. É apresentada uma lista de todas as definições no perfil de e o respetivo estado. Agora, pode rolar para encontrar a definição causando o erro:

  ![Ver a definição causando o erro](./media/security-baselines-monitor/profile-with-error-status.png)

Utilize este relatório para ver todas as definições num perfil que estão a causar um problema. Também obter mais detalhes sobre as políticas e perfis de implementação em dispositivos.

> [!NOTE]
> Quando uma propriedade está definida como **não configurado** na linha de base, a definição é ignorada e sem restrições são impostas. A propriedade não é mostrada em qualquer relatório.

### <a name="per-category-view"></a>Por visualização de categoria
Painel de descrição geral apresenta um gráfico de por categoria para a linha de base; **Postura de linha de base de segurança por categoria**.  Esta vista apresenta cada categoria da linha de base e identifica a percentagem de dispositivos que pertencem a uma classificação de estado para cada uma dessas categorias. 
 
![Modo de exibição por categoria de estado](./media/security-baselines-monitor/monitor-baseline-per-category.png)

Estado para **linha de base de correspondências** não apresenta até que o estado para a categoria de relatório de 100% dos dispositivos.   

Pode ordenar o modo de exibição por categoria por cada coluna, selecionando o ícone de seta para cima para baixo na parte superior da coluna.  


## <a name="monitor-the-profile"></a>Monitorizar o perfil

O perfil de monitorização dá-lhe informações sobre o estado de implementação dos seus dispositivos, mas não o estado de segurança com base nas recomendações da linha de base.

1. No Intune, selecione **linhas de base de segurança** > Selecione uma linha de base > **perfis criados**.

2. Selecione um perfil. Na **descrição geral**, a imagem mostra o número de dispositivos e os utilizadores têm este perfil atribuído:

    ![Veja quantos dispositivos e utilizadores são atribuídos do perfil de linhas de base de segurança](./media/security-baselines-monitor/existing-profile-overview.png)

3. Sob **Manage** > **propriedades**, uma lista de todas as definições na linha de base são mostradas. Também pode alterar qualquer uma destas definições:

    ![Ver e atualizar as definições do perfil de linhas de base de segurança](./media/security-baselines-monitor/manage-settings.png)

4. Na **Monitor**, pode ver o estado de implementação do perfil de dispositivos individuais, o estado de cada utilizador e o estado para cada definição na linha de base:

    ![Ver as opções de monitor diferente para um perfil de linhas de base de segurança](./media/security-baselines-monitor/monitor-status-options.png)

## <a name="troubleshoot-using-per-setting-status"></a>Resolver problemas com o estado por definição

Implementou uma linha de base de segurança, mas o estado de implementação é apresentado um erro. Os passos seguintes dão-lhe algumas orientações sobre como resolver o erro.

1. No Intune, selecione **linhas de base de segurança** > Selecione uma linha de base > **perfis criados**.
2. Selecione um perfil > sob **Monitor** > **estado por definição**.
3. A tabela mostra todas as definições e o estado de cada configuração. Selecione o **erro** coluna ou o **conflito** coluna para ver a definição causando o erro.

### <a name="mdm-diagnostic-information"></a>Informações de diagnóstico do MDM

Agora, sabe a definição problemática. A próxima etapa é descobrir por que esta definição está a causar um conflito ou erro. 

Em dispositivos Windows 10, existe um relatório de informações de diagnóstico interno do MDM. Este relatório inclui valores predefinidos, valores atuais, apresenta uma lista da política, mostra se for implementada para o dispositivo ou utilizador e muito mais. Utilize este relatório para ajudar a determinar por que a configuração está a causar um conflito ou erro.

1. No dispositivo, aceda a **configurações** > **contas** > **acesso profissional ou escolar**.
2. Selecione a conta > **Info** > **relatório de diagnóstico avançadas** > **criar relatório**.
3. Escolher **exportar**e abra o arquivo gerado.
4. No relatório, procure o erro ou a definição de conflito em diferentes seções do relatório.

  Por exemplo, procure na **inscritos origens de configuração e de recursos de destino** secção ou o **não gerido políticas** secção. Pode ter uma idéia de por que motivo que esteja a causar um conflito ou erro.

[Diagnosticar falhas MDM no Windows 10](https://docs.microsoft.com/windows/client-management/mdm/diagnose-mdm-failures-in-windows-10) fornece mais informações sobre este relatório incorporado.

> [!TIP]
> - Algumas definições também listam o GUID. Pode procurar este GUID no registo (regedit) local para qualquer conjunto de valores.
> - Os registos do Visualizador de eventos também podem incluir algumas informações de erro sobre a definição de problemática (**Visualizador de eventos** > **registos de serviços e aplicações**  >   **Microsoft** > **Windows** > **DeviceManagement Enterprise-diagnóstico fornecedor** > **Admin** ).

## <a name="next-steps"></a>Passos Seguintes

[Monitorizar perfis de dispositivos](device-profile-monitor.md) e [Consulte alguns problemas comuns e as resoluções](device-profile-troubleshoot.md).

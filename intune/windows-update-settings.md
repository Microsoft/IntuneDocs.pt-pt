---
title: Windows para definições de atualização de negócios para Microsoft Intune – Azure | Documentos da Microsoft
description: Definições de WUfB para dispositivos Windows 10 que pode implementar através do Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 03/04/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.reviewer: aiwang
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 28e7109a82a5c083b4be26bc823bb0e06d97a7ca
ms.sourcegitcommit: da9ee02de327f202b00be44c79bf7abd35b9929b
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/05/2019
ms.locfileid: "57334991"
---
# <a name="windows-update-settings-for-intune"></a>Windows atualizar as definições do Intune  

Ver as definições de atualização do Windows 10, pode [configurar e gerir](windows-update-for-business-configure.md) com o Microsoft Intune.  

Quando configurar as definições para cadências de atualização do Windows 10 no Intune, que está a configurar as definições de atualização do Windows.  Quando atualizar um Windows definição tem uma dependência de versão do Windows 10, a dependência de versão é indicada nos detalhes de definições.  

## <a name="update-settings"></a>Definições de atualização  

Controlo de definições de atualização que bits irá transferir um dispositivo, e quando. Consulte a documentação de referência do Windows para obter mais informações sobre o comportamento de cada configuração.  

### <a name="servicing-channel"></a>Canal de serviço  

- **Predefinido**: Canal Semianual (direcionado)  
- **Documentação de referência do Windows**: [Update/BranchReadinessLevel](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-branchreadinesslevel)  
Defina o canal (branch) a partir do qual o dispositivo recebe atualizações do Windows. Diferentes canais, podem utilizar períodos de diferimento diferente antes das atualizações são entregues.  

Por exemplo, o *via de atualizações Semianuais* tem um diferimento de seis meses. Isso significa que se utilizar este canal com nenhuma adiamento adicionais deste corpo de definições, o dispositivo instala os atualização de seis meses após o seu lançamento.  

Canais de atualização com suporte:  

- Canal semi-anual  
- Canal Semianual (direcionado)  
- Windows Insider-rápida  
- Windows Insider-lenta  
- Versão do Windows Insider  

Se selecionar um canal de Insider, o Intune configura automaticamente a definição de atualização do Windows [atualização/ManagePreviewBuilds](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-managepreviewbuilds) para que a compilação de insider funcionem.  


> [!IMPORTANT]  
> A partir do Windows versão 1903, a utilização do *via de atualizações Semianuais (direcionada)* (SAC-T), foi descontinuado. Com esta alteração, SAC-T mescla com o *via de atualizações Semianuais*. Para saber mais sobre esta alteração e como ele afeta o Windows Update para empresas, consulte a postagem de Blog de profissionais de TI do Windows [Windows Update para empresas e a desativação de SAC T](https://techcommunity.microsoft.com/t5/Windows-IT-Pro-Blog/Windows-Update-for-Business-and-the-retirement-of-SAC-T/ba-p/339523).
 


### <a name="microsoft-product-updates"></a>Atualizações de produtos da Microsoft  

- **Predefinido**:  Permitir
- **Documentação de referência do Windows**: [Update/AllowMUUpdateService](https://docs.microsoft.com/en-us/windows/client-management/mdm/policy-csp-update#update-allowmuupdateservice)

Escolher *permitir* uma análise de atualizações da aplicação no Microsoft Update.    

### <a name="windows-drivers"></a>Controladores do Windows  

- **Predefinido**:  Permitir
- **Documentação de referência do Windows**: [Update/ExcludeWUDriversInQualityUpdate](https://docs.microsoft.com/en-us/windows/client-management/mdm/policy-csp-update#update-excludewudriversinqualityupdate)

Escolher *permitir* para incluir os controladores do Windows Update durante as atualizações

### <a name="quality-update-deferral-period-days"></a>Período de diferimento da atualização de qualidade (dias)  

- **Predefinido**: 0  
- **Documentação de referência do Windows**: [Update/DeferQualityUpdatesPeriodInDays](https://docs.microsoft.com/en-us/windows/client-management/mdm/policy-csp-update#update-deferqualityupdatesperiodindays)  

Especifique o número de dias de 0 a 30 de diferimento das atualizações de qualidade. Este período é, além de qualquer período de diferimento que faz parte de um canal de serviço que selecionar. O período de diferimento começa quando a política é recebida pelo dispositivo.  

As atualizações de qualidade são, normalmente, correções e melhorias às funcionalidades existentes do Windows.  

### <a name="feature-update-deferral-period-days"></a>Período de diferimento da atualização de funcionalidades (dias)  

- **Predefinido**: 0  
- **Documentação de referência do Windows**: [Update/PauseFeatureUpdatesPeriodInDays](https://docs.microsoft.com/en-us/windows/client-management/mdm/policy-csp-update#update-deferfeatureupdatesperiodindays)  

Especifique o número de dias de diferimento das atualizações de funcionalidades. Este período é, além de qualquer período de diferimento que faz parte de um canal de serviço que selecionar. O período de diferimento começa quando a política é recebida pelo dispositivo.  
Período de diferimento suportados:  

- *Windows versão 1709 ou posterior*: 0 a 365 dias  
- *Windows versão 1703*:  0 a 180 dias  

Normalmente, as Atualizações de Funcionalidades são novas funcionalidades do Windows.  

### <a name="set-feature-update-uninstall-period-2--60-days"></a>Período (2 – 60 dias) de desinstalação de atualização de funcionalidades de conjunto  

- **Predefinido**: 10  
- **Documentação de referência do Windows**:  [Update/ConfigureFeatureUpdateUninstallPeriod](https://docs.microsoft.com/en-us/windows/client-management/mdm/policy-csp-update#update-configurefeatureupdateuninstallperiod)  

Configure um horário após o qual o recurso de atualizações não podem ser desinstalado.  

Após este período expirar, os bits de atualização anteriores são removidos do dispositivo e já não é possível desinstale para uma versão de atualização anterior.  

Por exemplo, considere uma cadência de atualização com uma funcionalidade de desinstalação de atualizações de período de 20 dias. Após 25 dias optar por revertê-lo a atualização mais recente do recurso e utilize a opção de desinstalação.  Dispositivos que instalaram a atualização de funcionalidade há mais de 20 dias não é possível desinstalá-lo à medida que removi os bits necessários como parte da sua manutenção. No entanto, os dispositivos que apenas instalaram a atualização de funcionalidade cópia de segurança para 19 dias atrás podem desinstalar a atualização se eles com êxito der entrada para receber o comando de desinstalação antes de exceder o período de desinstalação de 20 dias.  


## <a name="user-experience-settings"></a>Definições de experiência do utilizador  

Definições de experiência do utilizador controlam a experiência do utilizador final para lembretes e reinício do dispositivo. Consulte a documentação de referência do Windows para obter mais informações sobre o comportamento de cada configuração.  

### <a name="automatic-update-behavior"></a>Comportamento de atualização automática  

- **Predefinido**: Instalar automaticamente e reiniciar a uma hora agendada  
- **Documentação de referência do Windows**: [Update/AllowAutoUpdate](https://docs.microsoft.com/en-us/windows/client-management/mdm/policy-csp-update#update-allowautoupdate)  

Escolha a forma como as atualizações automáticas estão instaladas e se necessário, quando reiniciar o dispositivo.  

Consulte a documentação de referência do Windows para divulgar as completo das seguintes opções suportadas:  

- **Notificar transferência** – notificar o utilizador antes de transferir a atualização. Os utilizadores optar por transferir e instalar atualizações.  

- **Instalação automática ao tempo de manutenção** – automaticamente a transferência de atualizações e, em seguida, instalar durante a manutenção automática, quando o dispositivo não está em utilização ou de execução com baterias. Quando for necessário reiniciar, é pedido aos utilizadores para reiniciar durante sete dias e, em seguida, a reinicialização é forçada.  

  Esta opção pode reiniciar um dispositivo automaticamente após a atualização é instalada. Utilize o **horas ativas** configurações para definir um período durante o qual os reinícios automáticos estão bloqueados:  

  - **Início das horas ativas**: Especifique uma hora de início para a supressão dos reinícios de instalação de atualizações.  
    **Documentação de referência do Windows**:  [Update/ActiveHoursStart](https://docs.microsoft.com/en-us/windows/client-management/mdm/policy-csp-update#update-activehoursstart)  
    **Predefinido**: 8 AM  
  
  - **Fim de horas ativas**: Especifique uma hora de fim para a supressão dos reinícios de instalação de atualizações.  
    **Documentação de referência do Windows**:  [Update/ActiveHoursEnd](https://docs.microsoft.com/en-us/windows/client-management/mdm/policy-csp-update#update-activehoursend)  
    **Predefinido**: 5 PM  

- **Instalar automaticamente e reiniciar no período de manutenção** - automaticamente a transferência de atualizações e, em seguida, instalar durante a manutenção automática, quando o dispositivo não está em utilização ou de execução com baterias. Quando for necessário reiniciar, o dispositivo é reiniciado quando não são utilizadas. (Esta é a predefinição para dispositivos não geridos.)  

  Esta opção pode reiniciar um dispositivo automaticamente após a atualização é instalada. Utilizar o **horas ativas** definições não são descritas nas definições de atualização do Windows, mas são utilizadas pelo Intune para definir um período durante o qual os reinícios automáticos estão bloqueados:  

  - **Início das horas ativas**: Especifique uma hora de início para a supressão dos reinícios de instalação de atualizações.  
    **Documentação de referência do Windows**:  [Update/ActiveHoursStart](https://docs.microsoft.com/en-us/windows/client-management/mdm/policy-csp-update#update-activehoursstart)  
    **Predefinido**: 8 AM  

  - **Fim de horas ativas**: Especifique uma hora de fim para a supressão dos reinícios de instalação de atualizações.  
    **Documentação de referência do Windows**:  [Update/ActiveHoursEnd](https://docs.microsoft.com/en-us/windows/client-management/mdm/policy-csp-update#update-activehoursend)  
    **Predefinido**: 5 PM  

- **Instalar automaticamente e reiniciar na hora agendada** – Especifique um dia de instalação e a hora. Se não for especificado, instalação é executada às AM de 3 diariamente, seguida de uma contagem decrescente de 15 minutos para um reinício. Com sessão iniciada pode atrasar a contagem regressiva e reiniciar.  
  
  Esta opção suporta configurações adicionais.  
  **Documentação de referência do Windows**:  [Update/AllowAutoUpdate](https://docs.microsoft.com/en-us/windows/client-management/mdm/policy-csp-update#update-allowautoupdate)  

  - **Frequência de comportamento automático**: Utilize esta definição para agendar quando as atualizações são instaladas, incluindo a semana, o dia e a hora.  
    **Predefinido**: Todas as semanas

  - **Dia de instalação agendado**:  Especifica em que dia da semana pretende que as atualizações a instalar.  
    **Predefinido**: Qualquer dia  

  - **Hora de instalação agendada**:  Especifique a hora do dia em que pretende atualizações a instalar.  
    **Predefinido**: 3 AM  

- **Instalação automática e reinício sem controle de usuário final** – automaticamente a transferência de atualizações e, em seguida, instalar durante a manutenção automática, quando o dispositivo não está em utilização ou de execução com baterias. Quando for necessário reiniciar, o dispositivo é reiniciado quando não são utilizadas. Esta opção define o painel de controlo dos utilizadores finais para só de leitura.  

- **Repor para predefinição** -restaurar as definições de atualização automática original no Windows 10 máquinas em execução de atualização de Outubro de 2018 ou posterior.  


### <a name="restart-checks"></a>Verificações de reinício  

- **Predefinido**: Permitir  
- **Documentação de referência do Windows**: [Update/SetEDURestart](https://docs.microsoft.com/en-us/windows/client-management/mdm/policy-csp-update#update-setedurestart)  

Esta definição não tem resultados diferentes consoante a versão de dispositivos do Windows:  

- Windows versão 1703 e anterior: Quando reinicia um dispositivo, existem algumas verificações que ocorrem, incluindo a verificação de utilizadores ativos, níveis de bateria, jogos em execução e mais. Para ignorar estas verificações ao reiniciar um dispositivo, selecione **Ignorar**.  
- A partir da versão 1709 do Windows: Durante o horário de Active Directory, os seguintes processos não executam atualizações: Procurar, transferir, instalar e reiniciar. Após horas Active Directory, os processos de atualização executar e pode reativar o dispositivo do modo de suspensão, procurar, transferir, instalar e reiniciar o dispositivo, desde que as verificações de bateria e o power verifica pass. Para obter mais informações, consulte [atualização/SetEDURestart](https://docs.microsoft.com/en-us/windows/client-management/mdm/policy-csp-update#update-setedurestart).  

### <a name="block-user-from-pausing-windows-updates"></a>Impedir o utilizador da colocar em pausa atualizações do Windows  

- **Predefinido**: Permitir  
- **Documentação de referência do Windows**: [Update/SetDisablePauseUXAccess](https://docs.microsoft.com/en-us/windows/client-management/mdm/policy-csp-update#update-setdisablepauseuxaccess)  

Permitir ou impedir um utilizador de dispositivo de colocação em pausa a instalação de uma atualização.  

### <a name="require-users-approval-to-restart-outside-of-work-hours"></a>Exigir a aprovação do utilizador reinicie fora das horas de trabalho  

- **Predefinido**: Não configurado  
- **Documentação de referência do Windows**: [Update/AutoRestartRequiredNotificationDismissal](https://docs.microsoft.com/en-us/windows/client-management/mdm/policy-csp-update#update-autorestartrequirednotificationdismissal)
  
Selecione *necessário* para exigir que um utilizador aprovar um reinício de dispositivo fora do horário de trabalho.  
   
### <a name="remind-user-prior-to-required-auto-restart-with-dismissible-reminder-hours"></a>Lembrar o utilizador antes auto-reinício necessário com lembrete dispensáveis (horas)  

- **Predefinido**: *Isso não está configurado por predefinição e não lembrete é apresentada aos utilizadores*.  
- **Documentação de referência do Windows**: [Update/ScheduleRestartWarning](https://docs.microsoft.com/en-us/windows/client-management/mdm/policy-csp-update#update-schedulerestartwarning)  

Especifique o período de tempo antes de um reinício automático para apresentar uma notificação dispensáveis a um utilizador de dispositivo sobre o que o reinício. Os valores da **2**, **4**, **8**, **12**, ou **24** horas são suportadas.  

### <a name="remind-user-prior-to-required-auto-restart-with-permanent-reminder-minutes"></a>Lembrar o utilizador antes auto-reinício necessário com lembrete permanente (minutos)  

- **Predefinido**: *Isso não está configurado por predefinição e não lembrete é apresentada aos utilizadores*.  
- **Documentação de referência do Windows**: [Update/ScheduleImminentRestartWarning](https://docs.microsoft.com/en-us/windows/client-management/mdm/policy-csp-update#update-scheduleimminentrestartwarning) 

Especifique o período de tempo antes de um reinício automático para exibir um aviso não dispensáveis para um utilizador do dispositivo sobre o que o reinício. Os valores da **15**, **30** ou **60** minutos são suportados.  
 
### <a name="allow-user-to-restart-engaged-restart"></a>Permitir ao utilizador para reiniciar (reinício envolvido)  

- **Predefinido**: Não configurado  
- **Documentação de referência do Windows**: *Não aplicável*  
- **Versão do Windows**: Suporte para o Windows 10 versão 1803 e posterior  

  > [!NOTE]  
  > Windows 10 versão 1809 apresenta as definições de reinício envolvidos adicionais que permitem o separado de configurações a serem aplicadas às atualizações de funcionalidade e qualidade. No entanto, as definições geridas pelo Intune separadamente não são aplicáveis aos tipos de atualização diferentes. Em vez disso, o Intune aplica os mesmos valores para as atualizações de funcionalidade e qualidade.  

Quando definido como **necessário**, habilitar o uso das opções de reinício envolvidos para atualizações do Windows 10. Estas opções de interagir com o utilizador de um dispositivo para ajudar a gerir quando reiniciar um dispositivo depois de instalar uma atualização que requeira um reinício.  

Para obter mais informações sobre esta opção, consulte [envolvidos reinício](https://docs.microsoft.com/en-us/windows/deployment/update/waas-restart#engaged-restart) na documentação do Windows 10 para implementar atualizações.  

As seguintes definições são utilizadas para controlar quando ocorrem ações de reinício envolvidos.  

- **A transição de que os usuários envolvido reinício após um reinício automático (dias)**  
  - **Predefinido**:  Por predefinição, este não estiver configurada, mas suporta um valor de **2** ao **30**.  
  - **Documentação de referência do Windows**: [Update/EngagedRestartTransitionSchedule](https://docs.microsoft.com/en-us/windows/client-management/mdm/policy-csp-update#update-engagedrestarttransitionschedule)  
  Especifique o intervalo de tempo após instala a atualização até que o dispositivo entra o envolvidos comportamento de reinício. Depois do número de dias configurado, os utilizadores recebem um pedido para reiniciar o dispositivo.  

- **Lembrete de reinício envolvidos suspender (dias)**  
  - **Predefinido**:  Por predefinição, este não estiver configurada, mas suporta um valor de **1** ao **3**.  
  - **Documentação de referência do Windows**: [Update/EngagedRestartSnoozeSchedule](https://docs.microsoft.com/en-us/windows/client-management/mdm/policy-csp-update#update-engagedrestartsnoozeschedule)  
  Especifique o tempo que um reinício do pedido pode ser snoozed.  Após o período de suspender, é oferecido novamente o pedido de reinício. O utilizador pode continuar a suspender o lembrete até que seja atingido o prazo de instalação.  

- **Prazo de conjunto pendentes reinicia (dias)**  
  - **Predefinido**:  Por predefinição, este não estiver configurada, mas suporta um valor de **2** ao **30**.  
  - **Documentação de referência do Windows**: [Update/EngagedRestartDeadline](https://docs.microsoft.com/en-us/windows/client-management/mdm/policy-csp-update#update-engagedrestartdeadline)  
  Especifique um número máximo de dias a aguardar após o comportamento de reinício a envolvidos começa antes de um dispositivo impõe um reinício necessário. Este reinício solicitarão aos utilizadores que salvar seu trabalho

### <a name="delivery-optimization-download-mode"></a>Modo de transferência de otimização de entrega  

- **Predefinido**:  Não aplicável
- **Documentação de referência do Windows**: *Não aplicável*

Otimização da entrega já não está configurada como parte de uma cadência de atualização do Windows 10 em atualizações de Software. Otimização da entrega está agora definida por meio da configuração do dispositivo. No entanto, as configurações anteriores permanecem disponíveis na consola. Pode remover estas configurações anteriores ao editar que sejam *não configurado*, mas caso contrário, não pode ser modificados. 

Para evitar conflitos entre políticas novas e antigas, consulte [mover de cadências de atualização existente para a Otimização da entrega](delivery-optimization-windows.md#move-existing-update-rings-to-delivery-optimization) e, em seguida, mova as suas definições para um perfil de otimização de entrega.



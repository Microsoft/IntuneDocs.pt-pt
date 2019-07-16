---
title: Configurações de atualização do Windows para empresas para o Microsoft Intune-Azure | Microsoft Docs
description: Configurações de WUfB para dispositivos Windows 10 que você pode implantar usando o Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 04/18/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.reviewer: aiwang
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9e9baf3593883cf2fa2402a0b4daec638a336366
ms.sourcegitcommit: 7c251948811b8b817e9fe590b77f23aed95b2d4e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/15/2019
ms.locfileid: "67884199"
---
# <a name="windows-update-settings-for-intune"></a>Configurações do Windows Update para o Intune  

Exiba as configurações de atualização do Windows 10 que você pode [configurar e gerenciar](windows-update-for-business-configure.md) com Microsoft Intune.  

Ao definir configurações para anéis de atualização do Windows 10 no Intune, você está definindo as configurações de Windows Update. Se uma configuração do Windows Update tiver uma dependência de versão do Windows 10, a dependência de versão será observada nos detalhes de configurações.  

## <a name="update-settings"></a>Atualizar configurações  

As configurações de atualização controlam quais bits um dispositivo será baixado e quando. Para obter mais informações sobre o comportamento de cada configuração, consulte a documentação de referência do Windows.  

### <a name="servicing-channel"></a>Canal de manutenção  

- **Padrão**: Canal semianual (direcionado)  
- **Documentação de referência do Windows**: [Update/BranchReadinessLevel](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-branchreadinesslevel)  
Defina o canal (Branch) do qual o dispositivo recebe atualizações do Windows. Diferentes canais podem usar períodos de adiamento diferentes antes que as atualizações sejam entregues.  

Por exemplo, o *canal semestral* tem um adiamento de seis meses. Se você usar esse canal sem adiamentos adicionais deste corpo de configurações, o dispositivo instalará a atualização seis meses após seu lançamento.  

Canais de atualização com suporte:  

- Canal semianual  
- Canal semianual (direcionado)  
- Windows Insider – rápido  
- Windows Insider – lento  
- Versão do Windows Insider  

Se você selecionar um canal do Insider, o Intune configurará automaticamente a [atualização/ManagePreviewBuilds](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-managepreviewbuilds) da configuração do Windows Update para que a compilação Insider funcione.  


> [!IMPORTANT]  
> A partir do Windows versão 1903, o uso do *canal semianual (direcionado)* (SAC-T) é desativado. Com essa alteração, o SAC-T é mesclado com o *canal semestral*. Para saber mais sobre essa alteração e como ela afeta Windows Update para negócios, consulte a postagem do blog do Windows IT Pro [Windows Update para negócios e a desativação do SAC-T](https://techcommunity.microsoft.com/t5/Windows-IT-Pro-Blog/Windows-Update-for-Business-and-the-retirement-of-SAC-T/ba-p/339523).
 


### <a name="microsoft-product-updates"></a>Atualizações de produtos da Microsoft  

- **Padrão**:  Allow
- **Documentação de referência do Windows**: [Update/AllowMUUpdateService](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-allowmuupdateservice)

Escolha *permitir* uma verificação de atualizações de aplicativos do Microsoft Update.    

### <a name="windows-drivers"></a>Drivers do Windows  

- **Padrão**:  Allow
- **Documentação de referência do Windows**: [Update/ExcludeWUDriversInQualityUpdate](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-excludewudriversinqualityupdate)

Escolha *permitir* para incluir Windows Update drivers durante as atualizações

### <a name="quality-update-deferral-period-days"></a>Período de adiamento da atualização de qualidade (dias)  

- **Padrão**: 0  
- **Documentação de referência do Windows**: [Update/DeferQualityUpdatesPeriodInDays](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-deferqualityupdatesperiodindays)  

Especifique o número de dias de 0 a 30 para os quais as atualizações de qualidade são adiadas. Esse período é além de qualquer período de adiamento que faz parte do canal de serviço que você selecionar. O período de adiamento começa quando a política é recebida pelo dispositivo.  

Atualizações de qualidade normalmente são correções e melhorias na funcionalidade existente do Windows.  

### <a name="feature-update-deferral-period-days"></a>Período de adiamento da atualização de recurso (dias)  

- **Padrão**: 0  
- **Documentação de referência do Windows**: [Update/PauseFeatureUpdatesPeriodInDays](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-deferfeatureupdatesperiodindays)  

Especifique o número de dias durante os quais as atualizações de recurso são adiadas. Esse período é além de qualquer período de adiamento que faz parte do canal de serviço que você selecionar. O período de adiamento começa quando a política é recebida pelo dispositivo.  
Período de adiamento com suporte:  

- *Windows versão 1709 ou posterior*: 0 a 365 dias  
- *Versão do Windows 1703*:  0 a 180 dias  

Normalmente, as Atualizações de Funcionalidades são novas funcionalidades do Windows.  

### <a name="set-feature-update-uninstall-period-2--60-days"></a>Definir período de desinstalação de atualização de recurso (2 a 60 dias)  

- **Padrão**: 10  
- **Documentação de referência do Windows**:  [Update/ConfigureFeatureUpdateUninstallPeriod](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-configurefeatureupdateuninstallperiod)  

Configure um horário após o qual as atualizações de recurso não podem ser desinstaladas.  

Depois que esse período expirar, os bits de atualização anteriores serão removidos do dispositivo e não poderão mais ser desinstalados para uma versão de atualização anterior.  

Por exemplo, considere um anel de atualização com um período de desinstalação de atualização de recurso de 20 dias. Depois de 25 dias, você decide reverter a atualização de recursos mais recente e usar a opção de desinstalação.  Os dispositivos que instalaram a atualização de recursos há mais de 20 dias não podem desinstalá-lo, pois eles removeram os bits necessários como parte de sua manutenção. No entanto, os dispositivos que instalaram apenas a atualização de recursos até 19 dias atrás poderão desinstalar a atualização se eles fizerem check-in com êxito para receber o comando de desinstalação antes de exceder o período de desinstalação de 20 dias.  


## <a name="user-experience-settings"></a>Configurações de experiência do usuário  

As configurações de experiência do usuário controlam a experiência do usuário final para lembretes e reinicialização do dispositivo. Para obter mais informações sobre o comportamento de cada configuração, consulte a documentação de referência do Windows.  

### <a name="automatic-update-behavior"></a>Comportamento de atualização automática  

- **Padrão**: Instalar e reiniciar automaticamente em um horário agendado  
- **Documentação de referência do Windows**: [Update/AllowAutoUpdate](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-allowautoupdate)  

Escolha como as atualizações automáticas serão instaladas e, se necessário, quando reiniciar o dispositivo.  

Consulte a documentação de referência do Windows para obter uma divulgação completa das seguintes opções com suporte:  

- **Notificar download** – notificar o usuário antes de baixar a atualização. Os usuários optam por baixar e instalar atualizações.  

- **Instalação automática no momento da manutenção** – as atualizações são baixadas automaticamente e, em seguida, são instaladas durante a manutenção automática quando o dispositivo não está em uso ou com a energia da bateria. Quando a reinicialização é necessária, os usuários são solicitados a reiniciar por até sete dias e a reinicialização é forçada.  

  Esta opção pode reiniciar um dispositivo automaticamente após a instalação da atualização. Use as configurações de **horas ativas** para definir um período durante o qual as reinicializações automáticas são bloqueadas:  

  - **Início de horas ativas**: Especifique uma hora de início para suprimir reinicializações devido a instalações de atualização.  
    **Documentação de referência do Windows**:  [Update/ActiveHoursStart](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-activehoursstart)  
    **Padrão**: 8:00  
  
  - **Fim das horas ativas**: Especifique uma hora de término para suprimir reinicializações devido a instalações de atualização.  
    **Documentação de referência do Windows**:  [Update/ActiveHoursEnd](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-activehoursend)  
    **Padrão**: 5 PM  

- **Instalar automaticamente e reiniciar no momento da manutenção** -as atualizações são baixadas automaticamente e, em seguida, são instaladas durante a manutenção automática quando o dispositivo não está em uso ou com bateria. Quando a reinicialização é necessária, o dispositivo é reiniciado quando não está sendo usado. (Esse é o padrão para dispositivos não gerenciados.)  

  Esta opção pode reiniciar um dispositivo automaticamente após a instalação da atualização. O uso das configurações de **horas ativas** não é descrito em configurações de Windows Update, mas são usadas pelo Intune para definir um período durante o qual as reinicializações automáticas são bloqueadas:  

  - **Início de horas ativas**: Especifique uma hora de início para suprimir reinicializações devido a instalações de atualização.  
    **Documentação de referência do Windows**:  [Update/ActiveHoursStart](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-activehoursstart)  
    **Padrão**: 8:00  

  - **Fim das horas ativas**: Especifique uma hora de término para suprimir reinicializações devido a instalações de atualização.  
    **Documentação de referência do Windows**:  [Update/ActiveHoursEnd](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-activehoursend)  
    **Padrão**: 5 PM  

- **Instalar e reiniciar automaticamente no horário agendado** – especifique um dia e hora de instalação. Se não for especificado, a instalação será executada às 3h diariamente, seguida de uma contagem regressiva de 15 minutos para uma reinicialização. Os usos conectados podem atrasar a contagem regressiva e reiniciar.  
  
  Essa opção dá suporte a configurações adicionais.  
  **Documentação de referência do Windows**:  [Update/AllowAutoUpdate](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-allowautoupdate)  

  - **Frequência de comportamento automática**: Utilize esta definição para agendar quando as atualizações são instaladas, incluindo a semana, o dia e a hora.  
    **Padrão**: Toda semana

  - **Dia da instalação agendada**:  Especifique em qual dia da semana você deseja que as atualizações sejam instaladas.  
    **Padrão**: Qualquer dia  

  - **Horário de instalação agendado**:  Especifique a hora do dia em que você deseja que as atualizações sejam instaladas.  
    **Padrão**: 3 AM  

- **Instalação e reinicialização automáticas sem controle do usuário final** – as atualizações são baixadas automaticamente e, em seguida, são instaladas durante a manutenção automática quando o dispositivo não está em uso ou está em execução com a bateria. Quando a reinicialização é necessária, o dispositivo é reiniciado quando não está sendo usado. Essa opção define o painel de controle usuários finais como somente leitura.  

- **Redefinir para padrão** -restaure as configurações de atualização automática originais em computadores Windows 10 que executam a atualização de outubro de 2018 ou posterior.  


### <a name="restart-checks"></a>Reiniciar verificações  

- **Padrão**: Allow  
- **Documentação de referência do Windows**: [Update/SetEDURestart](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-setedurestart)  

Essa configuração tem resultados diferentes, dependendo da versão dos dispositivos do Windows:  

- Windows versão 1703 e anterior: Quando reinicia um dispositivo, existem algumas verificações que ocorrem, incluindo a verificação de utilizadores ativos, níveis de bateria, jogos em execução e mais. Para ignorar estas verificações ao reiniciar um dispositivo, selecione **Ignorar**.  
- A partir do Windows versão 1709: Durante o horário ativo, os seguintes processos não são executados para atualizações: verificação, download, instalação e reinicialização. Após o horário ativo, os processos de atualização executam e podem ativar o dispositivo de suspensão, verificação, download, instalação e reinicialização do dispositivo, desde que as verificações de bateria e as verificações de energia passem. Para obter mais informações, consulte [Update/SetEDURestart](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-setedurestart).  

### <a name="block-user-from-pausing-windows-updates"></a>Bloquear o usuário de pausar atualizações do Windows  

- **Padrão**: Allow  
- **Documentação de referência do Windows**: [Update/SetDisablePauseUXAccess](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-setdisablepauseuxaccess)  

Permitir ou bloquear um usuário de dispositivo de pausar a instalação de uma atualização. 

### <a name="block-user-from-scanning-for-windows-updates"></a>Bloquear o usuário de verificar atualizações do Windows  
- **Padrão**: Allow
- **Documentação de referência do Windows**: [Atualizar/SetDisableUXWUAccess](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-setdisableuxwuaccess) 

Especifica se deseja permitir ou bloquear o acesso de um usuário para verificar Windows Update. Por exemplo, se você configurar um *bloco*, os usuários não poderão acessar os recursos Windows Update verificação, download e instalação.  

### <a name="require-users-approval-to-restart-outside-of-work-hours"></a>Exigir que a aprovação do usuário seja reiniciada fora do horário de trabalho  

- **Padrão**: Não configurado  
- **Documentação de referência do Windows**: [Update/AutoRestartRequiredNotificationDismissal](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-autorestartrequirednotificationdismissal)
  
Selecione *necessário* para exigir que um usuário aprove uma reinicialização do dispositivo fora do horário de trabalho.  
   
### <a name="remind-user-prior-to-required-auto-restart-with-dismissible-reminder-hours"></a>Lembrar o usuário antes de reinicialização automática necessária com lembrete de quaisquer dispensáveis (horas)  

- **Padrão**: *Essa configuração não é configurada por padrão e nenhum lembrete é apresentado aos usuários*.  
- **Documentação de referência do Windows**: [Update/ScheduleRestartWarning](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-schedulerestartwarning)  

Especifique por quanto tempo antes de uma reinicialização automática exibir uma notificação quaisquer dispensáveis para um usuário do dispositivo sobre essa reinicialização. Há suporte para valores de **2**, **4**, **8**, **12**ou **24** horas.  

### <a name="remind-user-prior-to-required-auto-restart-with-permanent-reminder-minutes"></a>Lembrar o usuário antes de reinicialização automática necessária com lembrete permanente (minutos)  

- **Padrão**: *Essa configuração não é configurada por padrão e nenhum lembrete é apresentado aos usuários*.  
- **Documentação de referência do Windows**: [Update/ScheduleImminentRestartWarning](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-scheduleimminentrestartwarning) 

Especifique quanto tempo antes de uma reinicialização automática exibirá um aviso não quaisquer dispensáveis para um usuário do dispositivo sobre essa reinicialização. Há suporte para valores de **15**, **30** ou **60** minutos.  

### <a name="windows-update-notification-level"></a>Nível de notificação Windows Update  
- **Padrão**: Usar as notificações de Windows Update padrão 
- **Documentação de referência do Windows**: [Update/UpdateNotificationLevel](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-updatenotificationlevel)

Especifique o nível de notificações de Windows Update que os usuários veem. Essa configuração não controla como e quando as atualizações são baixadas e instaladas.

### <a name="allow-user-to-restart-engaged-restart"></a>Permitir que o usuário reinicie (reinício envolvido)  

- **Padrão**: Não configurado  
- **Documentação de referência do Windows**: *Não aplicável*  
- **Versão do Windows**: Com suporte para Windows 10 versão 1803 e posterior  

  > [!NOTE]  
  > O Windows 10 versão 1809 apresenta configurações de reinicialização adicionais contratadas que permitem que configurações separadas sejam aplicadas a atualizações de recursos e qualidade. No entanto, as configurações gerenciadas pelo Intune não se aplicam separadamente aos diferentes tipos de atualização. Em vez disso, o Intune aplica os mesmos valores às atualizações de recursos e qualidade.  

Quando definido como **obrigatório**, você habilita o uso das opções de reinicialização envolvidas para atualizações do Windows 10. Essas opções envolvem o usuário de um dispositivo para ajudar a gerenciar quando reiniciar um dispositivo após a instalação de uma atualização que requer uma reinicialização.  

Para obter mais informações sobre essa opção, consulte reinicialização [envolvida](https://docs.microsoft.com/windows/deployment/update/waas-restart#engaged-restart) na documentação do Windows 10 para implantar atualizações.  

As configurações a seguir são usadas para controlar quando ocorrem ações de reinicialização envolvidas.  

- **Fazer a transição de usuários para a reinicialização envolvida após uma reinicialização automática (dias)**  
  - **Padrão**:  Por padrão, isso não está configurado, mas dá suporte a um valor de **2** a **30**.  
  - **Documentação de referência do Windows**: [Update/EngagedRestartTransitionSchedule](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-engagedrestarttransitionschedule)  
  Especifique por quanto tempo depois que a atualização for instalada até que o dispositivo entre no comportamento de reinicialização envolvida. Após o número de dias configurado, os usuários recebem uma solicitação para reiniciar o dispositivo.  

- **Adiar lembrete de reinício estabelecido (dias)**  
  - **Padrão**:  Por padrão, essa configuração não é configurada, mas dá suporte a um valor de **1** a **3**.  
  - **Documentação de referência do Windows**: [Update/EngagedRestartSnoozeSchedule](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-engagedrestartsnoozeschedule)  
  Especifique por quanto tempo uma solicitação de reinicialização pode ser adiada.  Após o período de adiamento, o prompt de reinicialização é oferecido novamente. O usuário pode continuar a adiar o lembrete até que o prazo de instalação seja atingido.  

- **Definir prazo para reinicializações pendentes (dias)**  
  - **Padrão**:  Por padrão, essa configuração não é configurada, mas dá suporte a um valor de **2** a **30**.  
  - **Documentação de referência do Windows**: [Update/EngagedRestartDeadline](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-engagedrestartdeadline)  
  Especifique um número máximo de dias para aguardar depois que o comportamento de reinicialização envolvido começar antes que um dispositivo Force uma reinicialização necessária. Essa reinicialização solicitará que os usuários salvem seu trabalho.

### <a name="delivery-optimization-download-mode"></a>Modo de download da otimização de entrega  

A otimização de entrega não é mais configurada como parte de um anel de atualização do Windows 10 em atualizações de software. A otimização de entrega agora está definida por meio da configuração do dispositivo. No entanto, as configurações anteriores permanecem disponíveis no console do. Você pode remover essas configurações anteriores editando-as para que *não*estejam configuradas, mas elas não podem ser modificadas de outra forma. 

Para evitar conflitos entre a política nova e a antiga, consulte [mover de anéis de atualização existentes para a otimização de entrega](delivery-optimization-windows.md#move-existing-update-rings-to-delivery-optimization) e, em seguida, mover suas configurações para um perfil de otimização de entrega.

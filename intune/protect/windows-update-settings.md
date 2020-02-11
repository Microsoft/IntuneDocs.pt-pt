---
title: Definições de Windows para Atualização de Negócios para Microsoft Intune - Azure Microsoft Docs
description: As definições do WUfB para dispositivos Windows 10 que pode implementar utilizando o Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/18/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: medium
ms.technology: ''
ms.reviewer: aiwang
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 06982bdf0aff1870f1a759f68bc6cdd48227a3cf
ms.sourcegitcommit: e1ff157f692983b49bdd6e20cc9d0f93c3b3733c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/11/2020
ms.locfileid: "77125001"
---
# <a name="windows-update-settings-for-intune"></a>Definições de atualização do Windows para Intune  

Ver as definições de Atualização do Windows 10 pode [configurar e gerir](windows-update-for-business-configure.md) com o Microsoft Intune.  

Quando configurar as definições para os anéis de atualização do Windows 10 no Intune, está a configurar as definições de Atualização do Windows. Se uma definição de atualização do Windows tiver uma dependência da versão Do Windows 10, a dependência da versão é notada nos detalhes das definições.  

## <a name="update-settings"></a>Definições de atualização  

As definições de atualização controlam quais as bits que um dispositivo irá descarregar e quando. Para obter mais informações sobre o comportamento de cada definição, consulte a documentação de referência do Windows.  

- **Canal de serviço**  
  **Padrão**: Canal semi-anual  
  CSP de atualização do Windows: [Atualização/BranchReadinessLevel](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-branchreadinesslevel)  

  Desloque o canal (ramo) a partir do qual o dispositivo recebe atualizações do Windows. Diferentes canais podem usar diferentes períodos de diferimento antes de as atualizações serem entregues.  

  Por exemplo, o *Canal SemEstral* tem um adiamento de seis meses. Se utilizar este canal sem diferimentos adicionais deste conjunto de definições, o dispositivo instala a atualização seis meses após o seu lançamento.  

  Canais de atualização suportados:  

  - Canal Semestral  
  - Canal semestral (visado)  
  - Windows Insider – Rápido  
  - Windows Insider – Lento  
  - Versão do Windows Insider  

  Se selecionar um canal Insider, intune configura automaticamente a definição de atualização do Windows [Update/ManagePreviewBuilds](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-managepreviewbuilds) para que a construção de insider funcione.  


  > [!IMPORTANT]  
  > Começando com a versão 1903 do Windows, a utilização do *Canal Semi-Anual (visado)* (SAC-T), está reformada. Com esta mudança, a SAC-T funde-se com o *Canal SemEstral.* Para saber mais sobre esta mudança e como afeta o Windows Update for Business, consulte o Windows IT Pro Blog post [Windows Update for Business e a reforma do SAC-T](https://techcommunity.microsoft.com/t5/Windows-IT-Pro-Blog/Windows-Update-for-Business-and-the-retirement-of-SAC-T/ba-p/339523).  
 
- **Atualizações de produtos da Microsoft**  
  **Padrão**: Permitir  
  Windows Update CSP: [Update/AllowMUUpdateService](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-allowmuupdateservice)

  - **Permitir** - Selecione *Permitir* a digitalização de atualizações de aplicações a partir da Microsoft Update.  
  - **Block** - Selecione Block para evitar a verificação de atualizações de aplicações.  

- **Controladores windows**  
  **Padrão**: Permitir  
  Windows Update CSP: [Update/ExcludeWUDriversInQualityUpdate](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-excludewudriversinqualityupdate)  

  - **Permitir** - Selecione *Permitir* incluir controladores de atualização do Windows durante as atualizações.  
  - **Bloco** - Selecione Bloco para evitar a verificação dos condutores.  

- **Período de diferimento de atualização de qualidade (dias)**  
  **Padrão**: 0  
  CSP de atualização do Windows: [Atualização/DeferQualityUpdatesPeriodInDays](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-deferqualityupdatesperiodindays)  

  Especifique o número de dias de 0 a 30 para os quais as Atualizações de Qualidade são adiadas. Este período é para além de qualquer período de diferimento que faça parte do canal de serviço que selecionar. O período de adiamento começa quando a apólice é recebida pelo dispositivo.  

  As Atualizações de Qualidade são normalmente correções e melhorias na funcionalidade existente do Windows.  

- **Período de diferimento da atualização de funcionalidades (dias)**  
  **Padrão**: 0  
  CSP de atualização do Windows: [Atualização/PausaActualizaçõesPeriodInDays](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-deferfeatureupdatesperiodindays)  

  Especifique o número de dias para os quais as Atualizações de Funcionalidades são adiadas. Este período é para além de qualquer período de diferimento que faça parte do canal de serviço que selecionar. O período de adiamento começa quando a apólice é recebida pelo dispositivo.  

  Período de adiamento apoiado:  

  - *Windows versão 1709 e mais tarde* - 0 a 365 dias  
  - *Versão do Windows 1703* - 0 a 180 dias  

  Normalmente, as Atualizações de Funcionalidades são novas funcionalidades do Windows.  

- **Definir período de desinstalação de funcionalidades (2 a 60 dias)**  
  **Padrão**: 10  
  CSP de atualização do Windows: [Atualização/ConfigureFeatureUpdateUninstallPeriod](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-configurefeatureupdateuninstallperiod)  

  Configure um tempo após o qual as atualizações de funcionalidades não podem ser desinstaladas.  

  Após o termo deste período, as peças de atualização anteriores são removidas do dispositivo e já não podem desinstalar-se numa versão de atualização anterior.  

  Por exemplo, considere um anel de atualização com um período de desinstalação de atualização de recurso de 20 dias. Depois de 25 dias, você decide reverter a atualização de recursos mais recente e usar a opção de desinstalação.  Os dispositivos que instalaram a atualização de recursos há mais de 20 dias não podem desinstalá-lo, pois eles removeram os bits necessários como parte de sua manutenção. No entanto, os dispositivos que instalaram apenas a atualização de recursos até 19 dias atrás poderão desinstalar a atualização se eles fizerem check-in com êxito para receber o comando de desinstalação antes de exceder o período de desinstalação de 20 dias.  

## <a name="user-experience-settings"></a>Definições de experiência do utilizador  

As definições de experiência do utilizador controlam a experiência do utilizador final para reiniciar o dispositivo e lembretes. Para obter mais informações sobre o comportamento de cada definição, consulte a documentação do CSP do Windows Update.  

- **Comportamento de atualização automática**  
  **Predefinição**: Instalação automática no momento da manutenção  
  Atualização do Windows CSP: [Atualização/Atualização Automática](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-allowautoupdate)  

  Escolha como as atualizações automáticas são instaladas e, se necessário, quando reiniciar o dispositivo.  

  Opções suportadas:  

  - **Notifique** o download - Notifique o utilizador antes de descarregar a atualização. Os utilizadores optam por descarregar e instalar atualizações.  

  - **Instale automaticamente no tempo de manutenção** - As atualizações descarregam automaticamente e instalam-se durante a Manutenção Automática quando o dispositivo não estiver a ser utilizado ou a funcionar com a bateria. Quando é necessário reiniciar, os utilizadores são solicitados a reiniciar até sete dias e, em seguida, reiniciar é forçado.  

    Esta opção pode reiniciar automaticamente um dispositivo após a instalação da atualização. Utilize as definições de **horas ativas** para definir um período durante o qual os reinícios automáticos são bloqueados:  

    - **Início do horário ativo** - Especifique um tempo de início para suprimir os reinícios devido às instalações de atualização.  
      **Padrão**: 8 AM  
      Atualização do Windows CSP: [Update/ActiveHoursStart](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-activehoursstart)  
  
    - **Fim do horário ativo** - Especifique um tempo de fim para suprimir reboots devido a instalações de atualização.  
      **Predefinição**: 17:00  
      Atualização do Windows CSP: [Atualização/ActiveHoursEnd](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-activehoursend)  

  - **Instale e reinicie automaticamente no tempo de manutenção** - As atualizações descarregam automaticamente e instalam-se durante a Manutenção Automática quando o dispositivo não estiver a ser utilizado ou a funcionar com a energia da bateria. Quando é necessário reiniciar, o dispositivo reinicia quando não está a ser utilizado. (Esta é a falha para dispositivos não geridos.)  

    Esta opção pode reiniciar automaticamente um dispositivo após a instalação da atualização. A utilização das definições de **horas ativas** não é descrita nas definições do Windows Update, mas são utilizadas pela Intune para definir um período durante o qual os reinícios automáticos são bloqueados:  

    - **Início do horário ativo** - Especifique um tempo de início para suprimir os reinícios devido às instalações de atualização.  
      **Padrão**: 8 AM  
      Atualização do Windows CSP: [Update/ActiveHoursStart](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-activehoursstart)  
  
    - **Fim do horário ativo** - Especifique um tempo de fim para suprimir reboots devido a instalações de atualização.  
      **Predefinição**: 17:00  
      Atualização do Windows CSP: [Atualização/ActiveHoursEnd](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-activehoursend)  

  - **Instale e reinicie automaticamente na hora programada** - Especifique um dia e hora de instalação. Se não especificada, a instalação funciona às 3 da manhã diariamente, seguida de uma contagem regressiva de 15 minutos para um recomeço. O registo nas utilizações pode atrasar a contagem regressiva e reiniciar.   
  Atualização do Windows CSP: [Atualização/Atualização Automática](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-allowautoupdate)  

    Esta opção suporta configurações adicionais.  

    - **Frequência automática** de comportamento - Utilize esta definição para agendar quando as atualizações forem instaladas, incluindo a semana, o dia e a hora.  
      **Padrão**: Todas as semanas

    - Dia de **instalação agendado** - Especifique em que dia da semana pretende que as atualizações sejam instaladas.  
      **Padrão**: Qualquer dia  

    - **Hora de instalação programada** - Especifique a hora do dia quando pretender que as atualizações sejam instaladas.  
      **Padrão**: 3 AM  

  - **Instale e reinicie automaticamente sem controlo de utilizador final** - As atualizações descarregam automaticamente e instalam-se durante a Manutenção Automática quando o dispositivo não estiver a ser utilizado ou a funcionar com a energia da bateria. Quando é necessário reiniciar, o dispositivo reinicia quando não está a ser utilizado. Esta opção define o painel de controlo dos utilizadores finais apenas para leitura.  

  - **Reset para padrão** - Restaure as definições originais de atualização automática nas máquinas do Windows 10 que executam a Atualização de outubro de 2018 ou posteriormente.  


- **Reiniciar verificações**  
  **Padrão**: Permitir  
  CSP de atualização do Windows: [atualização/setEDurestart](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-setedurestart)  

  Para ignorar estas verificações ao reiniciar um dispositivo, selecione **Ignorar**. 
  
  Esta definição tem resultados diferentes dependendo da versão dos dispositivos do Windows:  
 
  - *Versão 1703 do Windows e mais cedo* - Quando reinicia um dispositivo, existem algumas verificações que ocorrem, incluindo a verificação de utilizadores ativos, níveis de bateria, jogos de corrida e muito mais.  
  
  - *Versão 1709 do Windows e posterior* - Durante o Dia ativo, os seguintes processos não funcionam para atualizações: digitalizar, descarregar, instalar e reiniciar. Após o Ative Hours, os processos de atualização funcionam e podem acordar o dispositivo do sono, digitalizar, descarregar, instalar e reiniciar o dispositivo desde que a bateria verifique e as verificações de energia passem. 

- **Bloqueie o utilizador de fazer uma pausa nas atualizações do Windows**  
  **Padrão**: Permitir  
  Windows Update CSP: [Update/SetDisablePauseUXAccess](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-setdisablepauseuxaccess)  

  - **Permitir** - Permita que os utilizadores do dispositivo façam uma pausa na instalação de uma atualização.  
  - **Bloco** - Evite que os utilizadores do dispositivo entrem na instalação de uma atualização.  

- **Bloquear o utilizador de procurar atualizações do Windows**  
  **Padrão**: Permitir  
  Windows Update CSP: [Update/SetDisableUXWUAccess](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-setdisableuxwuaccess) 

  - **Permitir** - Permita que os utilizadores do dispositivo utilizem o Windows Update para encontrar e descarregar atualizações e instalar funcionalidades.
  - **Block** - Evite que os utilizadores do dispositivo acedam à análise do Windows Update, descarreguem atualizações e instalam funcionalidades.  

- **Exigir a aprovação do utilizador para reiniciar fora do horário de trabalho**  
  **Predefinição**: Não configurado  
  CSP de atualização do Windows: [Atualização/Reinício automáticoDeDespedimento](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-autorestartrequirednotificationdismissal) de Notificação
  
  - **Não configurado**  
  - **Necessário** - Exija que um utilizador aprove um reinício do dispositivo fora do horário de trabalho.  
   
- **Lembre o utilizador antes do reinício automático necessário com um lembrete dispensável (horas)**  
  **Padrão**: 4  
  Atualização do Windows CSP: [aviso de atualização/reinício](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-schedulerestartwarning) de horário  

  Especifique quanto tempo antes de um reinício automático para apresentar uma notificação dispensável a um utilizador do dispositivo sobre esse reinício. São apoiados valores de **2**, **4,** **8**, **12**ou **24** horas.  
  
  Quando limpa o valor predefinido, esta definição torna-se *não configurada*.  

- **Lembre o utilizador antes do reinício automático necessário com um lembrete permanente (minutos)**  
  **Predefinição**: 15  
  Atualização do Windows CSP: [aviso de atualização/calendário iminente](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-scheduleimminentrestartwarning)  

  Especifique quanto tempo antes de um reinício automático para apresentar um aviso não dispensável a um utilizador do dispositivo sobre esse reinício. São suportados valores de **15,** **30** ou **60** minutos.  

  Quando limpa o valor predefinido, esta definição torna-se *não configurada*.  

- **Alterar nível de notificação de atualização**  
  **Predefinição**: Utilize as notificações predefinidas do Windows Update  
  CSP de atualização do Windows: Nível de [notificação de atualização/atualização](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-updatenotificationlevel)
  
  Especifique o nível de notificações do Windows Update que os utilizadores vêem. Esta definição não controla como e quando as atualizações são descarregadas e instaladas.  

  Opções suportadas:
  - **Não configurado**
  - **Utilize as notificações predefinidas do Windows Update**
  - **Desligue todas as notificações, excluindo avisos de reinício**
  - **Desligue todas as notificações, incluindo avisos de reinício**  

- **Utilizar as definições de prazo**  
  **Predefinição**: Não configurado  
 
  Permite ao utilizador utilizar as definições do prazo.  

  - **Não configurado**
  - **Permitir**

  Quando definido para *permitir,* pode configurar as seguintes definições para prazos:

  - **Prazo para atualizações de funcionalidades**  
    **Predefinição**: *Não configurado*  
    CSP de atualização do Windows: [Atualização/ConfigureDeadlineForFeatureUpdates](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-configuredeadlineforfeatureupdates)  

    Especifica o número de dias que um utilizador tem antes de as atualizações das funcionalidades serem instaladas automaticamente nos seus dispositivos (2-30).

  - **Prazo para atualizações de qualidade**  
    **Predefinição**: *Não configurado*  
    CSP de atualização do Windows: [Atualização/ConfigureDeadlineForQualityUpdates](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-configuredeadlineforqualityupdates)

    Especifica o número de dias que um utilizador tem antes de serem instaladas atualizações de qualidade nos seus dispositivos automaticamente (2-30).

  - **Período de graça**  
    **Predefinição**: CSP de atualização do Windows *não configurado:* [Atualização/ConfigureDeadlineGracePeriod]( https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-configuredeadlinegraceperiod)

    Especifica um número mínimo de dias após o prazo até que orine automaticamente (2-7).

  - **Reiniciar automaticamente antes do prazo**  
    **Predefinido**: Sim Atualização do Windows CSP: [Atualização/ConfigureDeadlineNoAutoReboot](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-configuredeadlinenoautoreboot)

    Especifica se o dispositivo deve reiniciar automaticamente antes do prazo.
    - **Sim**
    - **Não**

### <a name="delivery-optimization-download-mode"></a>Modo de descarregamento de otimização de entrega  

A otimização da entrega já não está configurada como parte de um Anel de Atualização do Windows 10 em atualizações de software. A otimização da entrega está agora definida através da configuração do dispositivo. No entanto, configurações anteriores permanecem disponíveis na consola. Pode remover estas configurações anteriores editando-as para não serem *configuradas,* mas não podem ser modificadas de outra forma. 

Para evitar conflitos entre a nova e antiga política, consulte [a Remoção da Otimização da Entrega dos Anéis de Atualização do Windows 10](../configuration/delivery-optimization-windows.md#remove-delivery-optimization-from-windows-10-update-rings) e, em seguida, mova as suas definições para um perfil de otimização de entrega.

---
# required metadata

title: Resolução de Problemas do Endpoint Protection | Microsoft Intune
description:
keywords:
author: Nbigman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: e31df2d2-bb1b-491b-9a71-04e0b18829c1

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Troubleshoot Endpoint Protection in Microsoft Intune

Utilize as informações nesta secção para o ajudar a resolver problemas ao utilizar o Endpoint Protection do Microsoft Intune.

Se estas informações não resolverem o problema, consulte [Como obter suporte para o Microsoft Intune](how-to-get-support-for-microsoft-intune.md) para ver mais formas de obter ajuda.


### Mensagens de erro do Endpoint Protection
Esta secção descreve possíveis causas e soluções para os seguintes erros e avisos que são apresentados no painel **Estado do Endpoint Protection** na [consola de administração do Intune](https://manage.microsoft.com)

|Item de estado|Possíveis causas|Possíveis soluções|
|---------------|--------------------|-----------------------|
|**Motor do Endpoint Protection indisponível**|O motor do Intune Endpoint Protection foi danificado ou eliminado.|Se o motor do Endpoint Protection do Intune estiver danificado, pode experimentar atualizar ou reinstalar o software.<br /><br />Para forçar uma atualização imediata, clique em **Atualizar** no software de cliente do Endpoint Protection (que se encontra na barra de tarefas nos computadores geridos).<br /><br />Se não for possível atualizar o motor, tem de reinstalar o motor do Endpoint Protection.<br /><br />Na lista de programas instalados, no Painel de Controlo do computador gerido, localize o **Agente do Endpoint Protection do Microsoft Intune** e, em seguida, desinstale a aplicação.<br /><br />Durante a próxima sincronização de atualizações, o Gestor de Atualizações do Microsoft Online Management deteta o programa em falta e reinstala-o na hora de instalação agendada.|
|**Endpoint Protection desativado**|O Endpoint Protection do Intune foi desativado por um administrador através de uma política ou por um utilizador num computador gerido.|Se o Endpoint Protection estiver desativado, pode ativá-lo a partir da [consola de administração do Intune](https://manage.microsoft.com) ou a partir de um computador gerido. Efetue uma das seguintes ações:<br /><br />Para ativar o Endpoint Protection a partir da [consola de administração do Intune](https://manage.microsoft.com), abra a área de trabalho **Política** e altere a definição **Ativar o Endpoint Protection** nas políticas que se aplicam ao computador.<br /><br />Ou,<br /><br />para ativar o Endpoint Protection a partir de um computador gerido, inicie o cliente Endpoint Protection do Intune a partir da área de notificação e ser-lhe-á pedido que ative o Endpoint Protection.|
|**Proteção em tempo real desativada**|A proteção em tempo real foi desativada por um administrador (através de uma política) ou por um utilizador num computador gerido.|Se a proteção em tempo real estiver desativada, pode ativá-lo a partir da [consola de administração do Intune](https://manage.microsoft.com) ou a partir de um computador gerido. Efetue uma das seguintes ações:<br /><br />Para ativar a proteção em tempo real a partir da [consola de administração do Intune](https://manage.microsoft.com), abra a área de trabalho **Política** e altere a definição **Ativar proteção em tempo real** para **Sim** nas políticas que se aplicam ao computador.<br /><br />Ou,<br /><br />para ativar a proteção em tempo real a partir de um computador gerido, inicie o software de cliente Endpoint Protection a partir da área de notificação. Ser-lhe-á então pedido para ativar a proteção em tempo real.|
|**Análise de transferências desativada**|A análise de transferências foi desativada por um administrador através de uma política ou por um utilizador num computador gerido.|Se a análise de transferências estiver desativada, pode ativá-la a partir da [consola de administração do Intune](https://manage.microsoft.com) ou a partir de um computador gerido. Efetue uma das seguintes ações:<br /><br />Para ativar a análise de transferências a partir da [consola de administração do Intune](https://manage.microsoft.com), abra a área de trabalho **Política** e altere a definição **Analisar todas as transferências** para **Sim** nas políticas que se aplicam ao computador.<br /><br />Ou,<br /><br />para ativar a análise de transferências a partir de um computador gerido, inicie o software de cliente Endpoint Protection a partir da área de notificação. Clique no separador **Definições**, clique em **Proteção em tempo real**, selecione a caixa de verificação **Analisar todas as transferências** e, em seguida, clique em **Guardar alterações**|
|**Monitorização da atividade de programas e ficheiros desativada**|A monitorização da atividade de programas e ficheiros foi desativada por um administrador que utilizou uma Política ou por um utilizador num computador gerido.|Se a monitorização da atividade de programas e ficheiros estiver desativada, pode ativá-la a partir da [consola de administração do Intune](https://manage.microsoft.com) ou de um computador gerido. Efetue uma das seguintes ações:<br /><br />Para ativar a monitorização da atividade de programas e ficheiros a partir da [consola de administração do Intune](https://manage.microsoft.com), abra a área de trabalho **Política** e altere a definição **Monitorizar a atividade dos ficheiros e programas no computador** para **Sim** nas políticas que se aplicam ao computador.<br /><br />Ou,<br /><br />para ativar a monitorização da atividade de programas e ficheiros a partir de um computador gerido, inicie o software de cliente Endpoint Protection a partir da área de notificação. Clique no separador **Definições**, clique em **Proteção em tempo real**, selecione a caixa de verificação **Monitorizar atividade de programas e ficheiros no seu computador** e, em seguida, clique em **Guardar alterações**|
|**Monitorização de comportamento desativada**|A monitorização de comportamento foi desativada por um administrador (através de uma política) ou por um utilizador num computador gerido.|Se a monitorização de comportamento estiver desativada, pode ativá-la a partir da [consola de administração do Intune](https://manage.microsoft.com) ou a partir de um computador gerido. Efetue uma das seguintes ações:<br /><br />Para ativar a monitorização de comportamento a partir da [consola de administração do Intune](https://manage.microsoft.com), abra a área de trabalho **Política**, altere a definição **Ativar monitorização de comportamento** para **Sim** nas políticas que se aplicam ao computador e, em seguida, reinicie o computador gerido.<br /><br />Ou,<br /><br />para ativar a monitorização de comportamento a partir de um computador gerido, inicie o software de cliente Endpoint Protection a partir da área de notificação. Clique no separador **Definições**, clique em **Proteção em tempo real**, selecione a caixa de verificação **Ativar monitorização de comportamento** e, em seguida, clique em **Guardar alterações**. Em seguida, reinicie o computador.|
|**Análise de scripts desativada**|A análise de scripts foi desativada por um administrador (através de uma política) ou por um utilizador num computador gerido.|Se a análise de scripts estiver desativada, pode ativá-la a partir da [consola de administração do Intune](https://manage.microsoft.com) ou a partir de um computador gerido. Efetue uma das seguintes ações:<br /><br />Para ativar a análise de scripts a partir da [consola de administração do Intune](https://manage.microsoft.com), abra a área de trabalho **Política** e altere a definição **Ativar análise de script** para **Sim** nas políticas que se aplicam ao computador.<br /><br />Ou,<br /><br />para ativar a análise de scripts a partir de um computador gerido, inicie o software de cliente Endpoint Protection a partir da área de notificação. Clique no separador **Definições**, clique em **Proteção em tempo real**, selecione a caixa de verificação **Ativar análise de script** e, em seguida, clique em **Guardar alterações**|
|**Sistema de Inspeção de Rede desativado**|O Sistema de Inspeção de Rede foi desativado por um administrador através de uma política ou por um utilizador num computador gerido.|Se o Sistema de Inspeção de Rede estiver desativado, pode ativá-lo a partir da [consola de administração do Intune](https://manage.microsoft.com) ou de um computador gerido. Efetue uma das seguintes ações:<br /><br />Para ativar o Sistema de Inspeção de Rede a partir da [consola de administração do Intune](https://manage.microsoft.com), abra a área de trabalho **Política**, altere a definição **Ativar Sistema de Inspeção de Rede** para **Sim** nas políticas que se aplicam ao computador e, em seguida, reinicie o computador gerido.<br /><br />Ou,<br /><br />para ativar o Sistema de Inspeção de Rede a partir de um computador gerido, inicie o software de cliente Endpoint Protection a partir da área de notificação. Clique no separador **Definições**, clique em **Proteção em tempo real**, selecione a caixa de verificação **Ativar Sistema de Inspeção de Rede** e, em seguida, clique em **Guardar alterações**. Reinicie o computador.|
|**Definições de software maligno desatualizadas**|O computador pode ter estado desligado da Internet durante um longo período de tempo e as definições de software maligno podem não ter sido atualizadas. Este estado é apresentado quando as definições de software maligno do computador estão desatualizadas há 14 dias ou mais.|Se as definições de software maligno estiverem desatualizadas, pode atualizá-las a partir da [consola de administração do Intune](https://manage.microsoft.com) ou de um computador gerido.<br /><br />Para mais informações, consulte o tópico [Ajude a proteger os PCs Windows com o Endpoint Protection para o Microsoft Intune](/intune/deploy-use/help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune).|
|**Análise completa em atraso**|Não foi concluída nenhuma análise completa nos últimos 14 dias. Esta situação pode ocorrer se o computador for reiniciado durante uma análise completa.|Se tiver uma análise completa em atraso, pode executar uma única análise completa ou agendar análises completas periódicas a partir da [consola de administração do Intune](https://manage.microsoft.com), seguindo as informações contidas no tópico [Tarefas de gestão comuns do PC Windows com o computador cliente do Microsoft Intune](/intune/deploy-use/common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client)|
|**Análise rápida em atraso**|Não foi concluída nenhuma análise rápida nos últimos 14 dias. Esta situação pode ocorrer se o computador for reiniciado durante uma análise rápida.|Se tiver uma análise rápida em atraso, pode executar uma única análise rápida ou agendar análises rápidas periódicas a partir da [consola de administração do Intune](https://manage.microsoft.com), seguindo as informações contidas no tópico [Tarefas de gestão comuns do PC Windows com o computador cliente do Microsoft Intune](/intune/deploy-use/common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client)|
|**Outra aplicação de Endpoint Protection em execução**|Está a ser executada outra aplicação de Endpoint Protection e o computador está em bom estado de funcionamento.|Por predefinição, se estiver instalada outra aplicação de Endpoint Protection e o Intune detetar essa aplicação, o Endpoint Protection desativa-se automaticamente. Se o Intune não detetar a outra aplicação de Endpoint Protection, o Endpoint Protection permanecerá ativado. Para mais informações, consulte [Ajude a proteger os PCs Windows com o Endpoint Protection para o Microsoft Intune](/intune/deploy-use/help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune)|

### Passos seguintes
Se estas informações de resolução de problemas não o ajudaram, contacte o Suporte da Microsoft, conforme descrito em [How to get support for Microsoft Intune (Como obter suporte para o Microsoft Intune)](how-to-get-support-for-microsoft-intune.md)


<!--HONumber=May16_HO2-->


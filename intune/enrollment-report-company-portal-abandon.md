---
title: Abandono da inscrição no portal da empresa no Intune
titlesuffix: Microsoft Intune
description: Saiba mais sobre o relatório de abandono do portal da empresa.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/20/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.openlocfilehash: 44a6d89b649514a08193d7144dff7d89dc3d9c55
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/20/2018
ms.locfileid: "52183371"
---
# <a name="company-portal-abandonment-report"></a>Relatório de abandono do portal da empresa

Este relatório indica-lhe em que ponto os utilizadores estão a abandonar o processo de inscrição no Portal da Empresa.

Para ver o relatório, selecione **Intune** > **Inscrição de dispositivos** > **Abandono do portal da empresa**.

Com base nestas informações sobre o abandono, pode atualizar os seus documentos de inclusão para ajudar os utilizadores a concluir a inscrição. Por exemplo, se existirem muitos utilizadores a desistir nos Termos de Utilização, pode investigar essa área e torná-la mais intuitiva para os utilizadores.

## <a name="what-is-abandonment"></a>O que é o abandono?

O abandono ocorre quando um utilizador opta por uma das seguintes ações:

-   Seleciona explicitamente uma ação para parar a inscrição
-   Fecha o Portal da Empresa durante a inscrição
-   Demora mais de 30 minutos entre as secções da inscrição

Se o utilizador optar por parar a inscrição e recomeçar múltiplas vezes, tal é contabilizado como múltiplas tentativas e múltiplos abandonos. Se o utilizador aguardar 30 minutos entre ecrãs de inscrição diferentes, tal será considerado como múltiplos abandonos.

## <a name="what-does-the-report-show"></a>O que mostra o relatório?

Os relatórios de inscrição incluem dados de dispositivos iOS e Android.

Os relatórios mostram os dados correspondentes às últimas duas semanas, mas pode filtrar o relatório para apresentar qualquer período até 30 dias anteriores.

Pode filtrar o intervalo de datas, o sistema operativo e a secção de inscrição através da opção **Filtro**.

### <a name="number-and-percentage-tiles"></a>Mosaicos de número e percentagem

Na parte superior do relatório, pode ver o número e a percentagem de relatórios de abandono em relação a todas as inscrições.

-   Inscrições iniciadas: o número de tentativas de inscrição.
-   Inscrições abandonadas: o número de tentativas de inscrição que não resultaram num dispositivo totalmente inscrito e conforme.
-   Taxa de abandono: a percentagem de tentativas de inscrição que foram abandonadas (Inscrições abandonadas/Inscrições iniciadas).

### <a name="line-graph"></a>Gráfico de linha

O gráfico de linha mostra os abandonos diários para cada uma das quatro principais secções de inscrição:

-   Lista de verificação da configuração
-   Ecrãs de plataforma
-   Termos de Utilização
-   Conformidade/Ativação

### <a name="user-abandonment-actions"></a>Ações de abandono do utilizador

As seguintes tabelas mostram a lista de ações do utilizador que são consideradas abandono. Para ver exemplos de ecrãs de inscrição, pode ver os vídeos de inscrição do [iOS](https://channel9.msdn.com/Series/IntuneEnrollment/iOS-Enrollment) e [Android](https://channel9.msdn.com/Series/IntuneEnrollment/Android-Enrollment). 


#### <a name="setup-checklist-section"></a>Secção da lista de verificação da configuração

| Nome do abandono | Ecrã ou fluxo | Platform | Ação |
| ---- |---- |---- |---- |
| EnrollmentWrapUp | Pedido para abrir uma página no Portal da Empresa | iOS/Android | **Cancelar** |
| EnrollmentWrapUp | Ecrã de inscrição do dispositivo até à conclusão da operação **A carregar recursos da empresa** | iOS/Android | Demorou mais de 30 minutos |
| DeviceCategory | Seleção da Categoria do Dispositivo (se configurado pelo administrador) até clicar em **Concluído** | iOS/Android | Demorou mais de 30 minutos |
| PreEnrollmentWizard | Ecrã de configuração do acesso quando inicia a inscrição, mas voltou à secção Configurar acesso | iOS/Android| **Adiar** |
| PreEnrollmentWizard | Ecrã de configuração do acesso até clicar em **Seguinte** no ecrã **O Que Se Segue** | iOS/Android | Demorou mais de 30 minutos |

#### <a name="platform-screens-section"></a>Secção dos ecrãs de plataforma

| Nome do abandono | Ecrã ou fluxo | Platform | Ação |
| ---- |---- |---- |---- |
| iOSProfileLaunch | Pedido para mostrar um perfil de configuração | iOS | **Ignorar** |
| iOSProfileLaunch | Ecrã de instalação do perfil | iOS | **Cancelar** |
| iOSProfileLaunch | Pedido para confiar na origem do perfil para inscrever o dispositivo | iOS | **Cancelar** |
| iOSProfileLaunch | Ecrã de instalação do perfil até à instalação com êxito do perfil | iOS | Demorou mais de 30 minutos |
| AndroidPermissions | Ecrã de ativação do administrador do dispositivo | Android | **Cancelar** |
| AndroidPermissions | Desde o pedido de aprovação para efetuar e gerir chamadas telefónicas até o administrador do dispositivo selecionar **Ativar** | Android | Demorou mais de 30 minutos |
| KnoxActivation | Ativação do agente KLMS (apenas Samsung) | Android| **Cancelar** |
| KnoxActivation | Ativação do agente KLMS até **Confirmar** | Android | Demorou mais de 30 minutos|

#### <a name="terms-of-use-section"></a>Secção dos termos de utilização

| Nome do abandono | Ecrã ou fluxo | Platform | Ação |
| ---- |---- |---- |---- |
| TermsofUse | Termos de utilização (se configurado pelo administrador) | iOS/Android | **Recusar Tudo** |
| TermsofUse | Termos de utilização até **Aceitar tudo** | iOS/Android | Demorou mais de 30 minutos |

#### <a name="complianceactivation-section"></a>Secção de Conformidade/Ativação

| Nome do abandono | Ecrã ou fluxo | Platform | Ação |
| ---- |---- |---- |---- |
| Conformidade | A conformidade do dispositivo (se configurado pelo administrador) é apresentada como não verde na fase de pós-inscrição da configuração do acesso| iOS/Android | **Adiar** |
| Conformidade | A conformidade do dispositivo é apresentada como não verde até ser atualizada e ficar a verde | iOS/Android | Demorou mais de 30 minutos |
| Ativação | A ativação da inscrição (se configurado pelo administrador) é apresentada como não verde na configuração do acesso | iOS/Android | **Adiar** |
| Conformidade | A ativação do dispositivo é apresentada como não verde até ser atualizada e ficar a verde | iOS/Android | Demorou mais de 30 minutos |

## <a name="next-steps"></a>Passos Seguintes

Depois de verificar as taxas de abandono, pode rever as [opções de inscrição](enrollment-options.md) para ver se pode fazer alterações para melhorar o processo de inscrição.
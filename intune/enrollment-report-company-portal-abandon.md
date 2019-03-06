---
title: Relatório de inscrições de utilizador incompleto no Intune
titlesuffix: Microsoft Intune
description: Saiba mais sobre o relatório de inscrições de utilizador incompleto.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 2/22/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0202fba7e31b7be1d325617867be9a43d4f2064a
ms.sourcegitcommit: 430b290474b11f9df87785b01edc178e6bae2049
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/05/2019
ms.locfileid: "57400233"
---
# <a name="incomplete-user-enrollments-report"></a>Relatório de inscrições de utilizador incompleto

Este relatório indica onde no Portal da empresa aos utilizadores do processo de inscrição não são concluir o processo de inscrição.

Para ver o relatório, selecione **Intune** > **inscrição de dispositivos** > **inscrições de utilizador incompleta**.

Usando essas informações, pode atualizar os documentos de inclusão para ajudar os utilizadores concluírem a inscrição. Por exemplo, se existirem muitos utilizadores a desistir nos Termos de Utilização, pode investigar essa área e torná-la mais intuitiva para os utilizadores.

## <a name="what-is-an-incomplete-enrollment"></a>O que é uma inscrição incompleta?

Uma inscrição incompleta é quando um usuário executa qualquer um dos seguintes:

-   Seleciona explicitamente uma ação para parar a inscrição
-   Fecha o Portal da Empresa durante a inscrição
-   Demora mais de 30 minutos entre as secções da inscrição

Se o utilizador opta pela inscrição de parar e reiniciar várias vezes, ele mostra como várias tentativas e várias inscrições incompletas. Se um utilizador tem de aguardar durante 30 minutos entre ecrãs de inscrição diferente, é considerado várias inscrições incompletas.

## <a name="what-does-the-report-show"></a>O que mostra o relatório?

Os relatórios incluem dados para dispositivos iOS e Android.

Os relatórios mostram os dados correspondentes às últimas duas semanas, mas pode filtrar o relatório para apresentar qualquer período até 30 dias anteriores.

Pode filtrar o intervalo de datas, o sistema operativo e a secção de inscrição através da opção **Filtro**.

### <a name="number-and-percentage-tiles"></a>Mosaicos de número e percentagem

Na parte superior do relatório, pode ver o número e percentagem de incompletas inscrições em relação a todas as inscrições.

-   Inscrições iniciadas: O número de inscrições tentada.
-   Inscrições incompletas: O número de inscrições de tentativas que não resulta num dispositivo totalmente inscrito e em conformidade.
-   Taxa de incompleta: A percentagem de tentativas de inscrição que foram abandonadas (abandonada inscrições / iniciada inscrições).

### <a name="line-graph"></a>Gráfico de linha

O gráfico de linha mostra as inscrições incompletas diárias para cada uma das seções de inscrição de quatro núcleos:

-   Lista de verificação da configuração
-   Ecrãs de plataforma
-   Termos de utilização
-   Conformidade/Ativação

### <a name="user-abandonment-actions"></a>Ações de abandono do utilizador

As tabelas seguintes mostram a lista de ações do usuário que ser qualificado como pedir uma inscrição incompleta. Para ver exemplos de ecrãs de inscrição, pode ver os vídeos de inscrição do [iOS](https://channel9.msdn.com/Series/IntuneEnrollment/iOS-Enrollment) e [Android](https://channel9.msdn.com/Series/IntuneEnrollment/Android-Enrollment). 


#### <a name="setup-checklist-section"></a>Secção da lista de verificação da configuração

| Nome da ação | Ecrã ou fluxo | Plataforma | Ação |
| ---- |---- |---- |---- |
| EnrollmentWrapUp | Pedido para abrir uma página no Portal da Empresa | iOS/Android | **Cancelar** |
| EnrollmentWrapUp | Ecrã de inscrição do dispositivo até à conclusão da operação **A carregar recursos da empresa** | iOS/Android | Demorou mais de 30 minutos |
| DeviceCategory | Seleção da Categoria do Dispositivo (se configurado pelo administrador) até clicar em **Concluído** | iOS/Android | Demorou mais de 30 minutos |
| PreEnrollmentWizard | Ecrã de configuração do acesso quando inicia a inscrição, mas voltou à secção Configurar acesso | iOS/Android| **Adiar** |
| PreEnrollmentWizard | Ecrã de configuração do acesso até clicar em **Seguinte** no ecrã **O Que Se Segue** | iOS/Android | Demorou mais de 30 minutos |

#### <a name="platform-screens-section"></a>Secção dos ecrãs de plataforma

| Nome da ação | Ecrã ou fluxo | Plataforma | Ação |
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

| Nome da ação | Ecrã ou fluxo | Plataforma | Ação |
| ---- |---- |---- |---- |
| TermsofUse | Termos de utilização (se configurado pelo administrador) | iOS/Android | **Recusar Tudo** |
| TermsofUse | Termos de utilização até **Aceitar tudo** | iOS/Android | Demorou mais de 30 minutos |

#### <a name="complianceactivation-section"></a>Secção de Conformidade/Ativação

| Nome da ação | Ecrã ou fluxo | Plataforma | Ação |
| ---- |---- |---- |---- |
| Conformidade | A conformidade do dispositivo (se configurado pelo administrador) é apresentada como não verde na fase de pós-inscrição da configuração do acesso| iOS/Android | **Adiar** |
| Conformidade | A conformidade do dispositivo é apresentada como não verde até ser atualizada e ficar a verde | iOS/Android | Demorou mais de 30 minutos |
| Ativação | A ativação da inscrição (se configurado pelo administrador) é apresentada como não verde na configuração do acesso | iOS/Android | **Adiar** |
| Conformidade | A ativação do dispositivo é apresentada como não verde até ser atualizada e ficar a verde | iOS/Android | Demorou mais de 30 minutos |

## <a name="next-steps"></a>Passos Seguintes

Depois de verificar os preços da inscrição incompleta, pode rever o [opções de inscrição](enrollment-options.md) para ver se pode fazer alterações para melhorar a inscrição.

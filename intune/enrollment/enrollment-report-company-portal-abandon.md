---
title: Relatório incompleto de registros de usuário no Intune
titleSuffix: Microsoft Intune
description: Saiba mais sobre o relatório inscrições de usuários incompletos.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 2/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: ae3c2380aa27096be2490d2404858179ea9d222e
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72503188"
---
# <a name="incomplete-user-enrollments-report"></a>Relatório incompleto de registros de usuário

Este relatório informa onde os usuários do processo de registro de Portal da Empresa não estão concluindo o processo de registro.

Para ver o relatório, escolha **Intune** > **registro de dispositivo** > registros de **usuário incompletos**.

Usando essas informações, você pode atualizar seus documentos de integração para ajudar os usuários a concluir o registro. Por exemplo, se existirem muitos utilizadores a desistir nos Termos de Utilização, pode investigar essa área e torná-la mais intuitiva para os utilizadores.

## <a name="what-is-an-incomplete-enrollment"></a>O que é um registro incompleto?

Um registro incompleto é quando um usuário faz qualquer uma das seguintes opções:

- Seleciona explicitamente uma ação para parar a inscrição
- Fecha o Portal da Empresa durante a inscrição
- Demora mais de 30 minutos entre as secções da inscrição

Se um usuário optar por parar o registro e reiniciar várias vezes, ele aparecerá como várias tentativas e vários registros incompletos. Se um usuário aguardar 30 minutos entre telas de registro diferentes, será considerado vários registros incompletos.

## <a name="what-does-the-report-show"></a>O que mostra o relatório?

Os relatórios incluem dados para dispositivos iOS e Android.

Os relatórios mostram os dados correspondentes às últimas duas semanas, mas pode filtrar o relatório para apresentar qualquer período até 30 dias anteriores.

Pode filtrar o intervalo de datas, o sistema operativo e a secção de inscrição através da opção **Filtro**.

### <a name="number-and-percentage-tiles"></a>Mosaicos de número e percentagem

Na parte superior do relatório, você pode ver o número e a porcentagem de registros incompletos em relação a todos os registros.

- Inscrições iniciadas: o número de tentativas de inscrição.
- Inscrições incompletas: o número de registros tentados que não resultaram em um dispositivo totalmente registrado e em conformidade.
- Taxa incompleta: a porcentagem de tentativas de registro que foram abandonadas (registros abandonados/inscrições iniciadas).

### <a name="line-graph"></a>Gráfico de linha

O gráfico de linhas mostra os registros diários incompletos para cada uma das quatro seções principais de registro:

- Lista de verificação da configuração
- Ecrãs de plataforma
- Termos de Utilização
- Conformidade/Ativação

### <a name="user-abandonment-actions"></a>Ações de abandono do utilizador

As tabelas a seguir mostram a lista de ações do usuário que se qualificam ao solicitar um registro incompleto. Para ver exemplos de ecrãs de inscrição, pode ver os vídeos de inscrição do [iOS](https://channel9.msdn.com/Series/IntuneEnrollment/iOS-Enrollment) e [Android](https://channel9.msdn.com/Series/IntuneEnrollment/Android-Enrollment). 


#### <a name="setup-checklist-section"></a>Secção da lista de verificação da configuração

| Nome da ação | Ecrã ou fluxo | Platform | Ação |
| ---- |---- |---- |---- |
| EnrollmentWrapUp | Pedido para abrir uma página no Portal da Empresa | iOS/Android | **Cancelar** |
| EnrollmentWrapUp | Ecrã de inscrição do dispositivo até à conclusão da operação **A carregar recursos da empresa** | iOS/Android | Demorou mais de 30 minutos |
| DeviceCategory | Seleção da Categoria do Dispositivo (se configurado pelo administrador) até clicar em **Concluído** | iOS/Android | Demorou mais de 30 minutos |
| PreEnrollmentWizard | Ecrã de configuração do acesso quando inicia a inscrição, mas voltou à secção Configurar acesso | iOS/Android| **Adiar** |
| PreEnrollmentWizard | Ecrã de configuração do acesso até clicar em **Seguinte** no ecrã **O Que Se Segue** | iOS/Android | Demorou mais de 30 minutos |

#### <a name="platform-screens-section"></a>Secção dos ecrãs de plataforma

| Nome da ação | Ecrã ou fluxo | Platform | Ação |
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

| Nome da ação | Ecrã ou fluxo | Platform | Ação |
| ---- |---- |---- |---- |
| TermsofUse | Termos de utilização (se configurado pelo administrador) | iOS/Android | **Recusar Tudo** |
| TermsofUse | Termos de utilização até **Aceitar tudo** | iOS/Android | Demorou mais de 30 minutos |

#### <a name="complianceactivation-section"></a>Secção de Conformidade/Ativação

| Nome da ação | Ecrã ou fluxo | Platform | Ação |
| ---- |---- |---- |---- |
| Conformidade | A conformidade do dispositivo (se configurado pelo administrador) é apresentada como não verde na fase de pós-inscrição da configuração do acesso| iOS/Android | **Adiar** |
| Conformidade | A conformidade do dispositivo é apresentada como não verde até ser atualizada e ficar a verde | iOS/Android | Demorou mais de 30 minutos |
| Ativação | A ativação da inscrição (se configurado pelo administrador) é apresentada como não verde na configuração do acesso | iOS/Android | **Adiar** |
| Conformidade | A ativação do dispositivo é apresentada como não verde até ser atualizada e ficar a verde | iOS/Android | Demorou mais de 30 minutos |

## <a name="next-steps"></a>Próximos passos

Depois de verificar suas taxas de registro incompletas, você pode examinar as [Opções de registro](enrollment-options.md) para ver se é possível fazer alterações para melhorar o registro.

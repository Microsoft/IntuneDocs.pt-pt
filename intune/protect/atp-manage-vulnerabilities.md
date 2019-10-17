---
title: Usar o Intune para corrigir vulnerabilidades encontradas pelo Microsoft defender ATP – Azure | Microsoft Docs
description: Veja como gerenciar tarefas de segurança do e do gerenciamento de vulnerabilidades & ameaças, parte da ATP (proteção avançada contra ameaças) do Microsoft defender no console do Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 07/12/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 65213dab28210ad8162a7c18fe0e733ec7964571
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/16/2019
ms.locfileid: "72502581"
---
# <a name="use-intune-to-remediate-vulnerabilities-identified-by-microsoft-defender-atp"></a>Usar o Intune para corrigir vulnerabilidades identificadas pelo Microsoft defender ATP  

Ao integrar o Intune à ATP (proteção avançada contra ameaças) do Microsoft defender, você pode aproveitar o ATPs Threat (gerenciamento de vulnerabilidades & TVM) e usar o Intune para corrigir o ponto fraco do ponto de extremidade identificado pelo TVM. Essa integração oferece uma abordagem baseada em risco à descoberta e à priorização de vulnerabilidades que podem melhorar o tempo de resposta de correção em seu ambiente.  

O [Gerenciamento de vulnerabilidades de & de ameaças](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/next-gen-threat-and-vuln-mgt) faz parte da [proteção avançada contra ameaças do Microsoft defender](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/windows-defender-advanced-threat-protection).  

## <a name="how-integration-works"></a>Como funciona a integração  

Depois de conectar o Intune à proteção avançada contra ameaças do Microsoft defender, a ATP recebe detalhes de ameaça e vulnerabilidade dos dispositivos gerenciados.  

No console da central de segurança do Microsoft defender, os administradores de segurança do ATP examinam dados sobre vulnerabilidades do ponto de extremidade. Em seguida, os administradores usam um clique único para criar tarefas de segurança que sinalizam os dispositivos vulneráveis para correção. As tarefas de segurança são passadas imediatamente para o console do Intune, onde os administradores do Intune podem exibi-las. A tarefa de segurança identifica o tipo de vulnerabilidade, prioridade, status e as etapas a serem seguidas para corrigir a vulnerabilidade. O administrador do Intune escolhe aceitar ou rejeitar a tarefa.  

Quando uma tarefa é aceita, o administrador do Intune age a corrigir a vulnerabilidade por meio do Intune, usando as diretrizes fornecidas como parte da tarefa de segurança.  

As ações comuns para correção incluem:  

- **Bloquear** a execução de um aplicativo  
- **Implante** uma atualização do sistema operacional para atenuar a vulnerabilidade.  
- **Modifique** um valor de registro.  
- **Desabilitar** ou **habilitar** uma configuração para afetar a vulnerabilidade.  
- **Exigir atenção** alerta o administrador para a ameaça quando não há recomendação adequada para fornecer.  

Um fluxo de trabalho de exemplo:

- No Microsoft defender ATP, uma vulnerabilidade para um aplicativo chamado contoso Media Player v4 é descoberta e um administrador cria uma tarefa de segurança para atualizar esse aplicativo. O player de mídia da Contoso é um aplicativo não gerenciado que foi implantado com o Intune.  

  Essa tarefa de segurança aparece no console do Intune com um status de pendente:  
  ![Exibir a lista de tarefas de segurança no console do Intune](./media/atp-manage-vulnerabilities/temp-security-tasks.png)
 
- O administrador do Intune seleciona a tarefa de segurança para exibir detalhes sobre a tarefa.  O administrador seleciona **aceitar**, que atualiza o status no Intune e, em ATP, para ser *aceito*.  
  ![Accept ou rejeitar uma tarefa de segurança @ no__t-1 
 
- Em seguida, o administrador corrige a tarefa com base nas diretrizes fornecidas.  A orientação varia dependendo do tipo de correção necessária. Quando disponível, as diretrizes de correção incluem links que abrem painéis relevantes para configurações no Intune. 

  Como o player de mídia neste exemplo não é um aplicativo gerenciado, o Intune só pode fornecer instruções de texto. Se o aplicativo foi gerenciado, o Intune pode fornecer instruções para baixar uma versão atualizada e fornecer um link para abrir a implantação do aplicativo para que os arquivos atualizados possam ser adicionados à implantação. 

- Após a conclusão da correção, o administrador do Intune abre a tarefa de segurança e seleciona **concluir tarefa**.  O status de correção é atualizado para o Intune e, no ATP, em que os administradores de segurança confirmam o status revisado da vulnerabilidade.  

## <a name="prerequisites"></a>Pré-requisitos  

**Assinaturas**:  

- Microsoft Intune  
- Proteção avançada contra ameaças do Microsoft defender ([Inscreva-se para uma avaliação gratuita](https://www.microsoft.com/WindowsForBusiness/windows-atp?ocid=docs-wdatp-main-abovefoldlink)).  

**Configurações do Intune para ATP**:  

- Configure um serviço para conexão de serviço com o Microsoft defender ATP.  
- Implante uma política de configuração de dispositivo com um tipo de perfil do **Microsoft defender ATP (Windows 10 Desktop)** para dispositivos que terão risco avaliado pela ATP.

  Para obter informações sobre como configurar o Intune para funcionar com ATP, consulte [impor a conformidade para o Microsoft defender ATP com acesso condicional no Intune](advanced-threat-protection.md#enable-microsoft-defender-atp-in-intune).  

## <a name="work-with-security-tasks"></a>Trabalhar com tarefas de segurança  

1. Entre no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) e vá para **segurança do dispositivo** > **tarefas de segurança**.  
2. Selecione uma tarefa na lista para abrir uma janela de recurso que exibe detalhes adicionais para essa tarefa de segurança.  
3. Ao exibir a janela de recursos da tarefa de segurança, você pode selecionar links adicionais:  
   - APLICATIVOS GERENCIADOs – exiba o aplicativo que está vulnerável. Quando a vulnerabilidade se aplica a vários aplicativos, você verá uma lista filtrada de aplicativos.  
   - DISPOSITIVOS – exiba uma lista dos *dispositivos vulneráveis*, dos quais você pode vincular a uma entrada com mais detalhes para a vulnerabilidade nesse dispositivo.  
   - SOLICITAnte-use o link para enviar email para o administrador que enviou esta tarefa de segurança.  
   - OBSERVAÇÕES-Leia as mensagens personalizadas enviadas pelo solicitante ao abrir a tarefa de segurança.  
4. Selecione **aceitar** ou **rejeitar** para enviar notificação para ATP para sua ação planejada. Ao aceitar ou rejeitar uma tarefa, você pode enviar anotações, que são enviadas para ATP.  

5. Depois de aceitar uma tarefa, reabra a tarefa de segurança (se ela foi fechada) e siga os detalhes de correção para corrigir a vulnerabilidade.  As instruções fornecidas por ATP nos detalhes da tarefa de segurança variam dependendo da vulnerabilidade envolvida.  

   Quando for possível fazer isso, as instruções de correção incluem links que abrem os objetos de configuração relevantes no console do Intune.  

6. Depois de concluir as etapas de correção, abra a tarefa de segurança e selecione **concluir tarefa**.  Essa ação atualiza o status da tarefa de segurança no Intune e no ATP.  

Após a correção ser bem-sucedida, a pontuação de exposição de risco na ATP pode ser descartada, com base nas novas informações dos dispositivos corrigidos. 

## <a name="next-steps"></a>Passos Seguintes
Saiba mais sobre o Intune e [o Microsoft defender ATP](advanced-threat-protection.md)  
Examinar a [defesa contra ameaças móveis](mobile-threat-defense.md) do Intune  
Examinar o [painel Threat & gerenciamento de vulnerabilidades](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/tvm-dashboard-insights) no Microsoft defender ATP

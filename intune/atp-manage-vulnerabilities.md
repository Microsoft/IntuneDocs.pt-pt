---
title: Utilizar o Intune para remediar vulnerabilidades descobertas por Microsoft Defender ATP - Azure | Documentos da Microsoft
description: Veja como gerir tarefas de segurança do e ameaças e vulnerabilidade gestão, parte do Microsoft Defender avançadas de proteção contra ameaças (ATP) da consola do Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 05/17/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: f6f6f319b5c38f290f3cdb6d4a04528f3b227212
ms.sourcegitcommit: f8bbd9bac2016a77f36461bec260f716e2155b4a
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/16/2019
ms.locfileid: "65733500"
---
# <a name="use-intune-to-remediate-vulnerabilities-identified-by-microsoft-defender-atp"></a>Utilizar o Intune para remediar vulnerabilidades identificadas por Microsoft Defender ATP  

Quando integra o Intune com o Microsoft Defender avançadas de proteção contra ameaças (ATP), pode tirar partido das ameaças ATPs & Gestão de vulnerabilidade (TVM) e utilizar o Intune para remediar ponto fraco do ponto de extremidade identificado pelo TVM. Esta integração proporciona uma abordagem baseada em risco para a deteção e atribuição de prioridades das vulnerabilidades que pode melhorar o tempo de resposta de remediação em todo o ambiente.  

[Ameaças e gestão de vulnerabilidades](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/next-gen-threat-and-vuln-mgt) faz parte da [proteção do Microsoft Defender avançada contra ameaças](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/windows-defender-advanced-threat-protection).  

## <a name="how-integration-works"></a>Como funciona a integração  

Depois de ligar o Intune para a proteção de ameaças avançada do Microsoft Defender, o ATP recebe os detalhes de ameaças e vulnerabilidade dos dispositivos geridos.  

Na consola do Centro de segurança do Windows Defender, os administradores de segurança ATP rever dados sobre vulnerabilidades de ponto final. Os administradores, em seguida, utilizam um único clique para criar tarefas de segurança que sinalizar os dispositivos vulneráveis de remediação. As tarefas de segurança imediatamente são transmitidas para a consola do Intune em que os administradores do Intune o podem visualizá-los. A tarefa de segurança identifica o tipo de vulnerabilidade, prioridade, estado e os passos necessários para remediar a vulnerabilidade. O administrador do Intune decida aceitar ou rejeitar a tarefa.  

Quando uma tarefa for aceita, o administrador do Intune funciona, em seguida, para corrigir a vulnerabilidade no entanto, Intune, utilizar as diretrizes fornecidas como parte da tarefa de segurança.  

Ações comuns de remediação incluem:  
- **Bloco** uma aplicação em execução  
- **Implementar** uma atualização do sistema operativo para reduzir a vulnerabilidade.  
- **Modificar** um valor de registo.  
- **Desativar** ou **ativar** uma configuração para afetar a vulnerabilidade.  
- **Necessitam da atenção** o administrador para a ameaça de alertas quando não existe nenhuma recomendação adequada para fornecer.  

Um fluxo de trabalho de exemplo:  
- No Microsoft Defender ATP, uma vulnerabilidade para uma aplicação com o nome Contoso Media Player v4 é detetada e um administrador cria uma tarefa de segurança para atualizar essa aplicação. O leitor de multimédia de Contoso é uma aplicação não gerida que foi implementada com o Intune.  

  Esta tarefa de segurança é apresentada na consola do Intune com o estado pendente:  
  ![Ver a lista de tarefas de segurança na consola do Intune](./media/atp-manage-vulnerabilities/temp-security-tasks.png)
 
- O administrador do Intune seleciona a tarefa de segurança para ver detalhes sobre a tarefa.  O administrador, em seguida, seleciona **Accept**, que atualiza o estado no Intune e no ATP para ser *aceites*.  
  ![Aceitar ou rejeitar uma tarefa de segurança](./media/atp-manage-vulnerabilities/temp-accept-task.png) 
 
- O administrador, em seguida, efetua a remediação da tarefa com base na diretriz fornecida.  A documentação de orientação varia consoante o tipo de remediação que é necessário. Se estiver disponível, diretrizes de atualizações incluem ligações que abrem painéis relevantes para as configurações no Intune. 

  Uma vez que o leitor de multimédia neste exemplo não é uma aplicação gerida, o Intune só pode fornecer instruções de texto. Se a aplicação foi gerida, o Intune pode fornecer instruções para transferir uma versão atualizada e fornecer um link para abrir a implementação da aplicação para que os ficheiros atualizados podem ser adicionados à implementação. 

- Após a remediação de concluir, o administrador do Intune abre-se a tarefa de segurança e seleciona **tarefa concluída**.  O estado de remediação é atualizado para o Intune e no ATP, em que os administradores de segurança confirmar o estado revisado para a vulnerabilidade.  

## <a name="prerequisites"></a>Pré-requisitos  

**Subscrições**:  
- Microsoft Intune  
- A proteção de ameaças avançada do Microsoft Defender ([Inscreva-se numa avaliação gratuita](https://www.microsoft.com/WindowsForBusiness/windows-atp?ocid=docs-wdatp-main-abovefoldlink).)  

**Configurações do Intune para ATP**:  
- Configure uma ligação de serviço para serviço com o Microsoft Defender ATP.  
- Implementar uma política de conformidade de dispositivos com o tipo de perfil **Microsoft Defender ATP (Windows 10 Desktop)** para dispositivos que terão o risco avaliado por ATP.
  Para obter informações sobre como configurar o Intune para funcionar com o ATP, consulte [impor a conformidade para Microsoft Defender ATP com acesso condicional no Intune](https://docs.microsoft.com/intune/advanced-threat-protection#enable-windows-defender-atp-in-intune).  

## <a name="work-with-security-tasks"></a>Trabalhar com tarefas de segurança  

1. Inicie sessão no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) e aceda à **segurança do dispositivo** > **tarefas de segurança**.  
2. Selecione uma tarefa na lista para abrir uma janela de recursos que apresenta detalhes adicionais para essa tarefa de segurança.  
3. Ao visualizar a janela de recursos de tarefas de segurança, pode selecionar links adicionais:  
   - Aplicações GERIDAS - ver a aplicação que está vulnerável. Quando se aplica a vulnerabilidade para várias aplicações, verá uma lista de aplicações filtrada.  
   - DISPOSITIVOS - ver uma lista do *dispositivos vulneráveis*, da qual pode ligar através de uma entrada com mais detalhes sobre a vulnerabilidade nesse dispositivo.  
   - REQUERENTE - utilize a ligação para enviar correio para o administrador que enviou esta tarefa de segurança.  
   - NOTAS de – mensagens personalizadas de leitura submetidas pelo requerente ao abrir a tarefa de segurança.  
4. Selecione **Accept** ou **rejeitar** Enviar notificação para ATP para a ação em planeadas. Quando aceita ou rejeitar uma tarefa, pode enviar anotações, o que são enviadas para o ATP.  

5. Depois de aceitar uma tarefa, volte a abrir a tarefa de segurança (se fechado) e siga os detalhes de REMEDIAÇÃO para remediar a vulnerabilidade.  As instruções fornecidas pelo ATP nos detalhes da tarefa de segurança variam consoante a vulnerabilidade envolvida.  

   Quando é possível fazer isso, as instruções de atualização incluem ligações que abrem os objetos de configuração relevantes na consola do Intune.  

6. Depois de concluir os passos de remediação, abra a tarefa de segurança e selecione **tarefa concluída**.  Esta ação atualiza o estado da tarefa de segurança no Intune e o ATP.  

Após remediação é concluída, pode remover a classificação de exposição de risco no ATP, com base nas novas informações dos dispositivos remediadas. 

## <a name="next-steps"></a>Próximos Passos
Saiba mais sobre o Intune e [Microsoft Defender ATP](https://docs.microsoft.com/intune/advanced-threat-protection)  
Reveja o Intune [defesa contra ameaças móveis](https://docs.microsoft.com/intune/mobile-threat-defense)  
Reveja os [dashboard de ameaças e gestão de vulnerabilidades](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/tvm-dashboard-insights) no Microsoft Defender ATP

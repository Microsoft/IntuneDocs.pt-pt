---
title: "Gerir versões de sistemas operativos com o Intune"
description: "Saiba como gerir versões de sistemas operativos em diversas plataformas com o Microsoft Intune."
keywords: 
author: dougeby
manager: dougeby
ms.date: 10/19/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 361ef17b-1ee0-4879-b7b1-d678b0787f5a
ms.openlocfilehash: 78abef01e968b59b81a74dcd6b67df31dbf29def
ms.sourcegitcommit: 2c7794848777e73d6a9502b4e1000f0b07ac96bc
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/01/2018
---
# <a name="manage-operating-system-versions-with-intune"></a>Gerir versões de sistemas operativos com o Intune
Nas plataformas modernas de ambiente de trabalho e dispositivos móveis, são constantemente publicadas atualizações importantes, patches e novas versões. Tem controlos para gerir atualizações e patches totalmente no Windows, mas outras plataformas como Android e iOS precisam que os seus utilizadores finais participem no processo.  O Microsoft Intune tem as ferramentas para o ajudar a estruturar a gestão das versões do seu sistema operativo em diferentes plataformas.

O Intune pode ajudá-lo a lidar com estes cenários comuns: 
- Determinar que versões do sistema operativo estão nos dispositivos dos seus utilizadores finais
- Controlar o acesso a dados organizacionais em dispositivos enquanto valida o lançamento de um novo sistema operativo
- Incentivar/exigir que os utilizadores finais atualizem os dispositivos para a versão do sistema operativo mais recente aprovada pela sua organização
- Gerir a implementação da nova versão de um sistema operativo em toda a organização
  
## <a name="operating-system-version-control-using-intune-mobile-device-management-mdm-enrollment-restrictions"></a>Controlo da versão do sistema operativo através das restrições de inscrição da gestão de dispositivos móveis (MDM) do Intune
As restrições de inscrição do MDM do Intune permitem-lhe definir os requisitos do dispositivo do cliente antes de permitir a inscrição do dispositivo. O objetivo é exigir que os utilizadores finais inscrevam apenas os dispositivos em conformidade antes de obterem acesso aos recursos organizacionais. Os requisitos dos dispositivos incluem as versões mínimas e máximas do sistema operativo permitidas para as plataformas suportadas.
 
![Painel de restrições na configuração da plataforma](./media/os-version-platform-configurations.png) 
 
### <a name="in-practice"></a>Procedimentos
As organizações estão a utilizar restrições aos tipos de dispositivos para controlarem o acesso aos recursos da organização através das seguintes definições: 
1. Utilizar uma versão mínima do sistema operativo para manter os utilizadores finais em plataformas atuais e suportadas na sua organização. 
2. Não especificar a versão máxima do sistema operativo (sem limite) ou definir a mesma para a versão validada mais recente na sua organização para dar tempo ao lançamento de testes internos de novos sistemas operativos.

Para obter mais informações, veja [Definir restrições de tipos de dispositivos](https://docs.microsoft.com/intune/enrollment-restrictions-set#set-device-type-restrictions).
 
## <a name="operating-system-version-reporting-and-compliance-with-intune-mdm-device-compliance-policies"></a>Relatórios sobre a versão do sistema operativo e a conformidade com as políticas de conformidade de dispositivo MDM do Intune
As políticas de conformidade de dispositivo MDM do Intune fornecem-lhe as seguintes ferramentas: 
- Regras específicas de conformidade
- A visualização do estado de conformidade através de relatórios
- Tomar medidas relativamente à não conformidade através da quarentena de dispositivos e acesso condicional

Tal como as restrições nas inscrições, as políticas de conformidade de dispositivos incluem as versões mínimas e máximas do sistema operativo. As políticas também têm uma linha cronológica de conformidade para fornecer aos utilizadores um período de tolerância para estar em conformidade. As políticas de conformidade de dispositivo mantêm os dispositivos do utilizador final inscritos com a política organizacional.

![Conformidade de dispositivos – ações para dispositivos não conformes](./media/os-version-actions-noncompliance.png) 

### <a name="in-practice"></a>Procedimentos
As organizações estão a utilizar as políticas de conformidade de dispositivos para os mesmos cenários apresentados nas restrições de inscrição. Estas políticas garantem que os utilizadores utilizam as versões atuais e validadas do sistema operativo na sua organização. Quando o utilizador final deixa de estar em conformidade, o acesso aos recursos organizacionais pode ser bloqueado através do acesso condicional até que os utilizadores finais se encontrem no intervalo suportado do sistema operativo para a sua organização. Os utilizadores finais são notificados quando deixam de estar em conformidade e são-lhe fornecidos os passos para voltar a obter acesso.   

Para obter mais informações, veja [Introdução à conformidade de dispositivos](https://docs.microsoft.com/intune/device-compliance-get-started).
 
## <a name="operating-system-version-controls-using-intune-app-protection-policies"></a>Controlo da versão do sistema operativo com as políticas de proteção de aplicações do Intune    
As políticas de proteção de aplicações e a gestão de aplicações móveis (MAM) do Intune acedem a definições que lhes permitem especificar a versão mínima do sistema operativo ao nível da aplicação. Isto permite-lhe informar e incentivar ou exigir que os seus utilizadores finais atualizem o seu sistema operativo para uma versão mínima específica.
 
Tem duas opções diferentes: 

|Aviso  |Bloqueio  |
|---------|---------|
|O Aviso informa o utilizador final de que deve realizar a atualização, se abrir uma aplicação com uma política de proteção de aplicações ou com definições de acesso MAM num dispositivo com uma versão do sistema operativo anterior à versão especificada. O acesso à aplicação e aos dados organizacionais é permitido.|O Bloqueio informa o utilizador final de que tem de realizar a atualização, quando abrir uma aplicação com uma política de proteção de aplicações ou com definições de acesso MAM num dispositivo com uma versão do sistema operativo anterior à versão especificada. O acesso à aplicação e aos dados organizacionais não é permitido.|
|![Caixa de diálogo de aviso de atualização do Android](./media/os-version-update-warning.png)    |![Caixa de diálogo Acesso à aplicação bloqueado](./media/os-version-access-blocked.png)          |

 
### <a name="in-practice"></a>Procedimentos
Atualmente, as organizações estão a utilizar as definições da política de proteção de aplicações quando as aplicações são abertas ou retomam uma ação, de forma a educar os utilizadores finais sobre a necessidade de manter as suas aplicações atualizadas. Um exemplo de configuração seria avisar os utilizadores que utilizarem uma versão um número abaixo da atual e bloquear os que utilizarem versões dois números abaixo da atual.
 
Para obter mais informações, veja [Como criar e atribuir políticas de proteção de aplicações](https://docs.microsoft.com/intune/app-protection-policies).

## <a name="managing-a-new-operating-system-version-rollout"></a>Gerir a implementação de um novo sistema operativo
Pode utilizar as funcionalidades do Intune descritas neste artigo para o ajudar a mover a sua organização para uma nova versão do sistema operativo na linha cronológica que definir. Os seguintes passos fornecem um exemplo de um modelo de implementação para mover os seus utilizadores da versão 1 do sistema operativo para a versão 2 do mesmo em sete dias.
- **Passo 1**: utilize as restrições de inscrição para exigir a versão 2 do sistema operativo como a versão mínima para inscrever o dispositivo. Isto garante que os dispositivos dos novos utilizadores finais estão em conformidade na altura da inscrição.
- **Passo 2a**: utilize as políticas de proteção de aplicações do Intune para avisar os seus utilizadores ,quando uma aplicação for aberta ou retomar uma ação, de que é necessária a versão 2 do sistema operativo.
- **Passo 2b**: utilize as políticas de conformidade de dispositivos para exigir a versão 2 do sistema operativo como a versão mínima para o dispositivo estar em conformidade. Utilize **Ações** de não conformidade para permitir um período de tolerância de sete dias e para enviar aos utilizadores finais uma notificação por e-mail com a sua linha cronológica e requisitos.
  -  Estas políticas informam os utilizadores de que existem dispositivos que precisam de ser atualizados, através de um e-mail, do Portal da Empresa do Intune e quando abrirem a aplicação (para aplicações com a política de proteção de aplicações ativada).
  - Pode criar um relatório de conformidade para identificar os utilizadores que não se encontram em conformidade. 
- **Passo 3a**: utilize as políticas de proteção de aplicações do Intune para bloquear utilizadores quando uma aplicação é aberta ou retoma uma ação, caso o dispositivo não esteja a executar a versão 2 do sistema operativo.
- **Passo 3b**: utilize as políticas de conformidade de dispositivos para exigir a versão 2 do sistema operativo como a versão mínima para o dispositivo estar em conformidade.
  - Estas políticas exigem que os dispositivos sejam atualizados para que os utilizadores continuem a ter acesso aos dados organizacionais. Os serviços protegidos são bloqueados quando forem utilizados com um dispositivo com acesso condicional. As aplicações com a política de proteção de aplicações ativada são bloqueadas quando abertas ou quando tentam aceder a dados organizacionais.

## <a name="next-steps"></a>Próximos passos
Utilize os seguintes recursos para gerir as versões de sistemas operativos na sua organização: 

- [Definir restrições de tipos de dispositivos](https://docs.microsoft.com/intune/enrollment-restrictions-set#set-device-type-restrictions)
- [Introdução à conformidade de dispositivos](https://docs.microsoft.com/intune/device-compliance-get-started)
- [Como criar e atribuir políticas de proteção de aplicações](https://docs.microsoft.com/intune/app-protection-policies)

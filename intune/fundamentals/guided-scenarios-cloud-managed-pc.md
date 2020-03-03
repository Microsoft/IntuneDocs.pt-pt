---
title: Cenário guiado - Desktop Moderno gerido pela Nuvem
titleSuffix: Microsoft Intune
description: Conheça o cenário guiado para configurar e configurar um ambiente de trabalho moderno básico a partir do portal de Gestão de Dispositivos Microsoft 365.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/26/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9ddd59715a0730a52738088700a1f2b9166bfa80
ms.sourcegitcommit: fab685b22a010fe231b27a0c5eda34a6f22f4c8d
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/02/2020
ms.locfileid: "78216207"
---
# <a name="guided-scenario---cloud-managed-modern-desktop"></a>Cenário guiado - Desktop Moderno gerido pela Nuvem

O ambiente de trabalho moderno é a plataforma de produtividade de última geração para o Trabalhador da Informação. O Office 365 ProPlus e o Windows 10 são os componentes centrais do ambiente de trabalho moderno, juntamente com as mais recentes linhas de segurança para o Windows 10 e microsoft Defender Advanced Threat Protection. 

Gerir o ambiente de trabalho moderno a partir da nuvem traz o benefício adicional de ações remotas em toda a Internet. A gestão da nuvem utiliza as políticas incorporadas de Gestão de Dispositivos Móveis windows e remove dependências da política local do grupo Ative Directory. 

Se quiser avaliar um ambiente de trabalho moderno gerido pela nuvem na sua própria organização, este cenário guiado predefine todas as configurações necessárias para uma implementação básica. Neste cenário guiado, irá criar um ambiente seguro onde poderá experimentar as capacidades de gestão de dispositivos Intune. 

## <a name="prerequisites"></a>Pré-requisitos
- [Defina a autoridade do MDM para Intune](~/fundamentals/mdm-authority-set.md#set-mdm-authority-to-intune) - A definição de autoridade de gestão de dispositivos móveis (MDM) determina como gere os seus dispositivos. Como administrador de TI, tem de definir uma autoridade de MDM antes de os utilizadores poderem inscrever dispositivos para gestão.
- Mínimo M365 E3 (ou M365 E5 para melhor segurança)
- Dispositivo Windows 10 1903 (registado com o Windows Autopilot para melhor experiência de utilizador final)
- Permissões de administrador insintonizadas necessárias para completar este cenário guiado:
  - Configuração do dispositivo Ler, Criar, Excluir, Atribuir e Atualizar
  - Programas de Inscrição Ler dispositivo, Ler perfil, Criar perfil, Atribuir perfil, Excluir perfil
  - Aplicativos móveis Ler, Criar, Excluir, Atribuir e Atualizar
  - Leitura e Atualização da Organização
  - Bases de Segurança Ler, Criar, Excluir, Atribuir e Atualizar
  - Conjuntos de política Ler, Criar, Excluir, Atribuir e Atualizar

## <a name="step-1---introduction"></a>Passo 1 - Introdução

Utilizando este cenário guiado, irá configurar um utilizador de teste, inscrever um dispositivo em Intune e implementar o dispositivo com configurações recomendadas por Intune, bem como o Windows 10 e o Office ProPlus. O seu dispositivo também será configurado para a Proteção de Ameaças Avançadas do Microsoft Defender, se optar por [ativar esta proteção em Intune](~/protect/advanced-threat-protection.md#enable-microsoft-defender-atp-in-intune). O utilizador que configurar e o dispositivo que se inscreveu serão adicionados a um novo grupo de segurança e serão configurados com as definições recomendadas para segurança e produtividade. 

### <a name="what-you-will-need-to-continue"></a>O que precisa para continuar

Deve fornecer o seu dispositivo de teste e o utilizador de teste neste cenário guiado. Certifique-se de que completa as seguintes tarefas:
- Criar uma conta de utilizador de teste no Diretório Ativo Azure.
- Crie um dispositivo de teste com o Windows 10, versão 1903 ou mais tarde.
- (Opcional) [Registe o dispositivo de teste com o Windows Autopilot](~/enrollment/enrollment-autopilot.md#add-devices).
- (Opcional) Ative a marca na página de entrada de [diretório sinuoso Azure Ative Diretório da sua organização](https://go.microsoft.com/fwlink/?linkid=2102455).

## <a name="step-2---user"></a>Passo 2 - Utilizador

Escolha um utilizador para configurar o dispositivo. Esta pessoa será o principal utilizador do dispositivo.

Se pretender adicionar mais utilizadores ou dispositivos a esta configuração, basta adicionar os utilizadores e dispositivos aos grupos de segurança AAD gerados pelo assistente. Ao contrário de outros Cenários Guiados, não é necessário executar o assistente mais de uma vez, uma vez que a configuração não é personalizável. Basta adicionar mais utilizadores e dispositivos aos grupos AAD criados. Após completar o assistente, poderá visualizar o grupo gerado com as polícias recomendadas. 

## <a name="step-3---device"></a>Passo 3 - Dispositivo

Certifique-se de que o seu dispositivo está a executar o Windows 10, versão 1903 ou mais tarde.  O utilizador principal terá de configurar o dispositivo quando o receber. Existem duas opções de configuração disponíveis para o utilizador. 

### <a name="option-a--windows-autopilot"></a>Opção A – Windows Autopilot
O Windows Autopilot automatiza a configuração de novos dispositivos para que os utilizadores possam instalá-los fora da caixa, sem assistência de TI. Se o seu dispositivo já estiver registado no Windows Autopilot, selecione-o pelo seu número de série. Para obter mais informações sobre a utilização do Windows Autopilot, consulte [o dispositivo Register com o piloto do Windows Auto (Opcional)](~/fundamentals/guided-scenarios-cloud-managed-pc.md#register-device-with-windows-autopilot-optional).

### <a name="option-b--manual-device-enrollment"></a>Opção B – Inscrição manual do dispositivo
Os utilizadores irão configurar manualmente e inscrever os seus novos dispositivos na gestão de dispositivos móveis. Depois de concluir este cenário, redefinir o dispositivo e dar ao utilizador principal as instruções de inscrição para dispositivos Windows. Para mais informações, consulte [Adesão a um dispositivo Windows 10 para a AD Azure durante a experiência de primeira execução](https://docs.microsoft.com/azure/active-directory/devices/azuread-joined-devices-frx#joining-a-device).

## <a name="step-4---review--create"></a>Passo 4 - Rever + criar

O passo final permite-lhe rever um resumo das definições configuradas. Depois de ter revisto as suas escolhas clique em **Implementar** para completar o cenário guiado. Uma vez concluído o cenário guiado, é apresentada uma tabela de recursos. Pode editar estes recursos mais tarde, no entanto, uma vez que saia da vista sumária, a mesa não será salva.

> [!IMPORTANT]
> Uma vez concluído o cenário guiado, apresentará um resumo. Pode modificar os recursos listados no resumo mais tarde, no entanto a tabela que exibe estas resouces não será guardada.

### <a name="verification"></a>Verificação
1. Verifique se o âmbito de utilização do MDM selecionado é atribuído
    - Certifique-se de que o [âmbito do utilizador do MDM](~/enrollment/windows-enroll.md#enable-windows-10-automatic-enrollment) é:
        - Definido para **Tudo** para a aplicação **Microsoft Intune** ou,
        - Definido para **Alguns**. Adicione também o grupo de utilizadores criado por este cenário guiado.
2. Verifique se o utilizador selecionado é capaz de se juntar aos dispositivos ao Diretório Ativo Azure.
    - Certifique-se de que a adesão à AAD é:
        - Definido para **Todos** ou,
        - Definido para **Alguns**. Adicione também o grupo de utilizadores criado por este cenário guiado.
3. Siga os passos adequados no dispositivo para o juntar ao Azure AD com base no seguinte:
    - Com piloto automático. Para mais informações, consulte o [modo de utilização do Windows Autopilot](https://docs.microsoft.com/windows/deployment/windows-autopilot/user-driven).
    - Sem Piloto Automático: Para mais informações, consulte [Juntar um dispositivo Windows 10 ao Azure AD durante a experiência de primeira execução](https://docs.microsoft.com/azure/active-directory/devices/azuread-joined-devices-frx#joining-a-device).

### <a name="what-happens-when-i-click-deploy"></a>O que acontece quando clico em Implementar?
O utilizador e o dispositivo serão adicionados a novos grupos de segurança. Também serão configurados com configurações recomendadas por Intune para segurança e produtividade no trabalho ou na escola. Depois de o utilizador se juntar ao dispositivo ao Azure AD, serão adicionadas aplicações e configurações adicionais ao dispositivo. Para saber mais sobre estas configurações adicionais, consulte [Quickstart: Inscreva o seu dispositivo Windows 10](~/enrollment/quickstart-enroll-windows-device.md).

## <a name="additional-information"></a>Informações adicionais

### <a name="register-device-with-windows-autopilot-optional"></a>Registar dispositivo com O Piloto Automático do Windows (Opcional)

Pode optar opcionalmente por utilizar um dispositivo Autopilot registado. Para o Autopilot, este cenário guiado atribuirá um perfil de implementação de Piloto Automático e o perfil da página de estado de inscrição. O perfil de implementação do Piloto Automático será configurado da seguinte forma:
- Modo orientado pelo utilizador – ou seja, exige que o utilizador final introduza o nome de utilizador e a palavra-passe durante a configuração do Windows.
- Azure AD junta-se.
- Personalize a configuração do Windows:
  - Ocultar o ecrã de termos de licenciamento do Microsoft Software
  - Ocultar definições de privacidade 
  - Criar o perfil local do utilizador sem privilégios administrativos locais
  - Ocultar as opções de Conta de Alteração na página de inscrição corporativa

A página de estado de Inscrição será configurada para ser ativada apenas para dispositivos Autopilot e não bloqueará a espera de que todas as aplicações sejam instaladas.

O cenário guiado também atribuirá o utilizador ao dispositivo Autopilot selecionado para uma experiência de configuração personalizada.

#### <a name="post-requisites"></a>Pós-requisitos
Uma vez que o utilizador se junte ao Diretório Ativo Azure, serão aplicadas as seguintes configurações no dispositivo:
1. O Office 365 ProPlus será automaticamente instalado no PC gerido pela Cloud. Inclui as aplicações que conhece, incluindo Access, Excel, OneNote, Outlook, PowerPoint, Publisher, Skype for Business e Word. Pode utilizar estas aplicações para se conectar com os serviços do Office 365, tais como SharePoint Online, Exchange Online e Skype para Business Online. O Office 365 ProPlus é atualizado regularmente com novas funcionalidades, ao contrário das versões não subscritas do Office. Para uma lista de novas funcionalidades, veja o que há de novo no Office 365.
2. As linhas de base de segurança do Windows serão instaladas no PC gerido pela Cloud. Se tiver configurado a Microsoft Defender Advanced Threat Protection, o cenário guiado também configurará as definições de base para o Defender. A Defender Advanced Threat Protection fornece uma nova camada de proteção pós-violação para a pilha de segurança do Windows 10. Com uma combinação de tecnologia cliente incorporada no Windows 10 e um robusto serviço na nuvem, ajudará a detetar ameaças que passaram por outras defesas. 

## <a name="next-steps"></a>Próximos passos

- Se estiver a utilizar a Deteção avançada de ameaças do Microsoft Defender, crie uma política de [conformidade intune](~/protect/advanced-threat-protection.md#create-and-assign-the-compliance-policy) para exigir que a análise de ameaças do Defender cumpra o cumprimento.
- Crie uma [política de acesso condicional baseada no Dispositivo](~/protect/advanced-threat-protection.md#create-a-conditional-access-policy) para bloquear o acesso se o dispositivo não cumprir a conformidade com o Intune.

---
title: Utilizar linhas de base de segurança no Microsoft Intune – Azure | Documentos da Microsoft
description: Adicione ou configure as definições de segurança do grupo recomendadas para proteger dados em dispositivos com o Microsoft Intune para gestão de dispositivos móveis e de utilizador. Ativar o bitlocker, configurar a proteção de ameaças avançada do Windows Defender, controlam o Internet Explorer, utilizar Smart Screen, definir políticas de segurança local, exigir uma palavra-passe, bloquear transferências de internet e muito mais.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/01/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 94fbd4b4f73dd24f83832af010a6350ae8a0aa25
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/14/2019
ms.locfileid: "57394678"
---
# <a name="create-a-windows-10-security-baseline-in-intune"></a>Criar uma linha de base de segurança do Windows 10 no Intune

Linhas de base de segurança é uma funcionalidade em pré-visualização que está disponível para dispositivos com Windows 10 e posterior. Esta funcionalidade inclui muitas configurações suportadas pelo Intune que pode utilizar para ajudar a proteger e proteger os seus utilizadores e dispositivos. Define também automaticamente estas definições para os valores recomendados por equipes de segurança. Por exemplo, a linha de base, automaticamente ativa o BitLocker automaticamente requer uma palavra-passe para desbloquear um dispositivo, Desabilita automaticamente a autenticação básica e muito mais.

Esta funcionalidade aplica-se a:

- Windows 10 versão 1809 e posterior

> [!NOTE]
> Enquanto as linhas de base de segurança está em pré-visualização, a Microsoft não recomendada através de perfis num ambiente de produção, como as linhas de base podem mudar ao longo da pré-visualização. Quando as linhas de base de segurança estão disponíveis em geral, perfis existentes não podem ser convertidos para os perfis mais recente suportados.

O objetivo de utilizar linhas de base de segurança é fornecer um fluxo de trabalho seguro do ponto-a-ponto, ao trabalhar com o Microsoft 365. Alguns dos benefícios incluem:

- Uma linha de base de segurança inclui as melhores práticas e recomendações sobre as definições que afetam a segurança. Parceiros do Intune com a equipe de segurança mesmo do Windows que cria as linhas de base de segurança de política de grupo. Estas recomendações baseiam-se nas orientações e ampla experiência.
- Se estiver totalmente familiarizado com o Intune e não tem a certeza onde começar, em seguida, linhas de base de segurança dá-lhe uma vantagem. Pode, rapidamente, criar e implementar um perfil de seguro, sabendo que está ajudando a proteger os dados e recursos da sua organização.
- Se utilizar atualmente a política de grupo, a migração para o Intune para gestão é muito mais fácil com essas linhas de base. Essas linhas de base estão nativamente incorporadas Intune e incluem uma experiência de gestão moderna.

Linhas de base de segurança criar um "perfil de configuração" no Intune. Este perfil inclui todas as definições na linha de base. Em seguida, aplicar ou atribuir este perfil para os utilizadores, grupos e dispositivos.

Depois do perfil é atribuído, pode monitorizar o perfil e monitorizar a linha de base. Por exemplo, pode ver quais os dispositivos que correspondem a linha de base ou não correspondem a linha de base.

Este artigo mostra-lhe como utilizar linhas de base de segurança para criar um perfil, atribuir o perfil e monitorizar o perfil.

[Linhas de base de segurança de Windows](https://docs.microsoft.com/windows/security/threat-protection/windows-security-baselines) é um ótimo recurso para obter mais informações sobre esta funcionalidade. [Gestão de dispositivos móveis](https://docs.microsoft.com/windows/client-management/mdm/) (MDM) é um ótimo recurso sobre MDM e o que pode fazer em dispositivos Windows.

## <a name="co-managed-devices"></a>Dispositivos cogeridos

Linhas de base de segurança nos dispositivos geridos pelo Intune são semelhantes aos dispositivos cogeridos com o Configuration Manager. Dispositivos cogeridos utilizam o System Center Configuration Manager e o Microsoft Intune para gerir os dispositivos Windows 10 em simultâneo. Permite-lhe na cloud-anexar o investimento existente do Configuration Manager para os benefícios do Intune. [Descrição geral de cogestão](https://docs.microsoft.com/sccm/comanage/overview) é um ótimo recurso, se utilizar o Configuration Manager e também desejam obter os benefícios da cloud.

Ao utilizar dispositivos cogeridos, tem de mudar a **configuração do dispositivo** carga de trabalho (suas configurações) para o Intune. [Cargas de trabalho de configuração de dispositivo](https://docs.microsoft.com/sccm/comanage/workloads#device-configuration) fornece mais informações.

## <a name="create-the-profile"></a>Criar o perfil

1. Na [portal do Azure](https://portal.azure.com/), selecione **todos os serviços** > Filtrar **Intune** > selecione **Intune**.
2. Selecione **linhas de base de segurança (pré-visualização)**. Está disponível uma lista de linhas de base disponíveis. À medida que são adicionadas mais linhas de base, irá vê-los aqui:

    ![Ver uma lista de linhas de base de segurança atualmente disponíveis no Intune](./media/security-baselines/available-baselines.png)

3. Selecione a linha de base que pretende utilizar > **criar perfil**.
4. Na **Noções básicas**, introduza as seguintes propriedades:

    - **Nome**: Introduza um nome para o seu perfil de linhas de base de segurança. Por exemplo, introduza `pilot Windows 10 MDM baseline - Oct 2018`.
    - **Descrição**: Introduza algum texto que descreve o que faz esta linha de base. A descrição é que digitar qualquer texto que pretende. É opcional, mas definitivamente recomendado.

5. Expanda **definições**. Na lista, pode ver todas as configurações nesta linha de base de segurança e o que a definição é automaticamente definida como. As definições e os respetivos valores são recomendados e podem ser alterados por si.

    ![Expanda a definição para ver todas as definições nesta linha de base de segurança no Intune](./media/security-baselines/sample-list-of-settings.png)

    Expanda algumas das definições para verificar seus valores. Por exemplo, expanda **o Windows Defender**. Observe que alguns das definições e o que eles estiverem definidos como:

    ![Veja quais são alguns do Windows Defender definições são definidas automaticamente como no Intune](./media/security-baselines/expand-windows-defender.png)

6. **Criar** o perfil. 
7. Selecione **perfis**. Seu perfil é criado e apresentado na lista. No entanto, ele não faz nada ainda. Em seguida, atribua o perfil.

## <a name="assign-the-profile"></a>Atribuir o perfil

Depois do perfil é criado, está pronto para ser atribuído aos seus utilizadores, dispositivos e grupos. Uma vez atribuído, o perfil e as respetivas definições são aplicadas para os utilizadores, dispositivos e grupos que escolher.

1. No Intune, selecione **linhas de base de segurança** > Escolha uma linha de base > **perfis**.
2. Selecione o seu perfil > **atribuições**.

    ![Escolha o seu perfil de linha de base de segurança no Intune e clique em atribuições para implementar o perfil](./media/security-baselines/assignments.png)

3. Na **inclusão** separador, adicione os grupos, usuários, ou dispositivos que pretende que esta política se aplique.

    > [!TIP]
    > Tenha em atenção que também pode **excluir** grupos. Se aplicar uma política para **todos os utilizadores**, considere excluir os grupos de administrador. No caso de algo acontece, os administradores não deseja são bloqueados.

4. **Guarde** as suas alterações.

Assim que guardar, o perfil é enviada por push para dispositivos quando eles dar entrada no Intune. Portanto, isso pode acontecer imediatamente.

## <a name="available-security-baselines"></a>Linhas de base de segurança disponíveis  

As seguintes linhas de base de segurança são avaialable para utilização com o Intune.
- **Pré-visualização: Linha de base de segurança MDM**
  - Versão: [Outubro de 2018](security-baseline-settings-windows.md)

## <a name="q--a"></a>Perguntas e Respostas

#### <a name="why-these-settings"></a>Por que estas definições?

A equipa de segurança da Microsoft tem anos de experiência trabalhando diretamente com os desenvolvedores do Windows e da Comunidade de segurança para criar estas recomendações. As definições nesta linha de base são consideradas as opções de configuração relacionadas com segurança mais relevantes. Em cada nova compilação do Windows, a equipe ajusta as recomendações com base nos recursos recentemente publicados.

#### <a name="is-there-a-difference-in-the-recommendations-for-windows-security-baselines-for-group-policy-vs-intune"></a>Existe uma diferença nas recomendações para linhas base de segurança do Windows para o vs de política de grupo. Intune?

Da mesma equipe de segurança da Microsoft escolheu e organizados as definições para cada linha de base. O Intune inclui todas as configurações relevantes na linha de base de segurança do Intune. Existem algumas definições na linha de base de política de grupo que são específicas para um controlador de domínio no local. Estas definições são excluídas da recomendações do Intune. Todas as outras definições são os mesmos.

#### <a name="are-the-intune-security-baselines-cis-or-nsit-compliant"></a>São as Intune segurança linhas de base de itens de configuração ou NSIT em conformidade?

Estritamente em termos, não. A equipe de segurança da Microsoft consulta organizações, como itens de configuração, para compilar suas recomendações. No entanto, não existe um mapeamento entre "CIS e compatível com" linhas de base da Microsoft.

#### <a name="what-certifications-does-microsofts-security-baselines-have"></a>As certificações tem linhas de base da Microsoft? 

- A Microsoft continua a publicar linhas de base de segurança para as políticas de grupo (GPOs) e o [Kit de ferramentas de compatibilidade de segurança](https://docs.microsoft.com/windows/security/threat-protection/security-compliance-toolkit-10), porque tem por muitos anos. Essas linhas de base são usadas por muitas organizações. As recomendações apresentadas nessas linhas de base são de envolvimento da equipe de segurança da Microsoft com clientes corporativos e órgãos externos, incluindo o departamento de defesa (DoD), instituto nacional de normas e tecnologia (NIST) e muito mais. Compartilhamos nosso recomendações e linhas de base com essas organizações. Essas organizações também têm suas próprias recomendações que espelham estreitamente recomendações da Microsoft. Como a gestão de dispositivos móveis (MDM) continua a crescer para a cloud, a Microsoft criou equivalentes recomendações de MDM dessas linhas de base de política de grupo. Essas linhas de base adicionais incorporadas no Microsoft Intune e incluem relatórios de conformidade em utilizadores, grupos e dispositivos que sigam (ou não siga) a linha de base.

- Muitos clientes estão a utilizar as recomendações de linha de base do Intune como um ponto de partida e, em seguida, personalizá-la para atender às suas IT e solicitações de segurança. Windows 10 RS5 do Microsoft **linha de base de segurança de MDM** é a primeira linha de base para libertar. Esta linha de base foi concebida como uma infraestrutura genérica que permite aos clientes, eventualmente, importar outras linhas de base de segurança com base nos itens de configuração, NIST e outros padrões. Atualmente, ele está disponível para Windows e, eventualmente, irá incluir o iOS e Android.

- Migrar de políticas de grupo do Active Directory no local para uma solução de cloud pura através do Azure Active Directory (AD) com o Microsoft Intune é uma jornada. Para ajudar a, existem complementar GPOs publicados para o AD híbrido e de dispositivos associados ao AD Azure. Estes dispositivos podem obter as definições de MDM da cloud (Intune) e as definições de política de grupo de controladores de domínio no local, conforme necessário.

## <a name="next-steps"></a>Passos Seguintes
- Ver os [definições de linha de base de segurança do Windows](security-baseline-settings-windows.md) suportados pelo Intune.  
- Verifique o estado e o monitor a [linha de base e perfil](security-baselines-monitor.md).

---
title: Utilizar o Windows Defender ATP no Microsoft Intune – Azure | Microsoft Docs
description: Veja como ativar a Proteção Avançada Contra Ameaças (ATP) do Windows Defender num cenário ponto a ponto, incluindo ativar a ATP no Intune e no Centro de Segurança do Windows Defender (portal ATP), carregar dispositivos através de um perfil de configuração ATP, criar a política de conformidade de dispositivos Intune, criar uma política de acesso condicional do Azure AD e monitorizar a conformidade do dispositivo.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 5/23/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: d43e95b2f236dc4c03bb3f63670b2b1400243531
ms.sourcegitcommit: 0303e3b8c510f56e191e6079e3dcdccfc841f530
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/16/2018
ms.locfileid: "40251850"
---
# <a name="enable-windows-defender-atp-with-conditional-access-in-intune"></a>Ativar o Windows Defender ATP com acesso condicional no Intune

A Proteção Avançada Contra Ameaças (ATP) do Windows Defender e o Microsoft Intune funcionam em conjunto para ajudar a evitar falhas de segurança e ajudar a limitar o impacto de violações dentro de uma organização.

Esta funcionalidade aplica-se a: dispositivos Windows 10

Por exemplo, alguém envia um anexo Word com código malicioso incorporado para um utilizador na sua organização. O utilizador abre o anexo e ativa o conteúdo. É iniciado um ataque de privilégios elevados e o atacante tem direitos de administrador no dispositivo da vítima a partir de um computador remoto. O atacante, em seguida, acede remotamente aos outros dispositivos do utilizador.

Esta falha de segurança pode afetar toda a organização.

O Windows Defender ATP pode resolver eventos de segurança como neste cenário. O Centro de Segurança do Windows Defender (consola ATP) avalia os dispositivos como sendo de “alto risco” e inclui um relatório detalhado da atividade suspeita. No nosso exemplo, o Windows Defender ATP deteta que o dispositivo executou código anormal, teve um escalamento de privilégios de processo, injetou código malicioso e emitiu uma shell remota suspeita. O Windows Defender ATP, em seguida, disponibiliza-lhe opções para mitigar a ameaça.

Com o Intune, pode criar uma política de conformidade que determina um nível de risco aceitável. Se um dispositivo exceder este risco, o dispositivo ficará não conforme. Quando combinado com o Acesso Condicional do Azure Active Directory (AD), o utilizador terá o acesso bloqueado aos recursos da empresa.

Este artigo mostra-lhe como:

- Ativar o Intune no ATP e ativar o ATP no Intune. Estas tarefas criam uma ligação de serviços entre o Intune e o Windows Defender ATP. Esta ligação permite que o Windows Defender ATP escreva o risco do computador para os seus dispositivos do Intune.
- Criar a política de conformidade no Intune.
- Ativar o acesso condicional no Azure Active Directory (AD) em dispositivos com base no seu nível de ameaça.

## <a name="prerequisites"></a>Pré-requisitos

Para utilizar o ATP com o Intune, confirme se tem o seguinte configurado e pronto a utilizar:

- Um inquilino com licença para o Enterprise Mobility + Security E3 e o Windows E5 (ou Microsoft 365 Enterprise E5)
- O ambiente do Microsoft Intune, com dispositivos Windows 10 [geridos pelo Intune](windows-enroll.md) que também estão associados ao Azure AD
- [Windows Defender ATP](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/windows-defender-advanced-threat-protection) e acesso ao Centro de Segurança do Windows Defender (portal ATP)

## <a name="enable-windows-defender-atp-in-intune"></a>Ativar o Windows Defender ATP no Intune

1. Inicie sessão no [portal do Azure](https://portal.azure.com).
2. Selecione **Todos os serviços**, filtre por **Intune** e selecione **Microsoft Intune**.
3. Selecione **Conformidade do dispositivo** > **Windows Defender ATP** > **Abrir o Centro de Segurança do Windows Defender**.

    ![Selecione para abrir o Centro de Segurança do Windows Defender](./media/atp-device-compliance-open-windows-defender.png)

4. No **Centro de Segurança do Windows Defender**:
    1. Selecione **Definições** > **Funcionalidades avançadas**.
    2. Em **Ligação do Microsoft Intune**, escolha **Ligado**:

        ![Ativar a ligação ao Intune](./media/atp-security-center-intune-toggle.png)

    3. Selecione **Guardar preferências**.

5. Volte ao Intune, **Conformidade do dispositivo** > **Windows Defender ATP**. Defina a opção **Ligar dispositivos Windows com versão 10.0.15063 e posterior a Windows Defender ATP** para **Ativado**.
6. Selecione **Guardar**.

Normalmente, executa esta tarefa uma vez. Por isso, se o ATP já estiver ativado no seu recurso do Intune, não terá de o fazer novamente.

## <a name="onboard-devices-using-a-configuration-profile"></a>Carregar dispositivos através de um perfil de configuração

O Windows Defender inclui um pacote de configuração carregado instalado nos dispositivos. Quando instalado, o pacote comunica com os [serviços do Windows Defender ATP](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/windows-defender-advanced-threat-protection) para analisar ficheiros, detetar ameaças e comunicar o risco ao Windows Defender ATP. Com o Intune, pode criar um perfil de configuração que utiliza este pacote de configuração. Em seguida, atribua este perfil aos dispositivos que carregar pela primeira vez.

Depois de carregar um dispositivo através do pacote de configuração, não precisará de o fazer novamente. Normalmente, é uma tarefa de execução única.

Também pode carregar dispositivos através de uma [política de grupo ou o System Center Configuration Manager (SCCM)](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/configure-endpoints-windows-defender-advanced-threat-protection).

Os passos seguintes mostram como carregar com o Intune.

#### <a name="download-configuration-package"></a>Transferir pacote de configuração

1. No [Centro de Segurança do Windows Defender](https://securitycenter.windows.com), selecione **Definições** > **Inclusão**.
2. Introduza as seguintes definições:
  - **Sistema operativo**: Windows 10
  - **Carregar um computador** > **Método de implementação**: Gestão de Dispositivos Móveis/Microsoft Intune
3. Selecione **Transferir pacote** e guarde o ficheiro **WindowsDefenderATPOnboardingPackage.zip**. Extraia o ficheiro.

Este ficheiro zip inclui **WindowsDefenderATP.onboarding**, que será necessário nos passos seguintes.

#### <a name="create-the-atp-configuration-profile"></a>Criar um perfil de configuração do ATP

Este perfil utiliza o pacote de inclusão que transferiu nos passos anteriores.

1. No [portal do Azure](https://portal.azure.com), selecione **Todos os serviços**, filtre o **Intune** e selecione **Microsoft Intune**.
2. Selecione **Configuração do Dispositivo** > **Perfis** > **Criar perfil**.
3. Introduza um **Nome** e uma **Descrição**.
4. Em **Plataforma**, selecione **Windows 10 e versões posteriores**
5. Em **Tipo de perfil**, selecione **Windows Defender ATP (Windows 10 Desktop)**.
6. Configure as definições:

  - **Carregar o Pacote de Configuração**: procure e selecione o ficheiro **WindowsDefenderATP.onboarding** que transferiu. Este ficheiro ativa uma definição para que os dispositivos possam comunicar com o serviço Windows Defender ATP.
  - **Partilha de amostras para todos os ficheiros**: permite que as amostras sejam recolhidas e partilhadas com o Windows Defender ATP. Por exemplo, se vir um ficheiro suspeito, poderá submetê-lo para o Windows Defender ATP para uma análise detalhada.
  - **Acelerar a frequência do relatório de telemetria**: para dispositivos que estão em risco elevado, ative esta definição para que estes comuniquem a telemetria para o serviço do Windows Defender ATP com mais frequência.
  - **Pacote de Configuração de Exclusão**: se quiser remover ou proceder à “descarga” da monitorização do Windows Defender ATP, poderá transferir um Pacote de descarga no [Centro de Segurança do Windows Defender](https://securitycenter.windows.com) e adicioná-lo. Caso contrário, ignore esta propriedade.

    O artigo [Onboard Windows 10 machines using System Center Configuration Manager](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/configure-endpoints-sccm-windows-defender-advanced-threat-protection) (Carregar computadores com o Windows 10 através do System Center Configuration Manager) inclui mais detalhes sobre estas definições do Windows Defender ATP.

7. Selecione **OK** e **Criar** para guardar as alterações. O perfil será criado.

## <a name="create-the-compliance-policy"></a>Criar a política de conformidade
A política de conformidade determina um nível de risco aceitável num dispositivo.

1. No [portal do Azure](https://portal.azure.com), selecione **Todos os serviços**, filtre o **Intune** e selecione **Microsoft Intune**.
2. Selecione **Conformidade do dispositivo** > **Políticas** > **Criar política**.
3. Introduza um **Nome** e uma **Descrição**.
4. Em **Plataforma**, selecione **Windows 10 e posterior**.
5. Nas definições do **Windows Defender ATP**, defina a opção **Exigir que o dispositivo esteja na classificação de risco de máquina ou inferior** para o seu nível favorito:

  - **Seguro**: este é o nível mais seguro. O dispositivo não poderá aceder aos recursos da empresa se contiver ameaças. Se forem detetadas ameaças, o dispositivo será avaliado como não conforme.
  - **Baixo**: o dispositivo estará em conformidade se só existirem ameaças de nível baixo. Os dispositivos com níveis de ameaça média ou alta não estão conformes.
  - **Médio**: o dispositivo estará conforme se as ameaças encontradas no dispositivo forem de nível baixo ou médio. Se forem detetadas ameaças de nível alto, o estado do dispositivo será determinado como não conforme.
  - **Elevado**: este nível é o menos seguro e permite todos os níveis de ameaça. Como tal, os dispositivos com níveis de ameaça altos, médios ou baixos são considerados conformes.

6. Selecione **OK** e **Criar** para guardar as alterações (e criar o perfil).

## <a name="assign-the-policy"></a>Atribuir a política

1. No [portal do Azure](https://portal.azure.com), selecione **Todos os serviços**, filtre o **Intune** e selecione **Microsoft Intune**.
2. Selecione **Conformidade do dispositivo** > **Políticas**> selecione a política de conformidade do Windows Defender ATP.
3. Selecione **Atribuições**.
4. Inclua ou exclua os grupos do Azure AD para lhes atribuir a política.
5. Para implementar a política aos grupos, selecione **Guardar**. Os dispositivos dos utilizadores visados pela política são avaliados quanto à conformidade.

## <a name="create-an-azure-ad-conditional-access-policy"></a>Criar uma política de acesso condicional do Azure AD
A política de acesso condicional bloqueará o acesso a recursos *se* o dispositivo não estiver conforme. Por isso, se um dispositivo exceder o nível de ameaça, poderá bloquear o acesso aos recursos empresariais, tais como o SharePoint ou o Exchange Online.

1. No [portal do Azure](https://portal.azure.com), abra o **Azure Active Directory** > **Acesso condicional** > **Nova política**.
2. Introduza um **Nome** para a política e selecione **Utilizadores e grupos**. Utilize as opções Incluir ou Excluir para adicionar os grupos à política e selecione **Concluído**.
3. Selecione **Aplicações na cloud** e escolha as aplicações que quer proteger. Por exemplo, escolha **Selecionar aplicações** e selecione **Office 365 SharePoint Online** e **Office 365 Exchange Online**.

    Selecione **Concluído** para guardar as alterações.

4. Selecione **Condições** > **Aplicações do cliente** para aplicar a política a aplicações e browsers. Por exemplo, selecione **Sim** e, em seguida, ative **Browser** e **Aplicações móveis e clientes de ambiente de trabalho**.

    Selecione **Concluído** para guardar as alterações.

5. Selecione **Conceder** para aplicar o acesso condicional baseado na conformidade do dispositivo. Por exemplo, selecione **Conceder acesso** > **Pedir que o dispositivo seja marcado como conforme**.

    Escolha **Selecionar** para guardar as alterações.

6. Selecione **Ativar política** e, em seguida, **Criar** para guardar as alterações.

[O que é o acesso condicional?](conditional-access.md) é um bom recurso.

## <a name="monitor-device-compliance"></a>Monitorizar a conformidade do dispositivo
Em seguida, monitorize o estado dos dispositivos que tenham a política de conformidade do Windows Defender ATP.

1. No [portal do Azure](https://portal.azure.com), selecione **Todos os serviços**, filtre o **Intune** e selecione **Microsoft Intune**.
2. Selecione **Conformidade do dispositivo** > **Conformidade com a política**.
3. Encontre a sua política do Windows Defender ATP na lista e veja que dispositivos estão conformes ou não conformes.

## <a name="more-good-stuff"></a>Mais artigos interessantes
[Windows Defender ATP conditional access](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/conditional-access-windows-defender-advanced-threat-protection) (Acesso condicional do Windows Defender ATP)  
[Windows Defender ATP risk dashboard](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/dashboard-windows-defender-advanced-threat-protection) (Dashboard de risco do Windows Defender ATP)  
[Introdução às políticas de conformidade de dispositivos](device-compliance-get-started.md)  
[Acesso condicional no Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)

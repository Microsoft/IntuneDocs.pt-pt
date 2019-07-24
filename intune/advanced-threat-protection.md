---
title: Usar o Microsoft defender ATP no Microsoft Intune – Azure | Microsoft Docs
description: Veja como habilitar o Microsoft defender ATP (proteção avançada contra ameaças) em um cenário de ponta a ponta, incluindo a ativação do Microsoft defender ATP no Intune e na central de segurança do Microsoft defender, dispositivos integrados usando um Microsoft defender ATP Perfil de configuração, criar uma política de conformidade do dispositivo do Intune, criar uma política de acesso condicional do Azure AD e monitorar a conformidade do dispositivo.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 07/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: af27a9b07434346a5425d0539759cb90ebf1ee6f
ms.sourcegitcommit: 614c4c36cfe544569db998e17e29feeaefbb7a2e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/24/2019
ms.locfileid: "68427093"
---
# <a name="enforce-compliance-for-microsoft-defender-atp-with-conditional-access-in-intune"></a>Impor a conformidade para o Microsoft defender ATP com acesso condicional no Intune  

A proteção avançada contra ameaças do Microsoft defender (Microsoft defender ATP) e o Microsoft Intune trabalham em conjunto para ajudar a evitar violações de segurança e ajudar a limitar o impacto de violações em uma organização.

Esta funcionalidade aplica-se a: Dispositivos com o Windows 10

Por exemplo, alguém envia um anexo Word com código malicioso incorporado para um utilizador na sua organização. O utilizador abre o anexo e ativa o conteúdo. É iniciado um ataque de privilégios elevados e o atacante tem direitos de administrador no dispositivo da vítima a partir de um computador remoto. O atacante, em seguida, acede remotamente aos outros dispositivos do utilizador.

Esta falha de segurança pode afetar toda a organização.

O Microsoft defender ATP pode resolver eventos de segurança como esse cenário. A central de segurança do Microsoft defender relata os dispositivos como "alto risco" e inclui um relatório detalhado de atividades suspeitas. Em nosso exemplo, o Microsoft defender ATP detecta que o dispositivo executou código anormal, experimentou um escalonamento de privilégios de processo, código mal-intencionado injetado e emitiu um shell remoto suspeito. Em seguida, o Microsoft defender ATP oferece opções para mitigar a ameaça.

Com o Intune, pode criar uma política de conformidade que determina um nível de risco aceitável. Se um dispositivo exceder este risco, o dispositivo ficará não conforme. Quando combinado com o Acesso Condicional do Azure Active Directory (AD), o utilizador terá o acesso bloqueado aos recursos da empresa.

Este artigo mostra-lhe como:

- Habilite o Intune na central de segurança do Microsoft defender e habilite o Microsoft defender ATP no Intune. Essas tarefas criam uma conexão entre serviços entre o Intune e o Microsoft defender ATP. Essa conexão permite que o Microsoft defender ATP grave o risco da máquina para seus dispositivos do Intune.
- Criar a política de conformidade no Intune.
- Habilite o acesso condicional no Azure Active Directory (AD) em dispositivos com base em seu nível de ameaça.

## <a name="prerequisites"></a>Pré-requisitos

Para usar o Microsoft defender ATP com o Intune, verifique se você tem os seguintes configurados e pronto para usar:

- Um inquilino com licença para o Enterprise Mobility + Security E3 e o Windows E5 (ou Microsoft 365 Enterprise E5)
- O ambiente do Microsoft Intune, com dispositivos Windows 10 [geridos pelo Intune](windows-enroll.md) que também estão associados ao Azure AD
- [Microsoft defender ATP](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection) e acesso à central de segurança do Microsoft defender (Portal ATP)

## <a name="enable-microsoft-defender-atp-in-intune"></a>Habilitar o Microsoft defender ATP no Intune

Quando você integra um novo aplicativo à defesa contra ameaças móveis do Intune e habilita a conexão, o Intune cria uma política de acesso condicional clássica em Azure Active Directory. Cada aplicativo MTD que você integra, como o [defender ATP](advanced-threat-protection.md) ou qualquer um de nossos [parceiros MTD](mobile-threat-defense.md#mobile-threat-defense-partners)adicionais, cria uma nova política de acesso condicional clássico.  Essas políticas podem ser ignoradas, mas não devem ser editadas, excluídas ou desabilitadas.

Políticas de acesso condicional clássico para aplicativos MTD: 

- São usados pelo Intune MTD para exigir que os dispositivos sejam registrados no Azure AD para que tenham uma ID de dispositivo. A ID é necessária para que os dispositivos e possam relatar com êxito seu status ao Intune.  
- São diferentes das políticas de acesso condicional que você pode criar para ajudar a gerenciar o MTD.
- Por padrão, não interaja com outras políticas de acesso condicional usadas para avaliação.  

Para exibir políticas de acesso condicional clássico, no [Azure](https://portal.azure.com/#home), acesse **Azure Active Directory** > **políticas clássicas**de**acesso** > condicional.

### <a name="to-enable-defender-atp"></a>Para habilitar o defender ATP
1. Entre no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Selecione **conformidade** > do dispositivo**Microsoft defender ATP**e, depois, *configurações do conector*, selecione **abrir a central de segurança do Microsoft defender**.

    ![Selecione para abrir a central de segurança do Microsoft defender](./media/advanced-threat-protection/atp-device-compliance-open-microsoft-defender.png)

4. Na **central de segurança do Microsoft defender**:
    1. Selecione **Definições** > **Funcionalidades avançadas**.
    2. Em **Ligação do Microsoft Intune**, escolha **Ligado**:

        ![Ativar a ligação ao Intune](./media/advanced-threat-protection/atp-security-center-intune-toggle.png)

    3. Selecione **Guardar preferências**.

4. Volte para o Intune, **conformidade** > **do dispositivo Microsoft defender ATP**. Defina **conectar dispositivos Windows versão 10.0.15063 e superior ao Microsoft defender ATP** como **ativado**.
5. Selecione **Guardar**.

Normalmente, executa esta tarefa uma vez. Portanto, se o Microsoft defender ATP já estiver habilitado em seu recurso do Intune, você não precisará fazê-lo novamente.

## <a name="onboard-devices-using-a-configuration-profile"></a>Carregar dispositivos através de um perfil de configuração

Quando um utilizador final se inscreve no Intune, pode emitir definições diferentes para o dispositivo através de um perfil de configuração. Isso também se aplica ao Microsoft defender ATP.

O Microsoft defender ATP inclui um pacote de configuração de integração que se comunica com os [Serviços do Microsoft defender ATP](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection) para verificar arquivos, detectar ameaças e relatar o risco para o Microsoft defender ATP.

Quando você carregar, o Intune Obtém um pacote de configuração gerado automaticamente do Microsoft defender ATP. O Intune envia por push o pacote de configuração para o dispositivo quando ele envia o perfil de configuração para o dispositivo, o que permite que o Microsoft defender ATP monitore o dispositivo para as ameaças.

Depois de carregar um dispositivo através do pacote de configuração, não precisará de o fazer novamente. Também pode carregar dispositivos através de uma [política de grupo ou o System Center Configuration Manager (SCCM)](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/configure-endpoints).

### <a name="create-the-configuration-profile"></a>Criar um perfil de configuração

1. Entre no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Selecione **Configuração do Dispositivo** > **Perfis** > **Criar perfil**.
3. Introduza um **Nome** e uma **Descrição**.
4. Em **Plataforma**, selecione **Windows 10 e versões posteriores**
5. Para **tipo de perfil**, selecione **Microsoft defender ATP (Windows 10 Desktop)** .
6. Configure as definições:

    - **Tipo de pacote de configuração de cliente do Microsoft defender ATP**: Selecione **carregar** para adicionar o pacote de configuração ao perfil. Selecione **Descarregar** para remover o pacote de configuração do perfil.
  
    > [!NOTE]  
    > Se você estabeleceu corretamente uma conexão com o Microsoft defender ATP, o Intune  integrará automaticamente o perfil de configuração para você e a configuração do **tipo de pacote de configuração do cliente Microsoft defender ATP** não estará disponível.
  
    - **Compartilhamento de amostra para todos os arquivos**: **Habilitar** permite que os exemplos sejam coletados e compartilhados com o Microsoft defender ATP. Por exemplo, se você vir um arquivo suspeito, poderá enviá-lo para o Microsoft defender ATP para análise profunda. **Não configurado** não compartilha amostras para o Microsoft defender ATP.
    - **Acelere a frequência de relatórios**de telemetria: Para dispositivos que estão em alto risco, **habilite** essa configuração para que ela relate a telemetria ao serviço Microsoft defender ATP com mais frequência.

    [Carregar computadores Windows 10 usando System Center Configuration Manager](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/configure-endpoints-sccm) tem mais detalhes sobre essas configurações do Microsoft defender ATP.

7. Selecione **OK** e **Criar** para guardar as alterações. O perfil será criado.

## <a name="create-the-compliance-policy"></a>Criar a política de conformidade
A política de conformidade determina um nível de risco aceitável num dispositivo.

1. Entre no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Selecione **Conformidade do dispositivo** > **Políticas** > **Criar política**.
3. Introduza um **Nome** e uma **Descrição**.
4. Em **Plataforma**, selecione **Windows 10 e posterior**.
5. Nas configurações do **Microsoft defender ATP** , defina **exigir que o dispositivo esteja em ou sob a pontuação de risco do computador** para seu nível preferido. As classificações de nível [de ameaça são determinadas pelo Microsoft defender ATP](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/alerts-queue).

   - **Limpar**: Esse nível é o mais seguro. O dispositivo não pode ter nenhuma ameaça existente e ainda acessar os recursos da empresa. Se forem detetadas ameaças, o dispositivo será avaliado como não conforme. (Os usuários do Microsoft defender ATP têm o valor *seguro*.)
   - **Baixo**: O dispositivo será compatível se houver apenas ameaças de nível baixo. Dispositivos com níveis de ameaça médio ou alto não são compatíveis.
   - **Médio**: O dispositivo estará em conformidade se as ameaças encontradas no dispositivo forem baixas ou médias. Se forem detetadas ameaças de nível alto, o estado do dispositivo será determinado como não conforme.
   - **Alto**: Esse nível é o menos seguro e permite todos os níveis de ameaça. Portanto, os dispositivos com níveis de ameaça altos, médios ou baixos são considerados compatíveis.

6. Selecione **OK** e **Criar** para guardar as alterações (e criar o perfil).

## <a name="assign-the-policy"></a>Atribuir a política

1. Entre no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Selecione**políticas**de **conformidade** > do dispositivo > selecione sua política de conformidade do Microsoft defender ATP.
3. Selecione **Atribuições**.
4. Inclua ou exclua os grupos do Azure AD para lhes atribuir a política.
5. Para implementar a política aos grupos, selecione **Guardar**. Os dispositivos dos utilizadores visados pela política são avaliados quanto à conformidade.

## <a name="create-a-conditional-access-policy"></a>Criar uma política de acesso condicional
A política de acesso condicional bloqueará o acesso aos recursos *se* o dispositivo não for compatível. Por isso, se um dispositivo exceder o nível de ameaça, poderá bloquear o acesso aos recursos empresariais, tais como o SharePoint ou o Exchange Online.  

> [!TIP]  
> O Acesso Condicional é uma tecnologia do Azure Active Directory (Azure AD). O nó de Acesso Condicional acedido a partir do *Intune* é o mesmo nó acedido a partir do *Azure AD*.  

1. Entre no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) e selecione **acesso** > condicional**nova política**.
2. Introduza um **Nome** para a política e selecione **Utilizadores e grupos**. Utilize as opções Incluir ou Excluir para adicionar os grupos à política e selecione **Concluído**.
3. Selecione **Aplicações na cloud** e escolha as aplicações que quer proteger. Por exemplo, escolha **Selecionar aplicações** e selecione **Office 365 SharePoint Online** e **Office 365 Exchange Online**.

    Selecione **Concluído** para guardar as alterações.

4. Selecione **Condições** > **Aplicações do cliente** para aplicar a política a aplicações e browsers. Por exemplo, selecione **Sim** e, em seguida, ative **Browser** e **Aplicações móveis e clientes de ambiente de trabalho**.

    Selecione **Concluído** para guardar as alterações.

5. Selecione **conceder** para aplicar o acesso condicional com base na conformidade do dispositivo. Por exemplo, selecione **Conceder acesso** > **Pedir que o dispositivo seja marcado como conforme**.

    Escolha **Selecionar** para guardar as alterações.

6. Selecione **Ativar política** e, em seguida, **Criar** para guardar as alterações.

[O que é o acesso condicional?](conditional-access.md) é um bom recurso.

## <a name="monitor-device-compliance"></a>Monitorizar a conformidade do dispositivo
Em seguida, monitore o estado dos dispositivos que têm a política de conformidade do Microsoft defender ATP.

1. Entre no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Selecione **Conformidade do dispositivo** > **Conformidade com a política**.
3. Localize sua política do Microsoft defender ATP na lista e veja quais dispositivos estão em conformidade ou em não conformidade.

## <a name="more-good-stuff"></a>Mais artigos interessantes
[Acesso condicional do Microsoft defender ATP](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/conditional-access)  
[Painel de riscos do Microsoft defender ATP](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/security-operations-dashboard)  

[Introdução às políticas de conformidade de dispositivos](device-compliance-get-started.md)  
[Acesso condicional no Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)
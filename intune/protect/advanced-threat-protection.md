---
title: Usar o Microsoft defender ATP no Microsoft Intune – Azure | Microsoft Docs
description: Use a proteção avançada contra ameaças do Microsoft defender (Microsoft defender ATP) com o Intune, incluindo instalação e configuração, integração de seus dispositivos Intune com ATP e, em seguida, use uma avaliação de risco ATP de dispositivos com a conformidade do dispositivo do Intune e condicional políticas de acesso para proteger os recursos de rede.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 09/06/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: shpate
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: d5234a8568911de075b1c8ee5d679ae40c6c494a
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/16/2019
ms.locfileid: "72502626"
---
# <a name="enforce-compliance-for-microsoft-defender-atp-with-conditional-access-in-intune"></a>Impor a conformidade para o Microsoft defender ATP com acesso condicional no Intune  

Você pode integrar a proteção avançada contra ameaças do Microsoft defender (Microsoft defender ATP) com o Microsoft Intune como uma solução de defesa contra ameaças móveis, para ajudar a evitar violações de segurança e limitar o impacto de violações em uma organização. O Microsoft defender ATP funciona com dispositivos que executam o Windows 10 ou posterior.

Para ter êxito, use as seguintes configurações em conjunto:
- **Estabeleça uma conexão entre serviços entre o Intune e o Microsoft defender ATP**. Essa conexão permite que o Microsoft defender ATP colete dados sobre o risco da máquina de dispositivos Windows 10 gerenciados com o Intune.  
- **Use um perfil de configuração de dispositivo para carregar dispositivos com o Microsoft defender ATP**. Você integra dispositivos para configurá-los para se comunicar com o Microsoft defender ATP e fornecer dados que ajudem a avaliar seu nível de risco.  
 - **Use uma política de conformidade do dispositivo para definir o nível de risco que você deseja permitir**. Os níveis de risco são relatados pelo Microsoft defender ATP.  Os dispositivos que excedem o nível de risco permitido são identificados como sem conformidade.  
- **Use uma política de acesso condicional** para impedir que os usuários acessem recursos corporativos de dispositivos que não são compatíveis.  

Além disso, ao integrar o Intune com o Microsoft defender ATP, você pode aproveitar o ATPs Threat (gerenciamento de vulnerabilidades & TVM) e [usar o Intune para corrigir a fraqueza do ponto de extremidade identificada pelo TVM](atp-manage-vulnerabilities.md).

## <a name="example-of-using-microsoft-defender-atp-with-intune"></a>Exemplo de uso do Microsoft defender ATP com o Intune  

O exemplo a seguir ajuda a explicar como essas soluções funcionam em conjunto para ajudar a proteger sua organização. Para este exemplo, o Microsoft defender ATP e o Intune já estão integrados.  

Considere um evento em que alguém envia um anexo de palavra com código mal-intencionado incorporado a um usuário em sua organização.  
- O utilizador abre o anexo e ativa o conteúdo.  
- É iniciado um ataque de privilégios elevados e o atacante tem direitos de administrador no dispositivo da vítima a partir de um computador remoto.  
- O atacante, em seguida, acede remotamente aos outros dispositivos do utilizador. Esta falha de segurança pode afetar toda a organização.  

O Microsoft defender ATP pode ajudar a resolver eventos de segurança como esse cenário.  
- Em nosso exemplo, o Microsoft defender ATP detecta que o dispositivo executou código anormal, experimentou um escalonamento de privilégios de processo, código mal-intencionado injetado e emitiu um shell remoto suspeito.  
- Com base nessas ações do dispositivo, o Microsoft defender ATP [classifica o dispositivo como de alto risco](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/alerts-queue#severity) e inclui um relatório detalhado de atividades suspeitas no portal da central de segurança do Microsoft defender.  

Como você tem uma política de conformidade do dispositivo do Intune para classificar dispositivos com um nível *médio* ou *alto* de risco como sem conformidade, o dispositivo comprometido é classificado como não compatível. Essa classificação permite que a política de acesso condicional inicie e bloqueie o acesso desse dispositivo aos recursos corporativos.  

## <a name="prerequisites"></a>Pré-requisitos

Para usar o Microsoft defender ATP com o Intune, verifique se você tem os seguintes configurados e pronto para uso:

- Um inquilino com licença para o Enterprise Mobility + Security E3 e o Windows E5 (ou Microsoft 365 Enterprise E5)
- O ambiente do Microsoft Intune, com dispositivos Windows 10 [geridos pelo Intune](../enrollment/windows-enroll.md) que também estão associados ao Azure AD
- [Microsoft defender ATP](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection) e acesso à central de segurança do Microsoft defender (Portal ATP)

## <a name="enable-microsoft-defender-atp-in-intune"></a>Habilitar o Microsoft defender ATP no Intune

A primeira etapa é configurar a conexão serviço a serviço entre o Intune e o Microsoft defender ATP. Isso requer acesso administrativo à central de segurança do Microsoft defender e ao Intune.  

### <a name="to-enable-defender-atp"></a>Para habilitar o defender ATP  

1. Entre no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Selecione **conformidade do dispositivo**@no__t-**1 Microsoft defender ATP**e, depois, *configurações do conector*, selecione **abrir a central de segurança do Microsoft defender**.

    ![Selecione para abrir a central de segurança do Microsoft defender](./media/advanced-threat-protection/atp-device-compliance-open-microsoft-defender.png)

4. Na **central de segurança do Microsoft defender**:
    1. Selecione **Definições** > **Funcionalidades avançadas**.
    2. Em **Ligação do Microsoft Intune**, escolha **Ligado**:

        ![Ativar a ligação ao Intune](./media/advanced-threat-protection/atp-security-center-intune-toggle.png)

    3. Selecione **Guardar preferências**.

4. Volte para o Intune, **conformidade do dispositivo** > **Microsoft defender ATP**. Defina **conectar dispositivos Windows versão 10.0.15063 e superior ao Microsoft defender ATP** como **ativado**.
5. Selecione **Guardar**.

Normalmente, executa esta tarefa uma vez. Depois de habilitar o Microsoft defender ATP para seu locatário do Intune, você não precisará fazê-lo novamente.

> [!TIP]  
> Quando você integra um novo aplicativo à defesa contra ameaças móveis do Intune e habilita a conexão com o Intune, o Intune cria uma política de acesso condicional clássica em Azure Active Directory. Cada aplicativo MTD que você integra, incluindo o [defender ATP](advanced-threat-protection.md) ou qualquer um de nossos [parceiros MTD](mobile-threat-defense.md#mobile-threat-defense-partners)adicionais, cria uma nova política de acesso condicional clássico. Essas políticas podem ser ignoradas, mas não devem ser editadas, excluídas ou desabilitadas.
> 
> Políticas de acesso condicional clássico para aplicativos MTD: 
> 
> - São usados pelo Intune MTD para exigir que os dispositivos sejam registrados no Azure AD para que tenham uma ID de dispositivo antes de se comunicarem com os parceiros do MTD. A ID é necessária para que os dispositivos e possam relatar com êxito seu status ao Intune.  
> - Não têm nenhum efeito sobre outros aplicativos ou recursos de nuvem.  
> - São diferentes das políticas de acesso condicional que você pode criar para ajudar a gerenciar o MTD.
> - Por padrão, não interaja com outras políticas de acesso condicional usadas para avaliação.  
> 
> Para exibir políticas de acesso condicional clássico, no [Azure](https://portal.azure.com/#home), acesse **Azure Active Directory** > **políticas clássicas**de**acesso** > .

## <a name="onboard-devices-by-using-a-configuration-profile"></a>Carregar dispositivos usando um perfil de configuração

Depois de estabelecer a conexão de serviço a serviço entre o Intune e o Microsoft defender ATP, você integra seus dispositivos gerenciados do Intune ao ATP para que os dados sobre seu nível de risco possam ser coletados e usados. Para integrar dispositivos, use um perfil de configuração de dispositivo para o Microsoft defender ATP.  

Quando você estabeleceu a conexão com o Microsoft defender ATP, o Intune recebeu um pacote de configuração de integração do Microsoft defender ATP do Microsoft defender ATP. Este pacote é implantado em dispositivos com o perfil de configuração do dispositivo. O pacote de configuração configura os dispositivos para se comunicar com os [Serviços do Microsoft defender ATP](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection) para verificar arquivos, detectar ameaças e relatar o risco para o Microsoft defender ATP.  

Depois de carregar um dispositivo usando o pacote de configuração, você não precisará fazê-lo novamente. Também pode carregar dispositivos através de uma [política de grupo ou o System Center Configuration Manager (SCCM)](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/configure-endpoints).


### <a name="create-the-device-configuration-profile"></a>Criar o perfil de configuração do dispositivo

1. Entre no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Selecione **Configuração do Dispositivo** > **Perfis** > **Criar perfil**.
3. Introduza um **Nome** e uma **Descrição**.
4. Em **Plataforma**, selecione **Windows 10 e versões posteriores**
5. Para **tipo de perfil**, selecione **Microsoft defender ATP (Windows 10 Desktop)** .
6. Configure as definições:

   - **Tipo de pacote de configuração de cliente do Microsoft defender ATP**: selecione **carregar** para adicionar o pacote de configuração ao perfil. Selecione **Descarregar** para remover o pacote de configuração do perfil.
  
     > [!NOTE]  
     > Se você estabeleceu corretamente uma conexão com o Microsoft defender ATP, o Intune **integrará automaticamente o perfil de configuração** para você e a configuração do **tipo de pacote de configuração do cliente Microsoft defender ATP** não estará disponível.
  
    - **Compartilhamento de amostra para todos os arquivos**: **habilitar** permite que amostras sejam coletadas e compartilhadas com o Microsoft defender ATP. Por exemplo, se você vir um arquivo suspeito, poderá enviá-lo para o Microsoft defender ATP para análise profunda. **Não configurado** não compartilha amostras para o Microsoft defender ATP.
    - **Acelerar a frequência de relatórios de telemetria**: para dispositivos que estão em alto risco, **habilite** essa configuração para que ela relate a telemetria ao serviço Microsoft defender ATP com mais frequência.

    [Carregar computadores Windows 10 usando System Center Configuration Manager](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/configure-endpoints-sccm) tem mais detalhes sobre essas configurações do Microsoft defender ATP.

7. Selecione **OK** e **Criar** para guardar as alterações. O perfil será criado.
8. [Atribua o perfil de configuração do dispositivo](../configuration/device-profile-assign.md) aos dispositivos que você deseja avaliar com o Microsoft defender ATP.  


## <a name="create-and-assign-the-compliance-policy"></a>Criar e atribuir a política de conformidade  

A política de conformidade determina o nível de risco que você considera aceitável para um dispositivo.

### <a name="create-the-compliance-policy"></a>Criar a política de conformidade  

1. Entre no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Selecione **Conformidade do dispositivo** > **Políticas** > **Criar política**.
3. Introduza um **Nome** e uma **Descrição**.
4. Em **Plataforma**, selecione **Windows 10 e posterior**.
5. Em **configurações**, selecione **Microsoft defender ATP**.
6. Defina **exigir que o dispositivo esteja em ou sob a pontuação de risco do computador** para seu nível preferido. 
   
   As classificações de nível [de ameaça são determinadas pelo Microsoft defender ATP](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/alerts-queue).

   - **Seguro**: este é o nível mais seguro. O dispositivo não pode ter nenhuma ameaça existente e ainda acessar os recursos da empresa. Se forem detetadas ameaças, o dispositivo será avaliado como não conforme. (Os usuários do Microsoft defender ATP têm o valor *seguro*.)
   - **Baixo**: o dispositivo estará em conformidade se só existirem ameaças de nível baixo. Dispositivos com níveis de ameaça médio ou alto não são compatíveis.
   - **Médio**: o dispositivo estará conforme se as ameaças encontradas no dispositivo forem de nível baixo ou médio. Se forem detetadas ameaças de nível alto, o estado do dispositivo será determinado como não conforme.
   - **Alto**: esse nível é o menos seguro e permite todos os níveis de ameaça. Portanto, os dispositivos com níveis de ameaça altos, médios ou baixos são considerados compatíveis.

6. Selecione **OK** e **Criar** para guardar as alterações (e criar o perfil).  
7. [Atribua a política de conformidade do dispositivo](create-compliance-policy.md#assign-the-policy) aos grupos aplicáveis.



## <a name="create-a-conditional-access-policy"></a>Criar uma política de acesso condicional  

A política de acesso condicional bloqueia o acesso a recursos para dispositivos que excedem o nível de ameaça que você definiu em sua política de conformidade. Você pode bloquear o acesso do dispositivo a recursos corporativos, como o SharePoint ou o Exchange Online.  

> [!TIP]  
> O Acesso Condicional é uma tecnologia do Azure Active Directory (Azure AD). O nó de Acesso Condicional acedido a partir do *Intune* é o mesmo nó acedido a partir do *Azure AD*.  

1. Entre no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) e selecione **acesso condicional** > **nova política**.
2. Introduza um **Nome** para a política e selecione **Utilizadores e grupos**. Utilize as opções Incluir ou Excluir para adicionar os grupos à política e selecione **Concluído**.
3. Selecione **Aplicações na cloud** e escolha as aplicações que quer proteger. Por exemplo, escolha **Selecionar aplicações** e selecione **Office 365 SharePoint Online** e **Office 365 Exchange Online**.

    Selecione **Concluído** para guardar as alterações.

4. Selecione **Condições** > **Aplicações do cliente** para aplicar a política a aplicações e browsers. Por exemplo, selecione **Sim** e, em seguida, ative **Browser** e **Aplicações móveis e clientes de ambiente de trabalho**.

    Selecione **Concluído** para guardar as alterações.

5. Selecione **conceder** para aplicar o acesso condicional com base na conformidade do dispositivo. Por exemplo, selecione **Conceder acesso** > **Pedir que o dispositivo seja marcado como conforme**.

    Escolha **Selecionar** para guardar as alterações.

6. Selecione **Ativar política** e, em seguida, **Criar** para guardar as alterações.



## <a name="monitor-device-compliance"></a>Monitorizar a conformidade do dispositivo  

Em seguida, monitore o estado dos dispositivos que têm a política de conformidade do Microsoft defender ATP.

1. Entre no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Selecione **Conformidade do dispositivo** > **Conformidade com a política**.
3. Localize sua política do Microsoft defender ATP na lista e veja quais dispositivos estão em conformidade ou em não conformidade.

## <a name="view-onboarding-status"></a>Exibir status de integração
Para exibir o status de integração de todos os dispositivos Windows 10 gerenciados pelo Intune, você pode ir para a **conformidade do dispositivo** > **Microsoft defender ATP**. Nessa página, você também pode iniciar a criação de um perfil de configuração de dispositivo para integração de mais dispositivos ao Microsoft defender ATP.

## <a name="next-steps"></a>Próximos passos  

@No__t de [acesso condicional do Microsoft defender ATP](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/conditional-access)-1  
[Painel de riscos do Microsoft defender ATP](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/security-operations-dashboard)  
[Use tarefas de segurança com o gerenciamento de vulnerabilidades do ATPs para corrigir problemas em dispositivos](atp-manage-vulnerabilities.md).  
[Introdução às políticas de conformidade de dispositivos](device-compliance-get-started.md)  
 

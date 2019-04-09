---
title: No desenvolvimento – Microsoft Intune
titleSuffix: ''
description: Funcionalidades do Microsoft Intune em desenvolvimento
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/29/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 327019527ea3c374a3ebeb3c29703dbd744d18dc
ms.sourcegitcommit: 9daaeba9a960c50efcc951856234fbfec3635737
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/08/2019
ms.locfileid: "59231773"
---
# <a name="in-development-for-microsoft-intune---april-2019"></a>No desenvolvimento do Microsoft Intune – Abril de 2019

Para ajudar na preparação de sua e planejamento, esta página, listas de atualizações de interface do Usuário do Intune e recursos que estão em desenvolvimento, mas ainda não lançadas. Além disso:

- Se prevemos que precisará executar uma ação antes de uma alteração, vamos publicar uma mensagem complementar do Centro de mensagens do Office.
- Quando um recurso é iniciado na produção, como uma pré-visualização ou em disponibilidade geral, a descrição da funcionalidade irá mover esta página e para o [página Novidades](whats-new.md).
- Esta página e o [página Novidades](whats-new.md) são atualizados periodicamente. Volte a consultar posteriormente para obter mais atualizações.
- Consulte a [M365 Roteiro](https://www.microsoft.com/microsoft-365/roadmap?rtc=2&filters=EMS) para resultados estratégicos e as linhas do tempo.

> [!Note]
> Estes itens refletem as expectativas de atuais da Microsoft sobre as capacidades do Intune numa versão futura. Datas e funcionalidades individuais podem ser alteradas. Nem todos os itens no desenvolvimento de tem uma descrição da funcionalidade nesta página.

**RSS feed**: Seja notificado quando esta página é atualizada ao copiar e colar o URL seguinte no seu leitor de feeds: `https://docs.microsoft.com/api/search/rss?search=%22in+development+-+microsoft+intune%22&locale=en-us`

<!--
## What's coming to Intune in the Azure portal 
## What's coming to Intune apps
## Notices
-->
 
## <a name="intune-in-the-azure-portal"></a>Intune no portal do Azure

<!-- 1904 start-->

### <a name="set-login-settings-and-control-restart-options-on-macos-devices----1210083---"></a>Configurar definições de início de sessão e controlar as opções de reinício em dispositivos macOS <!-- 1210083 -->
Em dispositivos macOS, pode criar um perfil de configuração do dispositivo (**configuração do dispositivo** > **perfis** > **criar perfil** > escolher **macOS** para a plataforma > **funcionalidades do dispositivo** para tipo de perfil). Novas definições de janela de início de sessão será incluem itens como que mostra uma faixa personalizada, escolha como os utilizadores iniciarem sessão, mostram ou ocultar as definições de energia e muito mais.

Para ver as definições atuais, aceda à [definições de funcionalidade do dispositivo macOS](macos-device-features-settings.md).

Aplica-se a: macOS

### <a name="advanced-settings-for-windows-defender-firewall----1311949---"></a>Definições avançadas do Firewall do Windows Defender <!-- 1311949 -->
Em breve poderá utilizar o Intune para gerir as regras de firewall personalizadas nos clientes para o Windows Defender. Regras podem especificar o comportamento de entrada e saído para aplicações, endereços de rede e portas. 

### <a name="require-app-protection-conditional-access----1634317---"></a>Necessitam de acesso condicional de proteção de aplicações  <!--1634317 -->
Poderá usar *política de proteção de aplicações requerem*, confirma que a política é aplicada a aplicação de um utilizador antes de início de sessão estiver concluída, para impedir que os utilizadores acedam a dados a proteger com o acesso condicional. Enquanto a garantia de política pode retardar a primeira experiência de utilização, ele ajuda a proteger contra problemas de rede, configurações incorretas administrativas ou intencionais esforços para permitem despistar políticas de proteção de aplicações. 

### <a name="deployment-of-online-licensed-microsoft-store-for-business-apps----16726660---"></a>Implementação de online licenciado Microsoft Store para aplicações de negócio <!-- 16726660 -->
Será capaz de atribuir necessário online licenciada Microsoft Store para aplicações de negócio no contexto do dispositivo. Implementar um Microsoft Store para a aplicação de negócios desta forma permitirá que a aplicação ser instalada para todos os utilizadores no dispositivo. Isto só é aplicável no Windows 10 RS4 + dispositivos de ambiente de trabalho. A opção para instalar no contexto do dispositivo está disponível na página de atribuição de aplicações de cliente para aplicações licenciadas Online do MSFB.

### <a name="include-and-exclude-mixture-of-user-groups-and-device-groups-when-assigning-policies-and-profiles----1807547---"></a>Incluir e excluir a mistura de grupos de utilizadores e grupos de dispositivos durante a atribuição de políticas e perfis <!-- 1807547 -->
Ao atribuir políticas de conformidade ou perfis de configuração, pode atribuí-las a grupos de segurança com utilizadores ou dispositivos. Atualmente, pode incluir e excluir apenas grupos de utilizadores, *ou* incluir e excluir apenas grupos de dispositivos. Não é possível incluir e excluir uma mistura de grupos, tal como incluir grupos de utilizadores *e* excluir um grupo de dispositivos.

Poderá incluir e excluir uma mistura de grupos de utilizadores e grupos de dispositivos. Pode incluir um grupo de utilizadores e excluir um grupo de dispositivos. Por exemplo, pode atribuir ou implementar um perfil de configuração do dispositivo a um grupo de utilizadores, mas exclua os dispositivos pessoais.

[Atribuir perfis de configuração do dispositivo](device-profile-assign.md) inclui mais informações sobre a atribuição de perfis a grupos de utilizadores e grupos de dispositivos.

Aplica-se a: Todas as plataformas

### <a name="retire-noncompliant-devices----1827291---"></a>Extinguir dispositivos não conformes <!-- 1827291 -->
Vamos adicionar uma nova ação de conformidade para extinguir um dispositivo não conforme. Extinguir um dispositivo não conforme remove todos os dados da empresa do mesmo e também remove o dispositivo seja gerido pelo Intune. Esta ação é executada quando é atingido o valor configurado em dias. O valor mínimo é de 30 dias. 

### <a name="configure-settings-for-kernel-extensions-on-macos-devices----2043024---"></a>Configurar definições para extensões de kernel em dispositivos macOS <!-- 2043024 -->
Em dispositivos macOS, pode criar um perfil de configuração do dispositivo (**configuração do dispositivo** > **perfis** > **criar perfil** > escolher **macOS** para a plataforma). Um novo grupo de definições permitirá configurar e utilizar extensões de kernel nos seus dispositivos.

Aplica-se a: macOS 10.13.2 e posterior

### <a name="configure-profile-to-skip-some-screens-during-setup-assistant----2276470---"></a>Configurar o perfil para ignorar algumas telas durante o Assistente de configuração <!-- 2276470 -->
Quando cria um perfil de inscrição do macOS, poderá configurá-lo para ignorar qualquer um dos ecrãs seguintes quando um utilizador executar o Assistente de Configuração:
- Migração de Android
- Sinal de Exibição
- Privacidade
- iCloudStorage se criar um novo perfil ou editar um perfil, selecionado ignorar ecrãs necessidade para sincronizar com o servidor de MDM da Apple. Os utilizadores podem emitir uma sincronização manual dos dispositivos, para que haja um atraso de escolher as alterações de perfil.
Para obter mais informações, consulte [inscrever automaticamente dispositivos macOS com o programa de inscrição de dispositivos ou do Apple School Manager](device-enrollment-program-enroll-macos.md).

### <a name="device-users-can-view-all-managed-apps-theyve-installed-or-tried-to-install----2352913---"></a>Os utilizadores de dispositivos, podem ver todas as aplicações geridas que tenham instalado ou tentou instalar <!-- 2352913 -->
Portal da empresa para Windows irá listar todas as aplicações geridas&ndash; tanto necessária quanto disponível&ndash; que estão instaladas no dispositivo de um utilizador. Os utilizadores serão capazes de vista de tentativa e pendentes instalações de aplicações e respetivos Estados atuais. Se sua organização não torne as aplicações necessárias ou disponíveis, os utilizadores verão uma mensagem que explica que não existem aplicações da empresa foram instaladas. Os utilizadores também serão capazes de classificar ou filtrar as suas aplicações por Estado da instalação.

### <a name="scope-tags-for-apple-vpp-tokens---2371886---"></a>Etiquetas de âmbito para tokens VPP da Apple <!--2371886 -->
Poderá adicionar etiquetas de âmbito para tokens VPP da Apple. Apenas os utilizadores com a mesma etiqueta de âmbito têm acesso para o token de Apple VPP com a mesma. As aplicações VPP e ebooks adquirido com esse token herdam suas etiquetas de âmbito. Para obter mais informações sobre etiquetas de âmbito, veja [marcas RBAC de utilização e âmbito](scope-tags.md).

### <a name="use-applicability-rules-when-creating-windows-10-device-configuration-profiles----2549910---"></a>Utilize "regras de aplicabilidade" quando criar perfis de configuração de dispositivo Windows 10 <!-- 2549910 -->
Criar perfis de configuração de dispositivo Windows 10 (**configuração do dispositivo** > **perfis** > **criar perfil**  >  **Windows 10** para a plataforma). Poderá criar uma **regra de aplicabilidade** para que o perfil apenas se aplica a uma edição específica ou uma versão específica. Por exemplo, criar um perfil que permite que algumas configurações de disco BitLocker. Depois de adicionar o perfil, utilize uma regra de aplicabilidade para que o perfil apenas se aplica a dispositivos com o Windows 10 Enterprise.

Aplica-se a: 
- Windows 10 e posterior

### <a name="enable-win32-app-dependencies----2617348---"></a>Ativar dependências de aplicações do Win32 <!-- 2617348 -->
Pré-visualização pública - como o administrador, poderá exigir que as outras aplicações são instaladas como dependências antes de instalar a aplicação de Win32. Especificamente, o dispositivo tem de instalar a aplicação dependente (ões) antes de instalar a aplicação de Win32. Esta funcionalidade estará disponível apenas depois de atualizar o agente de gestão do Intune para 1904 versão (mais de 1.18.120.0) que pode demorar 1 ou 2 semanas adicionais depois vamos atualizar o serviço para em 1904. No Intune, selecione **aplicações de cliente** > **aplicações** > **adicionar** para apresentar o **Adicionar aplicação** painel. Selecione **aplicação do Windows (Win32)** como o **tipo de aplicação**. Para obter mais informações, consulte [Intune autónomo - gestão de aplicações de Win32](apps-win32-app-management.md).

### <a name="new-device-restriction-setting-for-android-enterprise-device-owner-let-users-connect-to-wi-fi-networks-on-android-enterprise-dedicated-devices-running-multi-app-kiosk-mode---3041940---"></a>Nova definição de restrição de dispositivos do Android Enterprise, o proprietário do dispositivo: permitir que os utilizadores a ligar a redes Wi-Fi em dispositivos Android Enterprise dedicado com o modo de local público de várias aplicações <!--3041940 -->
Os administradores poderão Ativar/desativar uma nova definição que permite aos utilizadores configurar o Bluetooth nos respetivos dispositivos Android Enterprise dedicado com o modo de local público de várias aplicações. Para ver esta definição na consola do Intune, escolha **Intune** > **configuração do dispositivo** > **perfis**  >  **Criar perfil** > Escolha **Android Enterprise** para a plataforma > **apenas proprietário do dispositivo, restrições de dispositivo** para o tipo de perfil > **definições**   >  **Dispositivos dedicados** > selecione **várias aplicações** do **modo de local público** definição de lista pendente. Uma opção chamada **configuração de Wi-Fi** estarão disponíveis para ativar. 

Aplica-se a: Dispositivos Android da empresa dedicado com o modo de local público de várias aplicações. 

### <a name="new-device-restriction-setting-for-android-enterprise-device-owner-let-users-configure-bluetooth-and-pairing-on-android-enterprise-dedicated-devices---3041941---"></a>Nova definição de restrição de dispositivos do Android Enterprise, o proprietário do dispositivo: permitir que os utilizadores a configurar o Bluetooth e emparelhamento em dispositivos Android Enterprise dedicado <!--3041941 -->
Os administradores poderão Ativar/desativar uma nova definição que permite aos utilizadores configurar o Bluetooth nos respetivos dispositivos Android Enterprise dedicado com o modo de local público de várias aplicações. Para ver esta definição na consola do Intune, escolha **Intune** > **configuração do dispositivo** > **perfis**  >  **Criar perfil** > Escolha **Android Enterprise** para a plataforma > **apenas proprietário do dispositivo, restrições de dispositivo** para o tipo de perfil > **definições**   >  **Dispositivos dedicados** > selecione **várias aplicações** do **modo de local público** definição de lista pendente. Uma opção chamada **Bluetooth configuração** estarão disponíveis para ativar. 

Aplica-se a: Dispositivos Android da empresa dedicado com o modo de local público de várias aplicações. 

### <a name="monitor-security-baseline-status-public-preview----3082047---"></a>Monitorizar o estado de linha de base de segurança (pré-visualização pública) <!-- 3082047 --> 
Quando monitorar a *estado do dispositivo* suas linhas de base de segurança, a vista será organizar o estado pelas categorias de linha de base, como *acima bloqueio*, *BitLocker*e  *Browser*. Todas as categorias de linha de base disponíveis serão representadas. Para cada categoria, verá o número de dispositivos não correspondam a uma categoria de linha de base específica, foram configuradas corretamente ou não se aplicam.

###  <a name="intune-security-tasks-for-defender-atp-in-public-preview----3208597---"></a>Tarefas de segurança do Intune para Defender ATP (em pré-visualização pública) <!-- 3208597 -->
Disponível como pré-visualização pública, o Intune em breve adicionará tarefas de segurança para o recentemente anunciado Defender ameaças da Microsoft e gestão de vulnerabilidades.  Com esta integração, os administradores de operações de segurança no ATP do Windows Defender (WDATP) com mais eficiência podem comunicar as remediações recomendadas ameaças emergentes para os administradores do Intune. A adição de tarefas de segurança Adiciona uma abordagem com base no risco para o descobrir, priorizar e remediar vulnerabilidades do ponto final e configurações incorretas.

Para saber mais sobre as tarefas de segurança no Intune, consulte o mensagem de blogue sobre [usar tarefas de segurança do Intune para estender a gestão de vulnerabilidades e ameaças Microsoft Defender ATP](https://techcommunity.microsoft.com/t5/Enterprise-Mobility-Security/Microsoft-Intune-security-tasks-extend-Microsoft-Defender-ATP-s/ba-p/369857). 

### <a name="create-and-use-oemconfig-device-configuration-profiles-in-intune----3305883---"></a>Criar e utilizar perfis de configuração de dispositivos de OEMConfig no Intune <!-- 3305883 -->
O Intune suportará a configuração de dispositivos Android Enterprise com OEMConfig. Especificamente, pode criar um perfil de configuração do dispositivo e aplicar as definições para dispositivos Android Enterprise com OEMConfig (**configuração do dispositivo** > **perfis**  >  **Criar perfil** > **Android enterprise** para a plataforma).

Suporte para OEMs encontra-se numa base por OEM. Se uma aplicação de OEMConfig pretende não estiver disponível na lista de aplicações de OEMConfig, entre em contato com `IntuneOEMConfig@microsoft.com`.

Aplica-se a: 
- Android enterprise

### <a name="new-device-restriction-settings-for-android-enterprise-device-owner----3574254---"></a>Novas definições de restrição de dispositivos do Android Enterprise, o proprietário do dispositivo <!-- 3574254 -->
Em dispositivos Android Enterprise, pode criar um perfil de restrição de dispositivos para permitir ou restringir funcionalidades, o conjunto de regras de palavra-passe e muito mais (**configuração do dispositivo** > **perfis**  >  **Criar perfil** > Escolha **Android Enterprise** para a plataforma > **apenas proprietário do dispositivo > restrições de dispositivos** para tipo de perfil). 

Novas definições, incluindo as definições de palavra-passe, permitindo que total acesso a aplicações no Google Play Store para dispositivos totalmente geridos e outros serão disponibilizados. 

Para ver a lista atual de definições, aceda à [definições de dispositivos Android Enterprise para permitir ou restringir funcionalidades](device-restrictions-android-for-work.md). 

Aplica-se a: Android Enterprise dispositivos totalmente geridos

### <a name="check-for-a-tpm-chipset-in-a-windows-10-device-compliance-policy----3617671---"></a>Verifique a existência de um chipset TPM numa política de conformidade de dispositivos Windows 10 <!-- 3617671 -->
Muitos Windows 10 e dispositivos posteriores têm chipsets Trusted Platform Module (TPM). Uma nova definição de conformidade irá verificar se um TPM está no dispositivo.

[Windows 10 e posteriores definições de política de conformidade](compliance-policy-create-windows.md#windows-10-and-later-policy-settings) lista as definições atuais.

Aplica-se a: 
- Windows 10 e posterior

### <a name="configure-your-win32-apps-to-be-installed-on-intune-enrolled-azure-ad-joined-devices----3695227---"></a>Configurar as suas aplicações de Win32 a serem instalados nos inscritos no Intune dispositivos associados ao Azure AD <!-- 3695227 -->
Poderá para dispositivos associados ao atribuir as aplicações de Win32 para ser instalada no Intune inscrito do Azure AD. Para obter mais informações sobre as aplicações de Win32 no Intune, consulte [gestão de aplicações de Win32](apps-win32-app-management.md).

### <a name="windows-defender-advanced-threat-protection-baseline----3754134---"></a>Linha de base de proteção de ameaças avançada do Windows Defender <!-- 3754134 -->
Vamos adicionar a nova linha de base para o ajudar a configurar as definições de proteção de ameaças avançada do Windows Defender.

### <a name="device-overview-shows-primary-user---794259---"></a>Descrição geral do dispositivo mostra o utilizador primário <!--794259 -->
A página de descrição geral do dispositivo irá mostrar o utilizador primário, também chamado do utilizador de afinidade de dispositivo de utilizador (UDA). Para ver o utilizador primário para um dispositivo, escolha **Intune** > **dispositivos** > **todos os dispositivos** > Escolha um dispositivo. O utilizador primário aparecerá junto à parte superior do **descrição geral** página.

### <a name="expanded-support-for-android-enterprise-fully-managed-devices----3903241-3903244-3903246---"></a>Suporte expandido para dispositivos Android Enterprise totalmente gerido <!-- 3903241, 3903244, 3903246 -->
Vamos expandir o suporte de dispositivos empresariais Android totalmente gerido ([anunciada pela primeira vez em Janeiro de 2019](whats-new.md#week-of-january-14-2019) para incluir o seguinte:
- Conformidade
- Acesso condicional
- Novo utilizador final aplicação

Para configurar o Android totalmente geridos os dispositivos, aceda a **inscrição de dispositivos** > **inscrição de dispositivos Android** > **dispositivos de utilizador de propriedade da empresa, totalmente gerido**. Suporte para dispositivos Android geridos totalmente permanece em pré-visualização e algumas funcionalidades do Intune poderão não estar totalmente funcionais. 

### <a name="additional-managed-google-play-app-reporting-for-android-enterprise-work-profile-devices----4105925---"></a>Adicional Google Play gerido relatório da aplicação para dispositivos de perfil de trabalho do Android Enterprise <!-- 4105925 -->
Para o Google Play gerido aplicações implementadas para dispositivos de perfil de trabalho do Android Enterprise, será possível ver o número de versão específica da aplicação instalada num dispositivo. Isso se aplica apenas as aplicações necessárias. A mesma funcionalidade para aplicações disponíveis será habilitada numa versão futura.

### <a name="ios-third-party-keyboards----4111843---"></a>iOS teclados de terceiros <!-- 4111843 -->
Suporte para a política de proteção de aplicações do Intune (aplicação) para o **teclados de terceiros** definição vai terminar devido a uma alteração de plataforma iOS. Não será capaz de configurar esta definição na consola de administração do Intune e não serão imposto no cliente no SDK da aplicação Intune.

<!-- 1903 start-->

### <a name="block-users-from-scanning-for-windows-updates----3316758---"></a>Impedir que os utilizadores a analisar as atualizações do Windows <!-- 3316758 -->
Estamos a adicionar uma novo Windows anel definição de atualização que pode utilizar para impedir que os utilizadores a analisar as atualizações do Windows. Esta definição não estará disponível a partir do portal, mas pode ser configurada utilizando a Graph API do Intune.

### <a name="windows-update-notifications----3316782---"></a>Notificações de atualização do Windows <!-- 3316782 -->
Estamos a adicionar suporte para as configurações de anel de atualização do Windows para que possa configurar as notificações de atualização do Windows, que os seus utilizadores verão. Esta definição não estará disponível a partir do portal, mas pode ser configurada utilizando a Graph API do Intune.

### <a name="easier-access-to-diagnostic-settings----3804627---"></a>Facilitar o acesso às definições de diagnóstico <!-- 3804627 -->
Estamos a adicionar uma nova opção para o **registos de auditoria** painel em cada carga de trabalho do Log de auditoria na consola do Intune que pode utilizar para abrir diretamente a *das definições de diagnóstico* página.

## <a name="notices"></a>Avisos

[!INCLUDE [Intune notices](./includes/intune-notices.md)]

### <a name="see-also"></a>Consulte também
Veja [Novidades do Microsoft Intune](whats-new.md) para obter detalhes sobre os desenvolvimentos recentes.



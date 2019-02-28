---
title: Novidades no Microsoft Intune – Azure | Microsoft Docs
titlesuffix: ''
description: Descobrir as novidades do Intune no portal do Azure
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/27/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 791ed23f-bd13-4ef0-a3dd-cd2d7332c5cc
ms.reviewer: dougeby
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 83168acc6653f750b9cf32d91602464b62aebcfe
ms.sourcegitcommit: 0f4247914f55349f618f6176a4cdca08503215f5
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/27/2019
ms.locfileid: "56955634"
---
# <a name="whats-new-in-microsoft-intune"></a>Novidades do Microsoft Intune
[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Saiba mais sobre as novidades todas as semanas no Microsoft Intune. Também pode descobrir alterações futuras, [avisos importantes](#notices) e informações sobre [versões anteriores](whats-new-archive.md). 

> [!Note]
> É possível que algumas funcionalidades sejam implementadas durante várias semanas e que não estejam disponíveis para todos os clientes na primeira semana.

**RSS feed**: Seja notificado quando esta página é atualizada ao copiar e colar o URL seguinte no seu leitor de feeds: `https://docs.microsoft.com/api/search/rss?search=%22What%27s+new+in+microsoft+intune%3F+-+Azure%22&locale=en-us`

<!-- Common categories:  
### App management
### Device configuration
### Device enrollment
### Device management
### Intune apps
### Monitor and troubleshoot
### Role-based access control

-->     

<!-- ########################## -->
## <a name="week-of-february-25-2019"></a>Semana de 25 de Fevereiro de 2019

### <a name="device-configuration"></a>Configuração do dispositivo

#### <a name="intune-powershell-module----951068----"></a>Módulo do PowerShell do Intune <!-- 951068  -->
O módulo PowerShell do Intune, que fornece suporte para a API do Intune através do Microsoft Graph, está agora disponível na [Gallery do PowerShell Microsoft](https://www.powershellgallery.com/packages/Microsoft.Graph.Intune/6.1902.1.10).

- [Detalhes sobre como utilizam este módulo](https://github.com/Microsoft/Intune-PowerShell-SDK/blob/master/README.md)
- [Exemplos de cenário com este módulo](https://github.com/Microsoft/Intune-PowerShell-SDK/blob/master/Samples/README.md)

#### <a name="improved-support-for-delivery-optimization----3183757-------"></a>Suporte aprimorado para otimização de entrega  <!--3183757     -->
Expandimos o suporte do Intune para configurar a otimização de entrega. Agora, pode configurar uma lista expandida de [as definições de otimização de entrega](delivery-optimization-settings.md) e aplicá-lo para os seus dispositivos diretamente a partir do consola do Intune.


## <a name="week-of-february-18-2019"></a>Semana de 18 de Fevereiro de 2019

### <a name="app-management"></a>Gestão de aplicações

#### <a name="intune-will-leverage-google-play-protect-apis-on-android-devices----2577355-----"></a>Intune será tiram partido das APIs de proteger reproduzir da Google em dispositivos Android <!-- 2577355   -->
Alguns administradores de TI enfrentam um cenário BYOD onde os utilizadores finais podem acabar embota ou jailbreaking o celular. Este comportamento, embora às vezes, não mal-bem-intencionado, resulta numa omissão de muitas das políticas do Intune que estão definidas para proteger os dados da organização nos dispositivos do utilizador final. Assim, o Intune fornece deteção de raiz e jailbreak para dispositivos inscritos e não inscritos. Com esta versão, o Intune irá agora tirar Google Play proteger APIs para adicionar à nossa verificações existentes para a deteção de raiz para dispositivos não inscritos. Embora a Google não partilha a totalidade das verificações de deteção de raiz que ocorrem, esperamos que essas APIs para detetar os utilizadores que têm Root seus dispositivos por qualquer motivo de personalização do dispositivo para a capacidade de obter as atualizações de SO mais recente nos dispositivos mais antigos. Estes utilizadores, em seguida, podem ser impedidos de aceder a dados empresariais ou suas contas empresariais poderão ser eliminadas a partir das suas aplicações de política ativada. Para o valor adicional, o administrador de TI agora têm várias atualizações de geração de relatórios no painel de proteção de aplicações do Intune – o relatório de "Utilizadores sinalizados" irá mostrar os utilizadores que são detetados através do análise de SafetyNet API da Google Play Protect, o "potencialmente prejudicial aplicações" relatório irá mostre as aplicações são detetadas através verificar aplicações API da Google de verificação. Esta funcionalidade está disponível no Android.

#### <a name="win32-app-information-available-in-troubleshooting-blade----2617342-----"></a>Informações da aplicação Win32 disponíveis no painel de resolução de problemas <!-- 2617342   -->
Agora pode recolher ficheiros de registo de falha para uma instalação de aplicações de Win32 a partir da aplicação Intune **resolução de problemas** painel. Para obter mais informações sobre resolução de problemas de instalação de aplicação, consulte [resolver problemas de instalação de aplicações](troubleshoot-app-install.md) e [problemas de aplicações de Win32 de resolução de problemas](apps-win32-app-management.md#troubleshoot-win32-app-issues).

#### <a name="app-status-details-for-ios-apps----3761235-----"></a>Detalhes do Estado da aplicação para aplicações iOS <!-- 3761235   -->
Existem mensagens de erro de instalação de aplicação nova relacionadas ao seguinte:
- Falha de aplicações VPP durante a instalação num iPad partilhado
- Falha quando a loja de aplicações está desativada
- Falha ao localizar a licença do VPP para aplicação
- Falha ao instalar aplicações de sistemas com o fornecedor de MDM
- Falha ao instalar aplicações quando o dispositivo estiver no modo perdido ou o modo de local público
- Falha ao instalar a aplicação quando o utilizador não tem sessão iniciado na App Store

No Intune, selecione **aplicações de cliente** > **aplicações** > "Nome da aplicação" > **estado de instalação de dispositivo**. Novas mensagens de erro estará disponíveis na **detalhes do estado** coluna.

#### <a name="new-app-categories-screen-in-the-company-portal-app-for-windows-10---3834780----"></a>Novo ecrã de categorias de aplicação na aplicação Portal da empresa para Windows 10<!-- 3834780  -->
Um ecrã novo chamado **categorias de aplicações** foi adicionado para melhorar a experiência de navegação e a seleção de aplicação no Portal da empresa para Windows 10. Os utilizadores irão ver agora as aplicações ordenadas em categorias, como **em destaque**, **educação**, e **produtividade**. Esta alteração apareça em versões do Portal da empresa 10.3.3451.0 e mais tarde. Para ver o novo ecrã, consulte [quais são as novidades na IU da aplicação](https://docs.microsoft.com/intune/whats-new-app-ui). Para obter mais informações sobre as aplicações no Portal da empresa, consulte [instalar e partilhar aplicações no seu dispositivo](/intune-user-help/install-apps-cpapp-windows).  

#### <a name="power-bi-compliance-app----1455231-doc-work-item---"></a>Aplicação de conformidade do Power BI <!-- 1455231 doc-work-item -->
Aceder ao seu armazém de dados do Intune no Power BI Online com o [conformidade do Intune (armazém de dados)](https://app.powerbi.com/groups/me/getapps/services/Intune_dw_compliance) aplicação. Com esta aplicação do Power BI, pode agora aceder e partilhar relatórios previamente criados sem qualquer configuração e sem sair do seu navegador da web. Para obter mais informações, consulte [registo de alterações - aplicação de conformidade do Power BI](reports-changelog.md#power-bi-compliance-app). Para obter mais atualizações do armazém de dados do Intune, consulte [futuras alterações à API do armazém de dados do Intune](whats-new.md#upcoming-change-to-the-intune-data-warehouse-api).


### <a name="device-configuration"></a>Configuração do dispositivo

#### <a name="powershell-scripts-can-run-in-a-64-bit-host-on-64-bit-devices----1862675-----"></a>Scripts do PowerShell podem ser executado num host de 64 bits em dispositivos de 64 bits <!-- 1862675   -->
Quando adiciona um script do PowerShell para um perfil de configuração do dispositivo, o script é executado sempre de 32 bits, mesmo em sistemas de operativos de 64 bits. Com esta atualização, um administrador pode executar o script num host do PowerShell de 64 bits em dispositivos de 64 bits (**configuração do dispositivo** > **scripts do PowerShell**  >   **Adicione** > **configurar** > **executar script num anfitrião do PowerShell de 64 bits**).

Para obter mais detalhes sobre como utilizar o PowerShell, consulte [scripts do PowerShell no Intune](intune-management-extension.md).

Aplica-se a: Windows 10 e posterior

#### <a name="macos-users-are-prompted-to-update-their-password----1873216---"></a>utilizadores do macOS-lhe pedidos para atualizar a palavra-passe <!-- 1873216 -->
Intune é aplicar a **ChangeAtNextAuth** definição em dispositivos macOS. Esta definição irá afetar os utilizadores finais e dispositivos que têm políticas de conformidade de palavra-passe ou perfis de palavra-passe de restrição de dispositivos. Os utilizadores finais for pedidos, uma vez, para atualizar a palavra-passe. Este pedido acontece sempre que um utilizador primeiro executa uma tarefa que exige autenticação, como iniciar sessão no dispositivo. Também podem ser pedido aos utilizadores para atualizar a palavra-passe quando fazer nada que requer privilégios administrativos, como pedir acesso de keychain. 

Quaisquer alterações de política de palavra-passe nova ou existente pelo administrador pede-lhe os utilizadores finais novamente para atualizar a palavra-passe.

Aplica-se a:  
macOS

#### <a name="assign-scep-certificates-to-a-userless-macos-device-------2340521------"></a>Atribuir certificados SCEP para um dispositivo macOS sem utilizador    <!-- 2340521    -->
Pode atribuir certificados Simple Certificate Enrollment Protocol (SCEP), usando atributos de dispositivo para dispositivos macOS, incluindo os dispositivos sem afinidade do utilizador e associar o perfil de certificado, Wi-Fi ou perfis VPN. Isso expande o suporte já temos a [atribuir certificados SCEP para dispositivos com e sem afinidade do utilizador](certificates-scep-configure.md#create-a-scep-certificate-profile) que executam o Windows, iOS e Android.  Esta atualização adiciona a opção de selecionar um tipo de certificado de *dispositivo* ao configurar um perfil de certificado SCEP para o macOS.

Aplica-se a: 
- macOS

#### <a name="intune-conditional-access-ui-update------2432313-----"></a>Atualização de interface do Usuário de acesso condicional do Intune   <!-- 2432313   -->
Fizemos melhorias na interface do usuário para o acesso condicional na consola do Intune. Estas incluem:
-  Substituído do Intune *acesso condicional* painel com o painel do Azure Active Directory. Isto garante que terá acesso a uma gama completa de definições e configurações para [acesso condicional](conditional-access.md) (que continua sendo uma tecnologia do Azure AD), do Intune consola. 
- Mudamos o nome da *acesso no local* painel para *acesso ao Exchange*e realocada o *conector de serviço do Exchange* configuração deste painel nome mudado.  Esta alteração consolida onde [configurar e monitorizar detalhes relacionados com o Exchange online e no local](exchange-connector-install.md).  

#### <a name="kiosk-browser-and-microsoft-edge-browser-apps-can-run-on-windows-10-devices-in-kiosk-mode----2935135-----"></a>Aplicações de Browser de local público e o Browser do Microsoft Edge podem ser executadas em dispositivos Windows 10 no modo de local público <!-- 2935135   -->
Pode utilizar dispositivos Windows 10 no modo de local público para executar uma aplicação ou muitas aplicações. Esta atualização inclui várias alterações para utilizar aplicações de browser no modo de local público, incluindo:

- Adicionar o Browser do Microsoft Edge ou o Browser de local público para ser executado como aplicações no dispositivo local público (**configuração do dispositivo** > **perfis** > **novo perfil**  >  **Windows 10 e posterior** para a plataforma > **quiosque** para tipo de perfil).
- Novos recursos e as definições estão disponíveis para permitir ou restringir (**configuração do dispositivo** > **perfis** > **novo perfil**  >  **Windows 10 e posterior** para a plataforma > **restrições de dispositivos** para tipo de perfil), incluindo:

  - Microsoft Edge Browser:
    - Utilizar o modo de local público do Microsoft Edge
    - Atualize o browser após o tempo de inatividade

 - Favoritos e pesquisar:
    - Permitir alterações para o mecanismo de pesquisa

Para obter uma lista destas definições, consulte:

- [Windows 10 e posteriores definições do dispositivo para ser executado como um quiosque](kiosk-settings-windows.md)
- [Restrições de dispositivos de Browser do Microsoft Edge](device-restrictions-windows-10.md#microsoft-edge-browser)
- [Favoritos e restrições de dispositivos de pesquisa](device-restrictions-windows-10.md##favorites-and-search)

Aplica-se a: Windows 10 e posterior

#### <a name="new-device-restriction-settings-for-ios-and-macos-devices----3448774-----"></a>Novas definições de restrição de dispositivos para dispositivos iOS e macOS <!-- 3448774   -->
Pode restringir algumas definições e funcionalidades nos dispositivos que executam o iOS e macOS (**configuração do dispositivo** > **perfis** > **novo perfil**  >  **iOS** ou **macOS** para a plataforma > **restrições de dispositivos** para tipo de perfil). Esta atualização adiciona mais funcionalidades e as definições que pode controlar, incluindo o tempo de ecrã de configuração, alterar definições de eSIM e planos de celular e muito mais em dispositivos iOS. Além disso, atrasando a visibilidade do usuário de atualizações de software e a bloquear a colocação em cache conteúdo em dispositivos macOS. 

Para ver os recursos e configurações que pode restringir, consulte:

- [definições de restrição de dispositivos iOS](device-restrictions-ios.md)
- [definições de restrição de dispositivos macOS](device-restrictions-macos.md)

Aplica-se a:

- iOS
- macOS

#### <a name="kiosk-devices-are-now-called-dedicated-devices-on-android-enterprise-devices----3598402-----"></a>Dispositivos de "local público" são agora denominados "Dispositivos dedicados" em dispositivos Android Enterprise <!-- 3598402   -->
Para se alinhar a terminologia do Android, **quiosque** é alterado para **dispositivos dedicados** para dispositivos Android enterprise (**configuração do dispositivo**  >  **Perfis** > **criar perfil** > * * Android enterprise para a plataforma > **dispositivo proprietário apenas** > **dispositivo Restrições** > **dispositivos dedicados**).

Para ver as definições disponíveis, aceda à [definições do dispositivo para permitir ou restringir funcionalidades](device-restrictions-android-for-work.md#dedicated-device-settings).

Aplica-se a:  
Android Enterprise

#### <a name="safari-and-delaying-user-software-update-visibility-ios-settings-are-moving-in-the-intune-ui----3640850-3803313-----"></a>Safari e Delaying utilizador atualização de software iOS visibilidade definições estão a ser movidos na IU do Intune <!-- 3640850, 3803313   -->
Para dispositivos iOS, pode configurar as definições do Safari e configurar atualizações de Software. Nesta atualização, estas definições estão a ser movidos para diferentes partes da IU do Intune:

- As definições do Safari movidas de **Safari** (**configuração do dispositivo** > **perfis** > **novo perfil**  >  **iOS** para a plataforma > **restrições de dispositivos** para o tipo de perfil) para  **[aplicações incorporadas](device-restrictions-ios.md#built-in-apps)**.
- O **atrasar a visibilidade de atualização de software de utilizador para supervisionado dispositivos iOS** definição (**atualizações de Software** > **atualizar políticas para iOS**) está a mudar para  **Restrições de dispositivos** > **[geral](device-restrictions-ios.md#general)**.  Para obter detalhes sobre o impacto para as políticas existentes, consulte [atualizações de software iOS](software-updates-ios.md#configure-the-policy). 

Para obter uma lista das definições, consulte:

- [restrições de dispositivos iOS](device-restrictions-ios.md) 
- [atualizações de software do iOS](software-updates-ios.md)

Esta funcionalidade aplica-se a: 

- iOS

#### <a name="enabling-restrictions-in-the-device-settings-is-renamed-to-screen-time-on-ios-devices----3699164-----"></a>Ativar restrições nas definições do dispositivo foi mudado para o tempo de tela em dispositivos iOS <!-- 3699164   -->
Pode configurar o **ativar restrições nas definições do dispositivo** no supervisionado dispositivos iOS (**configuração do dispositivo** > **perfis**  >  **Novo perfil** > **iOS** para a plataforma > **restrições de dispositivos** para o tipo de perfil > **geral**). Nesta atualização, esta definição foi mudada para **tempo de ecrã (apenas supervisionado)**. 

O comportamento é o mesmo. Especificamente: 

- iOS 11.4.1 e versões anteriores: **Bloco** impede que os utilizadores finais a definição de suas próprias restrições nas definições do dispositivo. 
- iOS 12.0 e posterior: **Bloco** impede que os utilizadores finais definir seus próprios **ecrã tempo** nas definições do dispositivo, incluindo restrições de privacidade & de conteúdo. Dispositivos atualizados para o iOS 12.0 não verão a guia restrições nas definições do dispositivo deixa de poder. Estas definições estão em **tempo de tela**. 

Para obter uma lista das definições, consulte [restrições de dispositivos iOS](device-restrictions-ios.md#general).

Aplica-se a: 
- iOS


### <a name="device-management"></a>Gestão de dispositivos

#### <a name="rename-an-enrolled-windows-device----1911112----"></a>Mudar o nome de um dispositivo Windows inscrito <!-- 1911112  -->
Agora pode renomear um dispositivo Windows 10 inscrito (RS4 ou posterior). Para fazer, escolha **Intune** > **dispositivos** > **todos os dispositivos** > Escolha um dispositivo > **mudança de nome de dispositivo**.

#### <a name="auto-assign-scope-tags-to-resources-created-by-an-admin-with-that-scope----3173823----"></a>Atribuir automaticamente etiquetas de âmbito para recursos criados por um administrador com esse âmbito <!-- 3173823  -->
Quando um administrador cria um recurso, quaisquer etiquetas de âmbito atribuídas para o administrador serão automaticamente atribuídas a esses novos recursos.

### <a name="monitor-and-troubleshoot"></a>Monitorizar e resolver problemas

#### <a name="failed-enrollment-report-moves-to-the-device-enrollment-blade----3560202----"></a>Relatório de inscrição falha se move para o painel de inscrição de dispositivos <!-- 3560202  -->
O **falha inscrições** relatório foi movido para o **Monitor** seção o **inscrição de dispositivos** painel. Foram adicionadas duas novas colunas (método de inscrição e versão do SO).

#### <a name="company-portal-abandonment-report-renamed-to-incomplete-user-enrollments---3815076-eemiss---"></a>Relatório de abandonment de Portal da empresa foi mudado para inscrições de utilizador incompleto <!--3815076 eemiss -->
O **abandonment do Portal da empresa** relatório foi renomeado para **inscrições de utilizador incompleta**.


<!-- ########################## -->
## <a name="week-of-february-4-2019"></a>Semana de 4 de Fevereiro de 2019

### <a name="app-management"></a>Gestão de aplicações

#### <a name="intune-macos-company-portal-dark-mode----3300524----"></a>No modo escuro do Portal da empresa do Intune macOS <!-- 3300524  -->
O Portal da empresa do macOS do Intune agora suporta o modo escuro para macOS. Quando ativar o modo escuro num dispositivo macOS 10.14 +, o Portal da empresa irá ajustar sua aparência para as cores que refletem esse modo.

<!-- ########################## -->
## <a name="week-of-january-21-2019"></a>Semana de 21 de Janeiro de 2019

### <a name="app-management"></a>Gestão de aplicações

#### <a name="toast-notifications-for-win32-apps----3136566-----"></a>Notificações de alerta para aplicações de Win32 <!-- 3136566   -->
É possível suprimir notificações de alerta do utilizador final que mostra por atribuição de aplicações. A partir do Intune, selecione **aplicações de cliente** > **aplicações** > selecione a aplicação > **atribuições** > **grupos incluem**. 

#### <a name="intune-app-protection-policies-ui-update----3251427----"></a>Atualização da IU das políticas de proteção de aplicações do Intune <!-- 3251427  -->
Alterámos as etiquetas para as definições e botões para proteção de aplicações do Intune para que cada mais fácil de compreender. Algumas das alterações incluem:  
- Controles são alterados de **Sim** / **nenhum** controla principalmente para **bloco** / **permitir** e **desativar** / **ativar** controles. As etiquetas também são atualizadas.  
- As definições são reformatadas, portanto, a definição e a etiqueta são lado a lado no controle, para fornecer uma navegação melhor.   

As predefinições e diversas configurações permanecem os mesmos, mas esta alteração permite ao utilizador entender, navegar e utilizar as definições mais facilmente para aplicar políticas de proteção da aplicação selecionada. Para obter informações, consulte [definições do iOS](app-protection-policy-settings-ios.md) e [definições do Android](app-protection-policy-settings-android.md).

#### <a name="additional-settings-for-outlook----3301182----"></a>Definições adicionais para o Outlook <!-- 3301182  -->
Agora pode configurar as definições de followiong adicionais para o Outlook para iOS e Android com o Intune:
- Permitir apenas contas escolares ou profissionais a ser utilizado no Outlook no iOS e Android
- Implementar a autenticação moderna do Office 365 e a autenticação moderna híbrida contas no local
- Utilize `SAMAccountName` para o campo de nome de utilizador no perfil de e-mail quando a autenticação básica é seleccionada

As seguintes definições são ainda a ser lançadas gradualmente e estarão disponíveis na sua consola em breve:
- Permitir que os contactos sejam guardados
- Configurar destinatários externos dicas de email
- Configurar **caixa de entrada destaques**
- Exigir biometria para acessar o Outlook para iOS

A definição abaixo é apresentada na consola do Intune, mas quando configurado, não irá funcionar conforme esperado. Este problema será corrigido em breve:
- Bloquear a imagens externas

> [!NOTE]
> Se estiver a utilizar políticas de proteção de aplicações do Intune para gerir o acesso de identidades empresariais, deve considerar a ativação não **requerem biometria**. Para obter mais informações, consulte **requerer credenciais empresariais de acesso** para [iOS as definições de acesso](app-protection-policy-settings-ios.md#access-requirements) e [definições de acesso para Android](app-protection-policy-settings-android.md#access-requirements).

#### <a name="delete-android-enterprise-apps----1352553---"></a>Eliminar as aplicações do Android Enterprise <!-- 1352553 -->
Pode eliminar as aplicações geridas do Google Play do Microsoft Intune. Para eliminar uma aplicação do Google Play gerida, abra o Microsoft Intune no portal do Azure e selecione **aplicações de cliente** > **aplicações**. Da lista de aplicações, selecione as reticências (...) à direita da aplicação do Google Play gerida, em seguida, selecione **eliminar** na lista apresentada. Quando elimina uma aplicação do Google Play gerida da lista de aplicações, a aplicação do Google Play gerida é automaticamente não aprovada.

#### <a name="managed-google-play-app-type----1352580---"></a>Tipo de aplicação do Google Play gerido <!-- 1352580 -->
O **managed Google Play** tipo de aplicação permite-lhe adicionar especificamente [Google Play aplicações geridas](https://play.google.com/work/search?q=microsoft&c=apps) ao Intune. Como o administrador do Intune, pode agora navegar, procurar, aprovar, sincronizar e atribuir aprovados Google Play gerido aplicações no Intune.  Já não precisar de procurar na consola do Google Play gerido separadamente e já não tem de autenticar.  No Intune, selecione **aplicações de cliente** > **aplicações** > **adicionar**. Na **tipo de aplicação** lista, selecione **Google Play gerido** como o tipo de aplicação.

### <a name="default-android-pin-keyboard----3802457---"></a>Teclado de Android PIN predefinido <!-- 3802457 -->
Para os utilizadores finais que definiu uma aplicação de proteção de política (PIN da aplicação Intune) nos respetivos dispositivos Android com o tipo PIN de "Numérica", irão ver agora o teclado de Android padrão em vez de teclado Android fixo da interface do Usuário que foi criado anteriormente. Esta alteração foi feita para ser consistente ao utilizar o teclados padrão no Android e iOS, para os dois tipos PIN de "Numérica" e/ou de "Código de acesso". Para obter mais informações sobre as definições de acesso do utilizador final no Android, por exemplo, o PIN da aplicação, consulte [requisitos de acesso para Android](app-protection-policy-settings-android.md#access-requirements).

### <a name="device-configuration"></a>Configuração do dispositivo

#### <a name="use-microsoft-recommended-settings-with-security-baselines-public-preview----2055484-----"></a>Utilizar definições recomendadas pela Microsoft com linhas de base de segurança (pré-visualização pública) <!-- 2055484   -->

O Intune tem integração com outros serviços centrados na segurança, incluindo o Windows Defender ATP e o Office 365 ATP. Os clientes estão a pedir uma estratégia comum e um conjunto coeso de fluxos de trabalho de segurança de ponto a ponto em todos os serviços do Microsoft 365. O nosso objetivo é alinhar estratégias para desenvolver soluções que criem uma ponte entre operações de segurança e tarefas de administrador comuns. No Intune, pretendemos cumprir este objetivo através da publicação de um conjunto de "Linhas de base de segurança" recomendadas pela Microsoft (**Intune** > **Linhas de base de segurança**).  Um administrador pode criar políticas de segurança diretamente a partir dessas linhas de base e, em seguida, implementá-las aos respetivos utilizadores. Também pode personalizar as recomendações de melhores práticas para satisfazer as necessidades da sua organização. O Intune assegura que os dispositivos permanecem em conformidade com estas linhas de base e notifica os administradores de utilizadores ou dispositivos que não estejam em conformidade.

Esta funcionalidade está em pré-visualização pública, para que quaisquer perfis criados agora não serão movida aos modelos de linhas de base de segurança que estão em disponibilidade geral (GA). Não deve planeia utilizar estes modelos de pré-visualização no seu ambiente de produção.

Para saber mais sobre as linhas de base de segurança, veja [criar uma linha de base de segurança do Windows 10 no Intune](security-baselines-monitor.md).

Esta funcionalidade aplica-se a: Windows 10 e posterior

#### <a name="non-administrators-can-enable-bitlocker-on-windows-10-devices-joined-to-azure-ad---2147379-----"></a>Os não administradores podem ativar o BitLocker em dispositivos Windows 10 associados ao Azure AD<!-- 2147379   -->
Quando ativa as definições do BitLocker em dispositivos Windows 10 (**configuração do dispositivo** > **perfis** > **criar perfil**  >  **Windows 10 e posterior** para a plataforma > **proteção de ponto final** para o tipo de perfil > **encriptação Windows**), adicionar as definições do BitLocker. 

Esta atualização inclui uma nova definição de disco BitLocker para permitir que os usuários padrão (não-administradores) ativar a encriptação. 

Para ver as definições, aceda à [definições do Endpoint protection para Windows 10](endpoint-protection-windows-10.md#windows-encryption).

#### <a name="check-for-configuration-manager-compliance----2192052--eepublished----"></a>Verificar a conformidade do Configuration Manager <!-- 2192052  eepublished  -->
Esta atualização inclui uma nova definição de conformidade do System Center Configuration Manager (**conformidade do dispositivo** > **políticas** > **criar política**  >  **Windows 10 e posterior** > **compatibilidade do Configuration Manager**). O Configuration Manager envia sinais de conformidade ao Intune. Com esta definição, pode exigir a todos os sinais de Configuration Manager para retornar "em conformidade".

Por exemplo, pode exigir que todas as atualizações do software sejam instaladas nos dispositivos. No Configuration Manager, este requisito apresenta o estado "Instalado". Se todos os programas no dispositivo estão num Estado desconhecido, em seguida, o dispositivo está em conformidade no Intune.

[Compatibilidade do Configuration Manager](compliance-policy-create-windows.md#configuration-manager-compliance) descreve esta definição.

Aplica-se a: Windows 10 e posterior

#### <a name="customize-wallpaper-on-supervised-ios-devices-using-a-device-configuration-profile----2809324-----"></a>Personalizar a imagem de fundo em dispositivos iOS supervisionados a utilizar um perfil de configuração do dispositivo <!-- 2809324   -->
Quando cria um perfil de configuração do dispositivo para dispositivos iOS, pode personalizar algumas funcionalidades (**configuração do dispositivo** > **perfis** > **Create perfil** > **iOS** para a plataforma > **funcionalidades do dispositivo** para tipo de perfil). Esta atualização inclui novos **papel de parede** definições que permitem que um administrador utilizar uma imagem de formato. png,. jpg ou. JPEG na tela inicial ou no ecrã de bloqueio. Estas definições de imagem de fundo aplicam-se apenas a dispositivos supervisionados. 

Para obter uma lista destas definições, consulte [definições de funcionalidade do dispositivo iOS](ios-device-features-settings.md).

#### <a name="windows-10-kiosk-is-generally-available----3594661----"></a>Quiosque do Windows 10 está disponível em geral <!-- 3594661  -->
Nesta atualização, a funcionalidade de local público no Windows 10 e dispositivos posteriores está disponível em geral (GA). Para ver todas as definições que pode adicionar e configurar, consulte [definições de local público para o Windows 10 (e versões posteriores)](kiosk-settings.md).

#### <a name="contact-sharing-via-bluetooth-is-removed-in-device-restrictions--device-owner-for-android-enterprise----3598396-----"></a>Partilha de contactos através de Bluetooth for removido no restrições de dispositivos > proprietário do dispositivo do Android Enterprise <!-- 3598396   -->
Quando cria um perfil de restrições de dispositivos para dispositivos Android Enterprise, há uma **contacto partilha através de Bluetooth** definição. Nesta atualização, o **contacto partilha através de Bluetooth** configuração seja removida (**configuração do dispositivo** > **perfis**  >   **Criar perfil** > **Android Enterprise** para a plataforma > **restrições de dispositivos > proprietário do dispositivo** para o tipo de perfil > **geral** ). 

O **contacto partilha através de Bluetooth** definição não é suportada para a gestão de proprietário do dispositivo do Android Enterprise. Quando esta definição for removida, não afeta quaisquer dispositivos ou inquilinos, mesmo que esta definição está ativada e configurada no seu ambiente.

Para ver a lista atual de definições, aceda à [definições de dispositivos Android Enterprise para permitir ou restringir funcionalidades](device-restrictions-android-for-work.md).

Aplica-se a: Proprietário do dispositivo Android Enterprise

### <a name="device-management"></a>Gestão de dispositivos

#### <a name="selective-wipe-support-for-wip-without-enrollment-devices----1434452---"></a>Suporte de eliminação seletiva para WIP sem inscrição de dispositivos <!-- 1434452 -->
Windows Information Protection sem inscrição (WIP-PODEMOS) permite que os clientes proteger os dados empresariais em dispositivos Windows 10, sem a necessidade de inscrição de MDM completa. Assim que os documentos estão protegidos com um WIP-política de nós, os dados protegidos que podem ser apagados seletivamente por um administrador do Intune. Ao selecionar o utilizador e dispositivo e enviar um pedido de eliminação de dados, todos os dados que foi protegido por meio do WIP-política irá tornar-se inutilizável. No Intune, no portal do Azure, selecione **Aplicação móvel** > **Eliminação seletiva da aplicação**.

### <a name="monitor-and-troubleshoot"></a>Monitorizar e resolver problemas

#### <a name="new-operational-logs-and-ability-to-send-logs-to-azure-monitor-services----3762211----"></a>Novos registos operacionais e capacidade para enviar registos para serviços do Azure Monitor <!-- 3762211  -->
O Intune tem o log de auditoria interno que regista os eventos são feitas alterações. Esta atualização inclui novos recursos de Registro em log, incluindo: 
- Registos operacionais (pré-visualização) que mostram detalhes sobre os utilizadores e dispositivos inscritos, incluindo o êxito e tentativas falhadas.
- Os registos de auditoria e registos operacionais podem ser enviados para o Azure Monitor, incluindo contas de armazenamento, os hubs de eventos e do log analytics. Estes serviços permitem-lhe armazenar, utilizar a análise de como Splunk e QRadar e obtenha visualizações dos seus dados de registo.

[Enviar dados de registo para o armazenamento, os hubs de eventos ou do log analytics no Intune](review-logs-using-azure-monitor.md) fornece mais informações sobre esta funcionalidade.

### <a name="skip-more-setup-assistant-screens-on-an-ios-dep-device----2687509----"></a>Ignorar mais ecrãs do Assistente de configuração num dispositivo DEP iOS <!-- 2687509  -->
Além dos ecrãs que atualmente pode ignorar, pode definir iOS dispositivos DEP para ignorar os ecrãs seguintes no Assistente de configuração, quando um utilizador inscreve o dispositivo: Apresenta tom, privacidade, migração Android, botão Home page, iMessage & FaceTime, integração, migração de Watch, aparência, tempo de tela, atualização de Software, a configuração SIM.
Para escolher que telas para ignorar, aceda a **inscrição de dispositivos** > **inscrição da Apple** > **tokens do programa de inscrição** > Escolha um token > **Perfis** > Escolha um perfil > **propriedades** > **personalização do Assistente de configuração** > Escolha **ocultar**  para qualquer telas que pretende ignorar > **OK**.
Se criar um novo perfil ou editar um perfil, selecionado ignorar a necessidade de telas para sincronizar com o servidor de MDM da Apple. Os utilizadores podem emitir uma sincronização manual dos dispositivos, para que haja um atraso de escolher as alterações de perfil.

#### <a name="android-enterprise-app-we-app-deployment----1171203---"></a>Aplicação do Android Enterprise-implementação de aplicações, <!-- 1171203 -->
Para dispositivos Android num não inscritos proteção política sem inscrição de aplicações (APP-PODEMOS) cenário de implementação, pode agora utilizar geridos Google Play para implementar aplicações da loja e aplicações aos utilizadores LOB. Especificamente, pode fornecer aos utilizadores finais uma experiência de instalação e de catálogo de aplicações que já não necessita que os utilizadores finais flexibilize as a postura de segurança dos seus dispositivos ao permitir que as instalações de origens desconhecidas. Além disso, neste cenário de implementação irá fornecer uma experiência de usuário aprimorada do fim.

<!-- ########################## -->
## <a name="week-of-january-14-2019"></a>Semana de 14 de Janeiro de 2019

### <a name="preview-of-support-for-android-corporate-owned-fully-managed-devices----1574342----"></a>Pré-visualização do suporte para dispositivos Android de empresa, totalmente geridos <!-- 1574342  -->
Intune agora suporta totalmente geridos os dispositivos Android, uma empresa cenário de "proprietário do dispositivo" em que dispositivos totalmente geridos pelo IT e são associados aos utilizadores individuais. Isto permite aos administradores gerir todo o dispositivo, aplicar um conjunto expandido de controlos de política indisponíveis para perfis de trabalho e restringe os utilizadores a instalar aplicações da Google Play gerido apenas. Para obter mais informações, consulte [configurar o Intune inscrição do Android totalmente dispositivos geridos](android-fully-managed-enroll.md) e [inscrever o seu dispositivos dedicados ou dispositivos totalmente gerenciados](android-dedicated-devices-fully-managed-enroll.md).  Tenha em atenção que esta funcionalidade está em pré-visualização. Algumas funcionalidades do Intune, tais como certificados, conformidade e acesso condicional, não estão atualmente disponíveis com o Android totalmente geridos os dispositivos dos utilizadores.

<!-- ########################## -->
## <a name="week-of-january-7-2019"></a>Semana de 7 de Janeiro de 2019

### <a name="app-management"></a>Gestão de aplicações

#### <a name="intune-app-pin----2298397---"></a>PIN da aplicação Intune <!-- 2298397 -->
O administrador de TI, pode agora configurar o número de dias que um utilizador final pode aguardar até ser preciso Alterar PIN da aplicação Intune. É a nova definição *reposição após número de dias do PIN* e está disponível no portal do Azure ao selecionar **Intune** > **aplicações de cliente**  >   **Políticas de proteção de aplicações** > **criar política** > **definições** > **aceder aos requisitos de**. Disponível para [iOS](app-protection-policy-settings-ios.md) e [Android](app-protection-policy-settings-android.md) dispositivos, esse recurso oferece suporte a um valor de número inteiro positivo.


#### <a name="intune-device-reporting-fields----2748738---"></a>Campos de relatórios de dispositivos do Intune <!-- 2748738 -->
O Intune fornece relatórios campos, incluindo o Id de registo de aplicação, fabricante do Android, modelo e versão de patch de segurança, bem como o modelo de iOS adicionais do dispositivo. No Intune, estes campos estão disponíveis, selecionando **aplicações de cliente** > **estado de proteção de aplicações** e escolha **relatório de proteção de aplicações: iOS, Android**. Além disso, esses parâmetros irão ajudá-lo a configurar o **permitir** lista para o fabricante do dispositivo (Android), o **permitir** lista para o modelo do dispositivo (Android e iOS) e o patch de segurança mínima para Android definição de versão. 


### <a name="device-configuration"></a>Configuração do dispositivo

#### <a name="administrative-templates-are-in-public-preview-and-moved-to-their-own-configuration-profile----3322847---"></a>Modelos administrativos estão em pré-visualização pública e movido para o seu próprio perfil de configuração <!-- 3322847 -->

Modelos administrativos no Intune (**configuração do dispositivo** > **modelos administrativos**) estão atualmente em pré-visualização privada. Com esta atualização:

- Modelos administrativos incluem aproximadamente 300 definições que podem ser geridas no Intune. Anteriormente, estas definições só existiam no editor de políticas de grupo.
- Modelos administrativos estão disponíveis em pré-visualização pública.
- Estiver a mover de modelos administrativos **configuração do dispositivo** > **modelos administrativos** para **configuração do dispositivo**  >   **Perfis** > **criar perfil** > no **plataforma**, selecione **Windows 10 e posterior** > no **perfil tipo**, escolha **modelos administrativos**.
- O relatório está ativado

Para ler mais sobre esta funcionalidade, aceda a [modelos do Windows 10 para configurar as definições de política de grupo](administrative-templates-windows.md).

Aplica-se a: Windows 10 e posterior

#### <a name="use-smime-to-encrypt-and-sign-multiple-devices-for-a-user-----1333642---"></a>Utilizar S/MIME para encriptar e assinar vários dispositivos para um utilizador  <!-- 1333642 -->
Esta atualização inclui a encriptação de e-mails com S/MIME através de um novo perfil de certificado importado (**Configuração do dispositivo** > **Perfis** > **Criar perfil** > selecione a plataforma > tipo de perfil **Certificados PKCS importados**). No Intune, pode importar certificados no formato PFX. O Intune pode enviar esses mesmos certificados para múltiplos dispositivos inscritos por um único utilizador. Isto também inclui:
- O perfil de e-mail nativo do iOS suporta a ativação da encriptação S/MIME através de certificados importados no formato PFX.
- A aplicação de e-mail nativa dos dispositivos Windows Phone 10 utiliza automaticamente o certificado S/MIME.
- Os certificados privados podem ser fornecidos a várias plataformas. No entanto, nem todas as aplicações de e-mail suportam S/MIME.
- Noutras plataformas, talvez seja necessário configurar manualmente a aplicação de e-mail para permitir o S/MIME.  
- As aplicações de e-mail que suportam a encriptação S/MIME conseguem obter certificados para a encriptação S/MIME de e-mails de uma forma que não é suportada por MDM, como a leitura a partir do arquivo de certificados do respetivo publicador.
Para obter mais informações sobre esta funcionalidade, consulte [descrição geral de S/MIME para assinar e encriptar e-mail](certificates-s-mime-encryption-sign.md).
Suportado no: Windows Phone 10, Windows, iOS, Android e macOS

#### <a name="new-options-to-automatically-connect-and-persist-rules-when-using-dns-settings-on-windows-10-and-later-devices----1333665-2999078---"></a>Novas opções para automaticamente se ligar e manter regras ao utilizar as definições de DNS no Windows 10 e dispositivos posteriores <!-- 1333665, 2999078 -->
No Windows 10 e dispositivos posteriores, pode criar um perfil de configuração de VPN que inclui uma lista de servidores DNS para resolver domínios, tal como contoso.com. Esta atualização inclui novas definições para resolução de nomes (**configuração do dispositivo** > **perfis** > **criar perfil** > Escolha  **Windows 10 e posterior** para a plataforma > Escolha **VPN** para o tipo de perfil > **definições de DNS** >**adicionar**): 
- **Ligar automaticamente**: Quando **ativado**, o dispositivo estabelece ligação automaticamente para a VPN quando um dispositivo entra em contacto com um domínio, introduza, por exemplo, contoso.com.
- **Persistente**: Por predefinição, todas as regras de tabela (NRPT) de política de resolução de nome estão ativas, desde que o dispositivo estiver conectado com este perfil VPN. Quando esta definição for **ativado** numa regra NRPT, a regra permanece ativa no dispositivo, mesmo quando desliga a VPN. A regra permanece até que o perfil VPN é removido ou até que a regra é manualmente removida, que pode ser feito com o PowerShell.
[Definições de VPN do Windows 10](vpn-settings-windows-10.md) descreve as definições. 

#### <a name="use-trusted-network-detection-for-vpn-profiles-on-windows-10-devices----1500165---"></a>Utilizar a deteção de rede fidedigna para perfis VPN em dispositivos Windows 10 <!-- 1500165 -->
Ao utilizar a deteção de rede fidedigna, pode impedir que os perfis VPN crie automaticamente uma ligação VPN quando o utilizador já se encontra numa rede fidedigna. Com esta atualização, pode adicionar sufixos DNS para ativar a deteção de rede fidedigna em dispositivos com Windows 10 e posterior (**configuração do dispositivo** > **perfis**  >  **Criar perfil** > **Windows 10 e posterior** para a plataforma > **VPN** para tipo de perfil).
[Definições de VPN do Windows 10](vpn-settings-windows-10.md) lista as definições de VPN atuais.

#### <a name="manage-windows-holographic-for-business-devices-used-by-multiple-users----1907917-1063203---"></a>Gerir Windows Holographic for Business dispositivos usados por vários utilizadores <!-- 1907917, 1063203 -->
Atualmente, pode configurar definições do PC compartilhadas no Windows 10 e Windows Holographic for Business dispositivos com uma definição de OMA-URI personalizada. Com esta atualização, é adicionado um novo perfil para configurar definições de dispositivos partilhados (**configuração do dispositivo** > **perfis** > **criar perfil do**  >  **Windows 10 e posterior** > **dispositivos de vários utilizadores partilhado**).
Para saber mais sobre esta funcionalidade, aceda à [definições do Intune para gerir dispositivos partilhados](shared-user-device-settings.md).
Aplica-se a: Windows 10 e posterior, Windows Holographic for Business

#### <a name="new-windows-10-update-settings---2626030--2512994----"></a>Novas definições de atualização do Windows 10 <!--2626030  2512994  -->
Para sua [Cadências de atualização do Windows 10](windows-update-for-business-configure.md), pode configurar:
- **Comportamento de atualização automática** -utilize uma nova opção *repor para predefinição* para restaurar as definições de atualização automática original numa máquina de Windows 10 em computadores que executam o *atualização de Outubro de 2018*
- **Impedir o utilizador de atualizações do Windows a colocar em pausa** -configurar um novo Software de atualizações de definição que permite-lhe bloquear ou permitir que os utilizadores para a instalação da atualização de colocar em pausa a *definições* das suas máquinas. 

#### <a name="ios-email-profiles-can-use-smime-signing-and-encryption----2662949---"></a>perfis de e-mail do iOS podem utilizar a encriptação e assinatura S/MIME <!-- 2662949 -->
Pode criar um perfil de e-mail que inclui definições diferentes. Esta atualização inclui definições de S/MIME que podem ser utilizadas para assinar e criptografar as comunicações por e-mail em dispositivos iOS (**configuração do dispositivo** > **perfis**  >  **Criar perfil** > Escolha **iOS** para a plataforma > **E-Mail** para tipo de perfil).
[definições de configuração de e-mail do iOS](email-settings-ios.md) lista as definições.

#### <a name="some-bitlocker-settings-support-windows-10-pro-edition---2727036---"></a>Algumas definições de BitLocker suportam a edição Windows 10 Pro<!-- 2727036 -->
Pode criar um perfil de configuração que define as definições do endpoint protection em dispositivos Windows 10, inclusive BitLocker. Esta atualização adiciona suporte para a edição Windows 10 Professional para algumas configurações de disco BitLocker. Para ver estas definições de proteção, aceda à [definições do Endpoint protection para Windows 10](endpoint-protection-windows-10.md#windows-encryption).

#### <a name="shared-device-configuration-is-renamed-to-lock-screen-message-for-ios-devices-in-the-azure-portal---2809362---"></a>Configuração de dispositivos partilhados foi mudada para mensagem de ecrã de bloqueio para dispositivos iOS no portal do Azure<!-- 2809362 -->
Quando cria um perfil de configuração para dispositivos iOS, pode adicionar **configuração de dispositivos partilhados** definições para mostrar o texto específico no ecrã de bloqueio. Esta atualização inclui as seguintes alterações: 
- O **configuração de dispositivos partilhados** definições no portal do Azure são o nome mudadas para "Mensagem de ecrã de bloqueio (apenas supervisionada)" (**configuração do dispositivo** > **perfis**  >  **Criar perfil** > Escolha **iOS** para a plataforma > Escolha **funcionalidades do dispositivo** para o tipo de perfil > **bloqueio Mensagem de ecrã**).
- Ao adicionar mensagens de ecrã de bloqueio, pode inserir um número de série, um nome de dispositivo ou outro valor específicos do dispositivo como uma variável no **informações da etiqueta de recursos** e **nota de rodapé de ecrã de bloqueio**. Por exemplo, pode introduzir `Device name: {{devicename}}` ou `Serial number is {{serialnumber}}` usando chaves de saída. [iOS tokens](app-configuration-policies-use-ios.md#tokens-used-in-the-property-list) apresenta uma lista de tokens disponíveis que podem ser utilizados.
[Definições para apresentar mensagens no ecrã de bloqueio](shared-device-settings-ios.md) lista as definições.

#### <a name="new-app-store-doc-viewing-gaming-device-restriction-settings-added-to-ios-devices----2827760--"></a>Novo App Store, visualização de documentos, definições de restrição de dispositivos de jogos adicionadas para dispositivos iOS <!-- 2827760-->
Na **configuração do dispositivo** > **perfis** > **criar perfil** > **iOS** para Plataforma > **restrições de dispositivos** para o tipo de perfil > **App Store, visualização de documentos, jogos**, são adicionadas as seguintes definições: Permitir que aplicações geridas escrever contactos para contas de não-gerenciado contactos aplicações permitir não gerido para ler contactos geridos de contas para ver estas definições, vá para de [restrições de dispositivos iOS](device-restrictions-ios.md#app-store-doc-viewing-gaming).

#### <a name="new-notification-hints-and-keyguard-settings-to-android-enterprise-device-owner-devices----3201839-3201843---"></a>Novas definições de notificação, sugestões e keyguard para dispositivos de proprietário do dispositivo Android Enterprise <!-- 3201839 3201843 -->
Esta atualização inclui várias novas funcionalidades em dispositivos Android Enterprise quando em execução como proprietário do dispositivo. Para utilizar estas funcionalidades, aceda a **configuração do dispositivo** > **perfis** > **criar perfil** > no **plataforma**, escolha **Android Enterprise** > no **tipo de perfil**, escolha **proprietário do dispositivo só** > **dispositivo Restrições**.

Os novos recursos incluem: 

- Desative notificações de sistema do que mostra, incluindo a entrada chamadas, alertas do sistema, erros de sistema e muito mais.
- Sugere a ignorar a partir de tutoriais e dicas para aplicações que são abertas pela primeira vez.
- Desative keyguard avançada desbloquear as definições, tais como a câmara, notificações, impressão digital e muito mais.


Para ver as definições, aceda à [definições de restrição de dispositivos Android Enterprise](device-restrictions-android-for-work.md).

#### <a name="android-enterprise-device-owner-devices-can-use-always-on-vpn-connections----3202194---"></a>Dispositivos de proprietário de dispositivos empresariais Android podem utilizar ligações de VPN AlwaysOn <!-- 3202194 -->
Nesta atualização, pode utilizar ligações VPN sempre ativada nos dispositivos de proprietário do dispositivo Android empresarial. As ligações VPN Sempre Ativada permanecem ativadas ou voltam a ativar-se quando o utilizador desbloqueia o dispositivo, quando o dispositivo é reiniciado ou quando a rede sem fios é alterada. Também pode colocar a ligação em modo de "bloqueio". Este modo permite bloquear todo o tráfego de rede até à ativação da ligação de VPN.
Pode ativar a VPN sempre ativada no **configuração do dispositivo** > **perfis** > **criar perfil**  >   **Android enterprise** para a plataforma > **restrições de dispositivos** para o proprietário do dispositivo só > **conectividade** definições. Para ver as definições, aceda à [definições de restrição de dispositivos Android Enterprise](device-restrictions-android-for-work.md).

#### <a name="new-setting-to-end-processes-in-task-manager-on-windows-10-devices----3285177---"></a>Nova definição para processos de fim no Gerenciador de tarefas em dispositivos Windows 10 <!-- 3285177 --> 
Esta atualização inclui uma nova definição para terminar a processos usando o Gerenciador de tarefas em dispositivos Windows 10. Utilizar um perfil de configuração do dispositivo (**configuração do dispositivo** > **perfis** > **criar perfil** > no **plataforma** , escolha **Windows 10** > no **tipo de perfil**, escolha **restrições de dispositivos** > **geral** definições), optar por permitir ou impedir que esta definição.
Para ver estas definições, aceda à [definições de restrição de dispositivos Windows 10](device-restrictions-windows-10.md).
Aplica-se a: Windows 10 e posterior


### <a name="device-enrollment"></a>Inscrição de dispositivos

#### <a name="more-detailed-enrollment-restriction-failure-messaging----3111564---"></a>Mais mensagens de falha de restrição de inscrição <!-- 3111564 -->
Mensagens de erro mais detalhadas estão disponíveis quando restrições de inscrição não forem cumpridas. Para ver estas mensagens, aceda à **Intune** > **resolução de problemas** > e consulte a tabela de falhas de inscrição. Para obter mais informações, consulte a [lista de falhas de inscrição](help-desk-operators.md#configuration-policies-reference).



### <a name="monitor-and-troubleshoot"></a>Monitorizar e resolver problemas

#### <a name="tenant-status-dashboard-----1124854---"></a>Dashboard de estado do inquilino  <!-- 1124854 -->
A nova [página de estado do inquilino](tenant-status.md) fornece um único local onde pode ver o estado e os detalhes relacionados para o seu inquilino.  O dashboard está dividido em quatro áreas:
- **Detalhes de inquilino** -apresenta informações que inclui o nome de inquilino e a localização, a autoridade de MDM, o total nos dispositivos inscritos no seu inquilino e a conta de sua licença. Esta secção também apresenta a versão atual do serviço para o seu inquilino.
- **Estado do conector** -apresenta informações sobre conectores disponíveis que configurou e também pode listar os que ainda não tiver ativado.  
   Com base no estado atual de cada conector, eles são sinalizados como bom estado de funcionamento, aviso ou mau estado de funcionamento. Selecione um conector para explorar e ver detalhes ou configurar as informações adicionais para o mesmo.
-  **Estado de funcionamento do serviço Intune** -apresenta detalhes sobre incidentes activos ou falhas para o seu inquilino. As informações nesta secção são obtidas diretamente a partir do Centro de mensagens do Office.
-  **Notícias do Intune** -exibe mensagens de Active Directory para o seu inquilino. As mensagens incluem opções como notificações quando o seu inquilino recebe as mais recentes funcionalidades do Intune.  As informações nesta secção são obtidas diretamente a partir do Centro de mensagens do Office.

#### <a name="new-help-and-support-experience-in-company-portal-for-windows-10----1488939--"></a>Novo ajuda e suporte de experiência no Portal da empresa para Windows 10 <!-- 1488939-->
A nova página de ajuda de Portal da empresa e suporte ajuda os utilizadores a resolver problemas e pedir ajuda para problemas de acesso e aplicação. Na página nova, podem enviar por e-mail os detalhes de registo de diagnóstico e de erro e encontrar os detalhes de suporte técnico da sua organização. Eles também encontrará uma secção de FAQ com ligações para documentação relevante do Intune. 

#### <a name="new-help-and-support-experience-for-intune------3307080---"></a>Ajuda e suporte da nova experiência para o Intune   <!-- #3307080 -->
Estamos a implementar a nova experiência de ajuda e suporte para todos os inquilinos ao longo do daqui a alguns dias. Esta nova experiência está disponível para o Intune e podem ser acessada ao utilizar os painéis do Intune no [portal do Azure](https://portal.azure.com/).
A nova experiência permite-lhe descrever o seu problema pelas suas próprias palavras e receber informações de resolução de problemas e conteúdos de remediação baseados na Web. Estas soluções são oferecidas por meio de uma máquina com base na regra de algoritmo, orientado por utilizador de aprendizagem consultas. Além das orientações específicas do problema, utilize o novo fluxo de trabalho de criação de casos para abrir um incidente de suporte por e-mail ou telefone. Esta nova experiência substitui a experiência de ajuda e suporte anterior de um conjunto estático de opções previamente selecionadas que são baseiam-se a área da consola que estiver ao abrir a ajuda e suporte. Para obter mais informações, consulte [como obter suporte para o Microsoft Intune](get-support.md).

### <a name="role-based-access-control"></a>Controlo de acesso baseado em funções

#### <a name="scope-tags-for-apps----1081941---"></a>Etiquetas de âmbito para aplicações <!-- 1081941 -->
Pode criar etiquetas de âmbito para limitar o acesso para aplicações e funções. Pode adicionar uma etiqueta de âmbito a uma aplicação para que apenas as pessoas com funções atribuídas também essa etiqueta de âmbito tenham acesso à aplicação. Atualmente, aplicações que adicionar ao Intune a partir do Google Play gerido ou aplicações adquiridas através do Apple Volume Purchase Program (VPP) não não possível atribuir etiquetas de âmbito (mas suporte virão no futuro). Para obter mais informações, consulte [utilizar etiquetas de âmbito para políticas de filtro](scope-tags.md).

<!-- ########################## -->
## <a name="week-of-december-10-2018"></a>Semana de 10 de Dezembro de 2018

### <a name="app-management"></a>Gestão de aplicações

#### <a name="updates-for-application-transport-security----748318---"></a>Atualizações de segurança de transporte de aplicações <!-- 748318 -->

O Microsoft Intune suporta Transport Layer Security (TLS) 1.2 + para fornecer encriptação de melhor em classe, para garantir que o Intune é mais seguro por padrão e para se alinhar com outros serviços Microsoft como o Microsoft Office 365. Para cumprir este requisito, portais de empresa do iOS e macOS irão impor requisitos de segurança de transporte de aplicações (ATS) atualizados da Apple, que também necessitam de TLS 1.2 +. A ATS é utilizada para impor medidas de segurança mais rigorosas em todas as comunicações feitas por aplicações através de HTTPS. Esta alteração irá afetar os clientes do Intune a utilizar as aplicações de Portal da empresa iOS e macOS. Para obter mais informações, consulte a [blogue de suporte do Intune](https://aka.ms/compportalats).

#### <a name="the-intune-app-sdk-will-support-256-bit-encryption-keys----1832174---"></a>O SDK da aplicação Intune irá suportar as chaves de encriptação de 256 bits <!-- 1832174 -->
O SDK da aplicação Intune para Android utiliza agora as chaves de encriptação de 256 bits quando a encriptação está ativada por políticas de proteção de aplicações. O SDK irá continuar a fornecer suporte de chaves de 128 bits para compatibilidade com o conteúdo e aplicações que utilizam versões mais antigas do SDK.

### <a name="microsoft-auto-update-version-450-required-for-macos-devices----3503442---"></a>Versão de atualização automática de Microsoft 4.5.0 necessária para dispositivos macOS <!-- 3503442 -->
Para continuar a receber atualizações para o Portal da empresa e outros aplicativos do Office, dispositivos macOS geridos pelo Intune tem de atualizar para a atualização automática do Microsoft 4.5.0. Os utilizadores poderão já ter esta versão para seus aplicativos do Office.

### <a name="intune-requires-macos-1012-or-later----2827778---"></a>O Intune necessita de macOS 10.12 ou posterior <!-- 2827778 -->
O Intune requer agora macOS versão 10.12 ou posterior. Dispositivos com versões anteriores do macOS não é possível utilizar o Portal da empresa para inscrição no Intune. Para receber suporte e novos recursos, os utilizadores tem de atualizar o dispositivo para macOS 10.12 ou posterior e atualize o Portal da empresa para a versão mais recente.

<!-- ########################## -->
## <a name="week-of-november-26-2018"></a>Semana de 26 de Novembro de 2018

### <a name="app-management"></a>Gestão de aplicações

#### <a name="uninstalling-apps-on-corporate-owned-supervised-ios-devices----1281677---"></a>Desinstalar aplicações em dispositivos iOS supervisionados pertencentes à empresa <!-- 1281677 -->

Pode remover todas as aplicações em dispositivos iOS supervisionados pertencente à empresa. Pode remover qualquer aplicação ao visar os grupos de utilizadores ou dispositivos com um tipo de atribuição **Desinstalar**. Para dispositivos iOS pessoais ou não supervisionados, continuará a poder remover apenas as aplicações que foram instaladas com o Intune.

#### <a name="downloading-intune-win32-app-content----2617320---"></a>Transferir o conteúdo da aplicação Intune Win32 <!-- 2617320 -->
Windows 10 RS3 e aos clientes acima irá transferir o conteúdo da aplicação Intune Win32 usando um componente de Otimização da entrega no cliente Windows 10. Otimização da entrega fornece uma funcionalidade de ponto-a-ponto que ele está ativado por predefinição. Otimização da entrega pode ser configurada pela política de grupo e no futuro através de MDM do Intune. Para obter mais informações, consulte [otimização de entrega para o Windows 10](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization). 

#### <a name="end-user-device-and-app-content-menu----2771453---"></a>Menu de contexto em aplicações e dispositivos de utilizadores finais <!-- 2771453 -->
Os usuários finais agora pode utilizar o menu de contexto em aplicações e dispositivos para acionar ações comuns, como mudar o nome de um dispositivo ou a verificação de conformidade.

#### <a name="set-custom-background-in-managed-home-screen-app-----3041945---"></a>Configurar o fundo personalizado na aplicação Ecrã Inicial Gerido <!-- 3041945 -->
Estamos a adicionar uma definição que permite-lhe personalizar a aparência de plano de fundo da aplicação gerida tela home page no Android Enterprise, várias aplicações, dispositivos de modo de local público.  Para configurar o **Fundo do URL personalizado**, aceda ao Intune no portal do Azure > Configuração do dispositivo. Selecione um perfil de configuração de dispositivo atual ou crie um novo para editar as respetivas definições de quiosque.
Para ver as definições de local público, consulte [restrições de dispositivos Android Enterprise](device-restrictions-android-for-work.md).

#### <a name="app-protection-policy-assignment-save-and-apply----3104570---"></a>Guardar e aplicar a atribuição da política de proteção de aplicações <!-- 3104570 -->
Agora tem um melhor controle sobre sua [atribuições de política de proteção de aplicações](app-protection-policies.md#deploy-a-policy-to-users). Quando seleciona *atribuições* para definir ou editar as atribuições de uma política, deve **guardar** sua configuração antes da alteração aplica-se. Uso **descartar** para limpar todas as alterações fizer sem guardar as alterações para a inclusão ou exclusão apresenta uma lista.  Ao exigir que guarde ou rejeição, apenas os utilizadores que pretende são atribuídos uma política de proteção de aplicações.

#### <a name="new-microsoft-edge-browser-settings-for-windows-10-and-later----3174639---"></a>Novas definições do browser Microsoft Edge para Windows 10 e posterior <!-- 3174639 -->
Esta atualização inclui novas definições para ajudar a controlar e gerir o browser Microsoft Edge nos seus dispositivos. Para obter uma lista destas definições, consulte [restrição de dispositivos para Windows 10 (e versões posteriores)](device-restrictions-windows-10.md#microsoft-edge-browser).

#### <a name="new-apps-support-with-app-protection-policies----3330037---"></a>Suportam a novas aplicações com políticas de proteção de aplicações <!-- 3330037 -->
Agora pode gerir as seguintes aplicações com [políticas de proteção de aplicações do Intune](app-protection-policies.md):
- Stream (iOS)
- Para fazer (Android, iOS)
- PowerApps (Android, iOS)
- Fluxo (Android, iOS)

Utilize políticas de proteção de aplicações para proteger a empresa transferência de dados e controle de dados para estas aplicações, como outra aplicações geridas por políticas do Intune. Nota: Se o fluxo ainda não estiver visível na consola, adicionar fluxo quando criar ou editar e políticas de proteção de aplicações. Para tal, utilize o **+ mais aplicações** opção e, em seguida, especifique a *ID de aplicação* do Flow no campo de entrada. Para Android utilizam *com.microsoft.flow*, e para iOS utilize *com.microsoft.procsimo*.


### <a name="device-configuration"></a>Configuração do dispositivo

#### <a name="ios-and-macos-version-numbers-and-build-numbers-are-shown----1892471---"></a>Os números de compilação e da versão do iOS e macOS são apresentados <!-- 1892471 -->
Em **Conformidade do dispositivo** > **Conformidade do dispositivo**, são apresentadas as versões dos sistemas operativos iOS e macOS. Estas versões estão disponíveis para serem utilizadas nas políticas de conformidade. Esta atualização inclui o número de compilação, o que é configurável para ambas as plataformas.
Quando as atualizações de segurança são lançadas, normalmente, a Apple não altera o número da versão, mas atualiza o número de compilação. Ao utilizar o número de compilação numa política de conformidade, pode verificar facilmente se foi instalada uma atualização da vulnerabilidade.
Para utilizar esta funcionalidade, consulte [iOS](compliance-policy-create-ios.md#device-health) e [macOS](compliance-policy-create-mac-os.md#device-properties) políticas de conformidade.

#### <a name="update-rings-are-being-replaced-with-delivery-optimization-settings-for-windows-10-and-later----2753807---"></a>Cadências de atualização estão a ser substituídas com as definições de otimização de entrega para o Windows 10 e posterior <!-- 2753807 -->
Otimização da entrega é um novo perfil de configuração para Windows 10 e posterior. Esta funcionalidade fornece uma experiência mais simplificada para fornecer atualizações de software para dispositivos na sua organização. Esta atualização também ajuda a fornecer as definições de cadências de atualização de novas e existentes com um perfil de configuração.
Para configurar um perfil de configuração de otimização de entrega, consulte [as definições de otimização do Windows 10 (e mais recente) entrega](delivery-optimization-windows.md).

#### <a name="new-device-restriction-settings-added-to-ios-and-macos-devices----2827760---"></a>Novas definições de restrição de dispositivos adicionadas a dispositivos iOS e macOS <!-- 2827760 -->
Esta atualização inclui novas definições para os seus dispositivos iOS e macOS que são lançadas com o iOS 12:

**definições do iOS**: 
- Gerais: Remoção de aplicações de bloco (apenas supervisionada)
- Gerais: Modo de bloco USB restrito (apenas supervisionado)
- Gerais: Forçar automática data e hora (apenas supervisionado)
- Palavra-passe: Bloquear a palavra-passe de preenchimento automático (apenas supervisionado)
- Palavra-passe: Bloquear pedidos de proximidade de palavra-passe (apenas supervisionados)
- Palavra-passe: Bloquear a partilha de palavra-passe (apenas supervisionado)

**definições do macOS**: 
- Palavra-passe: Bloquear o preenchimento automático de palavra-passe
- Palavra-passe: Bloquear pedidos de proximidade de palavra-passe
- Palavra-passe: Bloquear a partilha de palavra-passe

Para saber mais sobre estas definições, consulte [iOS](device-restrictions-ios.md) e [macOS](device-restrictions-macos.md) definições de restrição de dispositivos.

### <a name="device-enrollment"></a>Inscrição de dispositivos

#### <a name="select-apps-tracked-on-the-enrollment-status-page---2531007---"></a>Selecionar aplicações monitorizadas na Página de Estado de Inscrição<!-- 2531007 -->
Pode escolher as aplicações que são controladas na página de estado de inscrição. Até que estas aplicações são instaladas, o utilizador não é possível utilizar o dispositivo. Para obter mais informações, consulte [configurar uma página de estado de inscrição](windows-enrollment-status.md).

#### <a name="search-for-autopilot-device-by-serial-number---2595788---"></a>Procurar dispositivos Autopilot por número de série <!--2595788 -->
Agora pode procurar por dispositivos Autopilot por número de série. Para tal, escolha **inscrição de dispositivos** > **inscrição Windows** > **dispositivos** > Escreva um número de série no **pesquisar por número de série** caixa > prima Enter.

#### <a name="track-installation-of-office-proplus---2620217---"></a>Monitorizar a instalação do Office ProPlus <!--2620217 -->
Os usuários podem controlar o progresso da instalação [Office ProPlus](apps-add-office365.md) utilizando o [página de estado de inscrição](windows-enrollment-status.md). Para obter mais informações, consulte [configurar uma página de estado de inscrição](windows-enrollment-status.md).

#### <a name="alerts-for-expiring-vpp-token-or-company-portal-license-running-low----2237572---"></a>Alertas de token VPP prestes a expirar ou de licenças do Portal da Empresa que se estão a esgotar <!-- 2237572 -->
Se estiver a utilizar o Volume Purchase Program (VPP) para pré-aprovisionar o Portal da empresa durante a inscrição de DEP, o Intune irá alertá-lo quando o token VPP está prestes a expirar e quando há pouca as licenças para o Portal da empresa.

### <a name="macos-device-enrollment-program-support-for-apple-school-manager-accounts---3006133---"></a>Suporte do Programa de Registo de Aparelho do macOS para as contas do Apple School Manager <!--3006133 -->
Intune agora suporta através do programa de inscrição de dispositivos em dispositivos macOS para contas de Gestor de escola da Apple.  Para obter mais informações, consulte [inscrever automaticamente dispositivos macOS com o Apple School Manager ou o programa de inscrição de dispositivos](device-enrollment-program-enroll-macos.md).

### <a name="new-intune-device-subscription-sku---3312071--"></a>Nova subscrição de dispositivo do Intune SKU <!--3312071-->
Para ajudar a reduzir o custo associado à gestão de dispositivos nas empresas, está agora disponível um novo SKU de subscrição baseado em dispositivos. Este SKU de dispositivos do Intune possui uma licença mensal por dispositivo. Os preços variam em função do programa de licenciamento. Está disponível diretamente por meio de portal de administração do Office e o [contrato Enterprise](https://www.microsoft.com/licensing/licensing-programs/enterprise?activetab=enterprise-tab:primaryr2) (EA), [Products da Microsoft e o contrato de serviços](https://www.microsoft.com/licensing/mpsa/default) (MPSA), [contratos aberto da Microsoft ](https://partner.microsoft.com/licensing/licensing-agreements), e [fornecedor de solução de Cloud](https://www.microsoftpartnercommunity.com/t5/Partnership-101/What-is-the-Cloud-Solution-Provider-CSP-program/td-p/2453) (CSP).

### <a name="device-management"></a>Gestão de dispositivos

#### <a name="temporarily-pause-kiosk-mode-on-android-devices-to-make-changes----3041935---"></a>Interromper temporariamente o modo de quiosque em dispositivos Android para fazer alterações <!-- 3041935 -->
Ao utilizar dispositivos Android no modo de quiosque de múltiplas aplicações, um administrador de TI poderá ter de fazer alterações ao dispositivo. Esta atualização inclui novas definições de local público de várias aplicações que permite que um administrador de TI temporariamente a colocar em pausa a utilização de um PIN de modo de local público e obtenha acesso a todo o dispositivo.
Para ver as definições de local público, consulte [restrições de dispositivos Android Enterprise](device-restrictions-android-for-work.md).

#### <a name="enable-virtual-home-button-on-android-enterprise-kiosk-devices-----3042021---"></a>Ativar o botão Home virtual em dispositivos de quiosque Android Enterprise <!-- 3042021 -->
Uma nova definição permitirá que os utilizadores toquem num botão de tecla de função no respetivo dispositivo para alternar entre a aplicação Ecrã Inicial Gerido e outras aplicações atribuídas no respetivo dispositivo de quiosque de múltiplas aplicações. Esta definição é particularmente útil em cenários onde a aplicação de quiosque do utilizador não responde adequadamente ao botão "retroceder". Poderá configurar esta definição para dispositivos Android de utilização única, pertencentes à empresa. Para ativar ou desativar o **botão Home virtual**, aceda ao Intune no portal do Azure > Configuração do dispositivo. Selecione um perfil de configuração de dispositivo atual ou crie um novo para editar as respetivas definições de quiosque.
Para ver as definições de local público, consulte [restrições de dispositivos Android Enterprise](device-restrictions-android-for-work.md).

<!-- ########################## -->
## <a name="week-of-november-12-2018"></a>Semana de 12 de Novembro de 2018

### <a name="network-access-control-nac-support-for-citrix-sso-for-ios----3259404---"></a>Suporte de Access Control (NAC) para Citrix SSO para iOS de rede <!-- 3259404 -->

Citrix lançou uma atualização para o Gateway da Citrix para permitir o controlo de acesso de rede (NAC) para Citrix SSO para iOS no Intune. Pode optar por incluir um ID de dispositivo de um perfil VPN no Intune e, em seguida, enviar este perfil para seus dispositivos iOS. Terá de instalar a atualização mais recente para o Gateway da Citrix para utilizar esta funcionalidade.

[Configurar definições de VPN em dispositivos iOS](vpn-settings-ios.md#base-vpn-settings) fornece mais informações sobre como usar o NAC, incluindo alguns requisitos adicionais. 

<!-- ########################## -->
## <a name="week-of-november-5-2018"></a>Semana de 5 de novembro de 2018

### <a name="support-for-ios-12-oauth-in-ios-email-profiles---2155106---"></a>Suporte para o OAuth do iOS 12 nos perfis de e-mail iOS <!--2155106 -->

Os perfis de e-mail iOS do Intune suportam o Open Authorization (OAuth) do iOS 12. Para ver esta funcionalidade, crie um novo perfil (**Configuração do Dispositivo** > **Perfis** > **Criar perfil**  >  **iOS** para a plataforma > **E-mail** para o tipo de perfil) ou atualize um perfil de e-mail iOS existente. Se ativar o OAuth num perfil que já foi implementado para utilizadores, será pedido aos utilizadores que autentiquem e transfiram novamente o respetivo e-mail.

Pode obter mais informações sobre como utilizar o OAuth num perfil de e-mail em [iOS email profiles](email-settings-ios.md) (Perfis de e-mail iOS).

### <a name="autopilot-support-for-hybrid-azure-active-directory-joined-devices-preview----1048100--"></a>Suporte do Autopilot para dispositivos associados ao Azure Active Directory híbrido (Pré-visualização) <!-- 1048100-->
Agora pode configurar dispositivos associados ao Azure Active Directory híbrido com o Autopilot. Os dispositivos têm de ser associados à rede da sua organização para utilizar a funcionalidade Autopilot híbrida. Para obter mais informações, veja [Implementar dispositivos associados ao Azure Active Directory híbrido com o Intune e o Windows Autopilot](windows-autopilot-hybrid.md).
Esta funcionalidade será implementada para a base de utilizadores nos próximos dias. Assim, poderá não conseguir seguir estes passos até que a mesma seja implementada na sua conta.

<!-- ########################## -->
## <a name="week-of-october-29-2018"></a>Semana de 29 de outubro de 2018

### <a name="app-management"></a>Gestão de aplicações

#### <a name="require-non-biometric-pin-after-a-specified-timeout----1506985---"></a>Exigir um PIN não biométrico após um tempo limite especificado <!-- 1506985 -->
Ao exigir um PIN não biométrico após um tempo limite especificado pelo administrador, o Intune fornece segurança melhorada para aplicações com Gestão de Aplicações Móveis (MAM) ativada ao restringir a utilização da identificação biométrica para aceder a dados da empresa. As definições afetam os utilizadores que dependem do Touch ID (iOS), Face ID (iOS), Android Biometric ou outros métodos de autenticação biométricos futuros para aceder a aplicações com APP/MAM ativada. Estas definições permitem que os administradores do Intune tenham um controlo mais abrangente sobre o acesso do utilizador, ao eliminar os casos em que um dispositivo com múltiplas impressões digitais ou outros métodos de acesso biométrico pode revelar dados da empresa a um utilizador errado. No portal do Azure, abra o **Microsoft Intune**. Selecione **Aplicações do cliente** > **Políticas de proteção de aplicações** > **Adicionar uma política** > **Definições**. Localize a secção **Acesso** para obter definições específicas. Para obter informações sobre as definições de acesso, veja as [definições do iOS](app-protection-policy-settings-ios.md#access-requirements) e as [definições do Android](app-protection-policy-settings-android.md#access-requirements).

#### <a name="intune-app-data-transfer-settings-on-ios-mdm-enrolled-devices----2244713---"></a>Definições de transferência de dados de aplicações do Intune em dispositivos iOS inscritos na MDM <!-- 2244713 -->
Pode separar o controlo das definições de transferência de dados de aplicações do Intune em dispositivos iOS inscritos na MDM da especificação da identidade do utilizador inscrito, também conhecida como Nome Principal de Utilizador (UPN). Os administradores que não utilizarem o IntuneMAMUPN não notarão a existência de uma alteração de comportamento. Quando esta funcionalidade estiver disponível, os administradores que utilizam o IntuneMAMUPN para controlar o comportamento de transferência de dados em dispositivos inscritos devem rever as novas definições e atualizar as respetivas definições das aplicações conforme necessário.

#### <a name="windows-10-win32-apps----2617325---"></a>Aplicações Win32 do Windows 10 <!-- 2617325 -->
Pode configurar as suas aplicações Win32 para que sejam instaladas no contexto de utilizador para utilizadores individuais ou para todos os utilizadores do dispositivo.

#### <a name="windows-win32-apps-and-powershell-scripts----2617330---"></a>Aplicações Win32 do Windows e scripts do PowerShell <!-- 2617330 -->
Os utilizadores finais já não necessitam de ter sessão iniciada no dispositivo para instalarem aplicações Win32 ou executarem scripts do PowerShell. 

#### <a name="troubleshooting-client-app-installation----1363711---"></a>Resolução de problemas relativos à instalação da aplicação cliente <!-- 1363711 -->
Pode resolver problemas relativos ao sucesso da instalação de aplicações cliente ao rever a coluna intitulada **Instalação da aplicação** e o painel **Resolução de Problemas**. Para ver o painel **Resolução de Problemas**, selecione **Resolução de Problemas** em **Ajuda e suporte**, no portal do Intune.

### <a name="device-configuration"></a>Configuração do dispositivo

#### <a name="network-access-control-support-on-ios-vpn-clients----1333693---"></a>Suporte de controlo de acesso à rede em clientes VPN do iOS <!-- 1333693 -->
Com esta atualização, há uma nova definição para ativar o Controlo de Acesso à Rede (NAC) quando criar um perfil de configuração de VPN para Cisco AnyConnect, F5 Access e Citrix SSO para iOS. Esta definição permite que o ID do NAC do dispositivo seja incluído no perfil de VPN. Atualmente, não existem clientes VPN nem soluções de parceiro de NAC que suportem este novo ID do NAC, mas iremos mantê-lo informado através da nossa [mensagem de blogue de suporte](ttps://aka.ms/iOS12_and_vpn) quando existirem.

Para utilizar o NAC, precisará de:
1. Optar ativamente por permitir que o Intune inclua IDs de dispositivos em perfis de VPN
2. Atualizar o software/firmware do seu fornecedor de NAC através da orientação fornecida diretamente pelo seu fornecedor de NAC

Para obter informações sobre esta definição num perfil de VPN do iOS, veja [Adicionar definições de VPN em dispositivos iOS no Microsoft Intune](vpn-settings-ios.md). Para obter mais informações sobre o controlo de acesso à rede, veja [Integração de controlo de acesso à rede (NAC) com o Intune](network-access-control-integrate.md). 

Aplica-se a: iOS

#### <a name="remove-an-email-profile-from-a-device-even-when-theres-only-one-email-profile----1818139---"></a>Remover um perfil de e-mail de um dispositivo, mesmo quando existe apenas um perfil de e-mail <!-- 1818139 -->
Anteriormente, não podia remover um perfil de e-mail de um dispositivo *se* fosse o único perfil de e-mail. Com esta atualização, este comportamento muda. Agora pode remover um perfil de e-mail, mesmo que seja o único perfil de e-mail no dispositivo. Para obter detalhes, veja [Adicionar definições de e-mail a dispositivos com o Intune](email-settings-configure.md).

#### <a name="powershell-scripts-and-aad----2309469---"></a>Scripts do PowerShell e AAD <!-- 2309469 -->
Os scripts do PowerShell no Intune podem ser direcionados a grupos de segurança de dispositivo do AAD.

#### <a name="new-required-password-type-default-setting-for-android-android-enterprise---2649963---"></a>Nova predefinição para "Tipo de palavra-passe necessária" para o Android e o Android Enterprise<!-- 2649963 -->
Ao criar uma nova política de conformidade (**Intune** > **Conformidade do dispositivo** > **Políticas** > **Criar política** > **Android** ou **Android Enterprise** para a Plataforma > Segurança do Sistema), o valor predefinido para **Tipo de palavra-passe necessária** muda:

De: Predefinição do dispositivo para: Pelo menos numérica

Aplica-se a: Android, Android Enterprise

Para ver estas definições, aceda a [Android](compliance-policy-create-android.md) e [Android Enterprise](compliance-policy-create-android-for-work.md).

#### <a name="use-a-pre-shared-key-in-a-windows-10-wi-fi-profile----2662938---"></a>Utilizar uma chave pré-partilhada num perfil de Wi-Fi do Windows 10 <!-- 2662938 -->
Com esta atualização, poderá utilizar uma chave pré-partilhada (PSK) com o protocolo de segurança WPA/WPA2-Pessoal para autenticar um perfil de configuração de Wi-Fi para o Windows 10. Na atualização de outubro de 2018 para dispositivos com o Windows 10, também pode especificar a configuração de custos para uma rede com tráfego limitado.

Atualmente, tem de importar um perfil de Wi-Fi ou criar um perfil personalizado para utilizar uma chave pré-partilhada. O artigo [Definições de Wi-Fi para o Windows 10](wi-fi-settings-windows.md) indica as definições atuais. 

#### <a name="remove-pkcs-and-scep-certificates-from-your-devices----3218390---"></a>Remover certificados PKCS e SCEP dos seus dispositivos <!-- 3218390 -->
Em alguns cenários, houve certificados PKCS e SCEP que permaneceram em dispositivos, mesmo quando se procedeu à remoção de uma política de um grupo ou à eliminação de uma implementação de configuração ou de conformidade, ou quando um administrador atualizou um perfil SCEP ou PKCS existente. Esta atualização altera o comportamento. Há alguns cenários onde os certificados PKCS e SCEP são removidos de dispositivos e outros cenários em que estes certificados permanecem no dispositivo. Para obter informações sobre estes cenários, veja [Remover certificados SCEP e PKCS no Microsoft Intune](remove-certificates.md).

#### <a name="use-gatekeeper-on-macos-devices-for-compliance----2504381---"></a>Utilizar o Controlador de Chamadas em dispositivos macOS para efeitos de conformidade <!-- 2504381 -->
Esta atualização inclui o controlador de chamadas para macOS para avaliar dispositivos quanto à conformidade. Para definir o Controlador de Chamadas, tem de [Adicionar uma política de conformidade para dispositivos macOS](compliance-policy-create-mac-os.md).


### <a name="device-enrollment"></a>Inscrição de dispositivos

#### <a name="enrollment-abandonment-report----1382924---"></a>Relatório de abandono de inscrições <!-- 1382924 -->
Um novo relatório que fornece detalhes sobre inscrições abandonadas está disponível em **Inscrição de dispositivos** > **Monitorização**. Para obter mais informações, veja [Relatório de abandono do Portal da Empresa](enrollment-report-company-portal-abandon.md).

#### <a name="new-azure-active-directory-terms-of-use-feature----2870393---"></a>Nova funcionalidade de termos de utilização do Azure Active Directory <!-- 2870393 -->
O Azure Active Directory tem uma funcionalidade de termos de utilização que pode utilizar em vez dos termos e condições do Intune existentes. A funcionalidade de termos de utilização do Azure AD proporciona mais flexibilidade relativamente aos termos a apresentar e a quando o fazer, melhor suporte para a localização, mais controlo sobre a forma como os termos são compostos e relatórios melhorados. A funcionalidade de termos de utilização do Azure AD necessita do Azure Active Directory Premium P1, que também faz parte do conjunto Enterprise Mobility + Security E3. Para saber mais, veja o artigo [Gerir os termos e condições da sua empresa para o acesso dos utilizadores](terms-and-conditions-create.md).

#### <a name="android-device-owner-mode-support---3188762--"></a>Suporte do modo Proprietário de Dispositivo Android <!--3188762-->
Para o Knox Mobile Enrollment da Samsung, o Intune suporta agora inscrição de dispositivos para o modo de gestão Proprietário de Dispositivo Android. Os utilizadores em redes Wi-Fi ou redes móveis podem inscrever com apenas alguns toques os respetivos dispositivos quando os ligarem pela primeira vez. Para obter mais informações, consulte [Automatically enroll Android devices by using Samsung's Knox Mobile Enrollment](android-samsung-knox-mobile-enroll.md) (Inscrever automaticamente dispositivos Android através do Knox Mobile Enrollment da Samsung).

### <a name="device-management"></a>Gestão de dispositivos
#### <a name="new-settings-for-software-updates------1907869---"></a>Novas definições de atualizações de Software   <!-- 1907869 -->  
- Agora, pode configurar algumas notificações aos utilizadores finais alerta sobre reinícios necessários para concluir a instalação das atualizações de software mais recente.   
- Agora, pode configurar uma mensagem de aviso de reinício para reinícios do que acontecer fora do horário de trabalho, que oferece suporte a cenários BYOD.

#### <a name="group-windows-autopilot-enrolled-devices-by-correlator-id----2075110---"></a>Agrupar dispositivos inscritos com o Windows Autopilot por ID de correlacionador <!-- 2075110 -->
O Intune suporta agora o agrupamento de dispositivos Windows por um ID de correlacionador se os mesmos forem inscritos com o [Autopilot para dispositivos existentes](https://techcommunity.microsoft.com/t5/Windows-IT-Pro-Blog/New-Windows-Autopilot-capabilities-and-expanded-partner-support/ba-p/260430), através do Configuration Manager. O ID de correlacionador é um parâmetro do ficheiro de configuração do Autopilot. O Intune irá definir automaticamente o [atributo enrollmentProfileName de dispositivos do Azure AD](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-dynamic-membership#using-attributes-to-create-rules-for-device-objects) para que seja igual a "OfflineAutopilotprofile-<correlator ID>". Isto permite que sejam criados grupos dinâmicos do Azure AD arbitrários com base no ID de correlacionador, através do atributo enrollmentprofileName para inscrições do Autopilot offline. Para obter mais informações, veja [Windows Autopilot for existing devices](enrollment-autopilot.md#windows-autopilot-for-existing-devices) (Windows Autopilot para dispositivos existentes).

#### <a name="intune-app-protection-policies----2984657---"></a>Políticas de proteção de aplicações do Intune <!-- 2984657 -->
As políticas de proteção de aplicações do Intune permitem-lhe configurar várias definições de proteção de dados para aplicações protegidas pelo Intune, como o Microsoft Outlook e o Microsoft Word. Alterámos o aspeto e funcionalidade destas definições tanto para [iOS](app-protection-policy-settings-ios.md) como para [Android](app-protection-policy-settings-android.md), de modo a facilitar a localização de definições individuais. Existem três categorias de definições de política:
- **Reposicionamento de dados**: este grupo inclui os controlos de prevenção de perda de dados (DLP), como as restrições das operações de cortar, copiar, colar e guardar como. Estas definições determinam como os utilizadores interagem com os dados nas aplicações.
- **Requisitos de acesso**: este grupo contém as opções de PIN por aplicação que determinam como o utilizador final utiliza as aplicações num contexto de trabalho.  
- **Iniciação condicional**: este grupo guarda definições como as definições de SO mínimo, de deteção de dispositivos desbloqueados por jailbreak ou rooting e de períodos de tolerância offline.  
  
A funcionalidade das definições não muda, mas será mais fácil encontrá-las quando trabalhar no fluxo de autoria de política.

### <a name="intune-apps"></a>Aplicações do Intune

#### <a name="intune-will-support-a-maximum-package-size-of-8-gb-for-lob-apps----1727158---"></a>O Intune suportará pacotes com um máximo de 8 GB para aplicações LOB <!-- 1727158 -->
O Intune aumentou a dimensão máxima dos pacotes para 8 GB para as aplicações de linha de negócio (LOB). Para obter mais informações, veja [Adicionar aplicações ao Microsoft Intune](apps-add.md).

#### <a name="add-custom-brand-image-for-company-portal-app----1916266---"></a>Adicionar uma imagem de marca personalizada na aplicação Portal da Empresa <!-- 1916266 -->
Enquanto administrador do Microsoft Intune, pode carregar uma imagem de marca personalizada que será apresentada como uma imagem de fundo na página de perfil do utilizador, na aplicação Portal da Empresa para iOS. Para obter mais informações sobre como configurar a aplicação Portal da Empresa, veja [Como configurar a aplicação Portal da Empresa do Microsoft Intune](company-portal-app.md).

#### <a name="intune-will-maintain-the-office-localized-language-when-updating-office-on-end-users-machines----2971030---"></a>O Intune irá manter o idioma localizado do Office ao atualizá-lo nos computadores dos utilizadores finais <!-- 2971030 -->
Quando o Intune instalar o Office nos computadores dos seus utilizadores finais, estes terão automaticamente os mesmos pacotes de idiomas de que dispunham com instalações anteriores do Office .MSI. Para obter mais informações, veja [Atribuir aplicações do Office 365 a dispositivos Windows 10 com o Microsoft Intune](apps-add-office365.md).

### <a name="monitor-and-troubleshoot"></a>Monitorizar e resolver problemas

#### <a name="new-intune-support-experience-in-the-microsoft-365-device-management-portal----3076965---"></a>Nova Experiência de Suporte do Intune no Portal de Gestão de Dispositivos do Microsoft 365 <!-- 3076965 -->
Estamos a implementar uma nova experiência de Ajuda e Suporte para o Intune no [portal de Gestão de Dispositivos do Microsoft 365]( http://devicemanagement.microsoft.com). A nova experiência permite-lhe descrever o seu problema pelas suas próprias palavras e receber informações de resolução de problemas e conteúdos de remediação baseados na Web. Estas soluções são disponibilizadas através de um algoritmo de aprendizagem automática baseado em regras, alimentado pelas perguntas dos utilizadores.  

Para além das orientações específicas de problemas, pode utilizar o novo fluxo de trabalho de criação de processos para abrir um processo de suporte por e-mail ou telefone.  

Para os clientes que fazem parte da implementação, esta nova experiência substitui a experiência atual de Ajuda e Suporte de um conjunto estático de opções previamente selecionadas que se baseiam na área da consola que é apresentada ao abrir a Ajuda e Suporte.  

*Esta nova experiência de Ajuda e Suporte está a ser implementada apenas para alguns inquilinos e está disponível no portal de Gestão de Dispositivos. Os participantes desta nova experiência são selecionados aleatoriamente a partir dos inquilinos do Intune disponíveis. Serão adicionados novos inquilinos à medida que expandimos a implementação.*  

Para obter mais informações, consulte [ajuda e suporte a experiência](get-support.md#help-and-support-experience) em como obter suporte para o Microsoft Intune.  

### <a name="powershell-module-for-intune--preview-available----951068---"></a>Módulo do PowerShell para o Intune – pré-visualização disponível <!-- 951068 -->
Está agora disponível para pré-visualização no [GitHub]( https://aka.ms/intunepowershell) um novo módulo do PowerShell que fornece suporte para a API do Intune através do Microsoft Graph. Para obter mais informações sobre como utilizar este módulo, veja o ficheiro LEIA-ME nessa localização. 


<!-- ########################## -->
## <a name="week-of-october-15-2018"></a>Semana de 15 de outubro de 2018

### <a name="pin-prompt-when-you-change-fingerprints-or-face-id-on-an-ios-device-----2637704----"></a>Pedido de PIN quando altera impressões digitais ou o Face ID num dispositivo iOS <!-- 2637704  -->
Agora é pedido um PIN aos utilizadores após fazerem alterações biométricas no respetivo dispositivo iOS. Isto inclui alterações ao nível de impressões digitais ou do Face ID registados. A altura em que o pedido é apresentado depende da configuração do tempo limite *Verificar novamente os requisitos de acesso após (minutos)*.  Quando não está definido nenhum PIN, é pedido ao utilizador para configurar um. 
 
Esta funcionalidade só está disponível para iOS e requer a participação de aplicações que integrem o SDK da aplicação Intune para iOS, versão 9.0.1 ou posterior. Precisa da integração do SDK para que o comportamento possa ser imposto nas aplicações de destino. Esta integração decorre de forma gradual e está dependente das equipas específicas da aplicação. Algumas aplicações participantes incluem: WXP, Outlook, Managed Browser e Yammer.


<!-- ########################## -->
## <a name="week-of-october-1-2018"></a>Semana de 1 de outubro de 2018

### <a name="app-management"></a>Gestão de aplicações

#### <a name="access-to-key-profile-properties-using-the-company-portal-app----772203---"></a>Acesso a propriedades de perfil fundamentais com a aplicação Portal da Empresa <!-- 772203 -->
Os utilizadores finais podem agora aceder a ações e propriedades de conta fundamentais, tais como a reposição de palavra-passe, a partir da aplicação Portal da Empresa. 

#### <a name="3rd-party-keyboards-can-be-blocked-by-app-settings-on-ios----1248481---"></a>Os teclados de terceiros podem ser bloqueados por definições de APP no iOS <!-- 1248481 -->
Em dispositivos iOS, os administradores do Intune podem bloquear a utilização de teclados de terceiros ao aceder a dados da organização em aplicações protegidas por políticas. Quando a Política de Proteção de Aplicações (APP) estiver definida para bloquear teclados de terceiros, o utilizador do dispositivo irá receber uma mensagem da primeira vez que interagir com dados da empresa ao utilizar um teclado de terceiros. Todas as opções, além do teclado nativo, estão bloqueadas e os utilizadores de dispositivos não irão vê-las. Os utilizadores de dispositivos só verão a mensagem de diálogo uma vez. 

#### <a name="user-account-access-of-intune-apps-on-managed-android-and-ios-devices----1248496---"></a>Acesso a contas de utilizadores por parte de aplicações do Intune em dispositivos Android e iOS geridos <!-- 1248496 -->
Enquanto administrador do Microsoft Intune, pode controlar as contas de utilizadores que são adicionadas a aplicações do Microsoft Office em dispositivos geridos. Pode limitar o acesso exclusivamente a contas de utilizadores autorizadas e bloquear contas pessoais em dispositivos inscritos. 

#### <a name="outlook-ios-and-android-app-configuration-policy---1828527---"></a>Política de configuração da aplicação Outlook para iOS e Android <!--1828527 -->
Agora pode criar uma política de configuração da aplicação Outlook para iOS e Android para os utilizadores no local que tiram partido da autenticação Básica com o protocolo ActiveSync. Serão adicionadas outras definições de configuração à medida que forem ativadas para o Outlook para iOS e Android.

#### <a name="office-365-pro-plus-language-packs----1833450---"></a>Pacotes de Idiomas do Office 365 Pro Plus <!-- 1833450 -->
Enquanto administrador do Intune, poderá implementar idiomas adicionais para aplicações do Office 365 Pro Plus geridas através do Intune. A lista de idiomas disponíveis inclui o **Tipo** do pacote de idiomas (núcleo, parcial e verificação). No portal do Azure, selecione **Microsoft Intune** > **Aplicações do cliente** > **Aplicações** > **Adicionar**. Na lista **Tipo de aplicação**, no painel **Adicionar aplicação**, selecione **Windows 10** em **Office 365 Suite**. Selecione **Idiomas** no painel **Definições do Conjunto de Aplicações**.

####  <a name="windows-line-of-business-lob-apps-file-extensions----1884873---"></a>Extensões de ficheiros de aplicações de linha de negócio (LOB) do Windows <!-- 1884873 -->
As extensões de ficheiros de aplicações de linha de negócio do Windows agora incluirão *.msi*, *.appx*, *.appxbundle*, *.msix* e *.msixbundle*. Pode adicionar uma aplicação no Microsoft Intune ao selecionar **Aplicações do cliente** > **Aplicações** > **Adicionar**. O painel **Adicionar aplicação** é apresentado, o qual lhe permite selecionar o **Tipo de aplicação**. Para aplicações LOB do Windows, selecione o tipo de aplicação **Linha de negócio**, selecione o **Ficheiro de pacote de aplicação** e, em seguida, introduza um ficheiro de instalação com a extensão adequada.

#### <a name="windows-10-app-deployment-using-intune----2309001---"></a>Implementação de aplicações para Windows 10 através do Intune <!-- 2309001 -->
Com base no suporte existente para aplicações de linha de negócio (LOB) e aplicações da Microsoft Store para Empresas, os administradores podem utilizar o Intune para implementar a maioria das aplicações existentes da respetiva organização nos utilizadores finais em dispositivos com o Windows 10. Os administradores podem adicionar, instalar e desinstalar aplicações para utilizadores do Windows 10 numa variedade de formatos, como MSIs, Setup.exe ou MSP. O Intune irá avaliar as regras de requisitos antes de transferir e instalar, e irá notificar os utilizadores finais sobre o estado ou os requisitos de reinício através do Centro de Ação do Windows 10. Esta funcionalidade irá efetivamente ajudar as organizações interessadas em mudar esta carga de trabalho para o Intune e a cloud. Esta funcionalidade está atualmente em pré-visualização pública e esperamos acrescentar-lhe novas funcionalidades relevantes durante os próximos meses. 

#### <a name="end-user-device-and-app-content-menu----2771453---"></a>Menu de contexto em aplicações e dispositivos de utilizadores finais <!-- 2771453 -->
Os utilizadores finais podem agora utilizar o menu de contexto em aplicações e dispositivos para acionar ações comuns, tais como mudar o nome de um dispositivo ou realizar verificações de conformidade. 

#### <a name="windows-company-portal-keyboard-shortcuts----2771518---"></a>Atalhos de teclado do Portal da Empresa do Windows <!-- 2771518 -->
Os utilizadores finais poderão agora ativar ações de aplicação e de dispositivo no Portal da Empresa do Windows com atalhos de teclado (aceleradores).

### <a name="device-configuration"></a>Configuração do dispositivo

#### <a name="create-dns-suffixes-in-vpn-configuration-profiles-on-devices-running-windows-10---1333668---"></a>Criar sufixos DNS em perfis de configuração VPN em dispositivos com o Windows 10<!-- 1333668 -->
Quando criar um perfil de configuração de um dispositivo VPN (**Configuração do dispositivo** > **Perfis** > **Criar perfil** >  plataforma **Windows 10 e versões posteriores** > tipo de perfil **VPN**), terá de introduzir algumas definições de DNS. Com esta atualização, também pode introduzir múltiplos **sufixos DNS** no Intune. Quando utilizar sufixos DNS, pode procurar um recurso de rede através do respetivo nome abreviado, em vez do nome de domínio completamente qualificado (FQDN). Esta atualização também permite alterar a ordem dos sufixos DNS no Intune.
O artigo [Definições de VPN do Windows 10](vpn-settings-windows-10.md#dns-settings) indica as definições de DNS atuais.
Aplica-se a: Dispositivos com o Windows 10

#### <a name="support-for-always-on-vpn-for-android-enterprise-work-profiles----1333705---"></a>Suporte para VPN Sempre Ativada para perfis de trabalho do Android Enterprise <!-- 1333705 -->
Nesta atualização, pode utilizar ligações VPN Sempre Ativada em dispositivos Android Enterprise com perfis de trabalho geridos. As ligações VPN Sempre Ativada permanecem ativadas ou voltam a ativar-se quando o utilizador desbloqueia o dispositivo, quando o dispositivo é reiniciado ou quando a rede sem fios é alterada. Também pode colocar a ligação em modo de "bloqueio". Este modo permite bloquear todo o tráfego de rede até à ativação da ligação de VPN.
Pode ativar a VPN Sempre Ativada nas definições **Configuração do dispositivo** > **Perfis** > **Criar perfil** > **Android Enterprise** para a plataforma > **Restrições do dispositivo** > **Conectividade**.

#### <a name="issue-scep-certificates-to-user-less-devices----1744554---"></a>Emitir certificados SCEP para dispositivos sem utilizador <!-- 1744554 -->
De momento, os certificados são emitidos para utilizadores. Com esta atualização, é possível emitir certificados SCEP para dispositivos, incluindo para dispositivos sem utilizador, tais como quiosques (**Configuração do dispositivo** > **Perfis** > **Criar perfil** > **Windows 10 e versões posteriores** para a plataforma > **Certificado SCEP** para o perfil). Outras atualizações incluem o seguinte:
- A propriedade **Requerente** nos perfis SCEP é agora uma caixa de texto personalizada e pode incluir novas variáveis. 
- A propriedade **Nome alternativo do requerente (SAN)** nos perfis SCEP tem agora um formato de tabela e pode incluir novas variáveis. Na tabela, os administradores podem adicionar um atributo e preencher o valor numa caixa de texto personalizada. O SAN suportará os seguintes atributos: 
  - DNS
  - Endereço de e-mail
  - UPN

  Estas variáveis novas podem ser adicionadas com texto estático numa caixa de texto de valor personalizado. Por exemplo, o atributo de DNS pode ser adicionado como `DNS = {{AzureADDeviceId}}.domain.com`.

  > [!NOTE]
  > As chavetas, os pontos e vírgulas e as barras verticais " { } ; | " não funcionarão no texto estático do SAN. As chavetas só podem delimitar uma das novas variáveis de certificado de dispositivo para que sejam aceites em `Subject` ou `Subject alternative name`. 

Variáveis de certificado de dispositivo novas:  

```
"{{AAD_Device_ID}}",
"{{Device_Serial}}",
"{{Device_IMEI}}",
"{{SerialNumber}}",
"{{IMEINumber}}",
"{{AzureADDeviceId}}",
"{{WiFiMacAddress}}",
"{{IMEI}}",
"{{DeviceName}}",
"{{FullyQualifiedDomainName}}",
"{{MEID}}",
```

> [!NOTE]
>  - `{{FullyQualifiedDomainName}}` só funciona em dispositivos com Windows e dispositivos associados a um domínio. 
>  -  Quando especificar as propriedades do dispositivo, tais como o IMEI, o Número de Série e o Nome de Domínio Completamente Qualificado, no requerente ou no SAN de um certificado de dispositivo, tenha em atenção que estas propriedades podem ser falsificadas por uma pessoa que tenha acesso ao dispositivo. 

O artigo [Criar um perfil de certificado SCEP](certificates-scep-configure.md#create-a-scep-certificate-profile) indica as variáveis atuais durante a criação de um perfil de configuração SCEP. 

Aplica-se a: Windows 10 e posterior e iOS, suportado para Wi-Fi

#### <a name="remotely-lock-uncompliant-devices----2064495---"></a>Bloquear remotamente dispositivos que não estejam em conformidade <!-- 2064495 -->
Quando um dispositivo não estiver em conformidade, poderá criar uma ação na política de conformidade que bloqueie remotamente o dispositivo. No Intune > **Conformidade do dispositivo**, crie uma nova política ou selecione uma política existente > **Propriedades**. Selecione **Ações para não conformidade** > **Adicionar** e selecione a opção para bloquear remotamente o dispositivo.
Suportado no: 
- Android
- iOS
- macOS
- Windows 10 Mobile 
- Windows Phone 8.1 e posterior 

#### <a name="windows-10-and-later-kiosk-profile-improvements-in-the-azure-portal----2748224---"></a>Melhorias ao nível do perfil de Quiosque do Windows 10 e versões posteriores no portal do Azure <!-- 2748224 -->
Esta atualização inclui as seguintes melhorias no perfil de configuração de dispositivos de Quiosque do Windows 10 (**Configuração do dispositivo** > **Perfis** > **Criar perfil** > **Windows 10 e versões posteriores** para a plataforma > **Pré-visualização de quiosque** para o tipo de perfil): 
- Atualmente, pode criar múltiplos perfis de quiosque no mesmo dispositivo. Com esta atualização, o Intune suportará apenas um perfil de quiosque por dispositivo. Se continuar a necessitar de múltiplos perfis de quiosque num só dispositivo, pode utilizar um URL personalizado.
- Num perfil **Quiosque de várias aplicações**, pode selecionar o tamanho e a ordem dos mosaicos das aplicações para o **Esquema do menu Iniciar** na grelha das aplicações. Se preferir um nível superior de personalização, pode avançar para carregar um ficheiro XML.
- As definições do Browser de Quiosque estão a passar para as definições de **Quiosque**. Neste momento, as definições do **browser de Quiosque** têm a sua própria categoria no portal do Azure.
Aplica-se a: Windows 10 e posterior




### <a name="device-enrollment"></a>Inscrição de dispositivos

#### <a name="apply-autopilot-profile-to-enrolled-win-10-devices-not-already-registered-for-autopilot----1558983---"></a>Aplicar um perfil do Autopilot a dispositivos com o Windows 10 inscritos e que ainda não estejam registados no Autopilot <!-- 1558983 -->
Pode aplicar um perfil do Autopilot a dispositivos com o Windows 10 inscritos e que ainda não tenham sido registados no Autopilot. No perfil do Autopilot, selecione a opção **Converter todos os dispositivos visados para o Autopilot** para registar automaticamente dispositivos não Autopilot com o serviço de implementação do Autopilot. O processo de registo demora até 48 horas, pelo que deverá aguardar. Quando a inscrição do dispositivo for anulada e o dispositivo for reposto, o Autopilot aprovisioná-lo-á.

#### <a name="create-and-assign-multiple-enrollment-status--page-profiles-to-azure-ad-groups----2526564---"></a>Criar e atribuir múltiplos perfis de Página de Estado de Inscrição a grupos do Azure AD <!-- 2526564 -->
Agora, pode [criar e atribuir](windows-enrollment-status.md) múltiplos perfis de Página de Estado de Inscrição a grupos do Azure AD.

#### <a name="migration-from-device-enrollment-program-to-apple-business-manager-in-intune---2748613--"></a>Migração do Programa de Registo de Aparelho para o Apple Business Manager no Intune <!--2748613-->
O Apple Business Manager (ABM) funciona no Intune, pelo que pode atualizar versão do software da sua conta do Programa de Registo de Aparelho (DEP) para o ABM. No Intune, o processo é o mesmo. Para atualizar a versão do software da sua conta Apple do DEP para o ABM, aceda a [ https://support.apple.com/en-us/HT208817]( https://support.apple.com/en-us/HT208817).

### <a name="alert-and-enrollment-status-tabs-on-the-device-enrollment-overview-page---2748656--"></a>Separadores de alerta e estado de inscrição na página Descrição geral de inscrições de dispositivos <!--2748656-->
Os alertas e os erros ao nível das inscrições aparecem agora em separadores diferentes da página Descrição geral de inscrições de dispositivos.

### <a name="device-management"></a>Gestão de dispositivos

#### <a name="restricts-apps-and-block-access-to-company-resources-on-android-devices----2451462----"></a>Restringir aplicações e bloquear o acesso aos recursos da empresa em dispositivos Android <!-- 2451462  -->  
Em **Conformidade do dispositivo** > **Políticas** > **Criar política** > **Android**  > **Segurança do Sistema**, há uma nova definição na secção *Segurança do Dispositivo* chamada **Aplicações restritas**. A definição **Aplicações restritas** utiliza uma política de conformidade para bloquear o acesso aos recursos da empresa, caso determinadas aplicações estejam instaladas no dispositivo. O dispositivo é considerado não compatíveis até que as aplicações restritas sejam removidas do dispositivo.
Aplica-se a: 
- Android

<!-- ########################## -->
## <a name="notices"></a>Avisos

### <a name="check-your-delay-visibility-of-software-updates-setting-in-intune"></a>Verifique a definição de "Visibility atraso das atualizações de Software" no Intune
Partilhámos na MC171466 que podemos foram movimentar algumas definições na consola do. Com a atualização de Março ao Intune, podemos irá remover completamente a definição "Atualizações de visibilidade de atraso do Software" do painel de política de atualização de iOS. Isto não vai alterar a forma de aplicam as atualizações de software agendadas, mas pode afetar o tempo que a visibilidade de uma atualização é atrasada para os utilizadores finais. Terá de executar uma ação antes do final de Março se utilizar esta definição.

#### <a name="how-does-this-affect-me"></a>Como é que isto me afeta?
Após a atualização de serviço do Intune de Fevereiro, perceberá que a definição aparece em perfis de restrição de dispositivos na consola e no iOS atualizar políticas no painel de atualização de Software. Quando vir essa alteração seja refletida na consola do, eis o que poderá ter de fazer.
• Para políticas de atualização existentes para iOS: Se tiver personalizado configurado esta definição para qualquer coisa diferente da predefinição de 30 dias e quiser as configurações existentes para a definição de visibilidade de atraso continuar a aplicar após o fim de Março, terá que criar um novo iOS perfil de restrição de dispositivos. Aqui, a definição de visibilidade de atraso terá de ter os mesmos valores como a política de atualização de iOS existente e ser direcionadas para os mesmos grupos. Após a atualização do serviço de Março, já não poderá editar os valores para esta definição nas políticas de atualização de iOS existente, uma vez que já não estarão visível neste painel. Em vez disso, irá configurar esta definição nos perfis de novo.
Se o valor de número de dias pode atrasar visibilidade não corresponde em ambos os locais para os valores de definição configurada personalizado, a visibilidade de atraso definição não funcionará, e os utilizadores finais irão ver a atualização nos respetivos dispositivos, assim que estiver disponível. Isto pode ter um impacto mínimo para a maioria dos clientes, uma vez que as outras definições no painel da política de atualização de Software sempre usaram precedência sobre esta definição na consola do.
• Para novas políticas de atualização para iOS: Se tentar criar novas políticas no painel de atualizações de Software após a atualização do serviço de Fevereiro do Intune, irá ver esta definição a cinzento. Verá uma nota na consola do redirecioná-lo para o painel de configuração do dispositivo se desejar atrasar a visibilidade das atualizações.

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>O que posso fazer para me preparar para esta alteração?
Não é necessário executar uma ação se não utilize esta definição ou não pretender que a visibilidade das atualizações de software de seus usuários finais.

Se desejar atrasar a visibilidade das atualizações, começar a configurar a definição em novos perfis no painel da configuração do dispositivo em restrições do dispositivo > geral. Se tiver personalizado esta definição configurada no iOS existente, as políticas de atualização, criar um novo perfil de restrição de dispositivos equivalente com o mesmo valor para "dias" atrasar a visibilidade das atualizações para os seus utilizadores, depois do Fevereiro de atualização e antes de Março de atualização for implementada. Pode querer atualizar a sua documentação de orientação para profissionais de TI e informe o suporte técnico.
Consulte o nosso blogue de suporte publicar as informações adicionais para obter detalhes sobre como configurar esta definição.
 
#### <a name="additional-information"></a>Informações adicionais
https://aka.ms/Delay_visibility_setting_iOS

###  <a name="upcoming-change-to-the-intune-data-warehouse-api"></a>Alteração futura à API do armazém de dados do Intune
Iremos fazer duas alterações durante o período de tempo de 1903:
- Descontinuação de filtro do Beta<br>
    Descontinuação de filtros de beta não suportado instanciado.   
- alterações 1.0 refletindo para o beta<br>
    As alterações feitas para nossas coleções de v1.0 agora serão refletidas na versão beta.  


###<a name="plan-for-change-workflow-changes-for-ios-12-enrollment-in-intune"></a>Planear a alteração: Alterações de fluxo de trabalho para iOS 12 inscrição no Intune
Apple anunciou algumas alterações relacionadas com dispositivos iOS, a inscrição para os serviços de gestão de dispositivos móveis (MDM). A alteração provavelmente será vista na versão da Primavera de 2019 do iOS, bem como todas as versões futuras do iOS.

####<a name="how-does-this-affect-me"></a>Como é que isto me afeta?
Se os utilizadores finais atualizarem os seus dispositivos para esta nova versão do iOS 12 na Primavera, sabe-se de que existe um fluxo de trabalho modificado e têm de efetuar passos adicionais que conclua a inscrição no Intune. Quando Apple apresenta estas alterações, os utilizadores finais terão para: • iniciar o processo de inscrição na aplicação Portal da empresa para transferir um • de perfil de gestão vá para definições > geral > perfis • selecione o perfil correto e clique em através de a instalação • regressar ao Portal da empresa que conclua a inscrição 

Dispositivos que já tenham sido inscritos e atualizar para a nova versão do iOS não seja afetado, a menos que eles são não inscritos e têm uma nova inscrição.
Experiência de inscrição em dispositivos com iOS 12.1 ou anteriores não serão alteradas com esta nova versão pela Apple.

####<a name="what-can-i-do-to-prepare-for-this-change"></a>O que posso fazer para me preparar para esta alteração?
Deve planear a atualização a documentação e as diretrizes de utilizador final. Também poderá permitir que o suporte técnico sabe dessas alterações. Iremos mantê-lo informado por meio do Centro de mensagens e nossa, o que é a nova página quando esta alteração entra no ar.

Clique em obter informações adicionais para uma mensagem de blogue de suporte com capturas de ecrã e um vídeo sobre o fluxo de inscrição esperado.

####<a name="additional-information"></a>Informações adicionais
https://aka.ms/iOS_enrollment_changes

### <a name="plan-for-change-user-experience-update-to-intune-company-portal-app-for-ios"></a>Planear a alteração: Atualização da experiência de utilizador para a aplicação Portal da empresa do Intune para iOS
Temos o prazer partilhar que Intune em breve lançar uma atualização da experiência de utilizador principais para a aplicação Portal da empresa iOS. A atualização será apresentam uma reformulação visual da home page com filtros avançados e acesso mais rápido para aplicações e livros.

#### <a name="how-does-this-affect-me"></a>Como é que isto me afeta?
Esta experiência de utilizador atualizada, enquanto mantém iOS atual funcionalidade do Portal da empresa, funcionalidade:
- Uma home page com aspeto e funcionalidade do iOS nativo 
- Recursos de filtragem em listagens de conteúdo e pesquisa, incluindo a capacidade de filtrar por tipo de conteúdo (aplicações ou e-Books) e a disponibilidade (gestão necessária ou disponível sem inscrição de dispositivos)
- Capacidade de pesquisar e-Books
- Procurar histórico para aplicações e e-Books, se é membro do programa TestFlight da Apple, será notificado sobre a versão de pré-lançamento da aplicação de Portal da empresa do Intune iOS atualizada quando ela se tornar disponível. Se não tiver a parte do programa TestFlight da Apple, não é muito tarde para se registar. Registar irá permitir-lhe utilizar a aplicação Portal da empresa atualizado antes de ser disponibilizado aos seus utilizadores finais. Também terá a oportunidade de fornecer seus comentários diretamente para a equipa do Intune.  

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>O que posso fazer para me preparar para esta alteração?
Não é necessário efetuar qualquer ação; Estas alterações serão lançadas numa versão de aplicação do iOS futuros CP. 

#### <a name="additional-information"></a>Informações adicionais
[https://aka.ms/cp_update_iOS](https://aka.ms/cp_update_iOS)


### <a name="reminder-removal-of-existing-exchange-online-to-intune-connectors"></a>Lembrete: Remoção de existentes Exchange Online para conectores do Intune
Partilhámos na MC165575 que podemos seria possível remover o Exchange Online para a funcionalidade de conector do Intune 'De serviços' numa atualização futura. Com a atualização de Fevereiro ao serviço do Intune, iremos irá desativar o botão configurar novos conectores. Estamos a planear remover todos os existentes Exchange Online para conectores do Intune em Março de 2019.
 
#### <a name="how-does-this-affect-me"></a>Como é que isto me afeta?
Está recebendo esta mensagem, uma vez que os nossos registos indicam que pode utilizar a funcionalidade de conector "De serviços" no seu ambiente. 

O conector de 'De serviços' suporta a gestão do Exchange Active Sync apenas os dispositivos do Intune para o Exchange Online e não suporta a infraestrutura no local. Este conector, a forma como o que é apresentado no console, é apresentada como necessários para acesso condicional (AC), quando, na realidade, não é necessária para a AC. Pode tem estado a utilizar este conector para compreender a utilização do Exchange Online antes de aplicar acesso condicional. Estas informações já são fornecidas pelo centro de administração do Microsoft 365. Aqui, encontrará fornece relatórios de utilização para o tipo de Exchange Online incluindo a aplicação a ser utilizado para entre 7 e 180 dias. Para obter mais informações consulte o Office 365 relatórios no Centro de administração - utilização de aplicações de E-Mail  

Se utilizar este conector no seu ambiente, não será possível monitorizar ou eliminar os Exchange Active Sync apenas os dispositivos no Intune após conectores foram desativados em Fevereiro. Não há nenhum impacto previsto aos seus utilizadores finais durante esta alteração.
 
#### <a name="what-can-i-do-to-prepare-for-this-change"></a>O que posso fazer para me preparar para esta alteração?
Se tiver o conector de serviços, configurar e executar o Exchange Active Sync apenas os dispositivos, mude para outros métodos de gerir os seus dispositivos. Tem as seguintes opções: • inscrever dispositivos na gestão de dispositivos móveis (MDM) • utilize políticas de proteção de aplicação Intune para gerir a sua • dispositivos Exchange utilização controla conforme descrito na documentação aqui
  
#### <a name="additional-information"></a>Informações adicionais
https://docs.microsoft.com/intune/exchange-service-connector-configure
 


### <a name="plan-for-change-performance-updates-to-intune-for-education---1750215--"></a>Planear a alteração: Atualizações de desempenho para o Intune for Education <!--1750215-->
Estamos a adicionar algumas atualizações ao Intune for Education de forma a aumentar a velocidade e a fiabilidade quando atribui definições aos seus utilizadores ou dispositivos. No âmbito desta alteração, perto do fim do mês de novembro, moveremos as suas políticas ou atribuições de definições para novos grupos.

#### <a name="how-does-this-affect-me"></a>Como é que isto me afeta?

Como do Intune para clientes de educação, tem dois grupos dinâmicos do Azure Active Directory (Azure AD): "Todos os utilizadores" e "Todos os dispositivos". Com estas atualizações, estes grupos "Todos os Utilizadores" e "Todos os dispositivos" do Azure AD não serão visíveis na consola do Intune for Education. Contudo, permanecerão visíveis na consola do Intune no Azure e o nome deles mudará para "Todos os utilizadores (Obsoleto, não utilizar)" e "Todos os Dispositivos (Obsoleto, não utilizar)".

Quando as atualizações forem implementadas, já não terá de utilizar grupos do Azure AD para atribuir aplicações e definições no Intune. Em vez disso, moveremos as suas atribuições de Definições para novos grupos da consola do Intune for Education que vamos criar automaticamente e que continuarão a ser apresentados como "Todos os Utilizadores" e "Todos os Dispositivos" conforme acontecia anteriormente. Estas alterações ocorrem ao nível do back-end, pelo que não se aperceberá da existência de diferenças na consola do Intune for Education. Não se prevê que os seus utilizadores finais ou dispositivos inscritos sejam afetados. 

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>O que preciso de fazer para me preparar para esta alteração?
Não tem de fazer nada enquanto movemos as suas atribuições de políticas. Se estiver a atribuir políticas na consola do Intune for Education, continue a fazê-lo.

Se estiver a atribuir políticas aos grupos do Azure AD acima mencionados no Intune no Azure, comece, em vez disso, a atribuí-los ao grupo Todos os Utilizadores e Todos os Dispositivos na consola do Intune for Education. Quando vir que o nome dos grupos do Azure AD mudou e passou a incluir a palavra "obsoleto" na consola, pare de atribuir políticas no Azure AD. Se não estiver a utilizar os grupos cujo nome mudou para outro fim, deve eliminá-los.


### <a name="take-action-please-update-your-android-device-restriction-or-compliance-policy-password-settings-in-intune"></a>Tome medidas: Atualize o seu dispositivo Android restrição ou a conformidade de palavra-passe definições de política no Intune
O Intune irá remover o tipo de palavra-passe "predefinição do dispositivo" disponível para dispositivos com o Android 4.4 e superior. Devido às diferenças entre plataformas e predefinições de dispositivos Android, essa política é normalmente considerada opcional pelo dispositivo. Para tornar claro em que momento esta definição é aplicada no Android, vamos remover esta definição da IU numa próxima versão. 
#### <a name="how-does-this-affect-me"></a>Como é que isto me afeta?
- Se quiser exigir uma palavra-passe nos dispositivos, recomendamos que, em vez de utilizar a "predefinição do dispositivo", edite os perfis da sua plataforma Android de modo a indicar claramente o tipo de palavra-passe exigido.
- Se quiser que a decisão de criar ou não uma palavra-passe seja do utilizador final, selecione o botão "Não configurado". Se a definição continuar a funcionar após a removermos da IU, ser-lhe-á pedido que selecione um valor diferente de "Predefinição do dispositivo" na próxima vez que editar o perfil.
O que preciso de fazer para me preparar para esta alteração?
Reveja as definições de palavra-passe no seu Android e nas políticas de restrição e conformidade de dispositivos empresariais Android. Estas estão listadas em Segurança do sistema, no menu Políticas de conformidade, e em Palavra-passe do dispositivo ou Definições do perfil de trabalho, no menu Restrições do dispositivo. A secção Informações adicionais contém uma ligação para detalhes e capturas de ecrã adicionais que mostra onde estas definições podem ser configuradas.
#### <a name="additional-information"></a>Informações adicionais
https://aka.ms/PasswordSettings 


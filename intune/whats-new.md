---
title: Novidades no Microsoft Intune – Azure | Microsoft Docs
titlesuffix: ''
description: Descobrir as novidades do Intune no portal do Azure
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 01/10/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 791ed23f-bd13-4ef0-a3dd-cd2d7332c5cc
ms.reviewer: dougeby
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.openlocfilehash: 699936a1cef35d0435b329d1f8e09a64174fe2bd
ms.sourcegitcommit: 911923e9fe0eed52b1c93e400f776956835e582f
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/17/2019
ms.locfileid: "54387088"
---
# <a name="whats-new-in-microsoft-intune"></a>Novidades do Microsoft Intune
[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Saiba mais sobre as novidades todas as semanas no Microsoft Intune. Também pode descobrir alterações futuras, [avisos importantes](#notices) e informações sobre [versões anteriores](whats-new-archive.md). É possível que algumas funcionalidades sejam implementadas durante várias semanas e que não estejam disponíveis para todos os clientes na primeira semana.

> [!Note]
> Para obter informações sobre novas funcionalidades na gestão de dispositivos móveis (MDM) híbrida, veja a nossa página [Hybrid What’s New (Novidades nas Implementações Híbridas)](/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management).


<!-- Common categories:  
### App management
### Device configuration
### Device enrollment
### Device management
### Intune apps
### Monitor and troubleshoot
### Role-based access control

-->     
## <a name="week-of-january-14-2019"></a>Semana de 14 de Janeiro de 2019

### <a name="preview-of-support-for-android-corporate-owned-fully-managed-devices----1574342----"></a>Pré-visualização do suporte para dispositivos Android de empresa, totalmente geridos <!-- 1574342  -->
Intune agora suporta totalmente geridos os dispositivos Android, uma empresa cenário de "proprietário do dispositivo" em que dispositivos totalmente geridos pelo IT e são associados aos utilizadores individuais. Isto permite aos administradores gerir todo o dispositivo, aplicar um conjunto expandido de controlos de política indisponíveis para perfis de trabalho e restringe os utilizadores a instalar aplicações da Google Play gerido apenas. Para obter mais informações, consulte [configurar o Intune inscrição do Android totalmente dispositivos geridos](android-fully-managed-enroll.md) e [inscrever o seu dispositivos dedicados ou dispositivos totalmente gerenciados](android-dedicated-devices-fully-managed-enroll.md).  Tenha em atenção que esta funcionalidade está em pré-visualização. Algumas funcionalidades do Intune, tais como certificados, conformidade e acesso condicional, não estão atualmente disponíveis com o Android totalmente geridos os dispositivos dos utilizadores.

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
- Desative as notificações de sistema de apresentação, incluindo a entrada chamadas, alertas do sistema, erros de sistema e muito mais
- Sugere a ignorar a partir de tutoriais e dicas para aplicações que são abertas pela primeira vez
- Desativar definições keyguard avançadas, como a câmara, notificações, desbloqueio por impressão digital e muito mais para ver as definições, vá para [definições de restrição de dispositivos Android Enterprise](device-restrictions-android-for-work.md).

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

#### <a name="skip-more-setup-assistant-screens-on-an-ios-dep-device----2687509---"></a>Ignorar mais ecrãs do Assistente de configuração num dispositivo DEP iOS <!-- 2687509 -->
Além dos ecrãs que atualmente pode ignorar, pode definir iOS dispositivos DEP para ignorar os ecrãs seguintes no Assistente de configuração, quando um utilizador inscreve o dispositivo: Apresenta tom, privacidade, migração Android, botão Home page, iMessage & FaceTime, integração, migração de Watch, aparência, tempo de tela, atualização de Software, a configuração SIM.
Para escolher que telas para ignorar, aceda a **inscrição de dispositivos** > **inscrição da Apple** > **tokens do programa de inscrição** > Escolha um token > **Perfis** > Escolha um perfil > **propriedades** > **personalização do Assistente de configuração** > Escolha **ocultar**  para qualquer telas que pretende ignorar > **OK**.


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
Pode criar etiquetas de âmbito para limitar o acesso para aplicações e funções. Pode adicionar uma etiqueta de âmbito a uma aplicação para que apenas as pessoas com funções atribuídas também essa etiqueta de âmbito tenham acesso à aplicação. Aplicações adquiridas através do Apple Volume Purchase Program (VPP) não não possível atribuir etiquetas de âmbito.  Para obter mais informações, consulte [utilizar etiquetas de âmbito para políticas de filtro](scope-tags.md).



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

## <a name="week-of-november-12-2018"></a>Semana de 12 de Novembro de 2018

### <a name="network-access-control-nac-support-for-citrix-sso-for-ios----3259404---"></a>Suporte de Access Control (NAC) para Citrix SSO para iOS de rede <!-- 3259404 -->

Citrix lançou uma atualização para o Gateway da Citrix para permitir o controlo de acesso de rede (NAC) para Citrix SSO para iOS no Intune. Pode optar por incluir um ID de dispositivo de um perfil VPN no Intune e, em seguida, enviar este perfil para seus dispositivos iOS. Terá de instalar a atualização mais recente para o Gateway da Citrix para utilizar esta funcionalidade.

[Configurar definições de VPN em dispositivos iOS](vpn-settings-ios.md#base-vpn-settings) fornece mais informações sobre como usar o NAC, incluindo alguns requisitos adicionais. 

## <a name="week-of-november-5-2018"></a>Semana de 5 de novembro de 2018

### <a name="support-for-ios-12-oauth-in-ios-email-profiles---2155106---"></a>Suporte para o OAuth do iOS 12 nos perfis de e-mail iOS <!--2155106 -->

Os perfis de e-mail iOS do Intune suportam o Open Authorization (OAuth) do iOS 12. Para ver esta funcionalidade, crie um novo perfil (**Configuração do Dispositivo** > **Perfis** > **Criar perfil**  >  **iOS** para a plataforma > **E-mail** para o tipo de perfil) ou atualize um perfil de e-mail iOS existente. Se ativar o OAuth num perfil que já foi implementado para utilizadores, será pedido aos utilizadores que autentiquem e transfiram novamente o respetivo e-mail.

Pode obter mais informações sobre como utilizar o OAuth num perfil de e-mail em [iOS email profiles](email-settings-ios.md) (Perfis de e-mail iOS).

### <a name="autopilot-support-for-hybrid-azure-active-directory-joined-devices-preview----1048100--"></a>Suporte do Autopilot para dispositivos associados ao Azure Active Directory híbrido (Pré-visualização) <!-- 1048100-->
Agora pode configurar dispositivos associados ao Azure Active Directory híbrido com o Autopilot. Os dispositivos têm de ser associados à rede da sua organização para utilizar a funcionalidade Autopilot híbrida. Para obter mais informações, veja [Implementar dispositivos associados ao Azure Active Directory híbrido com o Intune e o Windows Autopilot](windows-autopilot-hybrid.md).
Esta funcionalidade será implementada para a base de utilizadores nos próximos dias. Assim, poderá não conseguir seguir estes passos até que a mesma seja implementada na sua conta.

## <a name="week-of-october-29-2018"></a>Semana de 29 de outubro de 2018

### <a name="app-management"></a>Gestão de aplicações

#### <a name="require-non-biometric-pin-after-a-specified-timeout----1506985---"></a>Exigir um PIN não biométrico após um tempo limite especificado <!-- 1506985 -->
Ao exigir um PIN não biométrico após um tempo limite especificado pelo administrador, o Intune fornece segurança melhorada para aplicações com Gestão de Aplicações Móveis (MAM) ativada ao restringir a utilização da identificação biométrica para aceder a dados da empresa. As definições afetam os utilizadores que dependem do Touch ID (iOS), Face ID (iOS), Android Biometric ou outros métodos de autenticação biométricos futuros para aceder a aplicações com APP/MAM ativada. Estas definições permitem que os administradores do Intune tenham um controlo mais abrangente sobre o acesso do utilizador, ao eliminar os casos em que um dispositivo com múltiplas impressões digitais ou outros métodos de acesso biométrico pode revelar dados da empresa a um utilizador errado. No portal do Azure, abra o **Microsoft Intune**. Selecione **Aplicações do cliente** > **Políticas de proteção de aplicações** > **Adicionar uma política** > **Definições**. Localize a secção **Acesso** para obter definições específicas. Para obter informações sobre as definições de acesso, veja as [definições do iOS](app-protection-policy-settings-ios.md#access-settings) e as [definições do Android](app-protection-policy-settings-android.md#access-settings).

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


## <a name="week-of-october-15-2018"></a>Semana de 15 de outubro de 2018

### <a name="pin-prompt-when-you-change-fingerprints-or-face-id-on-an-ios-device-----2637704----"></a>Pedido de PIN quando altera impressões digitais ou o Face ID num dispositivo iOS <!-- 2637704  -->
Agora é pedido um PIN aos utilizadores após fazerem alterações biométricas no respetivo dispositivo iOS. Isto inclui alterações ao nível de impressões digitais ou do Face ID registados. A altura em que o pedido é apresentado depende da configuração do tempo limite *Verificar novamente os requisitos de acesso após (minutos)*.  Quando não está definido nenhum PIN, é pedido ao utilizador para configurar um. 
 
Esta funcionalidade só está disponível para iOS e requer a participação de aplicações que integrem o SDK da aplicação Intune para iOS, versão 9.0.1 ou posterior. Precisa da integração do SDK para que o comportamento possa ser imposto nas aplicações de destino. Esta integração decorre de forma gradual e está dependente das equipas específicas da aplicação. Algumas aplicações participantes incluem: WXP, Outlook, Managed Browser e Yammer.


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




## <a name="week-of-september-24-2018"></a>Semana de 24 de setembro de 2018

### <a name="microsoft-365-device-management-administration-center----3078424---"></a>Centro de administração da Gestão de Dispositivos do Microsoft 365 <!-- 3078424 -->
Tendo em conta que uma das promessas do Microsoft 365 é a administração simplificada, temos vindo a integrar, ao longo dos anos, os serviços de back-end do Microsoft 365 para fornecer cenários ponto a ponto, como o acesso condicional do Intune e do Azure AD. O novo [Centro de administração do Microsoft 365](http://devicemanagement.microsoft.com) é o lugar certo para consolidar, simplificar e integrar a experiência de administração. A área de trabalho de especialista para a Gestão de Dispositivos fornece acesso fácil a todas as informações e tarefas de gestão de dispositivos e aplicações de que a sua organização precisa. Esperamos que esta se torne na principal área de trabalho da cloud das equipas de informática de utilizador final empresarial.

### <a name="support-for-more-third-party-certification-authorities-ca----3093107---"></a>Suporte para mais autoridades de certificação de terceiros (CA) <!-- 3093107 -->
Ao utilizar o protocolo SCEP (Simple Certificate Enrollment Protocol), agora pode emitir novos certificados e renovar certificados em dispositivos móveis com o Windows, iOS, Android e macOS.

### <a name="intune-moves-to-support-ios-10-and-later----2454656---"></a>O Intune suporta agora o iOS 10 e versões posteriores <!-- 2454656 -->  
A inscrição do Intune, o Portal da Empresa e o browser gerido agora suportam apenas dispositivos iOS com o iOS 10 e versões posteriores. Para verificar que dispositivos ou utilizadores são afetados na sua organização, aceda ao Intune no portal do Azure > **Dispositivos** > **Todos os dispositivos**. Filtre por SO e, em seguida, clique em **Colunas** para ver os detalhes da versão do SO. Peça a esses utilizadores para atualizarem os respetivos dispositivos para uma versão suportada do SO.  

Se tiver um dos dispositivos listados abaixo ou quiser inscrever um deles, tenha em atenção que só suportam o iOS 9 e versões anteriores.  Para continuar a aceder ao Portal da Empresa do Intune, tem de fazer a atualização para dispositivos que suportem o iOS 10 ou versões posteriores:  

* iPhone 4S 
* iPod Touch  
* iPad 2 
* iPad (3ª Geração) 
* iPad Mini (1ª Geração)  

## <a name="week-of-september-17-2018"></a>Semana de 17 de setembro de 2018

### <a name="app-management"></a>Gestão de aplicações

### <a name="remove-duplication-of-app-protection-status-tiles----3083391---"></a>Remover a duplicação dos mosaicos de estado da proteção da aplicação <!-- 3083391 -->
Os mosaicos **Estado do utilizador para iOS** e **Estado do utilizador para Android** eram apresentados nas páginas **Aplicações do Cliente – Descrição Geral** e **Aplicações do Cliente – Estado de proteção de aplicação**. Os mosaicos de estado foram removidos da página **Aplicações do Cliente – Descrição Geral** para evitar a duplicação. 

## <a name="week-of-august-27-2018"></a>Semana de 27 de agosto de 2018

### <a name="app-management"></a>Gestão de aplicações

#### <a name="packet-tunnel-support-for-ios-per-app-vpn-profiles-for-custom-and-pulse-secure-connection-types----1520957---"></a>Suporte de túnel de pacotes para perfis VPN por aplicação iOS para tipos de ligações personalizadas e Pulse Secure <!-- 1520957 -->
Ao utilizar perfis VPN por aplicação iOS, pode optar por utilizar o túnel de camada de aplicação (proxy-de-aplicação) ou o túnel de nível do pacote (pacote-túnel). Estas opções estão disponíveis com os seguintes tipos de ligação:
- VPN Personalizada
- Pulse Secure, se não tiver a certeza sobre o valor a utilizar, consulte a documentação do seu fornecedor de VPN.

#### <a name="delay-when-ios-software-updates-are-shown-on-the-device----1949583---"></a>Atrasar quando as atualizações de software iOS são apresentadas no dispositivo <!-- 1949583 -->
Em Intune > **Atualizações de Software** > **Atualizar políticas para iOS**, pode configurar os dias e as horas em que não pretende que os dispositivos instalem as atualizações. Numa atualização futura, poderá atrasar a apresentação de uma atualização de software no dispositivo, entre 1 a 90 dias. 
[Configurar as políticas de atualização de iOS no Microsoft Intune](software-updates-ios.md) lista as definições atuais.

#### <a name="office-365-proplus-version----2213968---"></a>Office 365 versão ProPlus <!-- 2213968 -->
Ao atribuir as aplicações do Office 365 ProPlus a dispositivos com o Windows 10 com o Intune, poderá selecionar a versão do Office. No portal do Azure, selecione **Microsoft Intune** > **Aplicações** > **Adicionar Aplicações**. Em seguida, selecione **Conjunto de Aplicações Office 365 ProPlus (Windows 10)** na lista suspensa **Tipo**. Selecione **Definições do conjunto de aplicações** para apresentar o painel associado. Defina **Atualizar Canal** para um valor, como **Mensal**. Opcionalmente, remova a outra versão do Office (msi) dos dispositivos de utilizador final ao selecionar **Sim**. Selecione **Específico** para instalar uma versão específica do Office no canal selecionado em dispositivos de utilizador final. Agora, pode selecionar a **Versão específica** do Office a utilizar. As versões disponíveis serão alteradas ao longo do tempo. Por conseguinte, ao criar uma nova implementação, as versões disponíveis podem ser mais recentes e não ter determinadas versões mais antigas disponíveis. As implementações atuais continuarão a implementar a versão mais antiga, mas a lista de versões será constantemente atualizada por canal. Para obter mais informações, veja [Overview of update channels for Office 365 ProPlus](https://docs.microsoft.com/DeployOffice/overview-of-update-channels-for-office-365-proplus) (Descrição geral dos canais de atualização do Office 365 ProPlus).

#### <a name="support-for-register-dns-setting-for-windows-10-vpn----2282852---"></a>Suporte para a definição do Registo de DNS para VPN do Windows 10 <!-- 2282852 -->
Com esta atualização, pode configurar perfis VPN do Windows 10 para registar dinamicamente os endereços IP atribuídos à interface de VPN com o DNS interno, sem a necessidade de utilizar perfis personalizados.
Para obter informações sobre as definições de perfis VPN atualmente disponíveis, veja [Windows 10 VPN settings](vpn-settings-windows-10.md) (Definições de VPN do Windows 10). 

#### <a name="the-macos-company-portal-installer-now-includes-the-version-number-in-the-installer-file-name---2652728--"></a>O instalador do Portal da Empresa para macOS inclui agora o número da versão no nome do ficheiro do instalador <!--2652728-->

#### <a name="ios-automatic-app-updates----2729759---"></a>Atualizações automáticas da aplicação do iOS <!-- 2729759 -->
As atualizações automáticas da aplicação funcionam em aplicações licenciadas para o dispositivo e o utilizador para o iOS Versão 11.0 e versões superiores.




### <a name="device-configuration"></a>Configuração do dispositivo

#### <a name="windows-hello-will-target-users-and-devices----1106609---"></a>O Windows Hello destina-se a utilizadores e dispositivos <!-- 1106609 -->
Quando cria uma política [Windows Hello para Empresas](windows-hello.md), esta aplica-se a todos os utilizadores numa organização (ao nível dos inquilinos). Com esta atualização, a política também pode ser aplicada a utilizadores ou dispositivos específicos através de uma política de configuração de dispositivos (**Configuração do Dispositivo** > **Perfis** > **Criar perfil** > **Identity Protection** > **Windows Hello para Empresas**).
No Intune no portal do Azure, a configuração e as definições do Windows Hello estão agora presentes tanto na **Inscrição de dispositivos** como na **Configuração do dispositivo**. A **Inscrição de dispositivos** destina-se a toda a organização (ao nível dos inquilinos) e suporta o Windows AutoPilot (OOBE). A **Configuração do dispositivo** destina-se a dispositivos e utilizadores através de uma política aplicada durante o registo.
Esta funcionalidade aplica-se a:  
- Windows 10 e posterior
- Windows Holographic for Business

#### <a name="zscaler-is-an-available-connection-for-vpn-profiles-on-ios----1769858---"></a>Zscaler é uma ligação disponível para perfis VPN em dispositivos iOS <!-- 1769858 -->
Quando cria um perfil de configuração de dispositivo VPN de iOS (**Configuração do dispositivo** > **Perfis** > **Criar perfil** > **iOS** plataforma > **VPN** tipo de perfil), existem vários tipos de ligação, incluindo Cisco, Citrix e muito mais. Esta atualização adiciona o Zscaler como um tipo de ligação. 
A página [Definições de VPN para dispositivos com iOS](vpn-settings-ios.md) lista os tipos de ligação disponíveis.

#### <a name="fips-mode-for-enterprise-wi-fi-profiles-for-windows-10----1879077---"></a>Modo FIPS para perfis de Wi-Fi de Empresas para o Windows 10 <!-- 1879077 -->
Agora pode ativar o modo FIPS (Federal Information Processing Standards) para perfis de Wi-Fi de Empresas para o Windows 10 no Intune no portal do Azure. Certifique-se de que o modo FIPS está ativado na sua infraestrutura de Wi-Fi se o ativar nos seus perfis de Wi-Fi.
O artigo [Definições de Wi-Fi para dispositivos com o Windows 10 ou posterior no Intune](wi-fi-settings-windows.md) mostra-lhe como pode criar um perfil de Wi-Fi.

#### <a name="control-s-mode-on-windows-10-and-later-devices---public-preview----1958649---"></a>Controle o modo S nos dispositivos Windows 10 e posteriores – pré-visualização pública <!-- 1958649 -->
Com a atualização desta funcionalidade, poderá criar um perfil de configuração de dispositivos que retire um dispositivo com o Windows 10 do modo S ou que impeça os utilizadores de retirarem o dispositivo do modo S. Esta funcionalidade está em Intune > **Configuração do dispositivo** > **Perfis** >  **Windows 10 e versões posteriores** > **Atualização da edição e alteração de modo**.
[Introdução ao Windows 10 no modo S](https://www.microsoft.com/windows/s-mode) fornece mais informações sobre o modo S.
Aplica-se a: à versão mais recente do [Windows Insider](https://docs.microsoft.com/windows-insider/at-work-pro/) (período de pré-visualização).


#### <a name="windows-defender-atp-configuration-package-automatically-added-to-configuration-profile----2144658---"></a>Pacote de configuração do Windows Defender ATP adicionado automaticamente ao perfil de configuração <!-- 2144658 -->
Ao utilizar dispositivos de [Proteção Avançada Contra Ameaças e integração](advanced-threat-protection.md#onboard-devices-using-a-configuration-profile) no Intune, tinha de transferir um pacote de configuração e adicioná-lo ao seu perfil de configuração. Com esta atualização, o Intune obtém automaticamente o pacote a partir do Centro de Segurança do Windows Defender e adiciona-o ao seu perfil.
Aplica-se ao Windows 10 e posterior.

#### <a name="require-users-to-connect-during-device-setup---2311457--"></a>Exigir que os utilizadores estabeleçam ligação durante a configuração do dispositivo <!--2311457-->
Agora pode definir perfis de dispositivos de modo a exigir que o dispositivo esteja ligado a uma rede antes de avançar para além da página Rede durante a configuração do Windows 10. Enquanto esta funcionalidade estiver em pré-visualização, é necessário que tenha a versão 1809 ou versões posteriores do Windows Insider para utilizar esta definição.
Aplica-se a: à versão mais recente do [Windows Insider](https://docs.microsoft.com/windows-insider/at-work-pro/) (período de pré-visualização).


#### <a name="restricts-apps-and-block-access-to-company-resources-on-ios-and-android-enterprise-devices----2451462---"></a>Restringir aplicações e bloquear o acesso aos recursos da empresa em dispositivos iOS e Android Enterprise <!-- 2451462 -->
Em **Conformidade do dispositivo** > **Políticas** > **Criar política** > **iOS** > **Segurança do Sistema**, há uma nova definição de **Aplicações restritas**. Esta nova definição utiliza uma política de conformidade para bloquear o acesso aos recursos da empresa, caso determinadas aplicações estejam instaladas no dispositivo. O dispositivo é considerado não compatíveis até que as aplicações restritas sejam removidas do dispositivo.
Aplica-se a: iOS

#### <a name="modern-vpn-support-updates-for-ios----2459928-1819876-and-2650856---"></a>A VPN moderna suporta atualizações para iOS <!-- 2459928, 1819876, and 2650856 -->
Esta atualização adiciona suporte para os seguintes clientes VPN do iOS: 
- F5 Access (versão 3.0.1 e superior)
- Citrix SSO
- Palo Alto Networks GlobalProtect (versão 5.0 e superior). Também nesta atualização:
- O nome do tipo de ligação **F5 Access** foi alterado para **F5 Access Legacy** para o iOS.
- O nome do tipo de ligação **Palo Alto Networks GlobalProtect** foi alterado para **Palo Alto Networks GlobalProtect (legacy)** para o iOS.
Os perfis existentes com estes tipos de ligação continuam a funcionar com o respetivo cliente VPN legado. Se estiver a utilizar o Cisco Legacy AnyConnect, F5 Access Legacy, VPN do Citrix ou Palo Alto Networks GlobalProtect (versão 4.1 ou anterior) com o iOS, deve mudar para as novas aplicações. Faça-o assim que possível para garantir que o acesso VPN está disponível para dispositivos iOS, conforme os mesmos são atualizados para iOS 12.
Para obter mais informações sobre o iOS 12 e os perfis VPN, veja o [Blogue da Equipa de Suporte do Microsoft Intune](https://go.microsoft.com/fwlink/?linkid=2013806).

#### <a name="export-azure-classic-portal-compliance-policies-to-recreate-these-policies-in-the-intune-azure-portal----2469637---"></a>Exportar políticas de conformidade do portal clássico do Azure para recriar estas políticas no Intune no portal do Azure <!-- 2469637 -->
As políticas de conformidade que criou no portal clássico do Azure serão preteridas. Pode rever e eliminar quaisquer políticas de conformidade existentes, mas não pode atualizá-las. Se precisar de migrar políticas de conformidade para o Intune no portal do Azure atual, pode exportar as políticas sob a forma de um ficheiro separado por vírgulas (ficheiro *.csv*). Em seguida, utilize os detalhes no ficheiro para recriar estas políticas no Intune no portal do Azure.

> [!IMPORTANT]
> Quando o portal clássico do Azure for descontinuado, deixará de conseguir aceder ou ver as suas políticas de conformidade. Por isso, não se esqueça de as exportar e recriar no portal do Azure antes de o portal clássico do Azure ser descontinuado.

#### <a name="better-mobile---new-mobile-threat-defense-partner----22662717---"></a>Better Mobile – novo parceiro de Defesa Contra Ameaças para Dispositivos Móveis <!-- 22662717 -->
Pode controlar o acesso a recursos empresariais a partir de dispositivos móveis através do acesso condicional com base na avaliação de riscos realizada pelo Better Mobile, uma solução de Defesa Contra Ameaças para Dispositivos Móveis que está integrada com o Microsoft Intune.

### <a name="device-enrollment"></a>Inscrição de dispositivos

#### <a name="lock-the-company-portal-in-single-app-mode-until-user-sign-in---1067692---"></a>Bloquear o Portal da Empresa no modo de aplicação única até o utilizador iniciar sessão <!--1067692 --> 
Agora pode optar por executar o Portal da Empresa no modo de Aplicação Única se autenticar um utilizador através do Portal da Empresa em vez do Assistente de Configuração durante a inscrição de DEP. Esta opção bloqueia o dispositivo imediatamente após a conclusão do Assistente de Configuração, para que um utilizador tenha de iniciar sessão para aceder ao dispositivo. Este processo assegura que o dispositivo conclui a inclusão e não fica órfão num estado sem qualquer utilizador ligado.

#### <a name="assign-a-user-and-friendly-name-to-an-autopilot-device---1346521---"></a>Atribuir um utilizador e um nome amigável a um dispositivo do Autopilot <!--1346521 -->
Agora pode [atribuir um utilizador a um único dispositivo do Autopilot](enrollment-autopilot.md). Os administradores também serão capazes de atribuir nomes amigáveis para dar as boas-vindas ao utilizador quando estão a configurar o dispositivo com o Autopilot.
Aplica-se a: à versão mais recente do [Windows Insider](https://docs.microsoft.com/windows-insider/at-work-pro/) (período de pré-visualização).

#### <a name="use-vpp-device-licenses-to-pre-provision-the-company-portal-during-dep-enrollment----1608345---"></a>Utilizar licenças de dispositivos VPP para aprovisionar previamente o Portal da Empresa durante a inscrição do DEP <!-- 1608345 -->
Agora pode utilizar licenças de dispositivos do Programa de Compras em Volume (VPP) para aprovisionar previamente o Portal da Empresa durante as inscrições do Programa de Registo de Aparelho (DEP). Para tal, ao [criar ou editar um perfil de inscrição](device-enrollment-program-enroll-ios.md#create-an-apple-enrollment-profile), especifique o token VPP que pretende utilizar para instalar o Portal da Empresa. Certifique-se de que o token não expira e que tem licenças suficientes para a aplicação Portal da Empresa. Nos casos em que o token expirar ou esgotar as licenças, o Intune irá iniciar o Portal da Empresa a partir da App Store (esta ação irá exigir um ID Apple).

#### <a name="confirmation-required-to-delete-vpp-token-that-is-being-used-for-company-portal-pre-provisioning----2237634---"></a>Confirmação necessária para eliminar o token VPP que está a ser utilizado para aprovisionar previamente o Portal da Empresa <!-- 2237634 -->
É necessária uma confirmação para eliminar um token VPP (Volume Purchase Program) se o mesmo estiver a ser utilizado para aprovisionar previamente o Portal da Empresa durante a inscrição no DEP.

#### <a name="block-windows-personal-device-enrollments----1849498---"></a>Bloquear inscrições de dispositivos pessoais do Windows <!-- 1849498 -->
Pode [impedir que os dispositivos pessoais do Windows](enrollment-restrictions-set.md#set-device-type-restrictions) se inscrevam com a [gestão de dispositivos móveis](windows-enroll.md) no Intune. A inscrição de dispositivos com o [agente de PC do Intune](manage-windows-pcs-with-microsoft-intune.md) não pode ser bloqueada com esta funcionalidade. Esta funcionalidade será implementada durante as próximas semanas, pelo que poderá não a ver imediatamente na interface de utilizador.

#### <a name="specify-machine-name-patterns-in-an-autopilot-profile---1849855--"></a>Especificar os padrões de nome de computador num perfil do Autopilot <!--1849855-->
Pode [especificar um modelo de nome do computador](enrollment-autopilot.md#create-an-autopilot-deployment-profile) para gerar e definir o [nome do computador](https://docs.microsoft.com/windows/client-management/mdm/accounts-csp) durante a inscrição do Autopilot. Aplica-se a: à versão mais recente do [Windows Insider](https://docs.microsoft.com/windows-insider/at-work-pro/) (período de pré-visualização).


#### <a name="for-windows-autopilot-profiles-hide-the-change-account-options-on-the-company-sign-in-page-and-domain-error-page---1901669---"></a>Para os perfis do Windows Autopilot, oculte as opções de alteração de conta na página de início de sessão da empresa e na página de erro do domínio <!--1901669 -->
Existem [novas opções de perfil do Windows Autopilot](enrollment-autopilot.md#create-an-autopilot-deployment-profile) para os administradores ocultarem as opções de alteração de conta nas páginas de início de sessão da empresa e de erro no domínio. Para ocultar essas opções, é preciso configurar a Imagem Corporativa da Empresa no Azure Active Directory. Aplica-se a: à versão mais recente do [Windows Insider](https://docs.microsoft.com/windows-insider/at-work-pro/) (período de pré-visualização).



### <a name="device-management"></a>Gestão de dispositivos

#### <a name="delete-jamf-devices----2653306--"></a>Eliminar dispositivos Jamf <!-- 2653306-->
Pode eliminar dispositivos geridos pelo JAMF ao aceder a **Dispositivos** > selecionar o dispositivo Jamf > **Eliminar**.

#### <a name="change-terminology-to-retire-and-wipe----2175759---"></a>Alteração da terminologia para "extinguir" e "eliminar" <!-- 2175759 -->
Para ser consistente com o Graph API, os seguintes termos foram alterados na documentação e na interface de utilizador do Intune:
- **Remover dados da empresa** será alterado para "extinguir"
- **Reposição de fábrica** será alterado para **eliminar**

#### <a name="confirmation-dialog-if-admin-tries-to-delete-mdm-push-certificate----297909500--"></a>A caixa de diálogo de confirmação apresentada se o administrador tentar eliminar o Certificado Push de MDM <!-- 297909500-->
Se alguém tentar eliminar um Certificado Push de MDM da Apple, uma caixa de diálogo de confirmação apresenta o número de dispositivos iOS e macOS associados. Se o certificado for eliminado, será necessário inscrever novamente estes dispositivos.

### <a name="additional-security-settings-for-windows-installer----2282430---"></a>Definições de segurança adicionais para o Windows Installer <!-- 2282430 -->
Pode permitir que os utilizadores controlem a instalação de aplicações. Se estiver ativada, esta definição permite continuar as instalações que, caso contrário, seriam interrompidas devido a uma violação de segurança. Pode configurar o Windows Installer para utilizar permissões elevadas ao instalar programas num sistema. Além disso, pode ativar os itens do Windows Information Protection (WIP) para serem indexados e os metadados acerca dos mesmos para serem armazenados numa localização não encriptada. Quando a política está desativada, os itens protegidos pelo WIP não são indexados e não são apresentados nos resultados na Cortana ou no explorador de ficheiros. A funcionalidade destas opções está desativada por predefinição. 

### <a name="new-user-experience-update-for-the-company-portal-website---2000968---"></a>Nova atualização da experiência de utilizador do site do Portal da Empresa <!--2000968 -->
Adicionámos novas funcionalidades ao site do Portal da Empresa com base no feedback dos clientes. Irá ver uma melhoria significativa na facilidade de utilização e nas funcionalidades existentes nos seus dispositivos. Algumas áreas do site &ndash; tais como detalhes do dispositivo, feedback e suporte e descrição geral do dispositivo &ndash; receberam uma nova estrutura moderna e reativa. A atualização inclui ainda:

- Fluxos de trabalho simplificados em todas as plataformas de dispositivos
- Fluxos de inscrição e identificação de dispositivos melhorados
- Mensagens de erro mais úteis
- Linguagem mais simples, menos termos técnicos
- Capacidade de partilhar ligações diretas para as aplicações
- Desempenho melhorado para grandes catálogos de aplicações
- Acessibilidade melhorada para todos os utilizadores  

A [documentação do site do Portal da Empresa do Intune](https://docs.microsoft.com/intune-user-help/using-the-intune-company-portal-website) foi atualizada para refletir estas alterações. Para ver um exemplo das melhorias ao nível das aplicações, veja [Atualização da IU para aplicações de utilizadores finais do Intune](whats-new-app-ui.md).  

### <a name="monitor-and-troubleshoot"></a>Monitorizar e resolver problemas

#### <a name="enhanced-jailbreak-detection-in-compliance-reporting---2198738---"></a>Deteção de jailbreak avançada no relatório de conformidade<!-- 2198738 -->
Os estados da definição de deteção de jailbreak avançada são agora apresentados em todos os relatórios de conformidade na consola de administração.

### <a name="role-based-access-control"></a>Controlo de acesso baseado em funções

#### <a name="scope-tags-for-policies---1081974---"></a>Etiquetas de âmbito para políticas <!--1081974 -->
Pode [criar etiquetas de âmbito](scope-tags.md) para restringir o acesso aos recursos do Intune. Adicione uma etiqueta de âmbito a uma atribuição de função e, em seguida, adicione a etiqueta de âmbito a um perfil de configuração. A função apenas terá acesso aos recursos com perfis de configuração com etiquetas de âmbito correspondentes (ou nenhuma etiqueta de âmbito).

## <a name="week-of-august-14-2018"></a>Semana de 14 de agosto de 2018

### <a name="macos-support-for-apple-device-enrollment-program----747651---"></a>Suporte do macOS para o Programa de Inscrição de Dispositivos da Apple <!-- 747651 -->
Agora, o Intune suporta a inscrição de dispositivos macOS no Programa de Registo de Aparelho da Apple (DEP). Para obter mais informações, veja [Inscrever automaticamente dispositivos macOS com o Programa de Registo de Aparelho da Apple](device-enrollment-program-enroll-macos.md).

## <a name="week-of-july-23-2018"></a>Semana de 23 de julho de 2018

### <a name="app-management"></a>Gestão de aplicações

#### <a name="line-of-business-lob-app-support-for-macos----1895847---"></a>Suporte de aplicações de linha de negócio (LOB) para macOS <!-- 1895847 -->
O Microsoft Intune permite que as aplicações LOB para macOS sejam implementadas como **Necessário** ou **Disponível com inscrição**. Os utilizadores finais podem implementar as aplicações como **Disponível** com o Portal da Empresa para macOS ou com o [site do Portal da Empresa](https://portal.manage.microsoft.com).

#### <a name="ios-built-in-app-support-for-kiosk-mode----2051098---"></a>Suporte de aplicações integradas para iOS para o modo de quiosque <!-- 2051098 -->
Para além das Aplicações da Loja e das Aplicações Geridas, pode selecionar uma Aplicação Integrada (como o Safari) que executa em modo de quiosque num dispositivo iOS.

#### <a name="edit-your-office-365-pro-plus-app-deployments----2150145---"></a>Editar as implementações de aplicações do Office 365 Pro Plus <!-- 2150145 -->
Enquanto administrador do Microsoft Intune, tem maior capacidade de editar as suas implementações de aplicações do Office 365 Pro Plus. Adicionalmente, já não precisa de eliminar as suas implementações para alterar qualquer uma das propriedades do conjunto. No portal do Azure, selecione **Microsoft Intune** > **Aplicações do cliente** > **Aplicações**. A partir da lista de aplicações, selecione o Office 365 Pro Plus Suite.  


#### <a name="updated-intune-app-sdk-for-android-is-now-available----2744271--"></a>O SDK da Aplicação do Intune para Android atualizado já está disponível <!-- 2744271-->

Uma versão atualizada do SDK da Aplicação do Intune para Android está disponível para suportar o lançamento do Android P. Se é um programador de aplicações e utiliza o SDK do Intune para Android, tem de instalar a versão atualizada do SDK da aplicação do Intune para garantir que a funcionalidade do Intune nas suas aplicações Android continuam a funcionar conforme esperado nos dispositivos Android P. Esta versão do SDK da Aplicação do Intune fornece um plug-in integrado que efetua as atualizações do SDK. Não precisa de reescrever o código existente que estiver integrado. Para obter mais detalhes, veja [SDK do Intune para Android](https://github.com/msintuneappsdk/ms-intune-app-sdk-android). Se estiver a utilizar o estilo de criação de distintivos antigo do Intune, recomendamos que utilize o ícone de porta-documentos. Para obter informações corporativas, veja [este repositório do GitHub](https://github.com/msintuneappsdk/intune-app-partner-badge).


### <a name="device-configuration"></a>Configuração do dispositivo

#### <a name="create-device-compliance-policy-using-firewall-settings-on-macos-devices----1497640---"></a>Criar política de conformidade de dispositivos com as definições de firewall em dispositivos macOS <!-- 1497640 -->
Quando criar uma nova política de conformidade do macOS (**Conformidade do dispositivo** > **Políticas** > **Criar política** > **Plataforma: macOS** > **Segurança do sistema**), estarão disponíveis algumas definições de **Firewall** novas: 

- **Firewall**: Configurar ligações de entrada como são processadas no seu ambiente.
- **Ligações de entrada**: **Bloco** todas as ligações recebidas, exceto as necessárias para serviços básicos de internet, como DHCP, Bonjour e IPSec. Esta definição também bloqueia todos os serviços de partilha.
- **O modo invisível**: **Ativar** Modo Furtivo para impedir que o dispositivo responda aos pedidos de pesquisa. O dispositivo continua a responder a pedidos recebidos de aplicações autorizadas.

Aplica-se a: macOS 10.12 e posterior

#### <a name="new-wi-fi-device-configuration-profile-for-windows-10-and-later----1879077---"></a>Novo perfil de configuração de dispositivos Wi-Fi para Windows 10 e posterior <!-- 1879077 -->
Atualmente, pode importar e exportar perfis Wi-Fi através de ficheiros XML. Com esta atualização, pode criar um perfil de configuração de dispositivos Wi-Fi diretamente no Intune, tal como o faria em algumas outras plataformas.

Para criar o perfil, abra o menu **Configuração do dispositivo** > **Perfis** > **Criar Perfil** > **Windows 10 e versões posteriores** > **Wi-Fi**. 

Aplica-se ao Windows 10 e posterior.

#### <a name="kiosk---obsolete-is-grayed-out-and-cant-be-changed----2149998---"></a>A funcionalidade Quiosque (Obsoleto) foi desativada e não pode ser alterada <!-- 2149998 -->
A [funcionalidade Quiosque](device-restrictions-windows-10.md#kiosk-preview---obsolete) (**Configuração do dispositivo** > **Perfis** > **Criar perfil** > **Windows 10 e versões posteriores** > **Restrições do dispositivo**) está obsoleta e foi substituída pelas [definições do Quiosque para Windows 10 e posterior](kiosk-settings.md). Com esta atualização, a funcionalidade **Quiosque – Obsoleto** foi desativada e a interface de utilizador não pode ser alterada nem atualizada. 

Para ativar o modo de quiosque, veja [Definições de quiosque para Windows 10 e posterior](kiosk-settings.md).

Aplica-se ao Windows 10 e posterior e ao Windows Holographic for Business

#### <a name="apis-to-use-3rd-party-certification-authorities----2184013---"></a>APIs para utilização de autoridades de certificação externas <!-- 2184013 -->
Nesta atualização, foi disponibilizada uma API Java que permite a integração de autoridades de certificação externas no Intune e no SCEP. A partir daí, os utilizadores podem adicionar o certificado SCEP a um perfil e aplicá-lo aos dispositivos com MDM.

Atualmente, o Intune suporta [pedidos de SCEP que utilizam os Serviços de Certificados do Active Directory](certificates-scep-configure.md).

#### <a name="toggle-to-show-or-not-show-the-end-session-button-on-a-kiosk-browser----2455253---"></a>Alternar entre mostrar ou não mostrar o botão Terminar Sessão num browser do Quiosque <!-- 2455253 -->
Agora pode configurar as opções para determinar se os browsers do Quiosque devem ou não mostrar o botão Terminar Sessão. Pode ver o controlo em **Configuração do dispositivo** > **Quiosque (pré-visualização)** > **Browser da Web do Quiosque**. Se o botão estiver ativado e quando o utilizador clicar no mesmo, a aplicação pede confirmação para terminar a sessão. Ao confirmar, o browser limpa todos os dados de navegação e regressa ao URL predefinido.

#### <a name="create-an-esim-cellular-configuration-profile----2564077---"></a>Criar um perfil de configuração de rede móvel eSIM <!-- 2564077 -->
Em **Configuração do dispositivo**, pode criar um perfil celular eSIM. Pode importar um ficheiro com códigos de ativação de rede móvel fornecidos pela sua operadora móvel. Em seguida, poderá implementar estes perfis nos seus dispositivos Windows 10 compatíveis com eSIM LTE, como o Surface Pro LTE e outros dispositivos compatíveis com eSIM.

Verifique se os seus [dispositivos suportam perfis eSIM](https://support.microsoft.com/help/4020763/windows-10-use-esim-for-cellular-data).

Aplica-se ao Windows 10 e posterior. 




### <a name="device-enrollment"></a>Inscrição de dispositivos

#### <a name="automatically-mark-android-devices-enrolled-by-using-samsung-knox-mobile-enrollment-as-corporate----2404851---"></a>Marcar automaticamente dispositivos Android inscritos através do Samsung Knox Mobile Enrollment como "empresarial". <!-- 2404851 -->
Por predefinição, os dispositivos Android inscritos através do Samsung Knox Mobile Enrollment são marcados como **empresarial** em **Propriedade do Dispositivo**. Não tem de identificar manualmente os dispositivos empresariais através dos números de série ou do IMEI antes da inscrição com o Knox Mobile Enrollment.

### <a name="device-management"></a>Gestão de dispositivos

#### <a name="bulk-delete-devices-on-devices-blade----1793693---"></a>Eliminar dispositivos em massa no painel Dispositivos <!-- 1793693 -->

Agora pode eliminar múltiplos dispositivos de uma só vez no painel Dispositivos. Selecione **Dispositivos** > **Todos os dispositivos** > selecione os dispositivos que pretende eliminar > **Eliminar**. Será apresentado um alerta para os dispositivos que não puderem ser eliminados.

## <a name="week-of-july-16-2018"></a>Semana de 16 de julho de 2018  

### <a name="more-opportunities-to-sync-in-the-company-portal-app-for-windows"></a>Mais oportunidades de sincronização na aplicação Portal da Empresa para Windows  
Agora a aplicação Portal da Empresa para Windows permite-lhe iniciar uma sincronização a partir do menu Iniciar e da barra de tarefas do Windows. Esta funcionalidade é especialmente útil se a sua tarefa for sincronizar dispositivos e obter acesso a recursos da empresa. Para aceder à nova funcionalidade, clique com o botão direito do rato no ícone do Portal da Empresa que está afixado à barra de tarefas ou menu Iniciar. Nas opções do menu (também conhecido como lista de atalhos), selecione **Sincronizar este dispositivo**. O Portal da Empresa será aberto na página **Definições** e irá iniciar a sincronização. Para saber mais sobre a nova funcionalidade, veja [Novidades na IU](whats-new-app-ui.md).   

### <a name="new-browsing-experiences-in-the-company-portal-app-for-windows"></a>Novas experiências de navegação na aplicação Portal da Empresa para Windows  

Ao navegar ou procurar aplicações na aplicação Portal da Empresa para Windows, pode alternar entre a vista **Mosaicos** existente e a vista **Detalhes** recentemente adicionada. A nova vista apresenta os detalhes das aplicações, como o nome, o publicador, a data de publicação e o estado da instalação.  

A vista **Instalado** da página **Aplicações** permite-lhe ver detalhes sobre as instalações de aplicações concluídas e em curso. Para ver o aspeto da nova vista, veja [Novidades na IU](whats-new-app-ui.md).  
### <a name="improved-company-portal-app-experience-for-device-enrollment-managers"></a>Experiência da aplicação Portal da Empresa melhorada para gestores de inscrições de dispositivos  
Quando um gestor de inscrições de dispositivos (DEM) iniciar sessão na aplicação Portal da Empresa para Windows, agora a aplicação só apresentará o dispositivo atual do DEM. Esta melhoria irá reduzir os erros de tempo limite que ocorriam quando a aplicação tentava mostrar todos os dispositivos inscritos pelo DEM.  


## <a name="week-of-july-9-2018"></a>Semana de 9 de julho de 2018

### <a name="app-management"></a>Gestão de aplicações

### <a name="block-app-access-based-on-unapproved-device-vendors-and-models-----1425689----"></a>Bloquear o acesso a aplicações baseado em fornecedores e modelos de dispositivos não aprovados <!-- 1425689 ! -->
O administrador de TI do Intune pode impor uma lista específica de fabricantes Android e/ou de modelos iOS nas Políticas de Proteção de Aplicações do Intune. O administrador de TI pode fornecer uma lista separada por ponto e vírgula de fabricantes para políticas para Android e de modelos de dispositivos para políticas iOS. As Políticas de Proteção de Aplicações do Intune destinam-se apenas a Android e iOS. Existem duas ações separadas que podem ser realizadas na lista especificada:
- O bloqueio do acesso a aplicações em dispositivos não especificados.
- Uma eliminação seletiva de dados empresariais em dispositivos não especificados. 

O utilizador não conseguirá aceder à aplicação visada se os requisitos da política não forem cumpridos. Com base nas definições escolhidas, os dados empresariais do utilizador podem ser bloqueados ou eliminados seletivamente da aplicação. Nos dispositivos iOS, esta funcionalidade requer que a participação de aplicações (tais como o WXP, Outlook, Managed Browser, Yammer) integre o SDK da Aplicação Intune para que a funcionalidade seja imposta nas aplicações visadas. Esta integração decorre de forma gradual e está dependente das equipas específicas da aplicação. No Android, esta funcionalidade necessita da versão mais recente do Portal da Empresa. 

Nos dispositivos dos utilizadores finais, o cliente do Intune tomará medidas com base numa única correspondência das cadeias especificadas no painel Intune das Políticas de Proteção de Aplicações. Isto depende inteiramente do valor comunicado pelo dispositivo. Como tal, recomendamos que o administrador de TI se certifique de que o comportamento pretendido é preciso. Pode fazê-lo ao testar esta definição com base em vários fabricantes e modelos de dispositivos direcionados para um grupo de utilizadores pequeno. No Microsoft Intune, selecione **Aplicações do cliente** > **Políticas de proteção de aplicações** para ver e adicionar políticas de proteção de aplicações. Para obter mais informações sobre as políticas de proteção de aplicações, veja [O que são as políticas de proteção de aplicações?](app-protection-policy.md) e [Eliminação seletiva de dados através de ações de acesso das políticas de proteção de aplicações no Intune](app-protection-policies-access-actions.md).

### <a name="access-to-macos-company-portal-pre-release-build----1734766---"></a>Acesso à compilação de pré-lançamento do Portal da Empresa do macOS <!-- 1734766 -->
Com o Microsoft AutoUpdate, pode inscrever-se para receber compilações antecipadamente ao aderir ao programa Insider. A inscrição permitir-lhe-á utilizar o Portal da Empresa atualizado antes de este ser disponibilizado aos seus utilizadores finais. Para obter mais informações, veja o [blogue do Microsoft Intune](https://blogs.technet.microsoft.com/intunesupport/2018/07/13/use-microsoft-autoupdate-for-early-access-to-the-macos-company-portal-app/).

## <a name="week-of-july-2-2018"></a>Semana de 2 de julho de 2018

### <a name="app-management"></a>Gestão de aplicações

#### <a name="monitor-ios--app-configuration-status-per-device----880037---"></a>Monitorizar o estado de configuração da aplicação iOS por dispositivo <!-- 880037 -->
Enquanto administrador do Microsoft Intune, pode monitorizar o estado de configuração da aplicação iOS para cada dispositivo gerido. No **Microsoft Intune**, no portal do Azure, selecione **Dispositivos** > **Todos os dispositivos**. Na lista de dispositivos geridos, selecione um dispositivo específico para apresentar um painel do dispositivo. No painel do dispositivo, selecione **Configuração da aplicação**.

#### <a name="access-actions-for-app-protection-policies----1483510---"></a>Ações de acesso das políticas de proteção de aplicações <!-- 1483510 -->
Pode configurar políticas de proteção de aplicações para avisar, apagar ou bloquear explicitamente dispositivos que não estejam em conformidade. A ação *Apagar*, remove os seus dados empresariais de um dispositivo. Se ocorrer uma eliminação, o utilizador do dispositivo será notificado sobre os motivos da eliminação e os passos de remediação. Para algumas definições, como a versão mínima do SO, poderá realizar múltiplas ações, tais como bloquear e apagar. Tenha em atenção que estas ações são acionadas quando a aplicação é iniciada.

#### <a name="selective-wipe-of-organizations-app-data----1507030---"></a>Eliminação seletiva dos dados da aplicação da organização <!-- 1507030 -->
Os administradores podem agora configurar uma eliminação seletiva dos dados da organização como uma nova ação quando as condições de definições de Acesso de Políticas de Proteção de Aplicações (APP) não são cumpridas.  Esta funcionalidade ajuda os administradores a proteger e remover automaticamente dados confidenciais da organização de aplicações com base em critérios pré-configurados.

#### <a name="revoking-an-ios-app-purchased-through-vpp----1777384---"></a>Revogar uma aplicação iOS comprada através do VPP <!-- 1777384 -->
Enquanto administrador do Microsoft Intune, pode revogar todas as licenças de uma aplicação iOS selecionada comprada através do programa de compra em volume (VPP). Pode notificar os utilizadores quando uma aplicação com licença já não estiver atribuída aos mesmos. Revogar a licença de uma aplicação não desinstala a aplicação VPP relacionada do dispositivo. Para desinstalar uma aplicação VPP, tem de alterar a ação de atribuição para **Desinstalar**. A contagem de licenças recuperadas será refletida no nó **Aplicações Licenciadas** na carga de trabalho **Aplicação** do Intune. Para obter mais informações relacionadas com aplicações iOS obtidas pelo VPP, veja [Como gerir aplicações iOS compradas através de um programa de compra em volume com o Microsoft Intune](vpp-apps-ios.md).

#### <a name="updates-to-out-of-compliance-messages-in-company-portal-app----1832222---"></a>Atualizações às mensagens de não conformidade na aplicação Portal da Empresa <!-- 1832222 -->
Revimos as mensagens que são apresentadas aos utilizadores dos dispositivos quando um dispositivo não está em conformidade. As mensagens mantêm o significado original, mas foram atualizadas de modo a incluírem uma linguagem mais simples e menos termos técnicos. Também atualizámos as ligações para documentação e os passos de remediação.
O seguinte exemplo do texto anterior e do novo demonstra as melhorias que verá nas mensagens:
- **Antes de**: *Este dispositivo não contacte o serviço do Intune no período de tempo especificado exigido pelo administrador de TI. Para resolver este problema, abra a aplicação Portal da Empresa no seu dispositivo e clique no botão Verificar Conformidade.*
- **Depois de**: *O dispositivo não verificou com a sua organização em algum tempo. Para voltar a estabelecer ligação, abra a aplicação Portal da Empresa no seu dispositivo e toque em Verificar Definições no mesmo.*

#### <a name="revoke-ios-vpp-app-license----1863797---"></a>Revogar licença de aplicação iOS obtida pelo VPP <!-- 1863797 -->
Enquanto administrador, pode recuperar uma licença de aplicação iOS obtida pelo VPP atribuída a um utilizador ou dispositivo. Desinstalar uma aplicação iOS obtida pelo VPP também permitirá recuperar a licença da aplicação. Antes de desinstalar a aplicação, o utilizador do dispositivo tem de ser removido do grupo a que se destina a aplicação. Remover o utilizador ou o dispositivo do grupo evita ter de reinstalar a aplicação. Quando estes passos forem concluídos, pode optar por atribuir a licença da aplicação a outro utilizador ou dispositivo. Para obter mais informações sobre licenças de aplicação iOS obtida pelo VPP, veja [Gerir aplicações iOS compradas em volume no Microsoft Intune](vpp-apps-ios.md).

### <a name="device-configuration"></a>Configuração do dispositivo

#### <a name="select-device-categories-by-using-the-access-work-or-school-settings----1058963-eenotready---"></a>Selecionar as categorias de dispositivos através das definições de Acesso Profissional ou Escolar<!-- 1058963 eenotready --> 
Se tiver ativado o [mapeamento do grupo de dispositivos](https://docs.microsoft.com/intune/device-group-mapping), agora será pedido aos utilizadores no Windows 10 que selecionem uma categoria de dispositivos após a inscrição através do botão **Ligar** em **Definições** > **Contas** > **Acesso profissional ou escolar**. 

#### <a name="use-samaccountname-as-the-account-username-for-email-profiles----1500307---"></a>Utilizar sAMAccountName como o nome de utilizador da conta para perfis de e-mail <!-- 1500307 -->
Pode utilizar **sAMAccountName** no local como o nome de utilizador da conta para perfis de e-mail para Android, iOS e Windows 10. Também pode obter o domínio do atributo `domain` ou `ntdomain` no Azure Active Directory (Azure AD). Em alternativa, introduza um domínio estático personalizado.

Para utilizar esta funcionalidade, tem de sincronizar o atributo `sAMAccountName` do seu ambiente do Active Directory no local com o Azure AD.

Aplica-se ao [Android](email-settings-android.md), [iOS](email-settings-ios.md), [Windows 10 e posterior](email-settings-windows-10.md)

#### <a name="see-device-configuration-profiles-in-conflict----1556983---"></a>Ver perfis de configuração de dispositivos em conflito <!-- 1556983 -->
Em **Configuração do Dispositivo**, é apresentada uma lista dos perfis existentes. Com esta atualização, é adicionada uma nova coluna que fornece detalhes sobre os perfis que apresentam conflitos. Pode selecionar uma linha de conflito para ver a definição e o perfil que está em conflito. 

Saiba mais sobre como [gerir perfis de configuração](device-profile-monitor.md#view-conflicts).

#### <a name="new-status-for-devices-in-device-compliance----2308882---"></a>Novo estado dos dispositivos em Conformidade do dispositivo <!-- 2308882 -->
Em **Conformidade do dispositivo** > **Políticas** > selecione uma política > **Descrição geral**, são adicionados os novos estados que se seguem:
- com êxito
- erro
- conflito
- Pendente
- não aplicável Também é apresentada uma imagem que mostra a contagem de dispositivos de uma plataforma diferente. Por exemplo, se observar um perfil iOS, o novo mosaico mostra a contagem de dispositivos não iOS atribuídos a este perfil. Veja [Políticas de conformidade do dispositivo](compliance-policy-monitor.md#view-status-of-device-policies).

#### <a name="device-compliance-supports-3rd-party-anti-virus-solutions----2325484---"></a>A conformidade do dispositivo suporta soluções de antivírus de terceiros <!-- 2325484 -->
Quando cria uma política de conformidade do dispositivo (**conformidade do dispositivo** > **políticas** > **criar política**  >  **Plataforma: Windows 10 e posterior** > **definições** > **segurança do sistema**), existem novos **[segurança de dispositivo](compliance-policy-create-windows.md#windows-10-and-later-policy-settings)** opções: 
- **Antivírus**: Quando definido como **requerem**, pode verificar a conformidade com as soluções antivírus que estão registadas com o Centro de segurança do Windows, por exemplo, Symantec e o Windows Defender. 
- **AntiSpyware**: Quando definido como **requerem**, pode verificar a conformidade com as soluções de antispyware registados no Centro de segurança do Windows, por exemplo, Symantec e o Windows Defender. 

Aplica-se a: Windows 10 e posterior 

### <a name="device-enrollment"></a>Inscrição de dispositivos

####  <a name="devices-without-profiles-column-in-the-list-of-enrollment-program-tokens----1853904---"></a>Coluna Dispositivos sem perfis na lista de tokens do programa de inscrição <!-- 1853904 -->
Na lista de tokens do programa de inscrição, existe uma nova coluna que apresenta o número de dispositivos sem um perfil atribuído. Isto ajuda os administradores a atribuírem perfis a estes dispositivos antes de os distribuírem pelos utilizadores. Para ver a nova coluna, aceda a **Inscrição de dispositivos** > **Inscrição da Apple** > **Tokens do programa de inscrição**.

### <a name="device-management"></a>Gestão de dispositivos

#### <a name="google-name-changes-for-android-for-work-and-play-for-work---842873---"></a>Alterações de nome da Google para Android for Work e Play for Work <!--842873 -->
O Intune atualizou a terminologia do "Android for Work" para refletir as alterações de imagem corporativa da Google. Os termos "Android for Work" e "Play for Work" já não são utilizados. É utilizada terminologia diferente consoante o contexto:
- "Android Enterprise" refere-se à pilha de gestão de Android global e moderna.
- "Perfil profissional" ou "Proprietário do Perfil" refere-se a dispositivos BYOD geridos com perfis profissionais.
- "Google Play Gerido" refere-se à loja de aplicações da Google.

#### <a name="rules-for-removing-devices----1609459---"></a>Regras para remover dispositivos <!-- 1609459 -->
Estão disponíveis novas regras que lhe permitem remover automaticamente dispositivos que não tenham sido registados durante o número de dias definido. Para ver a nova regra, aceda ao painel **Intune**, selecione **Dispositivos** e selecione **Regras de limpeza do dispositivo**.

#### <a name="corporate-owned-single-use-support-for-android-devices----1630973---"></a>Suporte de utilização única, pertencente à empresa para dispositivos Android <!-- 1630973 -->

O Intune agora suporta dispositivos Android ao estilo de quiosque, bloqueados e altamente geridos. Isto permite que os administradores bloqueiem a utilização de um dispositivo para uma única aplicação ou pequeno conjunto de aplicações e impede que os utilizadores ativem outras aplicações ou efetuem outras ações no dispositivo. Para configurar o quiosque Android, aceda a Intune > **Inscrição de dispositivos** > **Inscrição Android** > **Inscrição de quiosque e dispositivos de tarefas**. Para obter mais informações, veja [Set up enrollment of Android enterprise kiosk devices](android-kiosk-enroll.md) (Configurar a inscrição de dispositivos de quiosque do Android Enterprise).

#### <a name="per-row-review-of-duplicate-corporate-device-identifiers-uploaded----2203794--"></a>Revisão por linha de identificadores de dispositivos da empresa duplicados carregados <!-- 2203794-->
Ao carregar IDs empresariais, o Intune agora fornece uma lista de duplicados e dá-lhe a opção de substituir ou manter as informações existentes. O relatório será apresentado se existirem duplicados após selecionar **Inscrição do dispositivo** > **Identificadores de Dispositivo da Empresa** > **Adicionar Identificadores**. 

#### <a name="manually-add-corporate-device-identifiers----2203803---"></a>Adicionar manualmente identificadores de dispositivos da empresa <!-- 2203803 -->
Agora pode adicionar manualmente IDs de dispositivos da empresa. Selecione **Inscrição de dispositivos** > **Identificadores de Dispositivo da Empresa** > **Adicionar**. 

## <a name="week-of-june-25-2018"></a>Semana de 25 de junho de 2018

### <a name="pradeo---new-mobile-threat-defense-partner----1169249---"></a>Pradeo – novo parceiro de Defesa Contra Ameaças para Dispositivos Móveis <!-- 1169249 -->

Pode controlar o acesso a recursos empresariais a partir de dispositivos móveis através do acesso condicional com base na avaliação de riscos realizada pelo Pradeo, uma solução de Defesa Contra Ameaças para Dispositivos Móveis que está integrada com o Microsoft Intune.

## <a name="week-of-june-18-2018"></a>Semana de 18 de junho de 2018

### <a name="microsoft-edge-mobile-support-for-intune-app-protection-policies----1817882---"></a>Suporte móvel para o Microsoft Edge para políticas de proteção de aplicações do Intune <!-- 1817882 -->

O browser Microsoft Edge para dispositivos móveis agora suporta as políticas de proteção de aplicações definidas no Intune.

## <a name="week-of-june-11-2018"></a>Semana de 11 de junho de 2018

### <a name="use-fips-mode-with-the-ndes-certificate-connector----1333688---"></a>Utilizar o modo FIPS com o conector do Certificado NDES <!-- 1333688 -->
Ao instalar o conector do Certificado NDES num computador com o modo FIPS (Federal Information Processing Standard) ativado, a emissão e a revogação de certificados não funcionaram como esperado. Com esta atualização, é incluído suporte para FIPS com o conector do Certificado NDES. 

Esta atualização também inclui:

- O conector do Certificado NDES precisa do .NET 4.5 Framework, que é incluído automaticamente com o Windows Server 2016 e o Windows Server 2012 R2. Anteriormente, a versão mínima necessária era o .NET 3.5 Framework.
- É incluído suporte para o TLS 1.2 com o Certificate Connector do NDES. Assim, se o servidor com o Certificate Connector do NDES instalado suportar o TLS 1.2, será utilizado o TLS 1.2. Se o servidor não suportar o TLS 1.2, será utilizado o TLS 1.1. Atualmente, é utilizado o TLS 1.1 para a autenticação entre os dispositivos e o servidor.

Para obter mais informações, veja [Configurar e utilizar certificados SCEP](certificates-scep-configure.md) e [Configurar e utilizar certificados PKCS](certficates-pfx-configure.md).

## <a name="week-of-june-4-2018"></a>Semana de 4 de junho de 2018

### <a name="app-management"></a>Gestão de aplicações

#### <a name="retrieve-the-associated-app-user-model-id-aumid-for-microsoft-store-for-business-apps-in-kiosk-mode----1560077----"></a>Obter o ID do modelo do utilizador da aplicação (AUMID) associada para aplicações da Microsoft Store para Empresas no modo de quiosque <!-- 1560077 ! -->
O Intune pode obter o IDs do modelo do utilizador da aplicação (AUMIDs) para aplicações da Microsoft Store para Empresas (WSfB) para proporcionar uma configuração melhorada do perfil de quiosque.

Para obter mais informações sobre aplicações da Microsoft Store para Empresas, veja [Gerir aplicações a partir da Microsoft Store para Empresas](windows-store-for-business.md).

#### <a name="new-company-portal-branding-page----1916370---"></a>Nova página de imagem corporativa do Portal da Empresa <!-- 1916370 -->
A página de imagem corporativa do Portal da Empresa tem um novo esquema, mensagens e descrições.


### <a name="device-configuration"></a>Configuração do dispositivo

#### <a name="support-for-palo-alto-networks-globalprotect-vpn-profiles----1333680----"></a>Suporte para perfis de VPN do GlobalProtect da Palo Alto Networks <!-- 1333680 ! -->
Com esta atualização, pode escolher o GlobalProtect da Palo Alto Networks como um tipo de ligação VPN para perfis de VPN no Intune (**Configuração do dispositivo** > **Perfis** > **Criar perfil** > **Tipo de perfil** > **VPN**). Neste lançamento, são suportadas as seguintes plataformas: 

- iOS
- Windows 10

#### <a name="additions-to-local-device-security-options-settings----1403702---"></a>Adições às definições de Opções de Segurança do Dispositivo Local <!-- 1403702 -->
Agora é possível configurar definições adicionais de Opções de Segurança do Dispositivo Local para dispositivos com o Windows 10. As definições adicionais estão disponíveis nas áreas do Cliente de Rede da Microsoft, Servidor de Rede da Microsoft, Segurança e acesso à rede e Início de sessão interativo. Estas definições encontram-se na categoria Endpoint Protection durante a criação de uma política de configuração de dispositivo Windows 10.

#### <a name="enable-kiosk-mode-on-windows-10-devices----1560072----"></a>Ativar o modo de quiosque em dispositivos com o Windows 10 <!-- 1560072 ! -->
Nos dispositivos com o Windows 10, pode criar um perfil de configuração e ativar o modo de quiosque (**Configuração do Dispositivo** > **Perfis** > **Criar perfil** > **Windows 10** > **Restrições do Dispositivo** > **Quiosque**). Nesta atualização, o nome da definição **Quiosque (pré-visualização)** irá mudar para **Quiosque (obsoleto)**. A utilização da definição **Quiosque (obsoleto)** deixará de ser recomendada, embora continue a estar funcional até à atualização de julho. A definição **Quiosque (obsoleto)** será substituída pelo novo tipo de perfil de **Quiosque** (**Criar perfil** > **Windows 10** > **Quiosque (pré-visualização)**), que incluirá as definições para configurar Quiosques no Windows 10 RS4 e posterior.

Aplica-se ao Windows 10 e posterior.

#### <a name="device-profile-graphical-user-chart-is-back----2160133---"></a>O gráfico de utilizadores de perfis de dispositivos está de volta <!-- 2160133 -->
Durante a melhoria das contagens apresentadas no gráfico de utilizadores do perfil do dispositivo (**Configuração do dispositivo** > **Perfis** > selecione um perfil existente > **Descrição geral**), este gráfico foi removido temporariamente.

Com esta atualização, o gráfico de utilizadores está de volta e é apresentado no portal do Azure.

### <a name="device-enrollment"></a>Inscrição de dispositivos

#### <a name="support-for-windows-autopilot-enrollment-without-user-authentication----1165118---"></a>Suporte para a inscrição do Windows Autopilot sem autenticação de utilizador <!-- 1165118 -->
O Intune suporta a inscrição do Windows Autopilot sem autenticação de utilizador. Esta é uma opção nova no perfil de implementação do Windows Autopilot "Modo de implementação do Autopilot" definido para "Implementação Automática".  O dispositivo tem de estar a executar a Versão 17672 do Windows 10 Insider Preview ou posterior e ter um chip do TPM 2.0 para concluir este tipo de inscrição com êxito. Uma vez que não é necessária a autenticação de utilizador, só deve atribuir esta opção a dispositivos sobre os quais tenha o controlo físico.

#### <a name="new-languageregion-setting-when-configuring-oobe-for-autopilot----1821766---"></a>Nova definição de idioma/região ao configurar o OOBE para o AutoPilot <!-- 1821766 -->
É disponibilizada uma nova configuração para definir o idioma e a região de perfis AutoPilot durante a experiência OOBE (Out of Box Experience). Para ver a nova definição, selecione **Inscrição de dispositivos** > **Inscrição do Windows** > **Perfis de implementação** > **Criar perfil** > **Modo de implementação** = **Implementação automática** > **Predefinições configuradas**.

#### <a name="new-setting-for-configuring-device-keyboard----1821768---"></a>Nova definição para configurar o teclado do dispositivo <!-- 1821768 -->
Será disponibilizada uma nova definição para configurar o teclado de perfis AutoPilot durante a experiência OOBE (Out of Box Experience). Para ver a nova definição, selecione **Inscrição de dispositivos** > **Inscrição do Windows** > **Perfis de implementação** > **Criar perfil** > **Modo de implementação** = **Implementação automática** > **Predefinições configuradas**.

#### <a name="autopilot-profiles-moving-to-group-targeting----1877935---"></a>Mudança dos perfis do Autopilot para a filtragem de grupo <!-- 1877935 -->
Os perfis de implementação AutoPilot podem ser atribuídos a grupos do Azure AD com contenham dispositivos AutoPilot.

### <a name="device-management"></a>Gestão de dispositivos

#### <a name="set-compliance-by-device-location----851881----"></a>Definir a conformidade pela localização do dispositivo <!-- 851881 ! -->
Em algumas situações, pode ser útil restringir o acesso a recursos empresariais para uma localização específica, definida por uma ligação de rede. Pode criar uma política de conformidade (**Conformidade do dispositivo** > **Localizações**) baseada no endereço IP do dispositivo. Se o dispositivo estiver fora do intervalo de IP, não conseguirá aceder a recursos empresariais.

Aplica-se a: Dispositivos com o Android 6.0 e superior, com a aplicação Portal da Empresa atualizada

#### <a name="prevent-consumer-apps-and-experiences-on-windows-10-enterprise-rs4-autopilot-devices---1621980---"></a>Impedir as experiências e aplicações de consumidor em dispositivos AutoPilot com o Windows 10 Enterprise RS4<!-- 1621980 -->
Poderá impedir a instalação de experiências e aplicações de consumidor nos seus dispositivos AutoPilot com o Windows 10 Enterprise RS4. Para ver esta funcionalidade, aceda a **Intune** > **Configuração de dispositivos** > **Perfis** > **Criar perfil** > **Plataforma** = **Windows 10 ou posterior** > **Tipo de perfil** = **Restrições de dispositivos** > **Configurar** > **Windows Spotlight** > **Funcionalidades do consumidor**. 

#### <a name="uninstall-the-latest-from-windows-10-software-updates----1732948---"></a>Desinstalar as atualizações de software mais recentes do Windows 10 <!-- 1732948 -->
Se detetar um problema de interrupção em computadores com Windows 10, pode optar por desinstalar (reverter) a atualização mais recente da funcionalidade ou a atualização mais recente de qualidade. A desinstalação de uma atualização da funcionalidade ou qualidade só está disponível para o canal de serviço onde o dispositivo está ativado. A desinstalação irá acionar uma política para restaurar a atualização anterior em computadores com Windows 10. Especificamente para atualizações da funcionalidade, pode limitar o tempo de 2 a 60 dias em que pode ser aplicada uma desinstalação da versão mais recente. Para definir as opções de desinstalação da atualização do software, selecione **Atualizações do software** do painel **Microsoft Intune** no portal do Azure. Em seguida, selecione **Anéis de Atualização do Windows 10**, a partir do painel **Atualizações do software**. Em seguida, pode selecionar a opção **Desinstalar** na secção **Descrição geral**.

#### <a name="search-all-devices-for-imei-and-serial-number----1793685---"></a>Procurar IMEI e número de série em todos os dispositivos <!-- 1793685 -->
Pode procurar por IMEI e números de série no painel Todos os dispositivos (e-mail, UPN, nome do dispositivo e nome de gestão ainda estão disponíveis). No Intune, selecione **Dispositivos** > **Todos os dispositivos** > introduza a sua pesquisa na caixa de pesquisa.

#### <a name="management-name-field-will-be-editable----1875989---"></a>O campo Nome de gestão passará a ser editável <!-- 1875989 -->
Pode editar o campo Nome de gestão no painel **Propriedades** de um dispositivo. Para editar este campo, selecione **Dispositivos** > **Todos os dispositivos** > selecione o dispositivo > **Propriedades**. Pode utilizar o campo Nome de gestão para identificar um dispositivo de forma exclusiva.

#### <a name="new-all-devices-filter-device-category----1878520---"></a>Novo filtro de dispositivos todas as: Categoria de dispositivo <!-- 1878520 -->
Pode filtrar a lista **Todos os dispositivos** por categoria de dispositivo. Para tal, selecione **Dispositivos** > **Todos os dispositivos** > **Filtro** > **Categoria de dispositivo**.

#### <a name="use-teamviewer-to-screen-share-ios-and-macos-devices----1985547---"></a>Utilizar o TeamViewer para partilhar ecrãs de dispositivos iOS e MacOS <!-- 1985547 -->
Os administradores podem estabelecer ligação ao [TeamViewer](device-profile-android-teamviewer.md) e iniciar uma sessão de partilha de ecrã com dispositivos iOS e macOS. Os utilizadores de dispositivos iPhone, iPad e macOS podem partilhar os seus ecrãs em direto com qualquer outro computador ou dispositivo. 

#### <a name="multiple-exchange-connector-support----2070451---"></a>Suporte múltiplo do Exchange Connector <!-- 2070451 -->
Deixará de ficar limitado a um Microsoft Intune Exchange Connector por inquilino. O Intune suporta agora múltiplos Exchange Connectors para que possa configurar o acesso condicional do Intune com múltiplas organizações do Exchange no local.

Com um Exchange Connector no local do Intune, pode gerir o acesso de dispositivos a caixas de correio do Exchange no local com base no facto de um dispositivo estar ou não inscrito no Intune e estar ou não em conformidade com as políticas de conformidade de dispositivos do Intune. Para configurar um conector, transfira o Exchange Connector no local do Intune a partir do portal do Azure e instale-o num servidor na sua organização do Exchange. No dashboard do Microsoft Intune, selecione **Acesso no local** e, em **Configuração**, selecione **Conector do Exchange ActiveSync**. Transfira o Exchange Connector no local e instale-o num servidor na sua organização do Exchange. Como deixou de estar limitado a um Exchange Connector por inquilino, se tiver mais organizações do Exchange, pode seguir este processo para transferir e instalar um conector para cada organização do Exchange adicional.

#### <a name="new-device-hardware-detail-ccid----2156657---"></a>Detalhes de hardware do novo dispositivo: CCID <!-- 2156657 -->
As informações de Dispositivo de Interface de Cartão de Circuito Integrado (CCID) estão agora incluídas para cada dispositivo. Para vê-las, selecione **Dispositivos** > **Todos os dispositivos** > selecione um dispositivo > **Hardware**> verifique em **Detalhes da rede**>

#### <a name="assign-all-users-and-all-devices-as-scope-groups----2196803---"></a>Atribuir todos os utilizadores e dispositivos como grupos de âmbito <!-- 2196803 -->
Pode agora atribuir todos os utilizadores, todos os dispositivos e todos os utilizadores e dispositivos em grupos de âmbito. Para o fazer, selecione **Funções do Intune** > **Todas as funções** > **Gestor de políticas e perfis** > **Atribuições** > selecione uma atribuição > **Âmbito (grupos)**.

#### <a name="udid-information-now-included-for-ios-and-macos-devices----2219806---"></a>Informações de UDID incluídas para dispositivos iOS e macOS <!-- 2219806 -->
Para ver o Identificador Único do Dispositivo (UDID) para dispositivos iOS e macOS, aceda a **Dispositivos** > **Todos os dispositivos** > selecione um dispositivo > **Hardware**. O UDID só está disponível para dispositivos empresariais (como definido em **Dispositivos** > **Todos os dispositivos** > selecione um dispositivo > **Propriedades** > **Propriedade do dispositivo**).

### <a name="intune-apps"></a>Aplicações do Intune

#### <a name="improved-troubleshooting-for-app-installation----928990---"></a>Melhorias na resolução de problemas de instalação de aplicações <!-- 928990 -->
Por vezes, a instalação de aplicações em dispositivos geridos por MDM do Microsoft Intune pode falhar. Quando uma instalação de aplicações falha, pode ser difícil compreender o motivo da falha ou resolver o problema. Vamos lançar uma Pré-visualização Pública das nossas funcionalidades de Resolução de Problemas de Aplicações. Verá um novo nó em cada dispositivo denominado **Aplicações Geridas**. Este nó apresenta as aplicações que foram enviadas através do Intune MDM. Dentro do nó, verá uma lista de estados de instalação das aplicações. Se selecionar uma única aplicação, ser-lhe-á apresentada a vista de resolução de problemas dessa aplicação específica. Na vista de resolução de problemas, verá o ciclo de vida ponto a ponto da aplicação, por exemplo quando é que a aplicação foi criada, modificada, visada e enviada para um dispositivo. Além disso, se a instalação da aplicação não tiver sido concluída com êxito, ser-lhe-á apresentado o código de erro e uma mensagem útil sobre a causa do erro. 

#### <a name="intune-app-protection-policies-and-microsoft-edge----1818968---"></a>Políticas de proteção de aplicações do Intune e Microsoft Edge <!-- 1818968 -->
Agora o browser Microsoft Edge para dispositivos móveis (iOS e Android) suporta as políticas de proteção de aplicações do Microsoft Intune. Os utilizadores de dispositivos iOS e Android que iniciarem sessão com as suas contas empresariais do Azure AD na aplicação Edge passarão a ser protegidos pelo Intune. Em dispositivos iOS, a política **Exigir browser gerido para conteúdo Web** permitirá aos utilizadores abrir ligações no Microsoft Edge quando é gerido.

## <a name="week-of-may-14-2018"></a>Semana de 14 de maio de 2018

### <a name="app-management"></a>Gestão de aplicações

#### <a name="require-installation-of-policies-apps-certificate-and-network-profiles----1553555---"></a>Exigir a instalação de políticas, aplicações, perfis de certificado e de rede <!-- 1553555 -->

Os administradores podem impedir os utilizadores finais de aceder ao ambiente de trabalho do Windows 10 RS4 até que o Intune instale as políticas, aplicações e perfis de certificado e de rede durante o aprovisionamento de dispositivos AutoPilot. Para obter mais informações, veja [Configurar uma página de estado de inscrição](windows-enrollment-status.md).

#### <a name="configuring-your-app-protection-policies----2144597-part-2---"></a>Configurar as suas políticas de proteção de aplicações<!-- 2144597 Part 2 -->

Agora, no portal do Azure, em vez de aceder ao painel do serviço de Proteção de Aplicações do Intune, acede diretamente ao Intune. Só existe uma localização para as políticas de proteção de aplicações no Intune. Tenha em atenção que todas as suas políticas de proteção de aplicações se encontram no painel **Aplicação móvel** no Intune, em **Políticas de proteção de aplicações**. Esta integração ajuda a simplificar a sua administração da gestão da cloud. Tenha em atenção que todas as políticas de proteção de aplicações já se encontram no Intune e pode modificar as suas políticas configuradas anteriormente. A Política de Proteção de Aplicações (APP) do Intune e as políticas de Acesso Condicional (CA) estão em **Acesso condicional**, na secção **Gerir** do painel **Microsoft Intune**, ou na secção **Segurança** do painel **Azure Active Directory**. Para obter mais informações sobre a modificação de políticas de acesso condicional, veja [Acesso condicional no Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal). Para obter informações adicionais, veja [O que são as políticas de proteção de aplicações?](app-protection-policy.md)

## <a name="week-of-may-7-2018"></a>Semana de 7 de maio de 2018

### <a name="app-management"></a>Gestão de aplicações

#### <a name="samsung-knox-mobile-enrollment-support---1112863--"></a>Suporte do Knox Mobile Enrollment da Samsung<!--1112863-->

Ao utilizar o Intune com o Knox Mobile Enrollment (KME) da Samsung, pode inscrever um grande número de dispositivos Android da empresa. Os utilizadores em redes Wi-Fi ou redes móveis podem inscrever com apenas alguns toques os respetivos dispositivos quando os ligarem pela primeira vez. Ao utilizarem a Aplicação Knox Deployment, os dispositivos podem ser inscritos através de Bluetooth ou NFC. Para obter mais informações, consulte [Automatically enroll Android devices by using Samsung's Knox Mobile Enrollment](android-samsung-knox-mobile-enroll.md) (Inscrever automaticamente dispositivos Android através do Knox Mobile Enrollment da Samsung).

#### <a name="requesting-help-in-the-company-portal-for-windows-10----1874137---"></a>Pedir ajuda no Portal da Empresa para Windows 10 <!-- 1874137 -->

O Portal da Empresa para Windows 10 irá agora enviar registos de aplicações diretamente para a Microsoft quando o utilizador iniciar o fluxo de trabalho para obter ajuda com um problema. Isto facilitará a resolução dos problemas colocados à Microsoft.

## <a name="week-of-april-23-2018"></a>Semana de 23 de abril de 2018

### <a name="app-management"></a>Gestão de aplicações

#### <a name="passcode-support-for-mam-pin-on-android---1438086---"></a>Suporte de código de acesso para o PIN de MAM no Android<!-- 1438086 -->

Os administradores do Intune podem definir um requisito de execução da aplicação para impor um código de acesso em vez de um PIN numérico de MAM. Caso esteja configurado, é pedido ao utilizador que defina e utilize um código de acesso antes de poder aceder a aplicações otimizadas para a MAM. Os código de acesso são definidos como um PIN numérico com, pelo menos, um caráter especial ou letras em maiúsculas/minúsculas. O Intune suporta um código de acesso de forma semelhante ao PIN numérico existente, sendo capaz de definir um comprimento mínimo e de permitir sequências e carateres repetidos através da consola de administrador. Esta funcionalidade necessita da versão mais recente do Portal da Empresa no Android. Esta funcionalidade já se encontra disponível para iOS.

#### <a name="line-of-business-lob-app-support-for-macos----1473977---"></a>Suporte de aplicações de linha de negócio (LOB) para macOS <!-- 1473977 -->
O Microsoft Intune irá oferecer a capacidade de instalar aplicações LOB para macOS a partir do portal do Azure. Poderá adicionar uma aplicação LOB para macOS ao Intune depois de a mesma ter sido previamente processada pela ferramenta disponível no GitHub. No portal do Azure, selecione **Aplicações do cliente** no painel **Intune**. No painel **Aplicações do cliente**, selecione **Aplicações** > **Adicionar**. No painel **Adicionar Aplicação**, selecione **Aplicação de linha de negócio**. 

#### <a name="built-in-all-users-and-all-devices-group-for-android-enterprise-work-profile-app-assignment----1813073---"></a>Grupos Todos os Utilizadores e Todos os Dispositivos incorporados para a atribuição de aplicações do perfil de trabalho do Android Enterprise <!-- 1813073 -->
Pode tirar partido dos grupos incorporados **Todos os Utilizadores** e **Todos os Dispositivos** para a atribuição de aplicações de perfil de trabalho do Android Enterprise. Para obter mais informações, veja [Incluir e excluir atribuições de aplicações no Microsoft Intune](apps-inc-exl-assignments.md).

#### <a name="intune-will-reinstall-required-apps-that-are-uninstalled-by-users----1947010---"></a>O Intune irá reinstalar as aplicações necessárias que foram desinstaladas pelos utilizadores <!-- 1947010 -->
Se um utilizador final desinstalar uma aplicação necessária, o Intune reinstalará automaticamente a aplicação no prazo de 24 horas em vez de aguardar o ciclo de reavaliação de 7 dias.

### <a name="device-configuration"></a>Configuração do dispositivo

####  <a name="device-profile-chart-and-status-list-show-all-devices-in-a-group----1449153---"></a>O gráfico de perfis de dispositivos e a lista de estados mostra todos os dispositivos num grupo <!-- 1449153 -->
Quando configurar um perfil de dispositivo (**Configuração do dispositivo** > **Perfis**), selecione o perfil de dispositivo que pretende, como iOS. Atribua este perfil a um grupo que inclua dispositivos iOS e dispositivos não iOS. A contagem do gráfico mostra que o perfil é aplicado a dispositivos iOS *e* não iOS (**Configuração do dispositivo** > **Perfis** > selecione um perfil existente > **Descrição Geral**). Quando seleciona o gráfico no separador **Descrição Geral**, o **Estado do dispositivo** apresenta uma lista de todos os dispositivos no grupo, em vez de mostrar apenas os dispositivos iOS. 

Com esta atualização, o gráfico (**Configuração do dispositivo** > **Perfis** > selecione um perfil existente > **Descrição Geral**) mostra apenas a contagem do perfil do dispositivo específico. Por exemplo, se o perfil de configuração do dispositivo se aplicar a dispositivos iOS, o gráfico só apresentará a contagem de dispositivos iOS. Ao selecionar o gráfico e abrir o **Estado do dispositivo** só serão apresentados os dispositivos iOS.

Enquanto esta atualização estiver a ser efetuada, o gráfico de utilizadores será temporariamente removido. 

#### <a name="always-on-vpn-for-windows-10---1333666---"></a>Funcionalidade AlwaysOn através de VPN no Windows 10 <!--1333666 -->

Atualmente, a funcionalidade [AlwaysOn](https://docs.microsoft.com/windows/security/identity-protection/vpn/vpn-auto-trigger-profile#always-on) pode ser utilizada em dispositivos com o Windows 10 através da utilização de um perfil de rede privada virtual (VPN) personalizada criada com o OMA-URI.

Com esta atualização, os administradores podem ativar a funcionalidade AlwaysOn para perfis VPN do Windows 10 diretamente no Intune, no portal do Azure. Os perfis VPN AlwaysOn irão ligar automaticamente quando:

- Os utilizadores iniciarem sessão nos respetivos dispositivos
- A rede no dispositivo for alterada
- O ecrã do dispositivo se ligar novamente após o ter desligado

#### <a name="new-printer-settings-for-education-profiles----1308900---"></a>Novas definições de impressora para perfis de educação <!-- 1308900 -->

Para os perfis de educação, estão disponíveis em novas definições do **impressoras** categoria: **Impressoras**, **impressora predefinida**, **adicionar novas impressoras**.

#### <a name="show-caller-id-in-personal-profile---android-enterprise-work-profile---1098984---"></a>Mostrar o ID do chamador no perfil pessoal – perfil de trabalho do Android Enterprise <!--1098984 -->
Quando utiliza um perfil pessoal num dispositivo, os utilizadores finais podem não ver os detalhes do ID do autor da chamada de um contacto de trabalho. 

Com esta atualização, existe uma nova definição em **Android Enterprise** > **Restrições do dispositivo** > **Definições do perfil de trabalho**:
- Apresentar o ID do autor da chamada do contacto de trabalho no perfil pessoal

Quando a opção está ativada (não configurada), os detalhes do autor da chamada do contacto de trabalho são apresentados no perfil pessoal. Quando a opção está bloqueada, o número do autor da chamada do contacto de trabalho não é apresentado no perfil pessoal. 

Aplica-se a: Dispositivos de perfil de trabalho Android em Android OS v6.0 e mais recentes

#### <a name="new-windows-defender-credential-guard-settings-added-to-endpoint-protection-settings---1102252-----from-1802-and-1804--"></a>Novas definições do Windows Defender Credential Guard foram adicionadas às definições de proteção de ponto final <!--1102252 --><!--from 1802 and 1804-->

Com esta atualização, o [Windows Defender Credential Guard](https://docs.microsoft.com/windows/access-protection/credential-guard/credential-guard) (**Configuração do dispositivo** > **Perfis** > **Proteção de ponto final**) inclui as seguintes definições: 

- **Windows Defender Credential Guard**: Ativa o Credential Guard com segurança baseada em virtualização. Se ativar esta funcionalidade, ajudará a proteger as credenciais no próximo reinício quando o **Nível de Segurança da Plataforma com o Arranque Seguro** e a **Segurança Baseada em Virtualização** estiverem ativados. As opções incluem:
  - **Desativado**: Se o Credential Guard anteriormente foi ativado com o **ativada sem bloqueio**"opção, em seguida, ele se desligar Credential Guard remotamente.

  - **Ativada com bloqueio UEFI**: Garante que o Credential Guard não pode ser desativado através de uma chave de registro ou usando a diretiva de grupo. Para desativar o Credential Guard depois de utilizar esta definição, tem de definir a Política de Grupo como “Desativada”. Em seguida, remova a funcionalidade de segurança de cada computador, com um utilizador fisicamente presente. Estes passos limpam a configuração persistente na UEFI. Enquanto a configuração da UEFI persistir, o Credential Guard estará ativado.

  - **Ativada sem bloqueio**: Permite que o Credential Guard seja desativado remotamente através da política de grupo. Os dispositivos que utilizam esta definição têm de ter, pelo menos, o Windows 10 (Versão 1511).

As seguintes tecnologias dependentes são ativadas automaticamente ao configurar o Credential Guard: 

  - **Ativar a segurança baseada em Virtualização (VBS)**: Ativa a virtualização de segurança baseada em (VBS) na próxima reinicialização. A segurança baseada na virtualização utiliza o Windows Hypervisor para dar suporte aos serviços de segurança e requer o Arranque Seguro.
  - **Arranque com acesso direto à memória (DMA) seguro**: Ativa o VBS com Secure Boot e acesso direto à memória. As proteções de DMA precisam de suporte de hardware e serão ativadas apenas em dispositivos configurados corretamente. 

#### <a name="use-a-custom-subject-name-on-scep-certificate----2064190---"></a>Utilize um nome de requerente personalizado no certificado SCEP <!-- 2064190 -->
Poderá utilizar o nome comum **OnPremisesSamAccountName** num requerente personalizado num perfil de certificado SCEP. Por exemplo, pode utilizar `CN={OnPremisesSamAccountName})`.

####  <a name="block-camera-and-screen-captures-on-android-enterprise-work-profiles----1098977---"></a>Bloquear a câmara e as capturas de ecrã em perfis de trabalho do Android Enterprise <!-- 1098977 -->
Estão disponíveis duas propriedades novas para o bloqueio ao configurar as restrições dos dispositivos Android: 
- Câmara: Bloqueia o acesso a todas as câmaras no dispositivo
- Captura de ecrã: Bloqueia a captura de ecrã e também impede que o conteúdo a ser mostrado em dispositivos de visualização que não tenham uma saída de vídeo segura

Aplica-se a perfis de trabalho do Android Enterprise.


### <a name="device-enrollment"></a>Inscrição de dispositivos

#### <a name="new-enrollment-steps-for-users-on-devices-with-macos-high-sierra-10132---1734567---"></a>Novos passos de inscrição para os utilizadores em dispositivos com o macOS High Sierra 10.13.2 ou superior <!--1734567 -->
O macOS High Sierra 10.13.2 introduziu um conceito de inscrição "Aprovado Pelo Utilizador" na MDM. As inscrições aprovadas permitem que o Intune faça a gestão de algumas definições relacionadas com a segurança. Para obter mais informações, veja a documentação de suporte da Apple aqui: https://support.apple.com/HT208019.

Os dispositivos inscritos através do Portal da Empresa do macOS são considerados “Não Aprovados Pelo Utilizador”, a menos que o utilizador final abra as Preferências do Sistema e conceda a aprovação manualmente. Para tal, o Portal da Empresa do macOS agora direciona os utilizadores no macOS 10.13.2 e superior para que acedam e aprovem manualmente a inscrição no final do processo de inscrição. A consola de administrador do Intune irá indicar se um dispositivo inscrito for aprovado pelo utilizador.



### <a name="device-management"></a>Gestão de dispositivos

#### <a name="advanced-threat-protection-atp-and-intune-are-fully-integrated----1629303---"></a>A Proteção Avançada Contra Ameaças (ATP) e o Intune estão totalmente integrados <!-- 1629303 -->

A [Proteção Avançada Contra Ameaças (ATP)](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/dashboard-windows-defender-advanced-threat-protection) mostra o nível de risco dos dispositivos com o Windows 10. No Centro de Segurança do Windows Defender (portal ATP), pode criar uma ligação para o Microsoft Intune. Depois de a criar, uma política de conformidade do Intune serve para determinar um nível de ameaça aceitável. Se o nível de ameaça for excedido, uma política de acesso condicional do Azure Active Directory (AD) poderá bloquear o acesso a aplicações diferentes dentro da sua organização.

Esta funcionalidade permite ao ATP analisar ficheiros, detetar ameaças e reportar qualquer risco nos dispositivos Windows 10.

Veja [Enable ATP with conditional access in Intune](advanced-threat-protection.md) (Ativar o ATP com acesso condicional no Intune).

#### <a name="support-for-user-less-devices----1637553---"></a>Suporte para dispositivos sem utilizador <!-- 1637553 -->
O Intune permite avaliar a conformidade num dispositivo sem utilizadores, tal como o Microsoft Surface Hub. A política de conformidade pode ser aplicada a dispositivos específicos. Portanto, a conformidade e não conformidade podem ser determinadas para dispositivos que não tenham um utilizador associado.

#### <a name="delete-autopilot-devices----1713650---"></a>Eliminar dispositivos Autopilot <!-- 1713650 -->
Os administradores do Intune podem [eliminar dispositivos Autopilot](enrollment-autopilot.md#delete-autopilot-devices).

#### <a name="improved-device-deletion-experience---1832333---"></a>Experiência de eliminação de dispositivos melhorada <!--1832333 -->
Já não será obrigado a remover os dados da empresa ou a fazer uma reposição de fábrica do dispositivo antes de [eliminar um dispositivo do Intune](devices-wipe.md#delete-devices-from-the-intune-portal).

Para ver a nova experiência, inicie sessão no Intune e selecione **Dispositivos** > **Todos os Dispositivos** > o nome do dispositivo > **Eliminar**.

Se quiser continuar com a confirmação de eliminação/extinção, pode utilizar a rota de ciclo de vida do dispositivo padrão ao executar a opção **Remover dados da empresa** e **Reposição de Fábrica** antes de **Eliminar**. 

#### <a name="play-sounds-on-ios-when-in-lost-mode----1947769---"></a>Reproduzir sons no iOS quando está no Modo perdido <!-- 1947769 -->
Quando os dispositivos iOS supervisionados estiverem no [Modo perdido](device-lost-mode.md) na Gestão de Dispositivos Móveis (MDM), poderá [reproduzir um som](device-locate.md#activate-lost-mode-sound-alert-on-an-ios-device) (**Dispositivos** > **Todos os Dispositivos** > selecione um dispositivo iOS > **Descrição Geral** > **Mais**). O som continuará a ser reproduzido até que o dispositivo seja removido do Modo perdido ou que um utilizador desative o som no dispositivo. Aplica-se aos dispositivos iOS 9.3 e mais recentes.

#### <a name="block-or-allow-web-results-in-searches-made-on-an-intune-device---1972804--"></a>Bloquear ou permitir resultados da Web em pesquisas realizadas num dispositivo Intune <!--1972804-->

Os administradores podem agora bloquear resultados da Web em pesquisas realizadas num dispositivo.

#### <a name="improved-error-messaging-for-apple-mdm-push-certificate-upload-failure----2172331---"></a>Mensagens de erro melhoradas da falha de carregamento do Certificado Push de MDM da Apple <!-- 2172331 -->

A mensagem de erro explica que tem de utilizar o mesmo ID Apple ao renovar um certificado de MDM existente.

#### <a name="test-the-company-portal-for-macos-on-virtual-machines----2216679---"></a>Testar o Portal da Empresa para macOS em máquinas virtuais <!-- 2216679 -->

Publicamos orientações para ajudar os administradores de TI a testar a aplicação Portal da Empresa para macOS em máquinas virtuais no Parallels Desktop e na VMware Fusion. Saiba mais em [Inscrever máquinas virtuais macOS para teste](macos-enroll.md#enroll-virtual-macos-machines-for-testing).


### <a name="user-interface"></a>Interface de utilizador

#### <a name="improved-device-tiles-in-the-windows-10-company-portal---2213364---"></a>Mosaicos de dispositivos melhorados no Portal da Empresa do Windows 10 <!--2213364 -->

Os mosaicos foram atualizados para serem mais acessíveis a utilizadores de visão reduzida e para terem um melhor desempenho nas ferramentas de leitura de ecrãs.

#### <a name="send-diagnostic-reports-in-company-portal-app-for-macos----2216677---"></a>Enviar relatórios de diagnóstico na aplicação Portal da Empresa para macOS <!-- 2216677 -->
A aplicação do Portal da Empresa para dispositivos macOS foi atualizada para melhorar a forma como os utilizadores comunicam erros relacionados com o Intune. Na aplicação Portal da Empresa, os funcionários podem:

- Carregar os relatórios de diagnóstico diretamente para a equipa de programadores da Microsoft.
- Enviar o ID do incidente por e-mail para a equipa de suporte de TI da sua empresa.

Para obter mais informações, veja [Enviar erros do macOS](/intune-user-help/send-errors-macos).

#### <a name="intune-adapts-to-fluent-design-system-in-the-company-portal-app-for-windows-10----1195010---"></a>O Intune adapta-se ao Fluent Design System na aplicação Portal da Empresa para Windows 10 <!-- 1195010 -->
A aplicação Portal da Empresa do Intune para Windows 10 foi atualizada com a [vista de navegação do Fluent Design System](https://docs.microsoft.com/windows/uwp/design/basics/navigation-basics). Na parte lateral da aplicação, verá uma lista vertical estática de todas as páginas de nível superior. Clique em qualquer ligação para ver e alternar entre páginas rapidamente. Esta é a primeira de várias atualizações que verá como parte do nosso esforço contínuo para criar uma experiência mais adaptável, agradável e familiar no Intune. Para ver a versão atualizada, aceda a [Novidades na IU da aplicação](whats-new-app-ui.md).

## <a name="week-of-april-16-2018"></a>Semana de 16 de abril de 2018

#### <a name="use-cisco-anyconnect-client-for-ios----1333708---"></a>Utilizar o cliente Cisco AnyConnect para iOS <!-- 1333708 -->

Quando cria um novo perfil VPN para iOS, existem agora duas opções: **Cisco AnyConnect** e **Cisco Legacy AnyConnect**. Os perfis do Cisco AnyConnect suportam a versão 4.0.7x e versões mais recentes. Os perfis VPN existentes do Cisco AnyConnect para iOS são identificados como **Cisco Legacy AnyConnect** e continuarão a funcionar com a versão 4.0.5x e mais antigas do Cisco AnyConnect, tal como atualmente.

> [!NOTE]
> Esta alteração só se aplica ao iOS. Continua a existir apenas uma opção Cisco AnyConnect para as plataformas Android, perfis de trabalho do Android Enterprise e macOS.

#### <a name="jamf-enrolled-macos-devices-can-now-register-with-intune----2370684---"></a>Os dispositivos macOS inscritos com Jamf podem agora registar-se com o Intune <!-- 2370684 -->

As versões 1.3 e 1.4 do portal da empresa do macOS não conseguiam registar dispositivos com Jamf com o Intune. A versão 1.4.2 do portal do macOS corrige este problema.


## <a name="week-of-april-9-2018"></a>Semana de 9 de agosto de 2018  
#### <a name="updated-help-experience-in-company-portal-app-for-android----1631531---"></a>Experiência de ajuda atualizada na aplicação Portal da Empresa para Android <!-- 1631531 -->

Atualizámos a experiência de ajuda na aplicação Portal da Empresa para Android para estarmos alinhados com as melhores práticas para a plataforma Android. Agora, quando os utilizadores detetarem um problema na aplicação, podem tocar em **Menu** > **Ajuda** e:
- Carregar registos de diagnóstico para a Microsoft.
- Enviar um e-mail a descrever o problema e o ID do incidente para um membro da equipa de suporte da empresa.  

Para experimentar a experiência de ajuda atualizada, aceda a [Enviar registos por e-mail](/intune-user-help/send-logs-to-your-it-admin-by-email-android) e [Enviar erros para a Microsoft](/intune-user-help/send-logs-to-microsoft-android).


#### <a name="new-enrollment-failure-trend-chart-and-failure-reasons-table----1471783---"></a>Novo gráfico de tendências de falhas e tabela de motivos de falhas em novas inscrições <!-- 1471783 -->

Na página Descrição Geral de Inscrições, pode ver as tendências de falhas de inscrições e as cinco principais causas de falhas. Ao clicar no gráfico ou na tabela, pode pormenorizar os detalhes para encontrar conselhos de resolução de problemas e sugestões de remediação.

#### <a name="update-where-to-configure-your-app-protection-policies----2144597---"></a>Atualização do local de configuração das políticas de proteção de aplicações <!-- 2144597 -->

No portal do Azure no serviço do Microsoft Intune, iremos redirecioná-lo temporariamente do painel do serviço **Proteção de Aplicações do Intune** para o painel **Aplicação móvel**. Tenha em atenção que todas as suas políticas de proteção de aplicações já se encontram no painel **Aplicação móvel** no Intune, em Configuração da aplicação. Em vez de aceder à Proteção de Aplicações do Intune, acederá simplesmente ao Intune. Em abril de 2018, iremos interromper o redirecionamento e remover completamente o painel do serviço **Proteção de Aplicações do Intune**, de modo a que só exista uma única localização para políticas de proteção de aplicações no Intune. 

**Como é que isto me afeta?**
Esta alteração afetará os clientes autónomos e os clientes híbridos (Intune com o Configuration Manager) do Intune. Esta integração irá ajudar a simplificar a sua administração da gestão da cloud.

**O que preciso de fazer para me preparar para esta alteração?**
Adicione o **Intune** como um favorito em vez do painel do serviço **Proteção de Aplicações do Intune** e certifique-se de que está familiarizado com o fluxo de trabalho da Política de proteção de aplicações no painel **Aplicação móvel** no Intune. Iremos redirecionar os utilizadores durante um breve período de tempo e, em seguida, remover o painel **Proteção de Aplicações**. Tenha em atenção que todas as políticas de proteção de aplicações já se encontram no Intune e pode modificar as suas políticas de acesso condicional. Para obter mais informações sobre a modificação de políticas de acesso condicional, veja [Acesso condicional no Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal). Para obter informações adicionais, veja [O que são as políticas de proteção de aplicações?](app-protection-policy.md) 


## <a name="week-of-april-2-2018"></a>Semana de 2 de abril de 2018

### <a name="intune-apps"></a>Aplicações do Intune

#### <a name="user-experience-update-for-the-company-portal-app-for-ios---1412866---"></a>Atualização da experiência de utilizador da aplicação Portal da Empresa para iOS <!--1412866 -->
Lançámos uma atualização importante da experiência de utilizador para a aplicação Portal da Empresa para iOS. A atualização consiste numa reestruturação visual completa que inclui um aspeto e funcionalidade mais modernos. Mantivemos a funcionalidade da aplicação, mas aumentámos a facilidade de utilização e acessibilidade da mesma.  

A atualização inclui ainda:
- Suporte para iPhone X.
- Respostas de início e carregamento de aplicações mais rápidas, que poupam tempo aos utilizadores.
- Barras de progresso adicionais que mostram as informações de estado mais recentes aos utilizadores.
- Melhorias à forma como os utilizadores carregam os registos, para facilitar o envio de relatórios em caso de falha.  

Para ver a versão atualizada, aceda a [Novidades na IU da aplicação](whats-new-app-ui.md).

#### <a name="protect-on-premises-exchange-data-using-intune-app-and-ca----1056954---"></a>Proteger dados do Exchange no local com a Política de Proteção de Aplicações e o Acesso Condicional do Intune <!-- 1056954 -->
Agora pode utilizar a Política de Proteção de Aplicações (APP) e o Acesso Condicional (AC) do Intune para proteger o acesso a dados do Exchange no local com o Outlook Mobile. Para adicionar ou modificar uma política de proteção de aplicações no portal do Azure, selecione **Microsoft Intune** > **Aplicações do cliente** > **Políticas de proteção de aplicações**. Antes de utilizar esta funcionalidade, certifique-se de que cumpre os [requisitos do Outlook para iOS e Android](https://technet.microsoft.com/en-us/library/mt846639(v=exchg.160).aspx).

## <a name="notices"></a>Avisos

### <a name="plan-for-change-exchange-online-to-intune-connector-will-not-be-available-in-intune----3105122---"></a>Planear a alteração: Exchange Online para o conector do Intune não estarão disponível no Intune <!-- 3105122 -->
Para simplificar sua experiência com o Exchange Online e o acesso condicional, vamos desativar o Exchange Online para Intune "conector de serviços". Esta alteração irá começar com a atualização do serviço de Dezembro e ser concluída com a atualização do serviço de Fevereiro de 2019.

#### <a name="how-does-this-affect-me"></a>Como é que isto me afeta?
Está recebendo esta mensagem, uma vez que os nossos registos indicam que pode utilizar a funcionalidade de conector "De serviços" no seu ambiente. O conector de 'De serviços' suporta a gestão do Exchange Active Sync apenas os dispositivos do Intune para o Exchange Online e não suporta a infraestrutura no local. Este conector, a forma como o que é apresentado no console, é apresentada como necessários para acesso condicional (AC), quando, na realidade, não é necessária para a AC. Com a atualização de Dezembro para o serviço do Intune, para esclarecer na consola, podemos irá desativar o botão configurar novos conectores. Em seguida, em Fevereiro de 2019, todos os existentes Exchange Online para conectores do Intune será desativada.

Se utilizar estes conectores no seu ambiente, não será possível monitorizar ou eliminar os Exchange Active Sync apenas os dispositivos no Intune após conectores foram desativados em Fevereiro. Não há nenhum impacto previsto aos seus utilizadores finais durante esta alteração.

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>O que posso fazer para me preparar para esta alteração?

Se tiver o conector de serviços, configurar e executar o Exchange Active Sync apenas os dispositivos, mude para outros métodos de gerir os seus dispositivos. Tem as seguintes opções:

- Inscrever dispositivos na gestão de dispositivos móveis (MDM)
- Utilizar políticas de proteção de aplicações do Intune para gerir os seus dispositivos
- Utilize os controlos de Exchange, conforme descrito na documentação aqui. 

#### <a name="additional-information"></a>Informações adicionais
[Configurar o conector de serviço do Exchange para o Intune e Exchange Online](https://docs.microsoft.com/intune/exchange-service-connector-configure)



### <a name="plan-for-change-performance-updates-to-intune-for-education---1750215--"></a>Planear a alteração: Atualizações de desempenho para o Intune for Education <!--1750215-->
Estamos a adicionar algumas atualizações ao Intune for Education de forma a aumentar a velocidade e a fiabilidade quando atribui definições aos seus utilizadores ou dispositivos. No âmbito desta alteração, perto do fim do mês de novembro, moveremos as suas políticas ou atribuições de definições para novos grupos.

#### <a name="how-does-this-affect-me"></a>Como é que isto me afeta?

Como do Intune para clientes de educação, tem dois grupos dinâmicos do Azure Active Directory (Azure AD): "Todos os utilizadores" e "Todos os dispositivos". Com estas atualizações, estes grupos "Todos os Utilizadores" e "Todos os dispositivos" do Azure AD não serão visíveis na consola do Intune for Education. Contudo, permanecerão visíveis na consola do Intune no Azure e o nome deles mudará para "Todos os utilizadores (Obsoleto, não utilizar)" e "Todos os Dispositivos (Obsoleto, não utilizar)".

Quando as atualizações forem implementadas, já não terá de utilizar grupos do Azure AD para atribuir aplicações e definições no Intune. Em vez disso, moveremos as suas atribuições de Definições para novos grupos da consola do Intune for Education que vamos criar automaticamente e que continuarão a ser apresentados como "Todos os Utilizadores" e "Todos os Dispositivos" conforme acontecia anteriormente. Estas alterações ocorrem ao nível do back-end, pelo que não se aperceberá da existência de diferenças na consola do Intune for Education. Não se prevê que os seus utilizadores finais ou dispositivos inscritos sejam afetados. 

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>O que preciso de fazer para me preparar para esta alteração?
Não tem de fazer nada enquanto movemos as suas atribuições de políticas. Se estiver a atribuir políticas na consola do Intune for Education, continue a fazê-lo.

Se estiver a atribuir políticas aos grupos do Azure AD acima mencionados no Intune no Azure, comece, em vez disso, a atribuí-los ao grupo Todos os Utilizadores e Todos os Dispositivos na consola do Intune for Education. Quando vir que o nome dos grupos do Azure AD mudou e passou a incluir a palavra "obsoleto" na consola, pare de atribuir políticas no Azure AD. Se não estiver a utilizar os grupos cujo nome mudou para outro fim, deve eliminá-los.

### <a name="plan-for-change-new-intune-support-experience-for-premier-customers"></a>Planear a alteração: Experimente o novo suporte do Intune para Premier clientes 
12/4/18 atualização: Estamos tentando tornar esse processo melhor para si, para a criação do pedido de suporte no MPO será não desativada a 3 de Dezembro, mas numa data posterior em vez disso. Vamos informá-sei através do Centro de mensagens e atualizar esta publicação em breve para partilhar as linhas do tempo para que esta alteração.

Como cliente Premier da Microsoft, atualmente, pode utilizar o portal do Microsoft Premier Online (MPO) (premier.microsoft.com) e o Intune no Azure (portal.azure.com) para criar pedidos de suporte do Intune. A partir de 3 de dezembro de 2018, no sentido de continuar a melhorar a experiência de suporte Premier, poderá criar pedidos de suporte apenas no Intune no Azure.

#### <a name="how-does-this-affect-me"></a>Como é que isto me afeta?
Depois de 3 de dezembro, não poderá criar pedidos de suporte no MPO.  Quando tentar fazê-lo, verá uma mensagem a informar que será redirecionado para o Intune no Azure, a qual não poderá dispensar. Aqui, pode criar um pedido de suporte, que será encaminhado para o Suporte da Microsoft dedicado ao Intune para diagnosticar e resolver o seu problema atempadamente. Os pedidos de suporte criados no portal do MPO não podem ser visualizados no portal do Azure, pelo que deve parar de criar pedidos de suporte no MPO.  

Se utilizar uma gestão de dispositivos móveis híbrida (MDM híbrida) ou cogestão, pode continuar a utilizar o MPO para criar pedidos de suporte para o ConfigMgr, mas utilizar o portal do Azure para criar pedidos de suporte para o Intune. Lembre-se de que a MDM híbrida foi preterida e que deve planear mudar para o Intune no Azure o mais rapidamente possível. Para obter mais informações, veja [Move from Hybrid Mobile Device Management to Intune on Azure](https://aka.ms/hybrid_notification) (Mover da Gestão de Dispositivos Móveis Híbrida para o Intune no Azure).

Tenha em atenção que apenas os utilizadores com as funções Administrador Global, Administrador do Serviço Intune e Administrador de Assistência Técnica podem criar pedidos de suporte no portal do Azure.

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>O que posso fazer para me preparar para esta alteração?
- Pare de utilizar o MPO e utilize o Intune no Azure para criar e gerir todos os pedidos de suporte do Intune.  
- Notifique o seu suporte técnico e atualize a documentação, se necessário.
- Se tiver utilizadores sem as funções Administrador Global ou Administrador do Serviço Intune a criar pedidos de suporte no MPO, atribua-lhes a função Administrador de Assistência Técnica no Azure Active Directory, para que possam continuar a criar pedidos de suporte no portal do Azure.
- Clique em Informações Adicionais para obter mais informações e ligações úteis.

#### <a name="additional-information"></a>Informações adicionais
Para obter mais informações, veja a [mensagem de blogue da equipa de suporte do Microsoft Intune](https://aka.ms/IntuneSupport_MPO_to_Azure).


### <a name="take-action-please-update-your-android-device-restriction-or-compliance-policy-password-settings-in-intune"></a>Tome medidas: Atualize o seu dispositivo Android restrição ou a conformidade de palavra-passe definições de política no Intune
O Intune irá remover o tipo de palavra-passe "predefinição do dispositivo" disponível para dispositivos com o Android 4.4 e superior. Devido às diferenças entre plataformas e predefinições de dispositivos Android, essa política é normalmente considerada opcional pelo dispositivo. Para tornar claro em que momento esta definição é aplicada no Android, vamos remover esta definição da IU numa próxima versão. 
#### <a name="how-does-this-affect-me"></a>Como é que isto me afeta?
- Se quiser exigir uma palavra-passe nos dispositivos, recomendamos que, em vez de utilizar a "predefinição do dispositivo", edite os perfis da sua plataforma Android de modo a indicar claramente o tipo de palavra-passe exigido.
- Se quiser que a decisão de criar ou não uma palavra-passe seja do utilizador final, selecione o botão "Não configurado". Se a definição continuar a funcionar após a removermos da IU, ser-lhe-á pedido que selecione um valor diferente de "Predefinição do dispositivo" na próxima vez que editar o perfil.
O que preciso de fazer para me preparar para esta alteração?
Reveja as definições de palavra-passe no seu Android e nas políticas de restrição e conformidade de dispositivos empresariais Android. Estas estão listadas em Segurança do sistema, no menu Políticas de conformidade, e em Palavra-passe do dispositivo ou Definições do perfil de trabalho, no menu Restrições do dispositivo. A secção Informações adicionais contém uma ligação para detalhes e capturas de ecrã adicionais que mostra onde estas definições podem ser configuradas.
#### <a name="additional-information"></a>Informações adicionais
https://aka.ms/PasswordSettings 


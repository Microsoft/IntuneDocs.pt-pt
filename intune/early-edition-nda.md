---
title: Edição antecipada – Microsoft Intune
titlesuffix: ''
description: Edição antecipada do Microsoft Intune
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 12/3/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.openlocfilehash: 77aa0d1544351adaa8d338bc7c4c7182d35941e8
ms.sourcegitcommit: 0f19bc5c76b7c0835bfd180459f2bbd128eec1c2
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/11/2018
ms.locfileid: "53267026"
---
# <a name="the-early-edition-for-microsoft-intune---december-2018"></a>A edição antecipada do Microsoft Intune – Dezembro de 2018

> [!Note]
> Notificação de contrato de confidencialidade: As seguintes alterações estão em desenvolvimento para o Intune. Estas informações são partilhadas ao abrigo de um contrato de confidencialidade numa base muito limitada. Não publique estas informações em redes sociais ou em sites públicos como o Twitter, UserVoice, Reddit, entre outros. 

A **edição antecipada** oferece uma lista de funcionalidades, partilhadas ao abrigo de um contrato de confidencialidade, que estarão disponíveis em versões futuras do Microsoft Intune. Esta informação é fornecida numa base limitada e está sujeita a alterações. Não publique no Twitter nem no UserVoice, nem partilhe estas informações de nenhuma outra forma com pessoas fora da sua empresa. Algumas funcionalidades aqui indicadas estão em risco de não serem incluídas dentro das datas limite e podem ser adiadas até uma versão futura. Outras funcionalidades estão a ser testadas numa implementação piloto (distribuição de pacotes piloto) para garantir que estão prontas para os clientes. Contacte o seu contacto do grupo de produtos da Microsoft se tiver dúvidas ou preocupações.

Esta página é atualizada periodicamente. Volte a consultar posteriormente para obter mais atualizações.

<!--
## What's coming to Intune in the Azure portal  
## What's coming to Intune apps
## Notices
-->
 
## <a name="intune-in-the-azure-portal"></a>Intune no portal do Azure

<!-- 1812 start -->

### <a name="android-enterprise-app-we-app-deployment----1171203---"></a>Aplicação do Android Enterprise-implementação de aplicações, <!-- 1171203 -->
Para dispositivos Android num não inscritos proteção política sem inscrição de aplicações (APP-PODEMOS) cenário de implementação, poderá usar o Google Play gerido para implementar aplicações da loja e aplicações aos utilizadores LOB. Especificamente, o departamento de TI pode fornecer aos utilizadores finais uma experiência de instalação e de catálogo de aplicações que já não necessita que os utilizadores finais flexibilize as a postura de segurança dos seus dispositivos ao permitir que as instalações de origens desconhecidas. Além disso, neste cenário de implementação irá fornecer uma experiência de usuário aprimorada do fim.

### <a name="new-options-to-automatically-connect-and-persist-rules-when-using-dns-settings-on-windows-10-and-later-devices----1333665-2999078---"></a>Novas opções para automaticamente se ligar e manter regras ao utilizar as definições de DNS no Windows 10 e dispositivos posteriores <!-- 1333665, 2999078 -->
No Windows 10 e dispositivos posteriores, poderá criar um perfil de configuração de VPN que inclui uma lista de servidores DNS para resolver domínios, tal como contoso.com. Isto irá incluir as novas definições para resolução de nomes (**configuração do dispositivo** > **perfis** > **criar perfil** > Escolha  **Windows 10 e posterior** para a plataforma > Escolha **VPN** para o tipo de perfil > **definições de DNS** >**adicionar**): 

- **Ligar automaticamente**: Quando **ativado**, o dispositivo estabelece ligação automaticamente para a VPN quando um dispositivo entra em contacto com um domínio, introduza, por exemplo, contoso.com.
- **Persistente**: Por predefinição, todas as regras de tabela (NRPT) de política de resolução de nome estão ativas, desde que o dispositivo estiver conectado com este perfil VPN. Quando esta definição for **ativado** numa regra NRPT, a regra permanece ativa no dispositivo, mesmo quando desliga a VPN ou o perfil VPN é removido. A regra mantém-se até ser manualmente removido, que pode ser feito com o PowerShell.

[Definições de VPN do Windows 10](vpn-settings-windows-10.md) descreve a lista atual de definições. 

### <a name="use-smime-to-encrypt-and-sign-multiple-devices-for-a-user----1333642-eeready---"></a>Utilizar S/MIME para encriptar e assinar vários dispositivos para um utilizador <!-- 1333642 eeready -->
Encriptação de correio eletrónico de S/MIME com um novo perfil de certificado importado será suportada (**configuração do dispositivo** > **perfis** > **criar perfil** > selecione a plataforma > **certificado importado PKCS** tipo de perfil). No Intune, pode importar certificados no formato PFX. O Intune pode enviar esses mesmos certificados para múltiplos dispositivos inscritos por um único utilizador. Isto também inclui:

- O perfil de e-mail nativo do iOS suporta a ativação da encriptação S/MIME através de certificados importados no formato PFX.
- A aplicação de e-mail nativa dos dispositivos Windows Phone 10 utiliza automaticamente o certificado S/MIME.
- Os certificados privados podem ser fornecidos a várias plataformas. No entanto, nem todas as aplicações de e-mail suportam S/MIME.
- Noutras plataformas, talvez seja necessário configurar manualmente a aplicação de e-mail para permitir o S/MIME.  
- As aplicações de e-mail que suportam a encriptação S/MIME conseguem obter certificados para a encriptação S/MIME de e-mails de uma forma que não é suportada por MDM, como a leitura a partir do arquivo de certificados do respetivo publicador.

Suportado no: Windows Phone 10, Windows, iOS, Android e macOS

### <a name="help-and-support-page-in-the-windows-company-portal-app----1488939---"></a>Página Ajuda e suporte na aplicação de Portal da empresa do Windows <!-- 1488939 -->
Aplicação de Portal da empresa do Windows será adicionada uma nova página. A página de ajuda e suporte irá fornecer informações de contacto de suporte técnico. Além disso, os utilizadores finais será capazes de enviar que registos do Portal da empresa, se estiver a ter problemas. A página também fornece uma secção de FAQ para ajudar os utilizadores finais.

### <a name="use-trusted-network-detection-for-vpn-profiles-on-windows-10-devices----1500165---"></a>Utilizar a deteção de rede fidedigna para perfis VPN em dispositivos Windows 10 <!-- 1500165 -->
Ao utilizar a deteção de rede fidedigna, poderá impedir que os perfis VPN crie automaticamente uma ligação VPN quando o utilizador já se encontra numa rede fidedigna. Será capaz de adicionar sufixos DNS para ativar a deteção de rede fidedigna em dispositivos com Windows 10 e posterior (**configuração do dispositivo** > **perfis**  >   **Criar perfil** > **Windows 10 e posterior** para a plataforma > **VPN** para tipo de perfil).
[Definições de VPN do Windows 10](vpn-settings-windows-10.md) lista as definições de VPN atuais.

### <a name="the-intune-app-sdk-will-support-256-bit-encryption-keys----1832174---"></a>O SDK da aplicação Intune irá suportar as chaves de encriptação de 256 bits <!-- 1832174 -->
Quando a encriptação está ativada por políticas de proteção de aplicações, o SDK da aplicação Intune para iOS utilizará as chaves de encriptação de 256 bits. O SDK irá continuar a fornecer suporte de chaves de 128 bits para compatibilidade com o conteúdo e aplicações que utilizam versões mais antigas do SDK.

### <a name="enabled-shared-pc-settings-in-intune-profile----1907917---"></a>Definições do PC partilhadas ativadas no perfil do Intune <!-- 1907917 -->
Atualmente, pode configurar definições do PC compartilhado em dispositivos de ambiente de trabalho Windows 10 com uma definição de OMA-URI personalizada. Será adicionado um novo perfil para configurar definições do PC compartilhado (**configuração do dispositivo** > **perfis** > **criar perfil**  >  **Windows 10 e posterior** > **dispositivos de vários utilizadores partilhado**).
Aplica-se a: Windows 10 e posterior, Windows Holographic for Business

### <a name="intune-policies-update-authentication-method-and-company-portal-app-installation-----1927359---"></a>As políticas do Intune atualizar o método de autenticação e a instalação da aplicação Portal da empresa  <!-- 1927359 -->
Nos dispositivos já inscritos através do Assistente de configuração através de um dos métodos de inscrição de dispositivos da empresa da Apple, o Intune suportará já não é o Portal da empresa quando é instalado manualmente pelos usuários finais da loja de aplicações. Esta alteração é relevante apenas quando se autenticar com o Assistente de configuração da Apple durante a inscrição. Esta alteração afeta também apenas dispositivos iOS inscritos através de:  
* Do Apple configurator
* Gerente de negócios da Apple
* Gestor Escolar da Apple
* Programa de inscrição de dispositivos Apple (DEP)

Se os utilizadores instalarem a aplicação Portal da empresa a partir da App store e, em seguida, tentar inscrever estes dispositivos através do mesmo, receberá um erro. Estes dispositivos serão esperados para utilizar o Portal da empresa apenas quando ele é foi emitido, automaticamente, pelo Intune durante a inscrição. Perfis de inscrição no Intune no portal do Azure serão atualizados para que pode especificar a forma como os dispositivos serão autenticados e se eles recebem a aplicação Portal da empresa. Se pretender que os utilizadores de dispositivos do DEP para o portal da empresa, terá de especificar as suas preferências num perfil de inscrição. Além disso, o **identificar o seu dispositivo** ecrã na aplicação Portal da empresa em breve se tornarão obsoleta.  
Para instalar o Portal da empresa em dispositivos DEP já inscrito, terá de ir para o Intune > aplicações de cliente e enviá-los como uma aplicação gerida com as políticas de configuração de aplicações. Detalhes sobre como efetuar estes passos irão ser descritos nos documentos futuros.

### <a name="non-administrators-can-enable-bitlocker-on-windows-10-devices-joined-to-azure-ad---2147379---"></a>Os não administradores podem ativar o BitLocker em dispositivos Windows 10 associados ao Azure AD<!-- 2147379 -->
Quando ativa as definições do BitLocker em dispositivos Windows 10 (**configuração do dispositivo** > **perfis** > **criar perfil**  >  **Windows 10 e posterior** para a plataforma > **proteção de ponto final** para o tipo de perfil > **encriptação Windows**), adicionar as definições do BitLocker. Esta atualização inclui uma nova definição de disco BitLocker para permitir que os usuários padrão (não-administradores) ativar a encriptação. Para ver as definições atuais, veja [definições do Endpoint protection para Windows 10](endpoint-protection-windows-10.md#windows-encryption).

### <a name="intune-app-pin----2298397---"></a>PIN da aplicação Intune <!-- 2298397 -->
O administrador de TI, poderá configurar o número de dias que um utilizador final pode aguardar até ser preciso Alterar PIN da aplicação Intune. A nova definição vai estar disponível no portal do Azure, selecionando **Intune** > **aplicações de cliente** > **políticas de proteção de aplicações**  >  **Criar política** > **definições** > **os requisitos de acesso**. Esta funcionalidade estará disponível em dispositivos iOS e Android. Esta definição suporta um valor de número inteiro positivo.

### <a name="new-windows-10-update-settings----2626030-2512994---"></a>Novas definições de atualização do Windows 10 <!-- 2626030 2512994 -->
Para sua Cadências de atualização do Windows 10, poderá:
- restaurar as definições de atualização automática original numa máquina de Windows 10 em computadores que executam o *atualização de Outubro de 2018*
- configurar um novo Software de atualizações de definição que permite-lhe bloquear ou permitir que os utilizadores para a instalação da atualização de colocar em pausa a *definições* das suas máquinas. 



### <a name="ios-email-profiles-can-use-smime-signing-and-encryption----2662949---"></a>perfis de e-mail do iOS podem utilizar a encriptação e assinatura S/MIME <!-- 2662949 -->
Será capaz de criar um perfil de e-mail que inclui definições diferentes. Isso inclui configurações de S/MIME que podem ser utilizadas para assinar e criptografar as comunicações por e-mail em dispositivos iOS (**configuração do dispositivo** > **perfis**  >   **Criar perfil** > escolher **iOS** para a plataforma > **E-Mail** para tipo de perfil).

[definições de configuração de e-mail do iOS](email-settings-ios.md) lista as definições atuais.

### <a name="skip-more-setup-assistant-screens-on-an-ios-dep-device----2687509---"></a>Ignorar mais ecrãs do Assistente de configuração num dispositivo DEP iOS <!-- 2687509 -->
Além dos ecrãs que atualmente pode ignorar, poderá definir iOS dispositivos DEP para ignorar os ecrãs seguintes no Assistente de configuração, quando um utilizador inscreve o dispositivo: Apresenta tom, privacidade, migração Android, botão Home page, iMessage & FaceTime, integração, migração de Watch, aparência, tempo de tela, atualização de Software, a configuração SIM.
Para escolher que telas para ignorar, aceda a **inscrição de dispositivos** > **inscrição da Apple** > **tokens do programa de inscrição** > Escolha um token > **Perfis** > Escolha um perfil > **propriedades** > **personalização do Assistente de configuração** > Escolha **ocultar**  para qualquer telas que pretende ignorar > **OK**.

### <a name="some-bitlocker-settings-support-windows-10-pro-edition---2727036---"></a>Algumas definições de BitLocker suportam a edição Windows 10 Pro<!-- 2727036 -->
Será capaz de criar um perfil de configuração que define as definições do endpoint protection em dispositivos Windows 10, inclusive BitLocker. Esta ação adiciona suporte para a edição Windows 10 Professional para algumas configurações de disco BitLocker. Para ver as definições de edição atuais do Windows 10, consulte [definições do Endpoint protection para Windows 10](endpoint-protection-windows-10.md#windows-encryption).
Intune irá oferecer relatórios campos, incluindo Android fabricante, modelo e versão de patch de segurança, bem como o modelo de iOS adicionais do dispositivo. No Intune, estes campos estarão disponíveis, selecionando **aplicações de cliente** > **estado de proteção de aplicações** e escolha **relatório de proteção de aplicações: iOS, Android**. Além disso, esses parâmetros irão ajudá-lo a configurar o **permitir** lista para o fabricante do dispositivo (Android), o **permitir** lista para o modelo do dispositivo (Android e iOS) e o patch de segurança mínima para Android definição de versão. 

### <a name="intune-device-reporting-fields----2748738---"></a>Campos de relatórios de dispositivos do Intune <!-- 2748738 -->
Intune irá oferecer relatórios campos, incluindo Android fabricante, modelo e versão de patch de segurança, bem como o modelo de iOS adicionais do dispositivo. No Intune, estes campos estarão disponíveis, selecionando **aplicações de cliente** > **estado de proteção de aplicações** e escolha **relatório de proteção de aplicações: iOS, Android**. Além disso, esses parâmetros irão ajudá-lo a configurar o **permitir** lista para o fabricante do dispositivo (Android), o **permitir** lista para o modelo do dispositivo (Android e iOS) e o patch de segurança mínima para Android definição de versão. 

### <a name="shared-device-configuration-is-renamed-to-lock-screen-message-for-ios-devices-in-the-azure-portal----2809362---"></a>Configuração de dispositivos partilhados foi mudada para mensagem de ecrã de bloqueio para dispositivos iOS no portal do Azure <!-- 2809362 -->
Quando cria um perfil de configuração para dispositivos iOS, poderá adicionar **configuração de dispositivos partilhados** definições para mostrar o texto específico no ecrã de bloqueio. Isto inclui as seguintes alterações: 

- O **configuração de dispositivos partilhados** definições no portal do Azure são o nome mudadas para "Mensagem de ecrã de bloqueio (apenas supervisionada)" (**configuração do dispositivo** > **perfis**  >  **Criar perfil** > Escolha **iOS** para a plataforma > Escolha **funcionalidades do dispositivo** para o tipo de perfil > **bloqueio Mensagem de ecrã**).
- Ao adicionar mensagens de ecrã de bloqueio, pode inserir um número de série, um nome de dispositivo ou outro valor específicos do dispositivo como uma variável no **informações da etiqueta de recursos**. Por exemplo, pode introduzir `Device name: {{device name}}` ou `Serial number is {{serial number}}` usando chaves de saída. [iOS tokens](app-configuration-policies-use-ios.md#tokens-used-in-the-property-list) apresenta uma lista de tokens disponíveis que podem ser utilizados.

[Definições para apresentar mensagens no ecrã de bloqueio](shared-device-settings-ios.md) lista as definições atuais.

### <a name="more-detailed-enrollment-restriction-failure-messaging----3111564--"></a>Mais mensagens de falha de restrição de inscrição <!-- 3111564-->
Mensagens de erro mais detalhadas estará disponíveis quando não forem cumpridas restrições de inscrição. Para ver estas mensagens, aceda à **Intune** > **resolução de problemas** > e consulte a tabela de falhas de inscrição.

### <a name="new-notification-hints-and-keyguard-settings-to-android-enterprise-device-owner-devices----3201839-3201843---"></a>Novas definições de notificação, sugestões e keyguard para dispositivos de proprietário do dispositivo Android Enterprise <!-- 3201839 3201843 -->
Esta atualização inclui várias novas funcionalidades em dispositivos Android Enterprise quando em execução como proprietário do dispositivo. Para utilizar estas funcionalidades, aceda a **configuração do dispositivo** > **perfis** > **criar perfil** > no **plataforma**, escolha **Android Enterprise** > no **tipo de perfil**, escolha **proprietário do dispositivo só** > **dispositivo Restrições**.
Os novos recursos incluem: 
- Desative as notificações de sistema de apresentação, incluindo a entrada chamadas, alertas do sistema, erros de sistema e muito mais
- Sugere a ignorar a partir de tutoriais e dicas para aplicações que são abertas pela primeira vez
- Desativar keyguard avançada desbloquear as definições, tais como a câmara, notificações, impressão digital e muito mais

Para ver as definições atuais, aceda à [definições de restrição de dispositivos Android Enterprise](device-restrictions-android-for-work.md).

### <a name="android-enterprise-device-owner-devices-can-use-always-on-vpn-connections----3202194---"></a>Dispositivos de proprietário de dispositivos empresariais Android podem utilizar ligações de VPN AlwaysOn <!-- 3202194 -->
Nesta atualização, pode utilizar ligações VPN sempre ativada nos dispositivos de proprietário do dispositivo Android empresarial. As ligações VPN Sempre Ativada permanecem ativadas ou voltam a ativar-se quando o utilizador desbloqueia o dispositivo, quando o dispositivo é reiniciado ou quando a rede sem fios é alterada. Também pode colocar a ligação em modo de "bloqueio". Este modo permite bloquear todo o tráfego de rede até à ativação da ligação de VPN.
Pode ativar a VPN sempre ativada no **configuração do dispositivo** > **perfis** > **criar perfil**  >   **Android enterprise** para a plataforma > **restrições de dispositivos** para o proprietário do dispositivo só > **conectividade** definições. Para ver as definições atuais, aceda à [definições de restrição de dispositivos Android Enterprise](device-restrictions-android-for-work.md).

### <a name="new-setting-to-end-processes-in-task-manager-on-windows-10-devices----3285177---"></a>Nova definição para processos de fim no Gerenciador de tarefas em dispositivos Windows 10 <!-- 3285177 --> 
Esta atualização inclui uma nova definição para terminar a processos usando o Gerenciador de tarefas em dispositivos Windows 10. Utilizar um perfil de configuração do dispositivo (**configuração do dispositivo** > **perfis** > **criar perfil** > no **plataforma** , escolha **Windows 10** > no **tipo de perfil**, escolha **restrições de dispositivos** > **geral** definições), optar por permitir ou impedir que esta definição.
Para ver as definições atuais, aceda à [definições de restrição de dispositivos Windows 10](device-restrictions-windows-10.md).
Aplica-se a: Windows 10 e posterior

### <a name="administrative-templates-are-in-public-preview-and-moved-to-their-own-configuration-profile----3322847---"></a>Modelos administrativos estão em pré-visualização pública e movido para o seu próprio perfil de configuração <!-- 3322847 -->
Modelos administrativos no Intune (**configuração do dispositivo** > **modelos administrativos**) estão atualmente em pré-visualização privada. Com esta atualização: Modelos administrativos inclui aproximadamente 300 configurações que podem ser geridas no Intune. Anteriormente, estas definições só existiam no editor de políticas de grupo.
Modelos administrativos estão disponíveis em pré-visualização pública, administração estiver a mover de modelos **configuração do dispositivo** > **modelos administrativos** para **dispositivo configuração** > **perfis** >**criar perfil** > no **plataforma**, escolha  **Windows 10 e posterior**, na **tipo de perfil**, escolha **modelos administrativos**.
O relatório está ativado aplica-se a: Windows 10 e posterior


<!-- 1810 start -->

### <a name="use-microsoft-recommended-settings-with-security-baselines----2055484---"></a>Utilizar definições recomendadas pela Microsoft com Linhas de Base de Segurança <!-- 2055484 -->
O Intune tem integração com outros serviços centrados na segurança, incluindo o Windows Defender ATP e o Office 365 ATP. Os clientes estão a pedir uma estratégia comum e um conjunto coeso de fluxos de trabalho de segurança de ponto a ponto em todos os serviços do Microsoft 365. O nosso objetivo é alinhar estratégias para desenvolver soluções que criem uma ponte entre operações de segurança e tarefas de administrador comuns. No Intune, pretendemos cumprir este objetivo através da publicação de um conjunto de "Linhas de base de segurança" recomendadas pela Microsoft (**Intune** > **Linhas de base de segurança**).  Um administrador poderá criar políticas de segurança diretamente a partir dessas linhas de base e, em seguida, implementá-las nos seus utilizadores. Também pode personalizar as recomendações de melhores práticas para satisfazer as necessidades da sua organização. O Intune assegura que os dispositivos permanecem em conformidade com estas linhas de base e notifica os administradores de utilizadores ou dispositivos que não estejam em conformidade.

### <a name="scope-tags-for-apps---1081941---"></a>Etiquetas de âmbito para aplicações <!--1081941 -->
Poderá criar etiquetas de âmbito para limitar o acesso aos recursos do Intune. Adicione uma etiqueta de âmbito a uma atribuição de função e, em seguida, adicione a etiqueta de âmbito a um perfil de configuração. A função apenas terá acesso aos recursos com perfis de configuração com etiquetas de âmbito correspondentes (ou nenhuma etiqueta de âmbito).
Para criar uma etiqueta de âmbito, escolha **Funções do Intune** > **Âmbito (Etiquetas)** > **Criar**.
Para adicionar uma etiqueta de âmbito a uma atribuição de função, escolha **Funções do Intune** > **Todas as funções** > **Gestor de Políticas e Perfis** > **Atribuições** > **Âmbito (Etiquetas)**.
Para adicionar uma etiqueta de âmbito a um perfil de configuração, escolha **Configuração do dispositivo** > **Perfis** > escolha um perfil > **Propriedades** > **Âmbito (Etiquetas)**.

### <a name="tenant-health-dashboard----1124854---"></a>Dashboard de Estado de Funcionamento do Inquilino <!-- 1124854 -->
A página Estado do Inquilino no Intune irá fornecer-lhe informações sobre o estado do inquilino num único local. A página está dividida em quatro secções:  
- **Detalhes de inquilino**: Contém informações, tais como a autoridade de MDM, o total em dispositivos inscritos no seu inquilino e a conta de sua licença. Esta secção também fornece a versão do serviço atual do seu inquilino.
- **Estado do conector**: Contém informações sobre conectores configurados, por exemplo, o Apple VPP, Windows Store para empresas e conectores de certificados. Com base no respetivo estado atual, os conectores são sinalizados com *Bom estado de funcionamento*, *Aviso* ou *Mau estado de funcionamento*.
- **Estado de funcionamento do serviço Intune**: Contém incidentes activos ou falhas para o seu inquilino. As informações nesta secção são obtidas diretamente a partir do Centro de Mensagens do Office ([https://portal.office.com](https://portal.office.com)).
- **Notícias do Intune**: Contém mensagens ativas para o seu inquilino, que incluem opções como notificações que o seu inquilino tiver recebido as mais recentes funcionalidades do Intune. As informações nesta secção são obtidas diretamente a partir do Centro de Mensagens do Office ([https://portal.office.com](https://portal.office.com)).


### <a name="deployed-wip-policies-without-user-enrollment----1434452---"></a>Políticas WIP implementadas sem inscrição do utilizador <!-- 1434452 -->
As políticas do Windows Information Protection (WIP) poderão ser implementadas sem exigir que os utilizadores de MDM inscrevam os seus dispositivos Windows 10. Esta configuração permite que as empresas protejam os seus documentos empresariais com base na configuração do WIP, o que permite que o utilizador mantenha a gestão dos seus próprios dispositivos Windows. Assim que os documentos estiverem protegidos com uma política WIP, os dados protegidos poderão ser eliminados seletivamente por um administrador do Intune. Ao selecionar o utilizador e o dispositivo, e ao enviar um pedido de eliminação de dados, todos os dados protegidos através da política WIP ficarão inutilizáveis. No Intune, no portal do Azure, selecione **Aplicação móvel** > **Eliminação seletiva da aplicação**.


<!-- 1809 start -->  

### <a name="app-protection-policy-app-settings-for-web-data----2662995---"></a>Definições da Política de Proteção de Aplicações (APP) para dados da Web <!-- 2662995 -->
As definições da política APP para conteúdos da Web em dispositivos Android e iOS serão atualizadas para processar melhor ligações Web HTTP e HTTPS, bem como a transferência de dados através de Ligações Universais do iOS e Ligações de Aplicações do Android.  

<!-- 1808 start -->

### <a name="apple-vpp-token-used-by-another-mdm----1488946---"></a>Token Apple VPP utilizado por outra MDM <!-- 1488946 -->
O Intune irá detetar e mostrar detalhes se um token de programa de compras em volume (VPP) da Apple estiver a ser utilizado pelo Intune e outra MDM.

### <a name="retired-devices-in-the-device-compliance-dashboard----1981119---"></a>Dispositivos extintos no dashboard de conformidade do dispositivo <!-- 1981119 -->
Numa atualização futura, os dispositivos extintos serão removidos do dashboard de conformidade do dispositivo. Tal irá alterar os seus números de conformidade.


### <a name="change-in-the-update-process-for-on-premises-connectors----2277554---"></a>Alteração no processo de atualização de conectores no local <!-- 2277554 -->
Com base no feedback dos clientes, a forma como as atualizações são realizadas nos conectores no local será alterada. Depois da instalação inicial de um conector no local, as atualizações serão automáticas. Esta alteração começará com o novo PFX Certificate Connector para o Microsoft Intune e, em seguida, estender-se-á a outros tipos de conectores no local. 

<!-- 1807 start -->

### <a name="check-for-configuration-manager-compliance----2192052---"></a>Verificar a conformidade do Configuration Manager <!-- 2192052 -->
Uma futura atualização irá incluir uma nova definição de conformidade do System Center Configuration Manager (**Conformidade do dispositivo** > **Políticas** > **Criar política** > **Windows 10**). O Configuration Manager envia sinais de conformidade ao Intune. Com a definição do Intune, pode exigir que todos os sinais do Configuration Manager devolvam o estado "conforme".

Por exemplo, pode exigir que todas as atualizações do software sejam instaladas nos dispositivos. No Configuration Manager, este requisito apresenta o estado "Instalado". Se algum dos programas no dispositivo apresentar um estado desconhecido, o dispositivo será marcado como não compatível no Intune.

Aplica-se ao Windows 10 e posterior



## <a name="notices"></a>Avisos

Neste momento, não existem avisos ativos.

### <a name="see-also"></a>Consulte também
Veja [Novidades do Microsoft Intune](whats-new.md) para obter detalhes sobre os desenvolvimentos recentes.




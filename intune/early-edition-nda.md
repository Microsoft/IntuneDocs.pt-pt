---
title: Edição antecipada
description: ''
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 11/5/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 2f21df636ab429969429c6dbdf540daaa67a8f88
ms.sourcegitcommit: d8edd1c3d24123762dd6d14776836df4ff2a31dd
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/13/2018
ms.locfileid: "51576771"
---
# <a name="the-early-edition-for-microsoft-intune---november-2018"></a>A edição antecipada do Microsoft Intune – novembro de 2018

> [!Note]
> Notificação de contrato de confidencialidade: as seguintes alterações estão em desenvolvimento para o Intune. Estas informações são partilhadas ao abrigo de um contrato de confidencialidade numa base muito limitada. Não publique estas informações em redes sociais ou em sites públicos como o Twitter, UserVoice, Reddit, entre outros. 

A **edição antecipada** oferece uma lista de funcionalidades, partilhadas ao abrigo de um contrato de confidencialidade, que estarão disponíveis em versões futuras do Microsoft Intune. Esta informação é fornecida numa base limitada e está sujeita a alterações. Não publique no Twitter nem no UserVoice, nem partilhe estas informações de nenhuma outra forma com pessoas fora da sua empresa. Algumas funcionalidades aqui indicadas estão em risco de não serem incluídas dentro das datas limite e podem ser adiadas até uma versão futura. Outras funcionalidades estão a ser testadas numa implementação piloto (distribuição de pacotes piloto) para garantir que estão prontas para os clientes. Contacte o seu contacto do grupo de produtos da Microsoft se tiver dúvidas ou preocupações.

Esta página é atualizada periodicamente. Volte a consultar posteriormente para obter mais atualizações.

<!--
## What's coming to Intune in the Azure portal  
## What's coming to Intune apps
## Notices
-->
 
## <a name="intune-in-the-azure-portal"></a>Intune no portal do Azure

<!-- 1811 start -->

### <a name="uninstalling-apps-on-corporate-owned-supervised-ios-devices----1281677---"></a>Desinstalar aplicações em dispositivos iOS supervisionados pertencentes à empresa <!-- 1281677 -->
Poderá remover qualquer aplicação em dispositivos iOS supervisionados pertencentes à empresa. Pode remover qualquer aplicação ao visar os grupos de utilizadores ou dispositivos com um tipo de atribuição **Desinstalar**. Para dispositivos iOS pessoais ou não supervisionados, continuará a poder remover apenas as aplicações que foram instaladas com o Intune.

### <a name="track-installation-of-office-proplus---2620217--"></a>Monitorizar a instalação do Office ProPlus <!--2620217-->
Poderá monitorizar o progresso da instalação do [Office ProPlus](apps-add-office365.md) através da [Página de Estado de Inscrição](windows-enrollment-status.md).

### <a name="macos-device-enrollment-program-support-for-apple-school-manager-accounts---3006133--"></a>Suporte do Programa de Registo de Aparelho do macOS para as contas do Apple School Manager <!--3006133-->
O Intune fornecerá suporte através do Programa de Registo de Aparelho em dispositivos macOS para contas do Apple School Manager.

### <a name="temporarily-pause-kiosk-mode-on-android-devices-to-make-changes----3041935---"></a>Interromper temporariamente o modo de quiosque em dispositivos Android para fazer alterações <!-- 3041935 -->
Ao utilizar dispositivos Android no modo de quiosque de múltiplas aplicações, um administrador de TI poderá ter de fazer alterações ao dispositivo. Uma nova definição de quiosque de múltiplas aplicações que permitirá que um Administrador de TI interrompa temporariamente o modo de quiosque com um PIN e tenha acesso a todo o dispositivo.
Para ver as definições de quiosque atuais, veja [Android kiosk settings](android-kiosk-settings.md) (Definições de quiosque do Android).

### <a name="set-custom-background-in-managed-home-screen-app-----3041945---"></a>Configurar o fundo personalizado na aplicação Ecrã Inicial Gerido <!-- 3041945 -->
Vamos adicionar uma definição que lhe permite personalizar o aspeto do fundo da aplicação Ecrã Inicial Gerido em dispositivos Android Enterprise, com modo de quiosque de múltiplas aplicações.  Para configurar o **Fundo do URL personalizado**, aceda ao Intune no portal do Azure > Configuração do dispositivo. Selecione um perfil de configuração de dispositivo atual ou crie um novo para editar as respetivas definições de quiosque.

### <a name="enable-virtual-home-button-on-android-enterprise-kiosk-devices-----3042021---"></a>Ativar o botão Home virtual em dispositivos de quiosque Android Enterprise <!-- 3042021 -->
Uma nova definição permitirá que os utilizadores toquem num botão de tecla de função no respetivo dispositivo para alternar entre a aplicação Ecrã Inicial Gerido e outras aplicações atribuídas no respetivo dispositivo de quiosque de múltiplas aplicações. Esta definição é particularmente útil em cenários onde a aplicação de quiosque do utilizador não responde adequadamente ao botão "retroceder". Poderá configurar esta definição para dispositivos Android de utilização única, pertencentes à empresa. Para ativar ou desativar o **botão Home virtual**, aceda ao Intune no portal do Azure > Configuração do dispositivo. Selecione um perfil de configuração de dispositivo atual ou crie um novo para editar as respetivas definições de quiosque.

### <a name="app-protection-policy-assignment-save-and-apply----3104570---"></a>Guardar e aplicar a atribuição da política de proteção de aplicações <!-- 3104570 -->
Terá melhor controlo sobre as atribuições da política de proteção de aplicações. Ao guardar e aplicar as suas atribuições da política de proteção de aplicações, apenas os utilizadores pretendidos são diretamente afetados por uma política de proteção de aplicações.

### <a name="new-microsoft-edge-browser-settings-for-windows-10-and-later----3174639---"></a>Novas definições do browser Microsoft Edge para Windows 10 e posterior <!-- 3174639 -->
Será adicionada uma nova definição para ajudar a controlar e gerir o browser Microsoft Edge nos seus dispositivos. Para consultar uma lista das definições atuais, veja [Device restriction for Windows 10 (and newer)](device-restrictions-windows-10.md#microsoft-edge-browser) (Restrição de dispositivos para Windows e posterior).

### <a name="select-apps-tracked-on-the-enrollment-status-page---2531007---"></a>Selecionar aplicações monitorizadas na Página de Estado de Inscrição<!-- 2531007 -->
Poderá escolher quais serão as aplicações monitorizadas na Página de Estado de Inscrição.

### <a name="intune-app-protection-policies-ui-update----3251427---"></a>Atualização da IU das políticas de proteção de aplicações do Intune <!-- 3251427 -->

As políticas de proteção de Aplicações do Intune permitem-lhe configurar várias definições de proteção de dados para aplicações protegidas pelo Intune, como o Microsoft Outlook e o Word. Estamos a alterar a definição e as etiquetas de botão para facilitar a compreensão. Os controlos serão alterados dos controlos **sim**/**não** para os controlos **bloquear**/**permitir** e **desativar**/**ativar**. As etiquetas também serão atualizadas para uma maior clareza. As definições também serão reformatadas, pelo que a definição e respetiva etiqueta estão ao mesmo nível em relação ao controlo, o que proporciona uma melhor navegação. As predefinições e o número de definições permanecerão os mesmos, mas esta alteração permitirá que o utilizador compreenda, navegue e utilize as definições mais facilmente para aplicar determinadas políticas de proteção de aplicações.



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
- **Detalhes do Inquilino**: contém informações, como a sua Autoridade de MDM, o total de dispositivos inscritos no seu inquilino e as suas contagens de licenças. Esta secção também fornece a versão do serviço atual do seu inquilino.
- **Estado do Conector**: contém informações sobre os conectores configurados, como o Apple VPP, a Windows Store para Empresas e os conectores de Certificados. Com base no respetivo estado atual, os conectores são sinalizados com *Bom estado de funcionamento*, *Aviso* ou *Mau estado de funcionamento*.
- **Estado de Funcionamento do Serviço do Intune**: contém incidentes ativos ou falhas do seu inquilino. As informações nesta secção são obtidas diretamente a partir do Centro de Mensagens do Office ([https://portal.office.com](https://portal.office.com)).
- **Notícias do Intune**: contém mensagens ativas para o seu inquilino, incluindo notificações de que o mesmo recebeu as funcionalidades do Intune mais recentes. As informações nesta secção são obtidas diretamente a partir do Centro de Mensagens do Office ([https://portal.office.com](https://portal.office.com)).


### <a name="deployed-wip-policies-without-user-enrollment----1434452---"></a>Políticas WIP implementadas sem inscrição do utilizador <!-- 1434452 -->
As políticas do Windows Information Protection (WIP) poderão ser implementadas sem exigir que os utilizadores de MDM inscrevam os seus dispositivos Windows 10. Esta configuração permite que as empresas protejam os seus documentos empresariais com base na configuração do WIP, o que permite que o utilizador mantenha a gestão dos seus próprios dispositivos Windows. Assim que os documentos estiverem protegidos com uma política WIP, os dados protegidos poderão ser eliminados seletivamente por um administrador do Intune. Ao selecionar o utilizador e o dispositivo, e ao enviar um pedido de eliminação de dados, todos os dados protegidos através da política WIP ficarão inutilizáveis. No Intune, no portal do Azure, selecione **Aplicação móvel** > **Eliminação seletiva da aplicação**.


<!-- 1809 start -->  

### <a name="app-protection-policy-app-settings-for-web-data----2662995---"></a>Definições da Política de Proteção de Aplicações (APP) para dados da Web <!-- 2662995 -->
As definições da política APP para conteúdos da Web em dispositivos Android e iOS serão atualizadas para processar melhor ligações Web HTTP e HTTPS, bem como a transferência de dados através de Ligações Universais do iOS e Ligações de Aplicações do Android.  

<!-- 1808 start -->

### <a name="apple-vpp-token-used-by-another-mdm----1488946---"></a>Token Apple VPP utilizado por outra MDM <!-- 1488946 -->
O Intune irá detetar e mostrar detalhes se um token de programa de compras em volume (VPP) da Apple estiver a ser utilizado pelo Intune e outra MDM.

### <a name="ios-and-macos-version-numbers-and-build-numbers-are-available-in-compliance-policies----1892471---"></a>Os números de compilação e da versão do iOS e macOS estão disponíveis nas políticas de conformidade <!-- 1892471 -->
Em **Conformidade do dispositivo** > **Conformidade do dispositivo**, são apresentadas as versões dos sistemas operativos iOS e macOS. Estas versões estão disponíveis para serem utilizadas nas políticas de conformidade. Numa futura atualização, o número de compilação também será configurável para ambas as plataformas.

Quando as atualizações de segurança são lançadas, normalmente, a Apple não altera o número da versão, mas atualiza o número de compilação. Ao utilizar o número de compilação numa política de conformidade, pode verificar facilmente se foi instalada uma atualização da vulnerabilidade.

### <a name="retired-devices-in-the-device-compliance-dashboard----1981119---"></a>Dispositivos extintos no dashboard de conformidade do dispositivo <!-- 1981119 -->
Numa atualização futura, os dispositivos extintos serão removidos do dashboard de conformidade do dispositivo. Tal irá alterar os seus números de conformidade.


### <a name="change-in-the-update-process-for-on-premises-connectors----2277554---"></a>Alteração no processo de atualização de conectores no local <!-- 2277554 -->
Com base no feedback dos clientes, a forma como as atualizações são realizadas nos conectores no local será alterada. Depois da instalação inicial de um conector no local, as atualizações serão automáticas. Esta alteração começará com o novo PFX Certificate Connector para o Microsoft Intune e, em seguida, estender-se-á a outros tipos de conectores no local. 

<!-- 1807 start -->

### <a name="check-for-configuration-manager-compliance----2192052---"></a>Verificar a conformidade do Configuration Manager <!-- 2192052 -->
Uma futura atualização irá incluir uma nova definição de conformidade do System Center Configuration Manager (**Conformidade do dispositivo** > **Políticas** > **Criar política** > **Windows 10**). O Configuration Manager envia sinais de conformidade ao Intune. Com a definição do Intune, pode exigir que todos os sinais do Configuration Manager devolvam o estado "conforme".

Por exemplo, pode exigir que todas as atualizações do software sejam instaladas nos dispositivos. No Configuration Manager, este requisito apresenta o estado "Instalado". Se algum dos programas no dispositivo apresentar um estado desconhecido, o dispositivo será marcado como não compatível no Intune.

Aplica-se ao Windows 10 e posterior

### <a name="alerts-for-expiring-vpp-token-or-company-portal-license-running-low----2237572---"></a>Alertas de token VPP prestes a expirar ou de licenças do Portal da Empresa que se estão a esgotar <!-- 2237572 -->
Se utilizar o Programa de Compras em Volume (VPP) para aprovisionar previamente o Portal da Empresa durante a inscrição do DEP, o Intune irá alertá-lo quando o token VPP estiver prestes a expirar e quando as licenças do Portal da Empresa se estiverem a esgotar.



<!-- the following are present prior to 1711 -->

## <a name="notices"></a>Avisos

Neste momento, não existem avisos ativos.

### <a name="see-also"></a>Consulte também
Veja [Novidades do Microsoft Intune](whats-new.md) para obter detalhes sobre os desenvolvimentos recentes.




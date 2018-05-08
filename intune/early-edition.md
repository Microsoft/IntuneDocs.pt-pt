---
title: Edição antecipada
description: ''
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/24/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: d6a06326fbb60d910aef0411fc666b82a5f22078
ms.sourcegitcommit: 401cedcd7acc6cb3a6f18d4679bdadb0e0cdf443
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/28/2018
---
# <a name="the-early-edition-for-microsoft-intune---april-2018"></a>A edição antecipada do Microsoft Intune – abril de 2018

A **edição antecipada** oferece uma lista de funcionalidades disponíveis em versões futuras do Microsoft Intune. Esta informação é fornecida numa base limitada e está sujeita a alterações. Não partilhe estas informações fora da sua empresa. Algumas funcionalidades aqui indicadas estão em risco de não serem incluídas dentro das datas limite e podem ser adiadas até uma versão futura. Outras funcionalidades estão a ser testadas numa implementação piloto (distribuição de pacotes piloto) para garantir que estão prontas para os clientes. Contacte o seu contacto do grupo de produtos da Microsoft se tiver dúvidas ou preocupações.

Esta página é atualizada periodicamente. Volte a consultar posteriormente para obter mais atualizações.

> [!Note]
>As seguintes alterações estão em desenvolvimento para o Intune. Para obter mais informações sobre as novas funcionalidades híbridas, consulte a [página Hybrid What’s New (Novidades nas Implementações Híbridas)](/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management).

<!--
## What's coming to Intune in the Azure portal  
## What's coming to Intune apps
## Notices
-->
 
## <a name="intune-in-the-azure-portal"></a>Intune no portal do Azure

<!-- 1804 start -->




### <a name="additions-to-local-device-security-options-settings----1403702---"></a>Adições às definições de Opções de Segurança do Dispositivo Local <!-- 1403702 -->
Poderá configurar definições adicionais de Opções de Segurança do Dispositivo Local para dispositivos com o Windows 10. As definições adicionais estarão disponíveis nas áreas do Cliente de Rede da Microsoft, Servidor de Rede da Microsoft, Segurança e acesso à rede e Início de sessão interativo. Estas definições encontram-se na categoria Endpoint Protection durante a criação de uma política de configuração de dispositivo Windows 10.

### <a name="require-installation-of-policies-apps-certificate-and-network-profiles----1553555---"></a>Exigir a instalação de políticas, aplicações, perfis de certificado e de rede <!-- 1553555 -->
Os administradores poderão impedir os utilizadores finais de aceder ao ambiente de trabalho do Windows 10 RS4 até que o Intune instale as políticas, aplicações e perfis de certificado e de rede durante o aprovisionamento de dispositivos AutoPilot.

### <a name="rules-for-removing-devices----1609459---"></a>Regras para remover dispositivos <!-- 1609459 -->
Estarão disponíveis novas regras que lhe permitem remover automaticamente dispositivos que não se tenham registado durante o número de dias que definir. Para ver a nova regra, aceda ao painel **Intune**, selecione **Dispositivos** e selecione **Regras de remoção de dispositivo**.

### <a name="prevent-consumer-apps-and-experiences-on-windows-10-enterprise-rs4-autopilot-devices---1621980---"></a>Impedir as experiências e aplicações de consumidor em dispositivos AutoPilot com o Windows 10 Enterprise RS4<!-- 1621980 -->
Poderá impedir a instalação de experiências e aplicações de consumidor nos seus dispositivos AutoPilot com o Windows 10 Enterprise RS4. Para ver esta funcionalidade, aceda a **Intune** > **Inscrição de dispositivos** > **Inscrição no Windows** > **Perfis do Windows AutoPilot** > **Criar Novo** > **Definições de inscrição**. 


<!-- 1803 start -->

#### <a name="multiple-exchange-connector-support----2070451---"></a>Suporte múltiplo do Exchange Connector <!-- 2070451 -->

Deixará de ficar limitado a um Exchange Connector no Microsoft Intune por inquilino. O Intune suportará múltiplos Exchange Connectors para que possa configurar o acesso condicional do Intune com múltiplas organizações do Exchange no local.

Com um Exchange Connector no local do Intune, pode gerir o acesso de dispositivos a caixas de correio do Exchange no local com base no facto de um dispositivo estar ou não inscrito no Intune e estar ou não em conformidade com as políticas de conformidade de dispositivos do Intune. Para configurar um conector, transfira o Exchange Connector no local do Intune a partir do portal do Azure e instale-o num servidor na sua organização do Exchange. No dashboard do Microsoft Intune, selecione **Acesso no local** e, em **Configuração**, selecione **Conector do Exchange ActiveSync**. Transfira o Exchange Connector no local e instale-o num servidor na sua organização do Exchange. Como deixou de estar limitado a um Exchange Connector por inquilino, se tiver mais organizações do Exchange, pode seguir este processo para transferir e instalar um conector para cada organização do Exchange adicional.

### <a name="support-coming-for-new-cisco-anyconnect-client-for-ios----1333708---"></a>Suporte disponível em breve para o novo cliente do Cisco AnyConnect para iOS <!-- 1333708 -->

Os novos perfis de VPN criados para o Cisco AnyConnect para iOS funcionarão com a versão Cisco AnyConnect 4.0.7x e posteriores. Os perfis de VPN existentes do Cisco AnyConnect para iOS serão identificados como **Cisco Legacy AnyConnect** e continuarão a funcionar com a versão Cisco AnyConnect 4.0.5x tal como atualmente.

> [!NOTE]
> Esta alteração diz respeito apenas a dispositivos iOS. Continuará a haver apenas uma opção Cisco AnyConnect para Android, Android for Work e macOS.

#### <a name="more-information"></a>Mais informações

Tem de criar um novo perfil de VPN do Cisco AnyConnect para iOS para suportar a nova aplicação porque a nova aplicação Cisco AnyConnect e a aplicação Cisco Legacy AnyConnect são aplicações separadas. Se estiver a gerir o cliente AnyConnect no seu ambiente, também terá de implementar a nova aplicação Cisco AnyConnect. Para concluir uma atualização, também tem de eliminar o seu perfil de VPN Cisco Legacy AnyConnect e remover a aplicação Cisco Legacy AnyConnect.

A integração de controlo de acesso à rede (NAC) não funcionará para o novo cliente AnyConnect na versão inicial. Estamos a trabalhar com a Cisco para fornecer a integração de NAC numa versão futura do Intune.

### <a name="ability-to-deploy-required-line-of-business-lob-apps-to-all-users-on-windows-10-desktop-devices----1627835-rs4---"></a>Capacidade de implementar as aplicações de linha de negócio (LOB) necessárias em Todos os Utilizadores com computadores com o Windows 10 <!-- 1627835 RS4 -->
Os clientes poderão implementar as aplicações do Windows 10 de linha de negócio necessárias para as instalar em dispositivos. Isto permitirá que estas aplicações fiquem disponíveis para todos os utilizadores no dispositivo. Isto só é aplicável a computadores com o Windows 10.

### <a name="company-portal-enrollment-improved----1874230--"></a>Registo no Portal da Empresa melhorado <!-- 1874230-->
Os utilizadores que inscrevam um dispositivo ao utilizar o Portal da Empresa com a compilação 1703 e posteriores do Windows 10 poderão concluir o primeiro passo de inscrição sem sair da aplicação.

### <a name="updating-the-help-and-feedback-experience-on-company-portal-app-for-android---1631531---"></a>Atualizar a experiência de Ajuda e Feedback na aplicação Portal da Empresa para Android <!--1631531 -->

Iremos atualizar a experiência de Ajuda e Feedback na aplicação Portal da Empresa para Android para estarmos alinhados com as melhores práticas para aplicações Android. Iremos atualizar a aplicação Portal da Empresa para Android nos próximos meses para dividir o item de menu **Ajuda e Feedback** em itens de menu **Ajuda** e **Enviar Feedback** separados. A página **Ajuda** terá uma secção de **Perguntas Frequentes** e o botão **Suporte por E-mail** para que os utilizadores finais carreguem registos para a Microsoft e enviem e-mails para a empresa de suporte com a descrição do problema. O menu **Enviar Feedback** orientará o utilizador ao longo do processo padrão de submissão de feedback da Microsoft, que lhe pedirá para escolher entre "Gosto de algumas coisas", "Não de gosto de algumas coisas" ou "Tenho uma ideia".


<!-- the following are present prior to 1801 -->

### <a name="app-protection-policies-----679615---"></a>Políticas de Proteção de Aplicações <!-- 679615 -->
As Políticas de Proteção de Aplicações do Intune permitirão criar políticas predefinidas globais para ativar rapidamente a proteção em todos os utilizadores em todo o inquilino.

<!-- the following are present prior to 1711 -->

### <a name="azure-active-directory-web-sites-can-require-the-intune-managed-browser-app-and-support-single-sign-on-for-the-managed-browser-public-preview----710595---"></a>Os sites do Azure Active Directory podem exigir a aplicação Intune Managed Browser e o suporte do Início de Sessão Único do Managed Browser (Pré-visualização Pública) <!-- 710595 -->   
Com o Azure Active Directory (Azure AD), poderá restringir o acesso a sites em dispositivos móveis na aplicação Intune Managed Browser. No Managed Browser, os dados dos sites permanecerão protegidos e separados dos dados pessoais dos utilizadores finais. Além disso, o Managed Browser suporta as funcionalidades de Início de Sessão Único para sites protegidos pelo Azure AD. Iniciar sessão no Managed Browser ou utilizá-lo num dispositivo com outra aplicação gerida pelo Intune permite que o Managed Browser aceda a sites empresariais protegidos pelo Azure AD sem que o utilizador tenha de introduzir as suas credenciais. Esta funcionalidade aplica-se a sites como o Outlook Web Access (OWA) e o SharePoint Online, bem como a outros sites empresariais como recursos de intranet acedidos através do Proxy de Aplicações do Azure.




## <a name="notices"></a>Avisos

Neste momento, não existem avisos ativos.


### <a name="see-also"></a>Consulte também
Veja [Novidades do Microsoft Intune](whats-new.md) para obter detalhes sobre os desenvolvimentos recentes.



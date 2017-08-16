---
title: Ativar o BYOD com o Microsoft Intune
description: "Lista de passos gerais para configurar o Intune para ativar uma solução BYOD (Bring Your Own Device) na sua organização."
keywords: 
author: lindavr
ms.author: lindavr
manager: angrobe
ms.date: 07/26/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 
ms.reviewer: vlpetros
ms.suite: ems
ms.openlocfilehash: 0d05918a62549559a186376d99e28c952af16b9c
ms.sourcegitcommit: 1c71fff769ca0097faf46fc2b58b953ff28386e8
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/08/2017
---
# <a name="enable-byod-with-intune"></a>Ativar o BYOD com o Intune

Este tópico fornece uma lista de passos gerais para configurar o Intune para ativar uma solução BYOD (Bring Your Own Device) na sua organização. Esta lista organiza a tarefa em três processos e contém ligações para os tópicos com instruções de suporte.

A lista de passos está dividida nos três processos seguintes. Pode personalizar os aspetos de cada processo para corresponder às necessidades da sua organização.

-   A secção **[Inscrever dispositivos e verificar a conformidade](#enroll-devices-and-check-for-compliance)** descreve como permitir que os utilizadores inscrevam os seus dispositivos pessoais para gestão no Intune. O Intune gere dispositivos iOS, macOS, Android e Windows. Esta secção também descreve como implementar políticas em dispositivos e como se certificar de que estes cumprem os requisitos básicos de segurança.

- A secção **[Proporcionar o acesso aos recursos da empresa](#provide-access-to-company-resources)** mostra-lhe como pode permitir que os utilizadores acedam aos recursos da empresa de forma fácil e segura. Pode fazê-lo ao implementar perfis de aceso aos dispositivos geridos. Esta secção também explica como gerir as implementações de aplicações compradas em volume com o Intune.

-   A secção **[Proteger os dados da empresa](#protect-company-data)** ajuda-o a saber como fornecer acesso condicional aos recursos da empresa, evitar perdas de dados e remover aplicações e dados da empresa de dispositivos quando já não forem precisos para o seu trabalho ou se tiverem sido perdidos ou roubados.

[![Diagrama com uma lista de processos gerais para ativar a solução BYOD com o Microsoft Intune](./media/workflow-diagram-for-byod.png)](./media/workflow-diagram-for-byod.png)

<!--- > <sup>You can download this infographic at https://gallery.technet.microsoft.com/Infographic-Management-3644ae41.</sup> --->

## <a name="before-you-begin"></a>Antes de começar
Antes de os utilizadores poderem inscrever dispositivos, é necessário preparar o serviço do Intune. Para tal, [atribua licenças aos utilizadores](licenses-assign.md) e [defina a autoridade de gestão de dispositivos móveis](mdm-authority-set.md).

Pode aproveitar para [personalizar também o portal da empresa](company-portal-customize.md). Adicione a imagem corporativa da empresa e forneça informações de suporte aos utilizadores. Esta ação cria uma experiência de inscrição e suporte fidedigna para os seus utilizadores. Também pode criar [termos de utilização](terms-and-conditions-create.md) que os utilizadores têm de aceitar antes de se inscreverem ou [restrições de dispositivos](enrollment-restrictions-set.md) para especificar as plataformas que suporta.

## <a name="enroll-devices-and-check-for-compliance"></a>Inscrever dispositivos e verificar a conformidade

Após preparar o serviço do Intune, é necessário cumprir os diversos requisitos de inscrição para os diferentes tipos de dispositivos que pretende gerir. O processo de inscrição de dispositivos para gestão é muito simples, mas ligeiramente diferente consoante o tipo de dispositivo.

-   **Dispositivos Mac e iOS**: tem de [obter um Certificado Push de MDM da Apple](apple-mdm-push-certificate-get.md) para inscrever iPads, iPhones ou dispositivos MacOS. Depois de carregar o certificado push de MDM para o Intune, os utilizadores poderão [inscrever dispositivos iOS](/intune-user-help/enroll-your-device-in-intune-ios) através da aplicação Portal da Empresa e utilizar o site do Portal da Empresa para [inscrever dispositivos MacOS](/intune-user-help/enroll-your-device-in-intune-macos).

-   **Dispositivos Android**: não precisa de preparar nada no serviço do Intune para inscrever dispositivos Android. Os utilizadores podem simplesmente [inscrever os respetivos dispositivos Android](/intune-user-help/enroll-your-device-in-intune-android) para gestão através da aplicação do Portal da Empresa disponível no Google Play.

-   **Dispositivos Windows Phone e PCs**: os dispositivos Windows podem ser inscritos com configuração adicional. Para simplificar a experiência dos seus utilizadores, pode ativar a inscrição automática de PCs e dispositivos móveis com o Windows 10 no Azure Active Directory (AD) Premium. Se não tiver o Azure AD Premium ou precisar de suportar dispositivos com o Windows 8.1, pode criar [um alias de DNS para o endereço de servidor](windows-enroll.md#enable-windows-enrollment-without-azure-ad-premium) para facilitar a inscrição.


### <a name="make-sure-that-managed-devices-meet-basic-security-requirements"></a>Confirmar que os dispositivos geridos cumprem os requisitos básicos de segurança

Depois de os utilizadores inscreverem os respetivos dispositivos para gestão, os profissionais de TI têm de confirmar que os dispositivos que servem para aceder às aplicações e aos dados da empresa cumprem os requisitos básicos de segurança. As regras incluem a utilização de um PIN para aceder a dispositivos e encriptar dados armazenados em dispositivos. Um conjunto dessas regras denomina-se [política de conformidade](device-compliance.md).

Quando [implementar uma política de conformidade](device-compliance-get-started.md) para um utilizador, o Intune verifica todos os dispositivos que este tenha gerido pelo Intune, para confirmar que os requisitos básicos de segurança que definiu como parte da sua política BYOD são cumpridos. Depois de um dispositivo ter sido avaliado relativamente à conformidade com a política, comunica o respetivo estado ao Intune. Em alguns casos, pode ser pedido aos utilizadores para corrigir definições, como o PIN ou a encriptação do dispositivo. Noutros casos, a aplicação Portal da Empresa simplesmente notifica o utilizador acerca de definições que não cumprem a sua política.

## <a name="provide-access-to-company-resources"></a>Proporcionar o acesso aos recursos da empresa

A primeira coisa que a maioria dos funcionários quer nos dispositivos móveis é poder aceder aos e-mails e documentos da empresa. E esperam poder configurar esse acesso sem passar por processos complexos ou sem a ajuda do suporte técnico. O Intune facilita a [criação e a implementação de definições de e-mail](email-settings-configure.md) para as aplicações de e-mail nativas pré-instaladas nos dispositivos móveis.


> [!NOTE]
> O Intune suporta a configuração de perfis de e-mail do Android for Work para as aplicações de e-mail Gmail e Nine Work encontradas na Google Play Store.

O Intune ajuda-o a controlar e a proteger o acesso aos dados da empresa no local quando os utilizadores trabalham fora das instalações. Os perfis de e-mail, [Wi-Fi](wi-fi-settings-configure.md) e [VPN](vpn-settings-configure.md) do Intune funcionam em conjunto para conceder o acesso aos ficheiros e recursos de que os utilizadores precisam para trabalhar, estejam onde estiverem. As aplicações Web e os serviços alojados no local da empresa também podem ser acedidos de forma segura e protegida através do Proxy da Aplicação do Azure Active Directory e de acesso condicional.

### <a name="manage-volume-purchased-apps"></a>Gerir aplicações compradas em grandes volumes
Com o Intune, é fácil:
* Importar as informações de licenças em volume a partir de qualquer loja de aplicações
* Controlar quantas licenças utilizou
* Impedir os seus utilizadores de instalarem mais cópias da sua aplicação
* [Fornecer aplicações da loja a dispositivos geridos](apps-deploy.md)
* Direcionar aplicações para dispositivos não geridos através do site do portal da empresa

O Intune também lhe permite gerir e implementar as aplicações que comprou em volume na iOS App Store e na Loja Microsoft para Empresas. Esta possibilidade ajuda-o a reduzir a sobrecarga administrativa de controlar aplicações compradas em volume.

> [!TIP]
> Pode [configurar o Início de Sessão Único (SSO) com o Azure AD Connect](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect). O SSO permite aos utilizadores iniciar sessão em aplicações com o nome de utilizador e a palavra-passe do domínio que utilizam no local. Além disso, pode [fornecer acesso baseado na Internet a aplicações Web alojadas no local](https://docs.microsoft.com/azure/active-directory/active-directory-application-proxy-get-started) com o Proxy de Aplicações do Azure Active Directory.

-   [Gerir aplicações compradas em volume para dispositivos iOS](vpp-apps-ios.md). Compra múltiplas licenças para aplicações iOS através do [Apple Volume Purchase Program for Business](http://www.apple.com/business/vpp/). Tem de configurar uma conta Apple VPP no site da Apple e carregar o token Apple VPP para o Intune. Em seguida, pode sincronizar as informações de compra em volume com o Intune e controlar a utilização da aplicação comprada em volume.

-   [Gerir aplicações compradas na Loja Microsoft para Empresas](windows-store-for-business.md). Na [Loja Microsoft para Empresas](https://www.microsoft.com/business-store), pode encontrar e adquirir aplicações para a sua organização, individualmente ou em volume. Ao ligar a loja ao Intune, pode gerir as aplicações compradas em volume a partir do portal do Intune.

## <a name="protect-company-data"></a>Proteger os dados da empresa

O Intune protege os dados da empresa através de várias camadas de tecnologia. Na camada da identidade, o acesso condicional protege o acesso aos serviços. O Acesso Condicional só permite que dispositivos geridos e em conformidade acedam aos recursos da empresa. Na camada de aplicação do cliente, a gestão de aplicações móveis (MAM) protege contra a perda de dados.  As políticas de proteção da aplicação impedem que os dados sejam movidos para aplicações ou localizações de armazenamento que não estejam protegidas. Estas políticas também podem apagar os dados da empresa se um dos dispositivos for roubado ou perdido.

### <a name="enforce-conditional-access-to-company-resources"></a>Impor o acesso condicional aos recursos da empresa

Pode combinar as políticas de conformidade com [políticas de acesso condicional](device-compliance.md) para verificar se os dispositivos cumprem os requisitos básicos de segurança exigidos pela sua política BYOD. Se um dispositivo não cumprir os requisitos, as regras são impostas e o acesso é negado até que o dispositivo cumpra os requisitos da política. Assim garante que apenas os dispositivos geridos e em conformidade podem aceder aos dados da empresa a partir de serviços como o Exchange ([Exchange no Local](exchange-connector-install.md) ou [Exchange Online](conditional-access-exchange-create.md)), o SharePoint Online, o Skype para Empresas Online, entre outros.
<!---first link was (https://docs.microsoft.com/intune/deploy-use/restrict-access-to-email-and-o365-services-with-microsoft-intune)
third link was (https://docs.microsoft.com/intune/deploy-use/restrict-access-to-exchange-online-with-microsoft-intune). check with Andre--->

> [!IMPORTANT]
> As políticas de acesso condicional não funcionam se não existir uma política de conformidade em vigor para validar a conformidade.

### <a name="prevent-data-loss-of-company-data-with-application-protection-policies"></a>Evitar a perda de dados da empresa com as políticas de proteção de aplicações

Com as políticas de proteção de aplicações do Intune pode escolher a forma como os seus dados são acedidos, seja com ou sem a inscrição de dispositivos. Esta versatilidade permite-lhe proteger os dados da empresa de forma a que o utilizador possa continuar a aceder aos dados da empresa em segurança, mesmo sem inscrever o dispositivo no Intune.

Pode utilizar as [políticas de proteção de aplicações do Intune](app-protection-policies.md) para ajudar a proteger os dados da empresa que são acedidos pelos dispositivos iOS e Android dos seus utilizadores. Quando utiliza estas políticas ao nível da aplicação, pode controlar a forma como os dados da empresa são utilizados e partilhados pelos funcionários, mesmo que o dispositivo em si não seja gerido pelo Intune

Utilize as [políticas do Windows Information Protection (WIP)](app-protection-policies-configure-windows-10.md) para proceder da mesma forma nos dispositivos Windows 10 geridos. Estas políticas funcionam sem interferir com a experiência do funcionário. Não necessitam de alterações ao ambiente da sua rede ou outras aplicações.

### <a name="remove-company-data-while-leaving-personal-data-intact"></a>Remover dados da empresa, deixando intactos os dados pessoais

Quando um dispositivo deixa de ser necessário para fins profissionais, vai ser redirecionado para outros objetivos ou desapareceu, pode remover as aplicações e os dados da empresa do mesmo. Para o fazer, pode utilizar as funcionalidades de reposição de fábrica e remoção de dados da empresa do Intune. Os utilizadores também podem fazer a reposição remota dos respetivos dispositivos pessoais a partir do Portal da Empresa do Intune, caso estejam inscritos no Intune.

Uma [reposição de fábrica](devices-wipe.md) restaura as predefinições de fábrica de um dispositivo, remove os dados e definições do utilizador e elimina o dispositivo da gestão do Intune. A opção [Remover dados da empresa](devices-wipe.md#remove-company-data) só remove os dados da empresa do dispositivo, mas mantém os dados pessoais do utilizador intactos.

Uma vez iniciada, o dispositivo começa imediatamente o processo de reposição. Quando o processo estiver concluído, todos os dados da empresa serão eliminados e o nome do dispositivo será removido do Intune. Assim termina o ciclo de vida de gestão do dispositivo.

---
title: "Glossário do Intune"
titleSuffix: 
description: Saber mais sobre alguma da terminologia utilizada no Microsoft Intune
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 07/28/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: bd7b5613-ee9f-4dc3-990c-ab4c1d40720d
ms.custom: intune-azure
ms.openlocfilehash: 2df6c8c79954c2145ffa6eb33782cee690d78b1d
ms.sourcegitcommit: 79116d4c7f11bafc7c444fc9f5af80fa0b21224e
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/03/2017
---
# <a name="microsoft-intune-glossary"></a>Glossário do Microsoft Intune

## <a name="a"></a>A

|||
|-|-|
|Atribuição de aplicações|Permite que os utilizadores [localizem, transfiram e instalem](/intune/app-management) as aplicações de que necessitam. Tal era conhecido anteriormente como *implementação de aplicações*.|
|Perfil de configuração de aplicações <br/><br/>Política de configuração de aplicações|Disponível para aplicações móveis com configurações específicas do fornecedor. Configura uma aplicação [iOS](/intune/app-configuration-policies-use-ios) ou [Android](/intune/app-configuration-policies-use-android) com as definições específicas antes da execução.|
|Monitorização de aplicações|Permite que [analise a atividade e o estado recentes](/intune/apps-monitor) relacionados com a atribuição de aplicações.|
|Tarefa de remoção de dados de proteção de aplicações|[Remove os dados de aplicações](/intune/app-protection-policies) do dispositivo do utilizador.|
|Política de proteção de aplicações|Disponível para aplicações móveis que integrem tecnologias do Enterprise Mobility + Security (EMS). Garante que as aplicações do utilizador estão em conformidade com as [políticas de proteção de dados da empresa](/intune/app-protection-policies).|
|SDK da Aplicação|O [SDK da Aplicação do Microsoft Intune](/intune/app-sdk) permite-lhe adicionar funcionalidades às suas aplicações desenvolvidas internamente e permite que estas sejam geridas pelas políticas de proteção de aplicações do Intune.|
|Ação de desinstalação de aplicações|Permite que [desinstale aplicações](/intune/apps-deploy) de dispositivos do utilizador.|
|Ferramenta de Encapsulamento de Aplicações|Uma [aplicação da linha de comandos](/intune/apps-prepare-mobile-application-management) que cria um encapsulamento em torno de uma aplicação de linha de negócio ao permitir que esta seja gerida por uma política de proteção de aplicações do Intune.|
|Ação de atribuição|Uma escolha que faz quando [atribui uma aplicação](/intune/apps-deploy). Pode optar por tornar a instalação da aplicação obrigatória (necessária), opcional (disponível) ou pode desinstalá-la.|
|Instalação disponível|Quando atribui uma aplicação com esta ação, a aplicação é apresentada no portal da empresa e os utilizadores podem [instalá-la a pedido](/intune/apps-deploy).|
|Portal do Azure|A nova consola do Intune – [Leia mais](/intune/what-is-intune).|

## <a name="b"></a>B
|||
|-|-|
|BYOD|[Traga o seu próprio dispositivo](/intune/device-enrollment). Os utilizadores podem instalar a aplicação Portal da Empresa do Intune nos respetivos dispositivos e, em seguida, inscrevê-los, obtendo acesso aos recursos da empresa como e-mail, aplicações da empresa, dados da empresa e suporte.|

## <a name="c"></a>C
|||
|-|-|
|Perfil de certificado|Pode utilizar este tipo de política para [acesso seguro a recursos empresariais](/intune/certificates-configure) com certificados quando utilizar perfis de Wi-Fi, e-mail ou VPN.|
|COD|Os [Dispositivos pertencentes à empresa](/intune/device-enrollment) podem ser inscritos de várias formas, consoante as necessidades da organização e os tipos de dispositivos geridos.|
|Portal da Empresa|Uma aplicação ou um site que proporciona aos utilizadores [acesso a aplicações e dados da empresa](/intune/company-portal-customize).|
|Política de conformidade|Assegura que os dispositivos [estão em conformidade com determinadas regras, ](/intune/device-compliance) como a utilização de um PIN para aceder ao dispositivo e a encriptação dos dados armazenados no dispositivo.|
|Aplicações compatíveis e incompatíveis|Integradas num [perfil de restrição de dispositivos](/intune/device-restrictions-configure), estas definições permitem definir uma lista de aplicações que os utilizadores podem ou não executar. O Intune informa-o através de relatórios de que uma aplicação não conforme foi instalada ou executada. Em algumas plataformas, o Intune também pode bloquear a instalação de uma aplicação não conforme.|
|Acesso condicional|[Permite o acesso a e-mails da empresa, ao Office 365 e a outros serviços](/intune/conditional-access) apenas em dispositivos em conformidade com as regras que definiu.|
|Política personalizada|[Utilize estas políticas](/intune/custom-settings-configure) quando uma política de configuração geral não tiver uma definição incorporada que cumpra os seus requisitos. Poderá conseguir utilizar uma política personalizada para criar uma definição por outros meios, como o Apple Configurator ou o OMA-URI.|

## <a name="d"></a>D
|||
|-|-|
|Implementação|A ação de enviar uma aplicação ou política para um dispositivo ou utilizador gerido por si. Esta ação é conhecida agora como *atribuir*.|
|Gestor de inscrição de dispositivos|As organizações podem utilizar o Intune para gerir um grande número de dispositivos móveis com uma única conta de utilizador. A conta do [gestor de inscrição de dispositivos (DEM)](/intune/device-enrollment-program-enroll-ios) é uma conta especial do Intune, que pode inscrever até 1000 dispositivos.|
|Perfis de dispositivo|[Estes perfis](/intune/device-profile-create) permitem-lhe configurar uma ampla gama de definições de segurança, funcionalidades e acesso nos dispositivos que gere.|

## <a name="e"></a>E
|||
|-|-|
|Perfil de e-mail|Esta política pode ser utilizada para configurar as [definições de acesso ao e-mail](/intune/email-settings-configure) em dispositivos móveis ao minimizar a quantidade de configuração que o utilizador final deve efetuar.|
|EMS|O Microsoft Enterprise Mobility + Security (anteriormente conhecido por Enterprise Mobility Suite) mantém os dados da sua empresa protegidos e permite que os utilizadores [acedam às aplicações e aos conteúdos de que precisam](https://www.microsoft.com/cloud-platform/enterprise-mobility).|
|Utilizador final|Os [utilizadores de dispositivos como telemóveis e PCs ](/intune/end-user-educate) geridos através do Intune.|
|Inscrever|O Microsoft Intune utiliza a [inscrição](/intune/device-enrollment) para trazer dispositivos para gestão e permitir o acesso aos recursos.|

## <a name="f"></a>F
|||
|-|-|
|FastTrack|Um [serviço da Microsoft](https://technet.microsoft.com/library/mt228265.aspx) para utilizadores do Intune com 150 licenças num plano elegível. Ao utilizar este serviço, os especialistas da Microsoft podem colaborar consigo para colocar o serviço a funcionar com o Intune.|

## <a name="g"></a>G
|||
|-|-|
|Grupos|Os grupos permitem-lhe [reunir utilizadores ou dispositivos de forma lógica](/intune/groups-get-started). Por exemplo, pode criar um grupo de todos os PCs Windows. Em seguida, pode atribuir aplicações e perfis a esses grupos.|

## <a name="h"></a>H
|||
|-|-|
|Híbrido|Uma configuração na qual pode gerir os dispositivos inscritos com o Intune através da consola do System Center Configuration Manager.|

## <a name="i"></a>I
|||
|-|-|
|Portal do Intune|O portal do Azure que utiliza na maioria das operações de gestão do Intune.|
|Cliente de software do Intune|Uma forma alternativa de [gerir alguns PCs Windows](/intune-classic/get-started/choose-how-to-manage-devices) para ajudar a decidir qual o método a utilizar.|
|Intune Software Publisher|Uma ferramenta que utiliza para [definir as aplicações que pretende implementar e carregá-las para o seu espaço de armazenamento na cloud](/intune-classic/deploy-use/add-apps).|
|Inventário|Utilize-o para ver o [hardware e o software instalado](/intune/device-inventory) nos dispositivos que gere.|

## <a name="k"></a>K
|||
|-|-|
|Modo de local público|Configurado como parte de um [perfil de restrição de dispositivos](/intune/device-restrictions-configure), este modo permite-lhe bloquear dispositivos. Por exemplo, pode configurar um dispositivo de revenda de forma a permitir a execução apenas de algumas aplicações.|

## <a name="m"></a>M
|||
|-|-|
|Browser Gerido|Uma [aplicação de navegação na Web](/intune/app-configuration-managed-browser) que pode atribuir na sua organização ao utilizar o Intune. Uma política de browser gerido configura uma lista de permissões ou uma lista de bloqueios que restringe os sites que os utilizadores do browser gerido podem visitar.|
|Autoridade MDM|A [autoridade MDM](/intune/mdm-authority-set) define o serviço de gestão que tem permissão para gerir um conjunto de dispositivos. As opções para a autoridade de MDM incluem o Intune autónomo e o Configuration Manager com o Intune.|
|Política de configuração de aplicações móveis|Disponível para aplicações móveis com configurações específicas do fornecedor. Por exemplo, uma política de [iOS](/intune/app-configuration-policies-use-ios) ou [Android](/intune/app-configuration-policies-use-android) que é utilizada para fornecer definições a aplicações compatíveis quando estas são executadas (tais como um nome de empresa ou endereço de servidor).|
|Política de aprovisionamento de aplicações móveis|Uma política de iOS que o ajuda a garantir que os [perfis de aprovisionamento](/intune/app-provisioning-profile-ios) que atribui para aplicações iOS não expiram.|
|Gestão de aplicações móveis|A [Gestão de aplicações móveis (MAM)](/intune/app-lifecycle) permite-lhe publicar, efetuar push, configurar, proteger, monitorizar e atualizar aplicações móveis para os seus utilizadores.
|Gestão de dispositivos móveis|A [gestão de dispositivos móveis (MDM)](/intune/device-lifecycle) permite-lhe inscrever dispositivos no Intune para que possa aprovisionar, configurar, monitorizar e gerir esses dispositivos.



## <a name="o"></a>O
|||
|-|-|
|OMA-DM|Open Mobile Alliance Device Management. Um protocolo de gestão de dispositivos padrão na indústria, utilizado por muitos fabricantes de hardware para permitir o controlo das funcionalidades de dispositivos móveis e PCs.|
|OMA-URI|Open Mobile Alliance Uniform Resource Identifier. Estes itens identificam definições de dispositivos individuais conformes com o padrão OMA-DM. As definições podem ser utilizadas em [perfis personalizados do Intune](/intune/custom-settings-configure) quando não existe uma definição incorporada que corresponda às suas necessidades.|

## <a name="p"></a>P
|||
|-|-|
|Repor código de acesso|Funcionalidade do Intune que lhe permite forçar o utilizador final a [repor o código de acesso](/intune/device-passcode-reset) em dispositivos suportados.|

## <a name="r"></a>R
|||
|-|-|
|Bloqueio remoto|Funcionalidade do Intune que lhe permite [bloquear dispositivos suportados](/intune/device-remote-lock), mesmo que não tenha o dispositivo consigo.|
|Instalação necessária|Quando atribui uma aplicação com esta ação, a [intervenção do utilizador](/intune/apps-deploy) não é necessária para concluir a instalação. Em algumas plataformas, o utilizador final pode ter de aceitar a instalação.|


## <a name="s"></a>S
|||
|-|-|
|Eliminação seletiva|Uma [eliminação seletiva](/intune/device-company-data-remove) remove apenas os dados da empresa protegidos pela política de proteção de aplicações, incluindo as definições e perfis de e-mail, de um dispositivo. A eliminação seletiva mantém os dados pessoais do utilizador no dispositivo.|
|Sideloading|A ação de instalação de uma aplicação de linha de negócio sem aceder à mesma a partir de uma loja de aplicações.|
|Subscrição|O contrato que aceita e que lhe permite aceder a um inquilino do Intune.|

## <a name="t"></a>T
|||
|-|-|
|TeamViewer|Uma aplicação de terceiros que funciona em conjunto com o Intune para fornecer [capacidades de assistência remota](/intune/device-profile-android-teamviewer) para dispositivos Android que gere com o Intune.|
|Inquilino|Uma única instância do serviço do Intune à qual pode aceder com uma subscrição.|
|Termos e condições|Um tipo de política que atribui a utilizadores com informações que os utilizadores têm de [ler e aceitar](/intune/terms-and-conditions-create) para poderem utilizar o Portal da Empresa para inscrever e aceder aos trabalhos.|

## <a name="v"></a>V
|||
|-|-|
|Aplicações e livros comprados em volume|Algumas lojas de aplicações permitem comprar várias licenças para uma aplicação ou livro que deseja utilizar na empresa. O Intune ajuda-o a gerir [aplicações e livros adquiridos através desse programa](/intune/vpp-apps). Pode importar as informações da licença a partir da loja de aplicações, controlar o número de licenças que utilizou e impedir que instale mais cópias da aplicação do que aquelas que possui.|
|Perfil VPN|Uma política que atribui as [definições de VPN](/intune/vpn-settings-configure) em dispositivos que gere, minimizando as configurações necessárias para utilizadores finais.|

## <a name="w"></a>W
|||
|-|-|
|Perfil Wi-Fi|Uma política que atribui [definições de redes móveis](/intune/wi-fi-settings-configure) para dispositivos ao permitir aos utilizadores ligarem-se à sua rede empresarial sem terem de conhecer ou configurar definições.

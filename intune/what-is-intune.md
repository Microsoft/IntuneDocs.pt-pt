---
title: O que é o Microsoft Intune
description: Saiba como o Microsoft Intune é o componente de gestão (MAM) de aplicação móvel do Enterprise Mobility + solução de segurança e gestão de dispositivos móveis (MDM) e como o ajuda a proteger dados da empresa.
keywords: o que é o Intune
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 02/26/2019
ms.topic: overview
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 3b4e778d-ac13-4c23-974f-5122f74626bc
ms.reviewer: pmay
ms.suite: ems
search.appverid: MET150
ms.custom: get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 511e672193ec609f817c10572c99ac73831c54ae
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/14/2019
ms.locfileid: "57460585"
---
# <a name="what-is-microsoft-intune"></a>O que é o Microsoft Intune?

[!INCLUDE [both-portals](./includes/note-for-both-portals.md)]

O Microsoft Intune é um serviço baseado na nuvem no espaço de gestão (EMM) de mobilidade empresarial que ajuda a sua força de trabalho ser produtivo, mantendo os seus dados empresariais protegidos. Tal como outros serviços do Azure, o Microsoft Intune está disponível no portal do Azure. Com o Intune, pode:
* Gerir os dispositivos móveis e PCs em que sua força de trabalho utiliza para aceder a dados da empresa.
* Gerir as aplicações móveis que a sua força de trabalho utiliza.
* Proteger as informações da sua empresa ao ajudar a controlar a forma como a sua força de trabalho acede às mesmas e as partilha.
* Garantir que os dispositivos e as aplicações são compatíveis com os requisitos de segurança da empresa.

## <a name="common-business-problems-that-intune-helps-solve"></a>Problemas empresariais comuns que o Intune ajuda a resolver

* [Proteger o seu e-mail no local e os dados, para que os dispositivos móveis possam aceder aos mesmos](common-scenarios.md#protecting-your-on-premises-email-and-data-so-it-can-be-safely-accessed-by-mobile-devices)
* [Proteger o seu e-mail e dados do Office 365, para que os dispositivos móveis possam aceder em segurança aos mesmos](common-scenarios.md#protecting-your-office-365-email-and-data-so-it-can-be-safely-accessed-by-mobile-devices)
* [Distribuir telemóveis pertencentes à empresa à sua força de trabalho](common-scenarios.md#issue-corporate-owned-phones-to-your-employees)
* [Oferecer um programa BYOD ou de dispositivos pessoais a todos os funcionários](common-scenarios.md#offer-a-bring-your-own-device-program-to-all-employees)
* [Permitir que os seus funcionários acedam de forma segura ao Office 365 a partir de um quiosque público não gerido](common-scenarios.md#enable-your-employees-to-securely-access-office-365-from-an-unmanaged-public-kiosk)
* [Distribuir tablets partilhados de utilização limitada aos trabalhadores de tarefas](common-scenarios.md#issue-limited-use-shared-tablets-to-your-employees)


## <a name="how-does-intune-work"></a>Como é que o Intune funciona?
O Intune é o componente do Enterprise Mobility + suite Security (EMS) que gere dispositivos móveis e aplicações da Microsoft. Integra-se com outros componentes de EMS, como o Azure Active Directory (Azure AD) para controlo de acesso e identidade, e o Azure Information Protection para proteção de dados. Ao utilizá-lo com o Office 365, pode fomentar a produtividade da sua força de trabalho em todos os dispositivos e, ao mesmo tempo, manter as informações da sua organização protegidas.

![Imagem da arquitetura do Intune](./media/intunearch_sm.png)

Veja uma [versão maior](./media/intunearchitecture.svg) do diagrama da arquitetura do Intune.

A maneira como utiliza as funcionalidades de gestão de aplicações e dispositivos do Intune e a proteção de dados de EMS depende do [problema empresarial que está a tentar resolver](#common-business-problems-that-intune-helps-solve). Por exemplo:
* A funcionalidade de gestão de dispositivos será particularmente útil se estiver a criar um conjunto de dispositivos de utilização única para serem partilhados com funcionários de turnos numa loja de comércio a retalho.
* Deverá contar com as funcionalidades de gestão de aplicações e proteção de dados se permitir que a sua força de trabalho utilize os respetivos dispositivos pessoais para aceder a dados empresariais (BYOD).  
* Se distribuir telemóveis da empresa pelos técnicos de informação, irá depender de todas as tecnologias.

## <a name="intune-device-management-explained"></a>Explicação da gestão de dispositivos do Intune
A gestão de dispositivos do Intune funciona através de protocolos ou APIs disponíveis nos sistemas de operadoras móveis. Inclui tarefas como:
* Inscrever dispositivos para gestão para que o seu departamento de TI tenha um inventário dos dispositivos que acedem aos serviços empresariais
* A configuração de dispositivos para assegurar que cumprem as normas de segurança e de saúde da empresa
* O fornecimento de certificados e perfis Wi-Fi/VPN para aceder a serviços empresariais
* A criação de relatórios e a medição da conformidade dos dispositivos com as normas empresariais
* A remoção de dados empresariais dos dispositivos geridos  

Por vezes, as pessoas pensam **controlar o acesso a dados empresariais** é uma funcionalidade de gestão do dispositivo. Não pensamos dessa forma, porque não é algo que seja fornecido pelo sistema operativo do dispositivo móvel. Em vez disso, é algo proporcionado pelo fornecedor de identidade. No nosso caso, o fornecedor de identidade é o Azure Active Directory (Azure AD), o sistema de gestão de identidade e acesso da Microsoft.  

O Intune está integrado no Azure AD para possibilitar um conjunto abrangente de cenários de controlo de acesso. Por exemplo, pode exigir que um dispositivo móvel esteja em conformidade com as normas empresariais que define no Intune para que o mesmo possa aceder a um serviço empresarial, como o Exchange. Da mesma forma, pode bloquear o serviço empresarial para um conjunto específico de aplicações móveis. Por exemplo, pode bloquear o Exchange Online para que seja apenas acedido pelo Outlook ou o Outlook Mobile.

## <a name="intune-app-management-explained"></a>Explicação da gestão de aplicações do Intune
Quando mencionamos gestão de aplicações, isso traduz-se em:
* Atribuir aplicações móveis aos funcionários
* Configurar aplicações com definições padrão utilizadas durante a execução das mesmas
* O controlo da forma como os dados empresariais são utilizados e partilhados em aplicações móveis
* A remoção de dados empresariais de aplicações móveis   
* Atualizar aplicações
* A criação de relatórios sobre o inventário de aplicações móveis
* O controlo da utilização de aplicações móveis

O termo gestão de aplicações móveis (MAM) tem sido utilizado para designar qualquer dessas noções individualmente ou combinações específicas. Em particular, é comum a combinar o conceito de configuração de aplicações com o conceito de proteção de dados empresariais de aplicações móveis. Isso acontece porque algumas aplicações móveis apresentam definições que permitem a configuração das respetivas funcionalidades de segurança de dados.

Quando mencionamos a configuração de aplicações em conjunto com o Intune, referimo-nos especificamente a tecnologias como a [configuração de aplicações geridas em iOS](https://developer.apple.com/library/content/samplecode/sc2279/Introduction/Intro.html).

Ao utilizar o Intune com outros serviços do EMS, pode proporcionar a segurança de aplicações móveis à sua organização acima do que é fornecido pelo sistema operativo móvel e pelas próprias aplicações móveis através da configuração de aplicações. Uma aplicação gerida com o EMS tem acesso a um conjunto mais vasto de aplicações móveis e funcionalidades de proteção de dados que inclui:

* [Início de sessão único](https://docs.microsoft.com/azure/active-directory/active-directory-appssoaccess-whatis)  
*   [Autenticação multifator](https://docs.microsoft.com/azure/active-directory/authentication/multi-factor-authentication)
* [Acesso condicional a aplicações – permite o acesso se a aplicação móvel contiver dados empresariais](app-based-conditional-access-intune.md)
* [Separação entre dados empresariais e dados pessoais na mesma aplicação](app-protection-policy.md)
* [Política de proteção de aplicações (PIN, encriptação, Guardar Como, área de transferência, etc.)](app-protection-policies.md)
* [Eliminação de dados empresariais de uma aplicação móvel](apps-selective-wipe.md)
* [Suporte à gestão de direitos](https://docs.microsoft.com/information-protection/understand-explore/what-is-azure-rms)

![Imagem que mostra os níveis da segurança de dados de gestão de aplicações](./media/managing-mobile-apps.png)

### <a name="intune-app-security"></a>Segurança das aplicações do Intune
Proporcionar a segurança das aplicações faz parte da gestão de aplicações e, no Intune, a segurança das aplicações móveis traduz-se em:
* Manter as informações pessoais separadas da deteção de TI empresariais
* Restringir as ações que os utilizadores podem efetuar com informações empresariais, como copiar, cortar/colar, guardar e ver
* Remover dados empresariais de aplicações móveis, algo também conhecido como eliminação seletiva ou eliminação empresarial

Uma forma Intune fornece segurança de aplicações móveis é por meio de seus **política de proteção de aplicações** funcionalidade. A política de proteção de aplicações utiliza a identidade do Azure AD para separar os dados empresariais dos dados pessoais. Dados que são acedidos utilizando as credenciais empresariais receberão proteções empresariais adicionais.

Por exemplo, quando um utilizador inicia sessão no seu dispositivo com as credenciais da empresa, a identidade empresarial permite-lhes aceder aos dados negados à sua identidade pessoal. À medida que os dados empresariais são utilizados, as políticas de proteção de aplicações controlam como os mesmos são guardados e partilhados. Essas mesmas proteções não são aplicadas aos dados que são acedidos quando o utilizador inicia sessão nos respetivos dispositivos com a respetiva identidade pessoal. Dessa forma, IT tem controlo sobre os dados da empresa enquanto o utilizador final mantém o controlo e a privacidade sobre os seus dados pessoais.

## <a name="emm-with-and-without-device-enrollment"></a>EMM com e sem a inscrição de dispositivos
A maioria das soluções de gestão da mobilidade empresarial suporta dispositivos móveis básicos e tecnologias de aplicações móveis. Estas estão normalmente relacionadas com a inscrição do dispositivo na solução de gestão de dispositivos móveis (MDM) da sua organização. O Intune suporta estes cenários, bem como vários cenários "sem inscrição".  

As organizações divergem na forma de adoção de cenários "sem inscrição". Algumas organizações efetuam uma padronização. Outras permitem dispositivos complementares, como um tablet pessoal. Outras não suportam nenhuma das situações. Mesmo neste último caso, em que uma organização requer que todos os dispositivos dos funcionários estejam inscritos na MDM, normalmente suporta cenários "sem inscrição" para subcontratados, fornecedores e outros dispositivos que tenham uma isenção específica.

Pode até utilizar a tecnologia "sem inscrição" do Intune em dispositivos inscritos. Por exemplo, um dispositivo inscrito na MDM pode ter proteções "Open-in" fornecidas pelo sistema operativo móvel. Proteção "Open-in" é uma funcionalidade do iOS da Apple que impede a abertura de um documento de uma aplicação, como o Outlook, para outra aplicação, como o Word, a menos que ambas as aplicações são geridas pelo fornecedor MDM da mesmo. Além disso, IT podem aplicar-se a política de proteção de aplicações para aplicações móveis geridas pelo EMS, ao controle guardar-como, ou para fornecer autenticação multifator.

Qualquer que seja a posição da sua organização relativamente às aplicações e aos dispositivos móveis inscritos e não inscritos, o Intune, como parte do EMS, dispõe de ferramentas que o irão ajudar a aumentar a produtividade da força de trabalho, protegendo os seus dados empresariais.

## <a name="microsoft-intune-in-the-azure-portal"></a>Microsoft Intune no portal do Azure

Pode encontrar o serviço Microsoft Intune no [portal do Azure](https://portal.azure.com).

Os destaques da experiência do Microsoft Intune no portal do Azure incluem:

- Uma consola integrada para todos os componentes do Enterprise Mobility + Security (EMS)
- Uma consola baseada em HTML baseada em normas da Web
- Suporte do Microsoft Graph API para automatizar várias ações
- Grupos do Azure Active Directory (AD) para proporcionar compatibilidade em todas as suas aplicações do Azure
- Suporte para os browsers mais modernos

Para obter um guia rápido sobre como personalizar a sua experiência no portal, veja [Começar a utilizar o Intune no portal do Azure](get-started-azure.md).

> [!NOTE]
> Se tiver utilizado uma versão anterior do Microsoft Intune, poderá considerar úteis as seguintes informações:
> * O artigo [Onde estão as minhas funcionalidades no Azure?](ui-changes.md) é uma referência que lhe mostra as IUs e fluxos de trabalho específicos que foram alterados com a mudança para o Azure.
> * O artigo [Grupos clássicos do Intune no portal do Azure](groups-get-started.md) explica as implicações da transição para grupos de segurança do Azure Active Directory relativamente à gestão de grupos.

### <a name="before-you-start"></a>Antes de começar

Para utilizar o Intune no portal do Azure, tem de ter uma conta de administrador e de inquilino do Intune. Caso ainda não o tenha feito, [inscreva-se numa conta](https://admin.microsoft.com/Signup/Signup.aspx?OfferId=40BE278A-DFD1-470a-9EF7-9F2596EA7FF9&dl=INTUNE_A&ali=1#0%20).

### <a name="supported-web-browsers-for-the-azure-portal"></a>Browsers suportados para o portal do Azure

O portal do Azure funciona na maior parte dos PCs, Macs e tablets mais recentes. Os telemóveis não são suportados.
Atualmente, são suportados os seguintes browsers:

- Microsoft Edge (versão mais recente)
- Microsoft Internet Explorer 11
- Safari (versão mais recente, apenas Mac)
- Chrome (versão mais recente)
- Firefox (versão mais recente)

Consulte o [portal do Azure](https://docs.microsoft.com/azure/azure-preview-portal-supported-browsers-devices) para obter as informações mais recentes sobre browsers suportados.

## <a name="next-steps"></a>Passos Seguintes
* Ler sobre algumas das [formas comuns de utilizar o Intune](common-scenarios.md).
* Familiarizar-se com o produto [com uma avaliação de 30 dias do Intune](free-trial-sign-up.md).
* Aprofundar conhecimentos sobre os [requisitos técnicos e as capacidades](supported-devices-browsers.md) do Intune

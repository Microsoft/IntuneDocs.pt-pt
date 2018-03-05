---
title: "O que é o Microsoft Intune"
description: "Saiba como o Intune é o componente de gestão de dispositivos móveis (MDM) e gestão de aplicações móveis (MAM) da solução Microsoft Enterprise Mobility + Security e como o ajuda a proteger dados empresariais."
keywords: "o que é o Intune"
author: Lindavr
ms.author: lindavr
manager: dougeby
ms.date: 02/12/2018
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3b4e778d-ac13-4c23-974f-5122f74626bc
ms.reviewer: pmay
ms.suite: ems
ms.custom: 
ms.openlocfilehash: b528ff06eb163beeb14465cfb10e66b7d2623424
ms.sourcegitcommit: 754fcc31155b28d6910bba45419c6be745f8793e
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/14/2018
---
# <a name="what-is-intune"></a>O que é o Intune?

[!INCLUDE[both-portals](./includes/note-for-both-portals.md)]

O Intune é um serviço baseado na cloud no espaço de gestão de mobilidade enterprise (EMM) que ajuda a fomentar a produtividade da sua força de trabalho e a manter os seus dados empresariais protegidos ao mesmo tempo. Com o Intune, pode:
* Gerir os dispositivos móveis que a sua força de trabalho utiliza para aceder aos dados da empresa.
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
O Intune é o componente de Enterprise Mobility + Security (EMS) que gere aplicações e dispositivos móveis. Integra-se com outros componentes de EMS, como o Azure Active Directory (Azure AD) para controlo de acesso e identidade, e o Azure Information Protection para proteção de dados. Ao utilizá-lo com o Office 365, pode fomentar a produtividade da sua força de trabalho em todos os dispositivos e, ao mesmo tempo, manter as informações da sua organização protegidas.

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

Por vezes, as pessoas pensam que **controlar o acesso a dados empresariais** é uma funcionalidade da gestão de dispositivos. Não pensamos dessa forma, porque não é algo que seja fornecido pelo sistema operativo do dispositivo móvel. Em vez disso, é algo proporcionado pelo fornecedor de identidade. No nosso caso, o fornecedor de identidade é o Azure Active Directory (Azure AD), o sistema de gestão de identidade e acesso da Microsoft.  

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

O termo gestão de aplicações móveis (MAM) tem sido utilizado para designar qualquer dessas noções individualmente ou combinações específicas. É particularmente comum combinar o conceito de configuração de aplicações e o conceito de tornar os dados empresariais seguros em aplicações móveis. Isso acontece porque algumas aplicações móveis apresentam definições que permitem a configuração das respetivas funcionalidades de segurança de dados.

Quando mencionamos a configuração de aplicações em conjunto com o Intune, referimo-nos especificamente a tecnologias como a [configuração de aplicações geridas em iOS](https://developer.apple.com/library/content/samplecode/sc2279/Introduction/Intro.html).

Ao utilizar o Intune com outros serviços do EMS, pode proporcionar a segurança de aplicações móveis à sua organização acima do que é fornecido pelo sistema operativo móvel e pelas próprias aplicações móveis através da configuração de aplicações. Uma aplicação gerida com o EMS tem acesso a um conjunto mais abrangente de proteções de aplicações móveis e dados que incluem:

* [Início de sessão único](https://docs.microsoft.com/azure/active-directory/active-directory-appssoaccess-whatis)  
*   [Autenticação multifator](https://docs.microsoft.com/multi-factor-authentication/multi-factor-authentication)
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

Uma forma de o Intune proporcionar segurança de aplicações móveis é através da respetiva funcionalidade de **política de proteção de aplicações**. A política de proteção de aplicações utiliza a identidade do Azure AD para separar os dados empresariais dos dados pessoais. Os dados acedidos ao utilizar uma credencial empresarial receberão proteções empresariais adicionais.

Por exemplo, quando um utilizador inicia sessão no dispositivo com as respetivas credenciais empresariais, a identidade empresarial do mesmo permite-lhe aceder a dados que são negados à identidade de caráter pessoal. À medida que os dados empresariais são utilizados, as políticas de proteção de aplicações controlam como os mesmos são guardados e partilhados. Essas mesmas proteções não são aplicadas aos dados acedidos quando o utilizador inicia sessão no dispositivo com a respetiva identidade pessoal. Desta forma, o departamento de TI tem controlo sobre os dados empresariais, enquanto o utilizador final mantém o controlo e a privacidade sobre os dados pessoais.

## <a name="emm-with-and-without-device-enrollment"></a>EMM com e sem a inscrição de dispositivos
A maioria das soluções de gestão da mobilidade empresarial suporta dispositivos móveis básicos e tecnologias de aplicações móveis. Estas estão normalmente relacionadas com a inscrição do dispositivo na solução de gestão de dispositivos móveis (MDM) da sua organização. O Intune suporta estes cenários, bem como vários cenários "sem inscrição".  

As organizações divergem na forma de adoção de cenários "sem inscrição". Algumas organizações efetuam uma padronização. Outras permitem dispositivos complementares, como um tablet pessoal. Outras não suportam nenhuma das situações. Mesmo neste último caso, em que uma organização requer que todos os dispositivos dos funcionários estejam inscritos na MDM, normalmente suporta cenários "sem inscrição" para subcontratados, fornecedores e para outros dispositivos que tenham uma isenção específica.

Pode até utilizar a tecnologia "sem inscrição" do Intune em dispositivos inscritos. Por exemplo, um dispositivo inscrito na MDM pode ter proteções "Open-in" fornecidas pelo sistema operativo móvel. A proteção "Open-in" é uma funcionalidade do iOS que impede um documento de uma aplicação, como o Outlook, de ser aberto noutra aplicação, como o Word, a menos que ambas as aplicações sejam geridas pelo fornecedor de MDM. Além disso, o departamento de TI pode aplicar a política de proteção de aplicações para aplicações móveis geridas pelo EMS, para controlar a função Guardar Como ou proporcionar autenticação multifator.

Qualquer que seja a posição da sua organização relativamente às aplicações e aos dispositivos móveis inscritos e não inscritos, o Intune, como parte do EMS, dispõe de ferramentas que o irão ajudar a aumentar a produtividade da força de trabalho, protegendo os seus dados empresariais.



### <a name="next-steps"></a>Próximos passos
* Ler sobre algumas das [formas comuns de utilizar o Intune](common-scenarios.md).
* Familiarizar-se com o produto [com uma avaliação de 30 dias do Intune](free-trial-sign-up.md).
* Aprofundar conhecimentos sobre os [requisitos técnicos e as capacidades](supported-devices-browsers.md) do Intune

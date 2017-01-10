---
title: "O que é o Microsoft Intune? | Documentos da Microsoft"
description: "Saiba como o Intune é o componente de gestão de dispositivos móveis da solução Enterprise Mobility + Security e como ajuda a proteger os dados da sua empresa."
keywords: "o que é o Intune"
author: Lindavr
ms.author: lindavr
manager: angrobe
ms.date: 11/15/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3b4e778d-ac13-4c23-974f-5122f74626bc
ms.reviewer: pmay
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: eeb85a28ea6f99a0123ec5df3b0d476a678b85cb
ms.openlocfilehash: e373fe71f54472bca538ba4a14beff39d090e23d


---

# <a name="what-is-intune"></a>O que é o Intune?

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

O Intune é um serviço de gestão de mobilidade empresarial (EMM) baseado na cloud que ajuda a sua força de trabalho a ser produtiva, mantendo os seus dados empresariais protegidos. Com o Intune, pode:
* Gerir os dispositivos móveis que a sua força de trabalho utiliza para aceder aos dados da empresa.
* Gerir as aplicações móveis que a sua força de trabalho utiliza.
* Proteger as informações da sua empresa ao ajudar a controlar a forma como a sua força de trabalho acede às mesmas e as partilha.
* Garantir que os dispositivos e as aplicações são compatíveis com os requisitos de segurança da empresa.

O Intune está estreitamente integrado no Azure Active Directory (Azure AD) para controlo de identidade e acesso e no Azure Rights Management (Azure RMS) para proteção de dados. É o *braço de gestão* do Microsoft Enterprise Mobility + Security (EMS), enquanto o Office 365 é o *braço de produtividade* da solução de mobilidade da Microsoft.  

Em conjunto, o Office 365 e o EMS permitem que a sua força de trabalho seja produtiva em todos os respetivos dispositivos, mantendo as informações da sua organização protegidas. O Office 365 com EMS é um conjunto integrado completo para mobilidade empresarial, que inclui produtividade, identidade, controlo de acesso, gestão e proteção de dados. Proporciona uma forma eficaz de implementar e utilizar uma solução de mobilidade na sua organização.

## <a name="how-does-intune-work"></a>Como é que o Intune funciona?
O Intune proporciona a gestão de dispositivos móveis (MDM) e a gestão de aplicações móveis (MAM). As funcionalidades MDM e MAM do Intunes contribuem para o conjunto EMS de cenários de proteção de dados e conformidade.  

A forma como irá utilizar as funcionalidades MDM/MAM do Intune e a proteção de dados EMS depende do [problema empresarial que estiver a tentar resolver](#common-business-problems-that-intune-helps-solve). Por exemplo:
* Irá utilizar bastante a MDM se estiver a criar um conjunto de dispositivos de utilização única a ser partilhado por trabalhadores de turno numa loja de revenda.
* Deverá contar com a MAM e com a proteção de dados, se permitir que a sua força de trabalho utilize os respetivos dispositivos pessoais para aceder a dados empresariais (BYOD).  
* Se distribuir telemóveis empresariais a técnicos de informação, irá depender bastante de todas as tecnologias.

## <a name="intune-mobile-device-management-mdm-explained"></a>Compreender a gestão de dispositivos móveis (MDM) do Intune
A MDM funciona através de protocolos ou APIs disponíveis nos sistemas operativos móveis. Inclui tarefas como:
* A inscrição de dispositivos para gestão, para que o departamento de TI tenha um inventário dos dispositivos que estão a aceder aos serviços empresariais
* A configuração de dispositivos para assegurar que cumprem as normas de segurança e de saúde da empresa
* O fornecimento de certificados e perfis Wi-Fi/VPN para aceder a serviços empresariais
* A criação de relatórios e a medição da conformidade dos dispositivos com as normas empresariais
* A remoção de dados empresariais dos dispositivos geridos  

Por vezes, as pessoas pensam que **o controlo do acesso a dados empresariais ** é uma funcionalidade da MDM. Não pensamos dessa forma, porque não é algo que seja fornecido pelo sistema operativo do dispositivo móvel. Em vez disso, é algo proporcionado pelo fornecedor de identidade. No nosso caso, o fornecedor de identidade é o Azure Active Directory (Azure AD), o sistema de gestão de identidade e acesso da Microsoft.  

O Intune está integrado no Azure AD para possibilitar um conjunto abrangente de cenários de controlo de acesso. Por exemplo, pode exigir que um dispositivo móvel esteja em conformidade com as normas empresariais, conforme definido no Intune, para que possa aceder a um serviço empresarial, como o Exchange. Da mesma forma, pode bloquear o serviço empresarial para um conjunto específico de aplicações móveis. Por exemplo, pode bloquear o Exchange Online para que seja apenas acedido pelo Outlook ou o Outlook Mobile.

## <a name="intune-mobile-app-management-mam-explained"></a>Compreender a gestão de aplicações móveis (MAM) do Intune
Quando falamos de MAM, falamos do conjunto de ações que as nossas soluções permitem que os profissionais de TI efetuem com as aplicações móveis, tais como:
* Publicação de aplicações móveis para os funcionários
* A configuração de alertas
* O controlo da forma como os dados empresariais são utilizados e partilhados em aplicações móveis
* A remoção de dados empresariais de aplicações móveis   
* A atualização de aplicações móveis
* A criação de relatórios sobre o inventário de aplicações móveis
* O controlo da utilização de aplicações móveis

Temos visto a utilização do termo MAM para designar qualquer uma destas ações individuais ou combinações específicas. Em particular, é comum a associação do conceito de configuração de aplicações (ou seja, utilizar tecnologias como a [configuração de aplicações geridas no iOS](https://developer.apple.com/library/content/samplecode/sc2279/Introduction/Intro.html)) ao conceito de proteção de dados empresariais de aplicações móveis. Isso acontece porque algumas aplicações móveis apresentam definições que permitem a configuração das respetivas funcionalidades de segurança de dados.

Isto, em conjunto com as funcionalidades do sistema operativo para a proteção de dados (por exemplo, funcionalidades MDM como o Windows Information Protection no Windows 10), proporciona uma grande proteção de dados em dispositivos móveis.

Ao utilizar o Intune com outros serviços do EMS, pode proporcionar a segurança de aplicações móveis à sua organização acima do que é fornecido pelo sistema operativo móvel e pelas próprias aplicações móveis através da configuração de aplicações. Uma aplicação gerida com o EMS tem acesso a um conjunto mais abrangente de proteções de aplicações móveis e dados que incluem:

* [Início de sessão único](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-appssoaccess-whatis)  
*   [Autenticação multifator](https://docs.microsoft.com/en-us/multi-factor-authentication/multi-factor-authentication)
* [Acesso condicional a aplicações (permite o acesso se a aplicação móvel contiver dados empresariais)](https://docs.microsoft.com/en-us/intune/deploy-use/allow-policy-managed-apps-access-to-o365)
* [Separação entre dados empresariais e dados pessoais na mesma aplicação](https://docs.microsoft.com/en-us/intune/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune)
* [Política de proteção de aplicações (PIN, encriptação, Guardar Como, área de transferência, etc.)](https://docs.microsoft.com/en-us/intune/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune)
* [Eliminação de dados empresariais de uma aplicação móvel](https://docs.microsoft.com/en-us/intune/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune)
* [Suporte à gestão de direitos](https://docs.microsoft.com/en-us/information-protection/understand-explore/what-is-azure-rms)

![Imagem que mostra os níveis da segurança de dados de gestão de aplicações](./media/managing-mobile-apps.png)

### <a name="intune-mobile-app-security"></a>Segurança de aplicações móveis do Intune
Proporcionar a segurança de aplicações faz parte da MAM e, no Intune, quando falamos sobre segurança de aplicações móveis, queremos dizer:
* Manter as informações pessoais separadas da deteção de TI empresariais
* Restringir as ações que os utilizadores podem efetuar com informações empresariais, como copiar, cortar/colar, guardar e ver
* Remover dados empresariais de aplicações móveis, algo também conhecido como eliminação seletiva ou eliminação empresarial

Uma forma de o Intune proporcionar segurança de aplicações móveis é através da respetiva funcionalidade de **política de proteção de aplicações**. A política de proteção de aplicações utiliza a identidade do Azure AD para separar os dados empresariais dos dados pessoais. Os dados acedidos ao utilizar uma credencial empresarial receberão proteções empresariais adicionais.

Quando um utilizador inicia sessão no dispositivo com as respetivas credenciais empresariais, a respetiva identidade empresarial permite o acesso aos dados negados à identidade de caráter pessoal. Quando esses dados empresariais são utilizados, o Intune, juntamente com outras tecnologias EMS, controla a forma como são guardados e partilhados. Essas mesmas proteções não são aplicadas aos dados acedidos quando o utilizador inicia sessão no dispositivo com a respetiva identidade pessoal. Desta forma, o departamento de TI tem controlo sobre os dados empresariais, enquanto o utilizador final mantém o controlo e a privacidade sobre os dados pessoais.

## <a name="emm-with-and-without-device-enrollment"></a>EMM com e sem a inscrição de dispositivos
A maioria das soluções de gestão da mobilidade empresarial suporta dispositivos móveis básicos e tecnologias de aplicações móveis. Normalmente, existe associação ao dispositivo que está a ser inscrito na solução de MDM da sua organização. O Intune suporta estes cenários, bem como vários cenários "sem inscrição".  

As organizações divergem na forma de adoção de cenários "sem inscrição". Algumas organizações efetuam uma padronização. Outras permitem dispositivos complementares, como um tablet pessoal. Outras não suportam nenhuma das situações. Mesmo neste último caso, em que uma organização requer que todos os dispositivos dos funcionários estejam inscritos na MDM, normalmente estas organizações suportam cenários "sem inscrição" para subcontratados, fornecedores e para outros dispositivos que tenham uma isenção específica.

Pode até utilizar a tecnologia "sem inscrição" do Intune em dispositivos inscritos. Por exemplo, um dispositivo inscrito na MDM pode ter proteções "open in" fornecidas pelo sistema operativo móvel. Além disso, o departamento de IT pode aplicar a política de proteção de aplicações para aplicações móveis geridas pelo EMS, para controlar a função Guardar Como ou proporcionar autenticação multifator.

Qualquer que seja a posição da sua organização relativamente às aplicações e aos dispositivos móveis inscritos e não inscritos, o Intune, como parte do EMS, dispõe de ferramentas que o irão ajudar a aumentar a produtividade da força de trabalho, protegendo os seus dados empresariais.

## <a name="common-business-problems-that-intune-helps-solve"></a>Problemas empresariais comuns que o Intune ajuda a resolver
A seguinte lista de problemas empresariais permite aceder a informações mais detalhadas sobre as soluções fornecidas. Apenas o último item requer a inscrição na MDM como parte da solução:

* [Proteger o seu e-mail no local e os dados, para que os dispositivos móveis possam aceder aos mesmos](common-ways-to-use-intune.md#protecting-your-on-premises-email-and-data-so-it-can-be-safely-accessed-by-mobile-devices)
* [Proteger o seu e-mail e dados do Office 365, para que os dispositivos móveis possam aceder em segurança aos mesmos](common-ways-to-use-intune.md#protecting-your-office-365-email-and-data-so-it-can-be-safely-accessed-by-mobile-devices)
* [Distribuir telemóveis pertencentes à empresa à sua força de trabalho](common-ways-to-use-intune.md#issue-corporate-owned-phones-to-your-information-workers)
* [Oferecer um programa BYOD ou de dispositivos pessoais a todos os funcionários](common-ways-to-use-intune.md#offer-a-bring-your-own-device-program-to-all-employees)
* [Permitir que os seus funcionários acedam de forma segura ao Office 365 a partir de um quiosque público não gerido](common-ways-to-use-intune.md#enable-your-employees-to-securely-access-office-365-from-an-unmanaged-public-kiosk)
* [Distribuir tablets partilhados de utilização limitada aos trabalhadores de tarefas](common-ways-to-use-intune.md#issue-limited-use-shared-tablets-to-your-task-workers)

### <a name="next-steps"></a>Passos seguintes
* Ler sobre algumas das [formas comuns de utilizar o Intune](common-ways-to-use-intune.md).
* Familiarizar-se com o produto [com uma avaliação de 30 dias do Intune](get-started-with-a-30-day-trial-of-microsoft-intune.md).
* Aprofundar conhecimentos sobre os [requisitos técnicos e as capacidades](/intune/get-started/what-to-know-before-you-start-microsoft-intune) do Intune



<!--HONumber=Dec16_HO2-->



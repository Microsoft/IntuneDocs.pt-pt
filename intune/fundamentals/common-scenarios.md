---
title: Formas comuns de utilizar o Microsoft Intune
description: Saiba quais são as seis tarefas mais comuns que o Microsoft Intune pode ajudar a gerir.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 11/29/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 1f37d4ff-b5a7-4a89-8884-a6184908b09c
ms.reviewer: dougeby
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: f0e2e2101706b9b9afa77553244a438a2299903b
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/05/2019
ms.locfileid: "73414015"
---
# <a name="common-ways-to-use-microsoft-intune"></a>Formas comuns de utilizar o Microsoft Intune

Antes de mergulhar nas tarefas de implementação, é importante alinhar os participantes da mobilidade corporativa da sua empresa em relação aos objetivos de negócios do uso do Intune. O alinhamento do participante é importante, seja você um novo no Enterprise Mobility ou migrando de outro produto.  

As necessidades em torno da mobilidade empresarial estão a evoluir de forma dinâmica e a abordagem da Microsoft para fazer face a estas necessidades pode, por vezes, ser diferentes de outras soluções existentes no mercado. A melhor forma de se alinhar em torno dos objetivos de negócio é expressá-los em termos de cenários que pretende permitir para os seus funcionários, parceiros e departamento de TI.  

Seguem-se algumas introduções breves aos seis cenários mais comuns que dependem do Intune, acompanhadas de ligações para mais informações sobre como planear e implementar cada um deles.

>[!NOTE]
>Quer saber como é que a TI da Microsoft utiliza o Intune para permitir à Microsoft aceder aos recursos da empresa nos respetivos dispositivos móveis mantendo também os dados empresariais protegidos? [Leia este estudo técnico de casos concretos](https://www.microsoft.com/itshowcase/Article/Content/588) para ver em pormenor de que forma a TI da Microsoft utiliza o Intune e outros serviços para gerir a identidade, os dispositivos e as aplicações e dados.  

>[!IMPORTANT]
>Queremos assegurar que os dispositivos móveis estão atualizados tendo em consideração os recentes ataques de software maligno "Trident" em dispositivos iOS. Publicámos uma mensagem de blogue denominada [Ensuring mobile devices are up-to-date using Microsoft Intune (Garantir que os dispositivos móveis estão atualizados com o Microsoft Intune)](https://blogs.technet.microsoft.com/enterprisemobility/2016/08/26/ensuring-mobile-devices-are-up-to-date-using-microsoft-intune/). Fornece informações sobre as diferentes formas através das quais o Intune consegue ajudar a manter os seus dispositivos protegidos e atualizados.

## <a name="protecting-your-on-premises-email-and-data-so-it-can-be-safely-accessed-by-mobile-devices"></a>Proteger o seu e-mail e dados no local, para que os dispositivos móveis possam aceder em segurança aos mesmos

A maioria das estratégias de mobilidade empresarial começa com um plano para permitir o acesso seguro ao e-mail para os funcionários com dispositivos móveis ligados à Internet. Muitas organizações ainda têm dados no local e servidores de aplicações, como o Microsoft Exchange, alojados na respetiva rede empresarial.

O Intune e o Microsoft Enterprise Mobility + Security (EMS) fornecem uma [solução de acesso condicional](../protect/conditional-access.md) integrada exclusivamente para o Exchange Server, o que garante que nenhum aplicativo móvel possa acessar o email até que esse dispositivo seja registrado no Intune. Você pode implementar esse tipo de acesso a email sem implantar outro computador de gateway na borda da rede corporativa.

O Intune também suporta permitir o acesso a aplicações móveis que exijam o acesso seguro a dados no local, como servidores de aplicações de linha de negócio. Normalmente, este tipo de acesso é feito através de [certificados geridos pelo Intune](../protect/certificates-configure.md) para controlo de acesso combinado com um proxy ou gateway de VPN padrão no perímetro, como o Proxy de Aplicações do Microsoft Azure Active Directory.

Nestes casos, a única forma de aceder aos dados da empresa é inscrever o dispositivo na gestão. Uma vez inscritos os dispositivos, o sistema de gestão assegura que estão em conformidade com as suas políticas antes de poderem aceder aos dados empresariais. Além disso, a [Ferramenta de Encapsulamento de Aplicações e o SDK da Aplicação](../developer/apps-prepare-mobile-application-management.md) do Intune podem ajudar a conter os dados acedidos na sua aplicação de linha de negócio, para que não possa transmitir dados empresariais a aplicações ou serviços de consumidor.

<!-- Learn more about how to plan and deploy Intune to help secure on-premises email and data. -->

## <a name="protecting-your-office-365-email-and-data-so-it-can-be-safely-accessed-by-mobile-devices"></a>Proteger o seu e-mail e os dados do Office 365, para que os dispositivos móveis possam aceder em segurança aos mesmos

Proteger os dados empresariais no Office 365 (e-mail, documentos, mensagens instantâneas, contactos) não podia ser mais fácil para si ou mais integrado para os seus utilizadores.

O Intune e o Microsoft Enterprise Mobility + Security fornecem uma solução de acesso condicional integrada exclusivamente que garante que nenhum usuário, aplicativo ou dispositivo possa acessar os dados do Office 365, a menos que eles atendam aos requisitos de conformidade da sua empresa (realizou a [autenticação multifator](../enrollment/multi-factor-authentication.md), registrada com o Intune, usando o aplicativo gerenciado, a versão do sistema operacional com suporte, o PIN do dispositivo, o perfil de baixo risco

As aplicações móveis do Office, nas respetivas lojas de aplicações, estão prontas a ser utilizadas com políticas de contenção de dados que pode configurar através do Intune. Estas funcionalidades permitem-lhe impedir que os dados sejam partilhados com aplicações (por exemplo, aplicações de e-mail nativas) e localizações de armazenamento (por exemplo, Dropbox) que não são geridas pela equipa de TI. Todas estas funcionalidades estão incorporadas no Office 365 e no EMS. Não é necessário implementar infraestruturas adicionais para obter este valor.

Uma prática de implementação comum do Office 365 é exigir que os dispositivos se inscrevam na gestão, se precisarem de ser totalmente integrados com configurações de aplicações, certificados, Wi-Fi ou VPN da empresa, que é um cenário comum dos dispositivos pertencentes à empresa.  

No entanto, se o usuário simplesmente precisar acessar documentos e emails corporativos, o que geralmente é o caso para dispositivos pessoais, você poderá exigir que o usuário use os aplicativos móveis do Office (aos quais você aplicou [as políticas de proteção de aplicativo](../apps/app-protection-policies.md) ) e ignorar completamente o registro do dispositivo.  

De qualquer forma, os dados do Office 365 serão protegidos pelas políticas que definiu.

<!-- Learn more about how to plan and deploy Intune to help secure Office 365 email and data. -->

## <a name="offer-a-bring-your-own-device-program-to-all-employees"></a>Oferecer um programa BYOD (Traga o Seu Próprio Dispositivo) a todos os funcionários

A popularidade do programa BYOD (Bring Your Own Device) continua a aumentar entre as organizações como um meio para reduzir as despesas de hardware ou aumentar as opções de produtividade móvel para os funcionários. Hoje em dia, praticamente todas as pessoas têm um telefone pessoal, então porquê colocar outro nos seus bolsos? O principal desafio foi sempre convencer os funcionários a inscreverem os seus dispositivos pessoais na gestão, uma vez que receiam o que o departamento de TI poderá ver e fazer nos respetivos dispositivos.  

Quando a inscrição de dispositivos não é uma opção viável, o Intune oferece um método BYOD alternativo que consiste simplesmente em [gerir as aplicações que contenham dados empresariais](../apps/app-protection-policies.md). O Intune protege os dados empresariais, mesmo que a aplicação em questão aceda a dados empresariais e pessoais, como é o caso das aplicações móveis do Office.  

Como administrador, pode exigir que os utilizadores acedam ao Office 365 a partir de aplicações móveis do Office e configurem as aplicações com políticas que mantêm os dados protegidos (encriptados, protegidos por PIN, etc.). Estas políticas de proteção de aplicações evitam a perda de dados em aplicações não geridas e localizações de armazenamento – dentro ou fora dessas aplicações. Por exemplo, as políticas impedem que um utilizador copie texto de um perfil de e-mail empresarial para um perfil de e-mail de consumidor, mesmo que ambos os perfis estejam configurados no Outlook Mobile. Podem ser implementadas configurações semelhantes para outros serviços e aplicações necessárias aos utilizadores de BYOD.

<!-- Learn more about how to plan and deploy Intune to support BYOD.-->

## <a name="issue-corporate-owned-phones-to-your-employees"></a>Distribuir telemóveis pertencentes à empresa aos seus funcionários

Hoje em dia, a maioria dos funcionários são trabalhadores móveis, o que torna a produtividade em dispositivos móveis fundamental para sermos competitivos. Estes funcionários necessitam de acesso constante a todas as aplicações e dados da empresa, em qualquer altura, onde quer que estejam. Tem de garantir que os dados empresariais são seguros e os custos administrativos são baixos.  

O Intune oferece [soluções de gerenciamento e provisionamento em massa](../enrollment/device-enrollment.md) que são integradas com as principais plataformas de gerenciamento de dispositivos corporativos no mercado atualmente, incluindo o Apple programa de registro de dispositivos e a plataforma de segurança móvel Samsung Knox. A criação centralizada de configurações de dispositivo com o Intune ajuda a fazer com que o aprovisionamento de dispositivos empresariais possa ser altamente automatizado.  

Imagine: entregue a um funcionário uma caixa de iPhone por abrir. O funcionário liga-o e é orientado ao longo de um fluxo de configuração de marca corporativa, onde tem de se autenticar. O iPhone está perfeitamente configurado com [políticas de segurança](../configuration/device-profiles.md).

Em seguida, o funcionário inicia a aplicação Portal da Empresa do Intune para aceder a aplicações empresariais opcionais que estão disponíveis.

<!-- Learn more about how to plan and deploy Intune to support corporate owned devices. -->

## <a name="issue-limited-use-shared-tablets-to-your-employees"></a>Distribuir tablets partilhados de utilização limitada aos seus funcionários

Os funcionários estão a recorrer cada vez mais às tecnologias móveis. Por exemplo, os tablets partilhados são agora utilizados frequentemente pelos funcionários de lojas de venda a retalho.  Quer sejam utilizados para processar uma venda ou para verificar instantaneamente o inventário, os tablets ajudam a criar ótimas interações com os clientes.

A simplicidade da experiência do utilizador é fundamental neste caso. Por esse motivo, os tablets geralmente são fornecidos aos funcionários em um modo de uso limitado, de forma que um único aplicativo de linha de negócios é a única coisa com a qual o funcionário pode interagir. O Intune permite que você provisione, proteja e gerencie centralmente esses dispositivos [Ios e Android](../configuration/device-profiles.md) compartilhados que podem ser configurados para serem executados nesse modo de uso limitado.

<!-- Learn more about how to plan and deploy Intune to support shared tablets. -->

## <a name="enable-your-employees-to-securely-access-office-365-from-an-unmanaged-public-kiosk"></a>Permitir que os seus funcionários acedam de forma segura ao Office 365 a partir de um quiosque público não gerido

Por vezes, os seus funcionários precisam de utilizar dispositivos, aplicações ou browsers que não pode gerir, tal como os computadores públicos em feiras para profissionais e átrios de hotel.

Deve permitir que os seus funcionários acedam ao e-mail da empresa a partir destes dispositivos? Com o Intune e o Microsoft Enterprise Mobility + Security, a resposta pode ser simplesmente "não", [limitando o acesso de email aos dispositivos que são gerenciados pela sua organização](../protect/conditional-access.md). Tal garante que o seu funcionário totalmente autenticado não deixe acidentalmente dados empresariais no computador não fidedigno.

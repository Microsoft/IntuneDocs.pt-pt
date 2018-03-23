---
title: Formas comuns de utilizar o Microsoft Intune
description: Saiba quais são as seis tarefas mais comuns que o Microsoft Intune pode ajudar a gerir.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/02/2018
ms.topic: get-started-article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 1f37d4ff-b5a7-4a89-8884-a6184908b09c
ms.reviewer: angrobe
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: b3010695c6562bab845d271775693f23daf99184
ms.sourcegitcommit: e30fb2375fb79f67e5c1e4ed7b2c21fb9ca80c59
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/17/2018
---
# <a name="common-ways-to-use-microsoft-intune"></a>Formas comuns de utilizar o Microsoft Intune

[!INCLUDE[both-portals](./includes/note-for-both-portals.md)]

Antes de explorar as tarefas de implementação, é importante alinhar os intervenientes da mobilidade empresarial da sua empresa em torno dos objetivos de negócio.  Esta ação é importante quer seja novo na mobilidade empresarial, quer esteja a fazer a migração a partir de outro produto.  

As necessidades em torno da mobilidade empresarial estão a evoluir de forma dinâmica e a abordagem da Microsoft para fazer face a estas necessidades pode, por vezes, ser diferentes de outras soluções existentes no mercado. A melhor forma de se alinhar em torno dos objetivos de negócio é expressá-los em termos de cenários que pretende permitir para os seus funcionários, parceiros e departamento de TI.  

Seguem-se algumas introduções breves aos seis cenários mais comuns que dependem do Intune, acompanhadas de ligações para mais informações sobre como planear e implementar cada um deles.

>[!NOTE]
>Quer saber como é que a TI da Microsoft utiliza o Intune para permitir à Microsoft aceder aos recursos da empresa nos respetivos dispositivos móveis mantendo também os dados empresariais protegidos? [Leia este estudo técnico de casos concretos](https://www.microsoft.com/itshowcase/Article/Content/588) para ver em pormenor de que forma a TI da Microsoft utiliza o Intune e outros serviços para gerir a identidade, os dispositivos e as aplicações e dados.  

>[!IMPORTANT]
>Queremos assegurar que os dispositivos móveis estão atualizados tendo em consideração os recentes ataques de software maligno "Trident" em dispositivos iOS. Publicámos uma mensagem de blogue denominada [Ensuring mobile devices are up-to-date using Microsoft Intune (Garantir que os dispositivos móveis estão atualizados com o Microsoft Intune)](https://blogs.technet.microsoft.com/enterprisemobility/2016/08/26/ensuring-mobile-devices-are-up-to-date-using-microsoft-intune/). Fornece informações sobre as diferentes formas através das quais o Intune consegue ajudar a manter os seus dispositivos protegidos e atualizados.

## <a name="protecting-your-on-premises-email-and-data-so-it-can-be-safely-accessed-by-mobile-devices"></a>Proteger o seu e-mail e dados no local, para que os dispositivos móveis possam aceder em segurança aos mesmos
A maioria das estratégias de mobilidade empresarial começa com um plano para permitir o acesso seguro ao e-mail para os funcionários com dispositivos móveis ligados à Internet. Muitas organizações ainda têm dados no local e servidores de aplicações, como o Microsoft Exchange, alojados na respetiva rede empresarial.


O Intune e o Microsoft Enterprise Mobility + Security (EMS) fornecem uma [solução de acesso condicional](conditional-access.md) integrada ([Portal clássico](/intune-classic/deploy-use/restrict-access-to-email-and-o365-services-with-microsoft-intune)) de forma exclusiva para o Exchange Server, que garante que nenhuma aplicação móvel possa aceder ao e-mail até que o dispositivo esteja inscrito no Intune. Pode fazê-lo sem ter de implementar outra máquina de gateway na periferia da rede empresarial.

O Intune também suporta permitir o acesso a aplicações móveis que exijam o acesso seguro a dados no local, como servidores de aplicações de linha de negócio. Tal é geralmente feito através de [certificados geridos pelo Intune](certificates-configure.md) ([Portal clássico](/intune-classic/deploy-use/secure-resource-access-with-certificate-profiles)) para controlo de acesso combinado com um proxy ou gateway de VPN padrão no perímetro, como o Proxy de Aplicações do Microsoft Azure Active Directory. 

Nestes casos, a única forma de aceder aos dados da empresa é inscrever o dispositivo na gestão. Uma vez inscritos os dispositivos, o sistema de gestão assegura que estão em conformidade com as suas políticas antes de poderem aceder aos dados empresariais. Além disso, a [Ferramenta de Encapsulamento de Aplicações e o SDK da Aplicação](apps-prepare-mobile-application-management.md) do Intune podem ajudar a conter os dados acedidos na sua aplicação de linha de negócio, para que não possa transmitir dados empresariais a aplicações ou serviços de consumidor.

<!-- Learn more about how to plan and deploy Intune to help secure on-premises email and data. -->


## <a name="protecting-your-office-365-email-and-data-so-it-can-be-safely-accessed-by-mobile-devices"></a>Proteger o seu e-mail e os dados do Office 365, para que os dispositivos móveis possam aceder em segurança aos mesmos
Proteger os dados empresariais no Office 365 (e-mail, documentos, mensagens instantâneas, contactos) não podia ser mais fácil para si ou mais integrado para os seus utilizadores.


O Intune e o Microsoft Enterprise Mobility + Security fornecem uma solução de acesso condicional exclusivamente integrada que assegura que nenhum utilizador, aplicação ou dispositivo possa aceder a dados do Office 365, a menos que cumpra os requisitos de conformidade da sua empresa (ter efetuado a [autenticação multifator](/intune-classic/deploy-use/multi-factor-authentication-azure-active-directory), estar inscrito no Intune, utilizar a aplicação gerida, versão suportada do SO, PIN do dispositivo, perfil de risco baixo de utilizador, etc.).


As aplicações móveis do Office, nas respetivas lojas de aplicações, estão prontas a ser utilizadas com políticas de contenção de dados que pode configurar através do Intune. Estas funcionalidades permitem-lhe impedir que os dados sejam partilhados com aplicações (por exemplo, aplicações de e-mail nativas) e localizações de armazenamento (por exemplo, Dropbox) que não são geridas pela equipa de TI. Todas estas funcionalidades estão incorporadas no Office 365 e no EMS. Não é necessário implementar infraestruturas adicionais para obter este valor.

Uma prática de implementação comum do Office 365 é exigir que os dispositivos se inscrevam na gestão, se precisarem de ser totalmente integrados com configurações de aplicações, certificados, Wi-Fi ou VPN da empresa, que é um cenário comum dos dispositivos pertencentes à empresa.  


No entanto, se o seu utilizador precisar simplesmente de aceder ao e-mail e a documentos da empresa, o que é muitas vezes o caso nos dispositivos pessoais, pode exigir que o utilizador utilize as aplicações móveis do Office (às quais aplicou [políticas de proteção de aplicações](app-protection-policies.md) [[Portal clássico](/intune-classic/deploy-use/protect-apps-and-data-with-microsoft-intune)]) e a ignorar completamente a inscrição do dispositivo.  



De qualquer forma, os dados do Office 365 serão protegidos pelas políticas que definiu.

<!-- Learn more about how to plan and deploy Intune to help secure Office 365 email and data. -->


## <a name="offer-a-bring-your-own-device-program-to-all-employees"></a>Oferecer um programa BYOD (Traga o Seu Próprio Dispositivo) a todos os funcionários
A popularidade do programa BYOD (Bring Your Own Device) continua a aumentar entre as organizações como um meio para reduzir as despesas de hardware ou aumentar as opções de produtividade móvel para os funcionários. Hoje em dia, praticamente todas as pessoas têm um telefone pessoal, então porquê colocar outro nos seus bolsos? O principal desafio foi sempre convencer os funcionários a inscreverem os seus dispositivos pessoais na gestão, uma vez que receiam o que o departamento de TI poderá ver e fazer nos respetivos dispositivos.  

Quando a inscrição de dispositivos não é uma opção viável, o Intune oferece um método BYOD alternativo que consiste simplesmente em [gerir as aplicações que contenham dados empresariais](app-protection-policies.md) ([Portal clássico](/intune-classic/deploy-use/protect-apps-and-data-with-microsoft-intune)). O Intune protege os dados empresariais, mesmo que a aplicação em questão aceda a dados empresariais e pessoais, como é o caso das aplicações móveis do Office.  

Como administrador, pode exigir que os utilizadores acedam ao Office 365 a partir de aplicações móveis do Office e configurem as aplicações com políticas que mantêm os dados protegidos (encriptados, protegidos por PIN, etc.). Estas políticas de proteção de aplicações evitam a perda de dados em aplicações não geridas e localizações de armazenamento – dentro ou fora dessas aplicações. Por exemplo, as políticas impedem que um utilizador copie texto de um perfil de e-mail empresarial para um perfil de e-mail de consumidor, mesmo que ambos os perfis estejam configurados no Outlook Mobile. Podem ser implementadas configurações semelhantes para outros serviços e aplicações necessárias aos utilizadores de BYOD.

<!-- Learn more about how to plan and deploy Intune to support BYOD.-->

## <a name="issue-corporate-owned-phones-to-your-employees"></a>Distribuir telemóveis pertencentes à empresa aos seus funcionários
Hoje em dia, a maioria dos funcionários são trabalhadores móveis, o que torna a produtividade em dispositivos móveis fundamental para sermos competitivos. Estes funcionários necessitam de acesso constante a todas as aplicações e dados da empresa, em qualquer altura, onde quer que estejam. Tem de garantir que os dados empresariais são seguros e os custos administrativos são baixos.  

O Intune oferece [soluções de aprovisionamento e gestão em massa](device-enrollment.md) ([Portal clássico](/intune-classic/deploy-use/manage-corporate-owned-devices)) que estão integradas nas principais plataformas de gestão de dispositivos empresariais disponíveis atualmente no mercado, incluindo o Programa de Inscrição de Dispositivos Apple e a plataforma de segurança móvel Samsung Knox. A criação centralizada de configurações de dispositivo com o Intune ajuda a fazer com que o aprovisionamento de dispositivos empresariais possa ser altamente automatizado.  

Imagine: entregue a um funcionário uma caixa de iPhone por abrir. O funcionário liga-o e é orientado ao longo de um fluxo de configuração de marca corporativa, onde tem de se autenticar. O iPhone está perfeitamente configurado com [políticas de segurança](device-profiles.md) ([Portal clássico](/intune-classic/deploy-use/manage-settings-and-features-on-your-devices-with-microsoft-intune-policies)).

Em seguida, o funcionário inicia a aplicação Portal da Empresa do Intune para aceder a aplicações empresariais opcionais que estão disponíveis.

<!-- Learn more about how to plan and deploy Intune to support corporate owned devices. -->

## <a name="issue-limited-use-shared-tablets-to-your-employees"></a>Distribuir tablets partilhados de utilização limitada aos seus funcionários
Os funcionários estão a recorrer cada vez mais às tecnologias móveis. Por exemplo, os tablets partilhados são agora utilizados frequentemente pelos funcionários de lojas de venda a retalho.  Quer sejam utilizados para processar uma venda ou para verificar instantaneamente o inventário, os tablets ajudam a criar ótimas interações com os clientes.

A simplicidade da experiência do utilizador é fundamental neste caso. Por este motivo, os tablets são, normalmente, entregues aos funcionários num modo de utilização limitada, de forma a que o funcionário possa interagir apenas com a aplicação de linha de negócio. O Intune permite aprovisionar em massa, proteger e gerir centralmente estes dispositivos [iOS e Android](device-profiles.md) ([Portal clássico](/intune-classic/deploy-use/manage-settings-and-features-on-your-devices-with-microsoft-intune-policies)) partilhados, que podem ser configurados para serem executados neste modo de utilização limitada.

<!-- Learn more about how to plan and deploy Intune to support shared tablets. -->

## <a name="enable-your-employees-to-securely-access-office-365-from-an-unmanaged-public-kiosk"></a>Permitir que os seus funcionários acedam de forma segura ao Office 365 a partir de um quiosque público não gerido
Por vezes, os seus funcionários precisam de utilizar dispositivos, aplicações ou browsers que não pode gerir, tal como os computadores públicos em feiras para profissionais e átrios de hotel.

Deve permitir que os seus funcionários acedam ao e-mail da empresa a partir destes dispositivos? Com o Intune e o Microsoft Enterprise Mobility + Security, a resposta pode ser “não” ao [limitar o acesso ao e-mail para dispositivos que são geridos pela sua organização](conditional-access.md) ([Portal clássico](/intune-classic/deploy-use/restrict-access-to-email-and-o365-services-with-microsoft-intune)). Tal garante que o seu funcionário totalmente autenticado não deixe acidentalmente dados empresariais no computador não fidedigno.

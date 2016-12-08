---
title: Formas comuns de utilizar o Intune | Microsoft Intune
description: Apresenta uma lista de seis das tarefas mais comuns em que o Intune ajuda
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 11/09/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1f37d4ff-b5a7-4a89-8884-a6184908b09c
ms.reviewer: robstackmsft
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 39e68e467c3295f4751bf3466957a8a377a8e7d6
ms.openlocfilehash: 095be86be3658a294d3f0aab525f5e0dd29b4cfe


---

# <a name="common-ways-to-use-intune"></a>Formas comuns de utilizar o Intune

Antes de explorar as tarefas de implementação, é importante alinhar os intervenientes da mobilidade empresarial da sua empresa em torno dos objetivos de negócio.  Isto é importante quer seja novo na mobilidade empresarial, quer esteja a fazer a migração a partir de outro produto.  

As necessidades em torno da mobilidade empresarial estão a evoluir de forma dinâmica e a abordagem da Microsoft para fazer face a estas necessidades pode, por vezes, ser diferentes de outras soluções existentes no mercado.  A melhor forma de se alinhar em torno dos objetivos de negócio é expressá-los em termos de cenários que pretende permitir para os seus funcionários, parceiros e departamento de TI.  

Seguem-se algumas introduções breves aos seis cenários mais comuns que dependem do Intune, acompanhadas de ligações para mais informações sobre como planear e implementar cada um deles.

>[!NOTE]
>Quer saber como é que a TI da Microsoft utiliza o Intune para permitir à Microsoft aceder aos recursos da empresa nos respetivos dispositivos móveis mantendo também os dados empresariais protegidos? [Leia este estudo técnico de casos concretos](https://www.microsoft.com/itshowcase/Article/Content/588) para ver em pormenor de que forma a TI da Microsoft utiliza o Intune e outros serviços para gerir a identidade, os dispositivos e as aplicações e dados.  

>[!IMPORTANT]
>Queremos assegurar que os dispositivos móveis são atualizados tendo em consideração os recentes ataques de software maligno "Trident" em dispositivos iOS. Publicámos uma publicação de blogue denominada [Garantir que os dispositivos móveis são atualizados com o Microsoft Intune](https://blogs.technet.microsoft.com/enterprisemobility/2016/08/26/ensuring-mobile-devices-are-up-to-date-using-microsoft-intune/). Fornece informações sobre as diferentes formas através das quais o Intune consegue ajudar a manter os seus dispositivos protegidos e atualizados.

## <a name="protecting-your-on-premises-email-and-data-so-it-can-be-safely-accessed-by-mobile-devices"></a>Proteger o seu e-mail e dados no local, para que os dispositivos móveis possam aceder em segurança aos mesmos
A maioria das estratégias de mobilidade empresarial começa com um plano para permitir o acesso seguro ao e-mail para os funcionários com dispositivos móveis ligados à Internet. Muitas organizações ainda têm dados no local e servidores de aplicações, como o Microsoft Exchange, alojados na respetiva rede empresarial.

O Intune e o Microsoft Enterprise Mobility + Security (EMS) fornecem uma [solução de acesso condicional](/intune/deploy-use/restrict-access-to-email-and-o365-services-with-microsoft-intune) integrada de forma exclusiva para o Exchange Server, que garante que nenhuma aplicação móvel possa aceder ao e-mail até que o dispositivo esteja inscrito no Intune. Pode fazê-lo sem ter de implementar outra máquina de gateway na periferia da rede empresarial!

O Intune também suporta permitir o acesso a aplicações móveis que exijam o acesso seguro a dados no local, como servidores de aplicações de linha de negócio. Isto é geralmente feito através de [certificados geridos pelo Intune](/intune/deploy-use/secure-resource-access-with-certificate-profiles) para controlo de acesso combinado com um proxy ou gateway de VPN padrão no perímetro, como o Proxy de Aplicações do Microsoft Azure Active Directory.  

Nestes casos, a única forma de aceder aos dados da empresa é inscrever o dispositivo na gestão. Uma vez inscritos os dispositivos, o sistema de gestão assegura que estão em conformidade com as suas políticas antes de poderem aceder aos dados empresariais.  Além disso, a [Ferramenta de Encapsulamento de Aplicações e o SDK da Aplicação](/intune/deploy-use/decide-how-to-prepare-apps-for-mobile-application-management-with-microsoft-intune) do Intune podem ajudar a conter os dados acedidos na sua aplicação de linha de negócio, para que não possa transmitir dados empresariais a aplicações ou serviços de consumidor.

<!-- Learn more about how to plan and deploy Intune to help secure on-premises email and data. -->


## <a name="protecting-your-office-365-email-and-data-so-it-can-be-safely-accessed-by-mobile-devices"></a>Proteger o seu e-mail e os dados do Office 365, para que os dispositivos móveis possam aceder em segurança aos mesmos
Proteger os dados empresariais no Office 365 (e-mail, documentos, mensagens instantâneas, contactos) não podia ser mais fácil para si ou mais integrado para os seus utilizadores.

O Intune e o Microsoft Enterprise Mobility + Security fornecem uma solução de acesso condicional exclusivamente integrada que assegura que nenhum utilizador, aplicação ou dispositivo possa aceder a dados do Office 365, a menos que cumpra os requisitos de conformidade da sua empresa (ter efetuado a [autenticação multifator](/intune/deploy-use/protect-windows-devices-with-multi-factor-authentication), estar inscrito no Intune, utilizar a aplicação gerida, versão suportada do SO, PIN do dispositivo, perfil de risco baixo de utilizador, etc.). As aplicações móveis do Office, nas respetivas lojas de aplicações, estão prontas para serem associadas às políticas de contenção de dados que pode configurar através do Intune, permitindo impedir a partilha de dados com aplicações (por exemplo, aplicação de e-mail nativa) e localizações de armazenamento (por exemplo: Dropbox) que não são geridas por TI.  Todas estas funcionalidades estão incorporadas no Office 365 e no EMS.  Não é necessário implementar infraestruturas adicionais para obter este valor.

As aplicações móveis do Office, nas respetivas lojas de aplicações, estão prontas a ser utilizadas com políticas de contenção de dados que pode configurar através do Intune. Estas funcionalidades permitem-lhe impedir que os dados sejam partilhados com aplicações (por exemplo, aplicações de e-mail nativas) e localizações de armazenamento (por exemplo, Dropbox) que não são geridas pela equipa de TI.  Todas estas funcionalidades estão incorporadas no Office 365 e no EMS.  Não é necessário implementar infraestruturas adicionais para obter este valor.


Uma prática de implementação comum do Office 365 é exigir que os dispositivos se inscrevam na gestão, se precisarem de ser totalmente integrados com configurações de aplicações, certificados, Wi-Fi ou VPN da empresa, o que é muitas vezes o caso dos dispositivos pertencentes à empresa.  

No entanto, se o utilizador precisar simplesmente de aceder ao e-mail e a documentos da empresa, o que é muitas vezes o caso nos dispositivos pessoais, este é obrigado a utilizar as aplicações móveis do Office (às quais [aplicou políticas de contenção de dados](/intune/deploy-use/protect-apps-and-data-with-microsoft-intune)) e a ignorar completamente a inscrição do dispositivo!  

Qualquer forma, os dados do Office 365 serão protegidos pelas políticas que definiu.

<!-- Learn more about how to plan and deploy Intune to help secure Office 365 email and data. -->


## <a name="offer-a-bring-your-own-device-program-to-all-employees"></a>Oferecer um programa BYOD (Traga o Seu Próprio Dispositivo) a todos os funcionários
A popularidade do programa BYOD (Bring Your Own Device) continua a aumentar entre as organizações como um meio para reduzir as despesas de hardware ou aumentar as opções de produtividade móvel para os funcionários. Hoje em dia, praticamente todas as pessoas têm um telefone pessoal, então porquê colocar outro nos seus bolsos? O principal desafio foi sempre convencer os funcionários a inscreverem os seus dispositivos pessoais na gestão, uma vez que receiam o que o departamento de TI poderá ver e fazer nos respetivos dispositivos.  

Quando a inscrição de dispositivos não é uma opção viável, o Intune oferece um método BYOD alternativo que consiste simplesmente em [gerir as aplicações que contenham dados empresariais](/intune/deploy-use/protect-apps-and-data-with-microsoft-intune).  O Intune protege os dados empresariais, mesmo que a aplicação em questão aceda a dados empresariais e pessoais, como é o caso das aplicações móveis do Office.  

Como administrador, pode exigir que os utilizadores acedam ao Office 365 a partir de aplicações móveis do Office e configurem as aplicações com políticas que mantêm os dados protegidos (encriptados, protegidos por PIN, etc.).  Estas políticas evitam a perda de dados em aplicações não geridas e localizações de armazenamento – dentro ou fora dessas aplicações.  Por exemplo, as políticas impedem que um utilizador copie texto de um perfil de e-mail empresarial para um perfil de e-mail de consumidor, mesmo que ambos os perfis estejam configurados no Outlook Mobile.  Podem ser implementadas configurações semelhantes para outros serviços e aplicações necessárias aos utilizadores de BYOD.

<!-- Learn more about how to plan and deploy Intune to support BYOD.-->

## <a name="issue-corporate-owned-phones-to-your-information-workers"></a>Distribuir telemóveis pertencentes à empresa aos técnicos de informação
Hoje em dia, a maioria dos técnicos de informação são trabalhadores móveis, o que torna a produtividade em dispositivos móveis um imperativo para serem competitivos.  Estes funcionários necessitam de acesso constante a todas as aplicações e dados da empresa, em qualquer altura, onde quer que estejam.  Tem de garantir que os dados empresariais são seguros e os custos administrativos são baixos.  

O Intune oferece [soluções de aprovisionamento e gestão em massa](/intune/deploy-use/manage-corporate-owned-devices) que estão integradas nas principais plataformas de gestão de dispositivos empresariais disponíveis atualmente no mercado, incluindo o Programa de Inscrição de Dispositivos Apple e a plataforma de segurança móvel Samsung KNOX.  A criação centralizada de configurações de dispositivo com o Intune ajuda a fazer com que o aprovisionamento de dispositivos empresariais possa ser altamente automatizado.  

Imagine: entregue a um funcionário uma caixa de iPhone por abrir. O funcionário liga-o e é orientado ao longo de um fluxo de configuração de marca corporativa, onde tem de se autenticar. O iPhone está configurado de forma totalmente integrada com [políticas de segurança](/intune/deploy-use/manage-settings-and-features-on-your-devices-with-microsoft-intune-policies) (por exemplo, uma unidade de disco rígido encriptada e um PIN de dispositivo), [perfis de e-mail, Wi-Fi/VPN e certificados](/intune/deploy-use/enable-access-to-company-resources-with-microsoft-intune) e um conjunto de linha de base de [aplicações](/intune/deploy-use/add-apps).

Em seguida, o funcionário inicia a aplicação Portal da Empresa do Intune para aceder a aplicações empresariais opcionais que estão disponíveis.

<!-- Learn more about how to plan and deploy Intune to support corporate owned devices. -->

## <a name="issue-limited-use-shared-tablets-to-your-task-workers"></a>Distribuir tablets partilhados de utilização limitada aos trabalhadores de tarefas
Os trabalhadores de tarefas estão a recorrer cada vez mais às tecnologias móveis.  Por exemplo, os tablets partilhados são agora utilizados frequentemente pelos funcionários de lojas de venda a retalho.  Quer sejam utilizados para processar uma venda ou para verificar instantaneamente o inventário, os tablets ajudam a criar ótimas interações com os clientes.

A simplicidade da experiência do utilizador é fundamental neste caso.  Por este motivo, os tablets são, normalmente, entregues aos funcionários num modo de utilização limitada, de forma a que o funcionário possa interagir apenas com a aplicação de linha de negócio.  O Intune permite aprovisionar em massa, proteger e gerir centralmente estes tablets [iOS](/intune/deploy-use/ios-policy-settings-in-microsoft-intune#general-configuration-policy-settings) e [Android](/intune/deploy-use/android-policy-settings-in-microsoft-intune#general-configuration-policy) partilhados, que podem ser configurados para serem executados neste modo de utilização limitada.

<!-- Learn more about how to plan and deploy Intune to support shared tablets. -->

## <a name="enable-your-employees-to-securely-access-office-365-from-an-unmanaged-public-kiosk"></a>Permitir que os seus funcionários acedam de forma segura ao Office 365 a partir de um quiosque público não gerido
Por vezes, os seus funcionários precisam de utilizar dispositivos, aplicações ou browsers que não pode gerir, tal como os computadores públicos em feiras para profissionais e átrios de hotel.

Deve permitir que os seus funcionários acedam ao e-mail da empresa a partir destes dispositivos? Com o Intune e o Microsoft Enterprise Mobility + Security, <!--you have choices. The--> a resposta pode ser "não" ao [limitar o acesso ao e-mail para dispositivos que são geridos pela sua organização](/intune/deploy-use/restrict-access-to-email-and-o365-services-with-microsoft-intune).  <!-- Alternatively, you can choose to allow limited access to these untrusted computers by requiring multi-factor authentication and only allowing browser access (Outlook Web Access) in a mode where files cannot be downloaded (e.g. email attachments).--> Isto garante que o seu funcionário totalmente autenticado não deixe acidentalmente dados empresariais no computador não fidedigno.

<!-- Learn more about how to plan and deploy Intune to support kiosks. -->



<!--HONumber=Nov16_HO3-->



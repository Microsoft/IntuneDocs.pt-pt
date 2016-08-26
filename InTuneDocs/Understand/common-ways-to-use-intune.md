---
title: Formas comuns de utilizar o Intune | Microsoft Intune
description: 
keywords: 
author: jeffgilb
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1f37d4ff-b5a7-4a89-8884-a6184908b09c
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 9cb6894cefad1da14332f9994fdf45fe2d1e9b9c
ms.openlocfilehash: c854893f457a60a7424010cdf69a91cb8476e167


---

# Formas comuns de utilizar o Intune

Antes de explorar as tarefas de implementação, é importante alinhar os intervenientes da mobilidade empresarial da sua empresa em torno dos objetivos de negócio.  Isto é importante quer seja novo na mobilidade empresarial, quer esteja a fazer a migração a partir de outro produto.  As necessidades em torno da mobilidade empresarial estão a evoluir de forma dinâmica e as abordagens da Microsoft para fazer face a estas necessidades podem, por vezes, ser diferentes de outras soluções existentes no mercado.  A melhor forma de se alinhar em torno dos objetivos de negócio é expressar o que pretende concretizar em termos de cenários que pretende permitir para os seus funcionários, parceiros e pessoal de TI.  Seguem-se algumas introduções breves aos seis cenários mais comuns que dependem do Intune, acompanhadas de ligações para mais informações sobre como planear e implementar cada um deles.

>[!NOTE] Pretende saber como é que a TI da Microsoft utiliza o Intune para permitir que os funcionários da Microsoft acedam aos recursos da empresa nos respetivos dispositivos móveis, mantendo também os dados empresariais protegidos? [Leia este estudo técnico de casos concretos](https://www.microsoft.com/itshowcase/Article/Content/588) para ver em pormenor de que forma a TI da Microsoft utiliza o Intune e outros serviços para gerir a identidade, os dispositivos e as aplicações e dados.  

## Proteger o seu e-mail no local e os dados, para que os dispositivos móveis possam aceder em segurança aos mesmos
A maioria das estratégias de mobilidade empresarial começam com um plano para permitir o acesso seguro ao e-mail para os funcionários com dispositivos móveis na Internet. Muitas organizações ainda têm dados no local e servidores de aplicações, como o Microsoft Exchange, alojados na respetiva rede empresarial. O Intune e o Enterprise Mobility Suite (EMS) fornecem uma solução de acesso condicional exclusivamente integrada para o Exchange Server, que garante que nenhuma aplicação móvel conseguirá aceder ao e-mail até o dispositivo ser inscrito no Intune, tudo sem implementar outro computador gateway na periferia da rede da sua empresa!

Para além do e-mail, o Intune suporta a permissão do acesso a aplicações móveis que exijam o acesso seguro a dados no local, como um servidor de aplicações de linha de negócio.  Isto é geralmente feito utilizando certificados geridos pelo Intune para controlo de acesso combinado com um proxy ou gateway de VPN padrão no perímetro, tal como o Proxy de Aplicações do Microsoft Azure AD.  Nestes casos, a única forma de aceder aos dados da empresa é inscrever o dispositivo na gestão.  Uma vez inscrito, o sistema de gestão assegura que os dispositivos que acedem a dados empresariais estão em conformidade com as suas políticas.  Além disso, a App Wrapping Tool do Intune pode ser utilizada para ajudar a conter os dados acedidos na sua aplicação de linha de negócio, para que não possa transmitir dados empresariais a aplicações ou serviços de consumidor.

<!-- Learn more about how to plan and deploy Intune to help secure on-premises email and data. -->

## Proteger o seu e-mail e os dados do Office 365, para que os dispositivos móveis possam aceder em segurança aos mesmos
Proteger os dados empresariais no Office 365 (e-mail, documentos, mensagens instantâneas, contactos) não podia ser mais fácil para si ou mais integrado para os seus utilizadores. O Intune e o Enterprise Mobility Suite fornecem uma solução de acesso condicional exclusivamente integrada que assegura que nenhum utilizador, aplicação ou dispositivo possa aceder a dados do Office 365, a menos que cumpra os requisitos de conformidade da sua empresa (ter efetuado a autenticação multifator, estar inscrito no Intune, utilizar a aplicação gerida, versão suportada do sistema operativo, do SO suportado, PIN do dispositivo, perfil de risco baixo de utilizador, etc.). As aplicações móveis do Office, nas respetivas lojas de aplicações, estão prontas para serem associadas às políticas de contenção de dados que pode configurar através do Intune, permitindo impedir a partilha de dados com aplicações (por exemplo, aplicação de e-mail nativa) e localizações de armazenamento (por exemplo: Dropbox) que não são geridas por TI.  Todas estas funcionalidades estão incorporadas no Office 365 e no EMS.  Não é necessário implementar infraestruturas adicionais para obter este valor.

Uma prática de implementação comum do Office 365 é exigir que os dispositivos se inscrevam na gestão, caso necessitem de ser totalmente aprovisionados com configurações de aplicações/certificados/Wi-Fi/VPN da empresa, o que é muitas vezes o caso dos dispositivos pertencentes à empresa.  No entanto, se o utilizador precisar simplesmente de aceder ao e-mail e a documentos da empresa, o que é muitas vezes o caso nos dispositivos pertencentes à empresa, o utilizador é obrigado a utilizar as aplicações móveis do Office (às quais aplicou as políticas de contenção de dados) e a ignorar a inscrição do dispositivo completamente!  Qualquer forma, os dados do Office 365 serão protegidos pelas políticas que definiu.

<!-- Learn more about how to plan and deploy Intune to help secure Office 365 email and data. -->

## Oferecer um programa “bring your own device” (BYOD) a todos os funcionários
A popularidade do programa BYOD continua a aumentar entre as organizações como um meio para reduzir as despesas de hardware ou aumentar as opções de produtividade móvel para os funcionários. Hoje em dia, praticamente todas as pessoas têm um telefone pessoal, então porquê colocar outro nos seus bolsos? O principal desafio foi sempre convencer os funcionários a inscreverem os seus dispositivos pessoais na gestão, uma vez que receiam o que o departamento de TI poderá ver e fazer nos respetivos dispositivos.  

Quando a inscrição de dispositivos não é uma opção viável, o Intune oferece um método BYOD alternativo que consiste em gerir simplesmente as aplicações que contenham dados empresariais.  O Intune protege os dados empresariais, mesmo que a aplicação em questão aceda a dados empresariais e pessoais, como é o caso das aplicações móveis do Office.  Como administrador, pode exigir que os utilizadores acedam ao Office 365 a partir de aplicações móveis do Office e configurem as aplicações com políticas que mantêm os dados protegidos (encriptados, protegidos por PIN, etc.).  Estas políticas evitam a perda de dados em aplicações não geridas e localizações de armazenamento – dentro ou fora dessas aplicações.  Por exemplo, as políticas impedirão que um utilizador copie texto de um perfil de e-mail empresarial para um perfil de e-mail de consumidor, mesmo que ambos os perfis estejam configurados no Outlook Mobile.  Podem ser implementadas configurações semelhantes para outros serviços e aplicações necessárias aos utilizadores de BYOD.

<!-- Learn more about how to plan and deploy Intune to support BYOD.-->

## Distribuir telemóveis pertencentes à empresa aos técnicos de informação
Hoje em dia, a maioria dos técnicos de informação são trabalhadores móveis, o que torna a produtividade em dispositivos móveis um imperativo para serem competitivos.  Estes funcionários necessitam de acesso constante a todas as aplicações e dados da empresa, em qualquer altura, onde quer que estejam.  Tem de garantir que os dados empresariais são seguros e os custos administrativos são baixos.  

O Intune oferece soluções de aprovisionamento e gestão em massa que estão integradas nas principais plataformas de gestão de dispositivos empresariais disponíveis atualmente no mercado, incluindo o Programa de Inscrição de Dispositivos Apple e a plataforma de segurança móvel Samsung KNOX.  A criação centralizada de configurações de dispositivo com o Intune faz com que o aprovisionamento de dispositivos empresariais possa ser altamente automatizado.  

Imagine: entregue a um funcionário uma caixa de iPhone por abrir. O funcionário liga-o e é orientado ao longo de um fluxo de configuração de marca corporativa, onde tem de se autenticar. O iPhone está configurado de forma totalmente integrada com políticas de segurança (encriptar a unidade de disco rígido, PIN do dispositivo, etc.), perfis de e-mail/Wi-Fi/VPN/certificados e um conjunto de linha de base de aplicações. Em seguida, o funcionário inicia a aplicação Portal da Empresa do Intune para aceder a aplicações empresariais opcionais que estão disponíveis.

<!-- Learn more about how to plan and deploy Intune to support corporate owned devices. -->

## Distribuir tablets partilhados de utilização limitada aos trabalhadores de tarefas
Os trabalhadores de tarefas estão a recorrer cada vez mais às tecnologias móveis.  Por exemplo, os tablets partilhados são agora comuns para os funcionários de lojas de venda a retalho.  Quer sejam utilizados para processar uma venda ou para verificar instantaneamente o inventário, os tablets ajudam a criar ótimas interações com os clientes.  A simplicidade da experiência do utilizador é fundamental neste caso.  Por este motivo, os tablets são, normalmente, entregues aos funcionários num modo de utilização limitada, de forma a que o funcionário possa interagir apenas com a aplicação de linha de negócio.  O Intune permite aprovisionar em massa, proteger e gerir centralmente estes tablets partilhados, que podem ser configurados para serem executados neste modo de utilização limitada.

<!-- Learn more about how to plan and deploy Intune to support shared tablets. -->

## Permitir que os seus funcionários acedam de forma segura ao Office 365 a partir de um quiosque público não gerido
Por vezes, os seus funcionários precisam de utilizar dispositivos, aplicações ou browsers que não pode gerir, tal como os computadores públicos em feiras para profissionais e átrios de hotel. Deve permitir que os seus funcionários acedam ao e-mail da empresa a partir destes dispositivos? Com o Intune e o enterprise mobility suite, <!--you have choices. The--> a resposta pode ser "não" ao limitar o acesso ao e-mail para dispositivos que são geridos pela sua organização.  <!-- Alternatively, you can choose to allow limited access to these untrusted computers by requiring multi-factor authentication and only allowing browser access (Outlook Web Access) in a mode where files cannot be downloaded (e.g. email attachments).-->  Isto irá garantir que o seu funcionário totalmente autenticado não deixe acidentalmente dados empresariais no computador não fidedigno.

<!-- Learn more about how to plan and deploy Intune to support kiosks. -->



<!--HONumber=Jun16_HO4-->



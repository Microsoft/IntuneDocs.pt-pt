---
title: incluir ficheiro
description: incluir ficheiro
author: ErikjeMS
ms.service: microsoft-intune
ms.topic: include
ms.date: 11/19/2019
ms.author: erikje
ms.custom: include file
ms.openlocfilehash: 9aa82268fb02f5124e48eb303f19cf32be02c284
ms.sourcegitcommit: c46b0c2d4507be6a2786a4ea06009b2d5aafef85
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/01/2020
ms.locfileid: "76912642"
---
Esses avisos fornecem informações importantes que podem ajudá-lo a se preparar para futuras alterações e recursos do Intune.

### <a name="updated-feature-new-rbac-role-coming-to-intune--4253397--"></a>Funcionalidade atualizada: Nova função RBAC chegando a Intune<!--4253397-->
Na atualização de serviços intune de janeiro, planeamos lançar um novo papel de segurança no Intune. Você verá este papel listado como "Endpoint Security Manager" em Intune e o papel é uma expansão do papel de "Administrador de Segurança" da Azure AD.
 
#### <a name="how-does-this-affect-me"></a>Como é que isto me afeta?
Hoje existem três funções disponíveis em Azure AD para os seus profissionais de segurança:
- Papel do Leitor de Segurança em Azure AD, que dá acesso apenas a Intune.
- Papel do Operador de Segurança na AD Azure, que dá acesso apenas a Intune.
- Administrador de Segurança em Azure AD. Quando a Intune envia a atualização de janeiro, juntamente com permissões apenas de leitura para Intune, as novas permissões fornecidas pelo papel de Gestor de Segurança endpoint são as seguintes:
    - Ler, Criar, Atualizar, Excluir e Atribuir Políticas de Conformidade de Dispositivos
    - Ler, Eliminar e atualizar dispositivos geridos
    - Ler, Criar, Atualizar, Excluir e Atribuir linhas de segurança
    - Ler e atualizar tarefas de segurança
 
### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>O que preciso de fazer para me preparar para esta alteração?
Reveja hoje as suas funções Intune RBAC. Se atualmente apenas tem a Global Admins como papéis, então não são necessárias alterações. Se usar papéis, e quiser a granularidade que o Gestor de Segurança endpoint proporciona, então atribua esse papel quando estiver disponível. Consulte a página Intune [What's New](../fundamentals/whats-new.md) para obter informações atualizadas sobre o lançamento do Intune. 

### <a name="updated-support-statement-for-adobe-acrobat-reader-for-intune-mobile-app--5746776--"></a>Foi atualizada a instrução de suporte para o aplicativo móvel ' Adobe Acrobat Reader for Intune '<!--5746776-->
Compartilhamos em MC188653 no final de agosto, que o Adobe Acrobat Reader para o aplicativo móvel do Intune estava atingindo o fim da vida útil em 1º de dezembro de 2019 e que a Adobe estava planejando dar suporte às políticas de proteção de aplicativo do Intune em seu aplicativo do Acrobat Reader principal. Desde então, recebemos comentários dos clientes que precisávamos fornecer mais tempo para continuar permitindo que os administradores de ti direcionem e os usuários finais comecem a usar o Adobe Acrobat Reader para Intune. Devido ao alto uso do Adobe Acrobat Reader para Intune em dispositivos de usuário final e sua importância em cenários empresariais, queremos garantir que qualquer experiência atenda às necessidades de proteção do aplicativo da sua organização. 

Embora ainda seja recomendável direcionar o aplicativo móvel Acrobat Reader em suas políticas, já que o aplicativo móvel Acrobat Reader dá suporte a políticas de proteção de aplicativo e integrou o SDK do Intune, o aplicativo Adobe Acrobat Reader para Intune continuará a ter suporte até 31 de março de 2020. 

#### <a name="how-does-this-affect-me"></a>Como é que isto me afeta?
Você está recebendo esta mensagem porque nosso relatório indica que uma ou mais políticas em sua organização estão direcionando o aplicativo Adobe Acrobat Reader para Intune e/ou você pode ter recebido nossa comunicação de EOL anterior. 

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>O que preciso de fazer para me preparar para esta alteração?
Permita que os usuários finais e a assistência técnica saibam dessa alteração. Você pode usar a [funcionalidade de informações de suporte do portal da empresa](../apps/company-portal-app.md#support-information) para estabelecer um canal para perguntas relacionadas ao Intune.

#### <a name="additional-information"></a>Informações Adicionais
https://helpx.adobe.com/acrobat/kb/intune-app-end-of-life.html


### <a name="end-support-for-windows-phone-81--3544909--"></a>Suporte final para Windows Phone 8,1<!--3544909-->
O suporte principal da Microsoft para o Windows Phone 8,1 foi encerrado em 2017 de julho e o suporte estendido terminou em 2019 de junho. O aplicativo Portal da Empresa para Windows Phone 8,1 esteve no modo de manutenção, desde 2017 de outubro. Microsoft Intune agora terminará o suporte em 20 de fevereiro de 2020 para Windows Phone 8,1.

#### <a name="how-does-this-affect-me"></a>Como é que isto me afeta?
Após 20 de fevereiro de 2020, esses dispositivos não receberão nenhuma atualização de segurança e você não poderá registrar nenhum dispositivo novo. Os dispositivos existentes do Windows Phone 8.1 permanecerão matriculados (política, apps, reportagens), mas note que qualquer resolução de problemas de uma inscrição existente não será suportada após esta data, uma vez que muitos componentes, como certificados de terceiros, já terminaram o suporte para o plataforma. O Intune irá parar o teste de compatibilidade com o Intune e Windows Phone 8,1.

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>O que preciso de fazer para me preparar para esta alteração?
Você pode verificar seus relatórios do Intune para ver quais dispositivos ou usuários podem ser afetados. Aceda a Dispositivos > Todos os dispositivos e filtre por SO. Você pode adicionar colunas adicionais para ajudar a identificar quem em sua organização tem dispositivos em execução Windows Phone 8,1. Solicite que os usuários finais atualizem seus dispositivos para uma versão do sistema operacional com suporte.


### <a name="take-action-use-microsoft-edge-for-your-protected-intune-browser-experience--5728447--"></a>Tomar medidas: Use microsoft edge para a sua experiência de navegador intune protegida<!--5728447-->
Como temos vindo a partilhar ao longo do último ano, o microsoft Edge mobile suporta o mesmo conjunto de funcionalidades de gestão que o Managed Browser, ao mesmo tempo que proporciona uma experiência de utilizador final muito melhorada. Para dar lugar às experiências robustas fornecidas no Microsoft Edge, vamos retirar o Navegador Gerido Intune. A partir de 27 de janeiro de 2020, a Intune deixará de suportar o Navegador Gerido Intune.  

#### <a name="how-does-this-affect-me"></a>Como é que isto me afeta? 
A partir de 1 de fevereiro de 2020, o Navegador Gerido Intune deixará de estar disponível na Google Play Store ou na App Store iOS. Neste ponto, você ainda será capaz de direcionar novas políticas de proteção de aplicativo para a Intune Managed Browser, embora novos usuários não possam baixar o aplicativo Intune Managed Browser. Além disso, no iOS, novos clips web que são empurrados para baixo para dispositivo sinuoso serão abertos no Microsoft Edge em vez do Navegador Gerido Intune.  

No dia 31 de março de 2020, o Navegador Gerido Intune será removido da consola Azure. Isto significa que já não será capaz de criar novas políticas para o Navegador Gerido intune. Se você tiver políticas de Intune Managed Browser existentes em vigor, elas não serão afetadas. O Intune Managed Browser aparecerá na consola como uma aplicação LOB sem ícone, e as políticas existentes mostrarão como direcionados para a app ainda. Neste ponto, também removeremos a opção de redirecionar conteúdo web para o Navegador Gerido Intune dentro da secção de Proteção de Dados das políticas de proteção de Aplicações.  

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>O que preciso de fazer para me preparar para esta alteração? 
Para garantir uma transição suave do Navegador Gerido Intune para o Microsoft Edge, recomendamos que tome os seguintes passos de forma proativa: 

1. Target Microsoft Edge para iOS e Android com política de proteção de aplicações (também referida como MAM) e definições de config de aplicações. Você pode reutilizar suas políticas de Intune Managed Browser para o Microsoft Edge direcionando essas políticas existentes para o Microsoft Edge também.  
2. Certifique-se de que todas as aplicações protegidas pelo MAM no seu ambiente têm a definição de política de proteção de aplicações "Restringir a transferência de conteúdos web com outras aplicações" definida para "Navegadores geridos pela política". 
3. Direcione todos os MAM protegidos com a configuração de configuração de aplicação gerida "com.microsoft.intune.useEdge" definida como verdadeira. A partir do próximo mês com o lançamento de 1911, poderá realizar os passos 2 e 3 simplesmente configurando a definição de "Restringir a transferência de conteúdos web com outras aplicações" para ter "Microsoft Edge" selecionado na secção de Proteção de Dados das suas políticas de proteção de aplicações . 

Está a chegar suporte para web clips no iOS e Android. Quando este suporte for lançado, terá de redirecionar os web clips pré-existentes para garantir que se abrem no Microsoft Edge em vez do Navegador Gerido. 

#### <a name="additional-information"></a>Informações adicionais
Visite os nossos médicos ao utilizar o Microsoft Edge com políticas de [proteção de aplicações](../apps/manage-microsoft-edge.md) para mais informações, ou veja o nosso post de blog de [suporte](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Use-Microsoft-Edge-for-your-Protected-Intune-Browser-Experience/ba-p/1004269).


### <a name="end-of-support-for-legacy-pc-management"></a>Fim do suporte para o gerenciamento de PC herdado

O gerenciamento de computadores herdados está ficando sem suporte em 15 de outubro de 2020. Atualize os dispositivos para o Windows 10 e registre-os novamente como dispositivos de MDM (gerenciamento de dispositivo móvel) para mantê-los gerenciados pelo Intune.

[Saiba mais](https://go.microsoft.com/fwlink/?linkid=2107122)

### <a name="decreasing-support-for-android-device-administrator"></a>Diminuindo o suporte para o administrador do dispositivo Android 
O administrador do dispositivo Android (às vezes chamado de gerenciamento do Android "herdado" e lançado com o Android 2,2) é uma maneira de gerenciar dispositivos Android. No entanto, a funcionalidade de gerenciamento aprimorada agora está disponível com o [Android Enterprise](../enrollment/connect-intune-android-enterprise.md) (lançado com Android 5,0). Em um esforço para migrar para o gerenciamento de dispositivos moderno, mais avançado e seguro, o Google está diminuindo o suporte ao administrador de dispositivos em novas versões do Android.

#### <a name="how-does-this-affect-me"></a>Como é que isto me afeta?
Devido a essas alterações feitas pelo Google, os usuários do Intune serão afetados das seguintes maneiras:  
- O Intune só poderá fornecer suporte completo para dispositivos Android gerenciados pelo administrador do dispositivo que executam o Android 10 e posterior por meio do Q2 CY2020. Dispositivos gerenciados pelo administrador do dispositivo que executam o Android 10 ou posterior após esse período não poderão ser totalmente gerenciados. Em particular, os dispositivos afetados não receberão novos requisitos de senha.
    - Os dispositivos Samsung Knox não serão afetados neste período porque o suporte estendido é fornecido por meio da integração do Intune com a plataforma Knox. Isso lhe dá mais tempo para planejar a transição do gerenciamento de administradores de dispositivos.    
- Os dispositivos Android gerenciados pelo administrador do dispositivo que permanecem em versões do Android abaixo do Android 10 não serão afetados e poderão continuar sendo totalmente gerenciados com o administrador do dispositivo.    
- Para todos os dispositivos que executam o Android 10 e posterior, o Google restringiu a capacidade para que os agentes de gerenciamento de administrador de dispositivos, como Portal da Empresa, acessem informações de identificador de dispositivo. Esta restrição afeta as seguintes funcionalidades Intune depois de um dispositivo ser atualizado para o Android 10 ou posteriormente:  
    - O controle de acesso à rede para VPN não funcionará mais.   
    - Identificar dispositivos como corporativos com um número de série ou IMEI não marcará automaticamente os dispositivos como corporativos.  
    - O IMEI e o número de série não estarão mais visíveis para os administradores de ti no Intune. 
        > [!NOTE]
        > Isso afeta somente dispositivos gerenciados pelo administrador do dispositivo no Android 10 e posterior e não afeta os dispositivos gerenciados como Android Enterprise. 

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>O que preciso de fazer para me preparar para esta alteração?
Para evitar a redução na funcionalidade que entra no T3 CY2020, recomendamos o seguinte:
- Não integre novos dispositivos ao gerenciamento de administradores de dispositivos.
- Se for esperado que um dispositivo receba uma atualização para o Android 10, migre-o do gerenciamento de administradores de dispositivos para o gerenciamento do Android Enterprise e/ou políticas de proteção de aplicativo.

#### <a name="additional-information"></a>Informações adicionais
- [Diretrizes do Google para migração do administrador do dispositivo para Android Enterprise](http://static.googleusercontent.com/media/android.com/en/enterprise/static/2016/pdfs/enterprise/Android-Enterprise-Migration-Bluebook_2019.pdf)
- [Documentação do Google no plano para substituir a API de administrador do dispositivo](https://developers.google.com/android/work/device-admin-deprecation)

### <a name="plan-for-change-intune-app-sdk-and-app-protection-policies-for-android-moving-to-support-android-50-and-higher-in-an-upcoming-release---4911065---"></a>Plano para alteração: SDK de aplicativo do Intune e políticas de proteção do aplicativo para Android migrando para suporte para Android 5,0 e posterior em uma versão futura <!--4911065 -->
O Intune mudará para oferecer suporte a Android 5. x (pirulito) e superior em uma versão futura. Atualize todos os aplicativos encapsulados com o SDK de aplicativos do Intune mais recente e atualize seus dispositivos.

#### <a name="how-does-this-affect-me"></a>Como é que isto me afeta?
Se você não estiver usando o ou planeja usar o SDK ou o aplicativo para Android, essa alteração não afetará você. Se você estiver usando o SDK de aplicativos do Intune, certifique-se de atualizar para a versão mais recente e também atualizar seus dispositivos para Android 5. x e superior. Se você não atualizar, os aplicativos não receberão atualizações, e a qualidade da sua experiência diminuirá ao longo do tempo.

Abaixo, encontre uma lista de dispositivos comuns registrados no Intune que executam o Android versão 4. x. Se você tiver um desses dispositivos, execute as etapas apropriadas para certificar-se de que este dispositivo dará suporte à versão 5,0 ou superior do Android ou que ele será substituído por um dispositivo que dá suporte à versão 5,0 ou superior do Android. Esta lista não é exaustiva em todos os dispositivos que talvez precisem ser avaliados:

- Samsung SM-T561  
- Samsung SM-T365
- Samsung GT-I9195
- Samsung SM-G800F
- Samsung SM-G357FZ
- XT1080 Motorola
- Samsung GT-I9305
- Samsung SM-T231

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>O que preciso de fazer para me preparar para esta alteração?
Encapsular seus aplicativos com o SDK de aplicativos do Intune mais recente. Você também pode definir a configuração de inicialização condicional "exigir versão mínima do sistema operacional (somente aviso)" para notificar os usuários finais sobre os dispositivos pessoais a serem atualizados.

### <a name="intune-plan-for-change-nearing-end-of-support-for-windows-7---3042987---"></a>Plano do Intune para alteração: próximo ao fim do suporte para o Windows 7<!-- 3042987 -->
À medida que recebemos a mensagem em MC148476, postou o último de setembro de 2018 e novamente no MC176794 de março de 2019, o Windows 7 atinge seu fim de suporte estendido em 14 de janeiro de 2020. Nesse momento, o Intune desativará o suporte para dispositivos que executam o Windows 7, para que possamos focar nosso investimento em dar suporte a tecnologias mais novas e fornecer novas experiências de usuário final. Após essa data, a assistência técnica e as atualizações automáticas que ajudam a proteger seu PC com Windows 7 não estarão mais disponíveis por meio do Intune. A Microsoft recomenda enfaticamente que você mude para o Windows 10 antes de janeiro de 2020 para evitar um cenário em que você precisa de serviço ou suporte que não esteja mais disponível. Leia mais sobre o ciclo de vida do suporte do Windows [aqui](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet).

#### <a name="how-does-this-affect-me"></a>Como é que isto me afeta?
Você está recebendo esta mensagem porque atualmente está gerenciando computadores com Windows 7 usando o agente de software de computador do Intune herdado. Como menos de um ano permanece antes do fim do suporte estendido do Windows 7, incentivamos a sua organização a começar a atualizar para o Windows 10 assim que possível.  

Os recursos de gerenciamento de PC são criados diretamente no sistema operacional Windows 10, e você não precisa mais instalar um agente cliente, como o cliente de software do Intune para Windows 7. A partir do Windows 8.1, a Microsoft usa a arquitetura de MDM (gerenciamento de dispositivo móvel) para provisionar, configurar, atualizar e gerenciar computadores Windows. Quando você tiver configurado o Intune, poderá simplificar o registro do Windows [registrando computadores Windows 10 no Intune](..\windows-enroll.md) por meio do canal MDM. Recomendamos que você use essa solução de gerenciamento de MDM "sem agente" para gerenciar seus PCs com Windows 10.

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>O que preciso de fazer para me preparar para esta alteração?
Incentivamos sua organização a considerar imediatamente este plano de ação:

- Planeje e atualize o Windows 7 frota para o Windows 10 antes de 14 de janeiro de 2020.
- Explore o [suporte à implantação do Windows 10](https://docs.microsoft.com/windows/deployment/) para saber mais sobre como atualizar sua frota existente de PCs com Windows 7 para o Windows 10.
- Examine o [aplicativo de desktop garanta](https://www.microsoft.com/fasttrack/microsoft-365/desktop-app-assure?rtc=1) a oferta por meio do FastTrack, que ajudará com a promessa de compatibilidade de aplicativos da Microsoft.
- Transição existente legado software Intune dispositivos geridos por clientes para a solução recomendada pela Microsoft para gerir o Windows 10 usando a gestão do MDM. Registre todos os novos computadores Windows 10 usando o gerenciamento de MDM para Intune no portal do Azure.

Para mais informações, consulte a publicação do [blog aqui](https://aka.ms/Windows7_Intune).



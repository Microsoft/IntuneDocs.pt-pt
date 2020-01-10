---
title: incluir ficheiro
description: incluir ficheiro
author: ErikjeMS
ms.service: microsoft-intune
ms.topic: include
ms.date: 11/19/2019
ms.author: erikje
ms.custom: include file
ms.openlocfilehash: e745290991da4d80c7e3839250edbfdd64ef1b7a
ms.sourcegitcommit: 01c57ac880dcb5f474908977c89810f5bedaf326
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/09/2020
ms.locfileid: "75760976"
---
Esses avisos fornecem informações importantes que podem ajudá-lo a se preparar para futuras alterações e recursos do Intune.

### <a name="updated-feature-new-rbac-role-coming-to-intune--4253397--"></a>Recurso atualizado: nova função RBAC chegando ao Intune<!--4253397-->
Na atualização de serviço do Intune de Janeiro, planejamos lançar uma nova função de segurança no Intune. Você verá essa função listada como "Gerenciador de segurança de ponto de extremidade" no Intune e a função é uma expansão da função "administrador de segurança" do Azure AD.
 
#### <a name="how-does-this-affect-me"></a>Como é que isto me afeta?
Hoje, há três funções disponíveis no Azure AD para seus profissionais de segurança:
- Função de leitor de segurança no Azure AD que fornece acesso somente leitura ao Intune.
- Função de operador de segurança no Azure AD que fornece acesso somente leitura ao Intune.
- Administrador de segurança no Azure AD. Quando o Intune envia a atualização de Janeiro, juntamente com as permissões somente leitura para o Intune, as novas permissões fornecidas pela função Endpoint Security Manager são as seguintes:
    - Ler, criar, atualizar, excluir e atribuir políticas de conformidade do dispositivo
    - Ler, excluir e atualizar dispositivos gerenciados
    - Ler, criar, atualizar, excluir e atribuir linhas de base de segurança
    - Ler e atualizar tarefas de segurança
 
### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>O que preciso de fazer para me preparar para esta alteração?
Examine suas funções de RBAC do Intune hoje mesmo. Se atualmente você tiver apenas administradores globais como funções, não haverá nenhuma alteração necessária. Se você usar funções e quiser a granularidade que o Gerenciador de segurança de ponto de extremidade fornece, atribua essa função quando ela estiver disponível. Verifique a página [novidades do](../fundamentals/whats-new.md) Intune para obter informações atualizadas sobre a versão do Intune. 

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
Após 20 de fevereiro de 2020, esses dispositivos não receberão nenhuma atualização de segurança e você não poderá registrar nenhum dispositivo novo. Os dispositivos Windows Phone 8,1 existentes permanecerão registrados (política, aplicativos, relatórios), mas observe que qualquer solução de problemas de um registro existente não terá suporte após essa data, pois muitos componentes, como certificados de terceiros, já terminaram o suporte para o plataforma. O Intune irá parar o teste de compatibilidade com o Intune e Windows Phone 8,1.

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>O que preciso de fazer para me preparar para esta alteração?
Você pode verificar seus relatórios do Intune para ver quais dispositivos ou usuários podem ser afetados. Aceda a Dispositivos > Todos os dispositivos e filtre por SO. Você pode adicionar colunas adicionais para ajudar a identificar quem em sua organização tem dispositivos em execução Windows Phone 8,1. Solicite que os usuários finais atualizem seus dispositivos para uma versão do sistema operacional com suporte.


### <a name="take-action-use-microsoft-edge-for-your-protected-intune-browser-experience--5728447--"></a>Agir: Use o Microsoft Edge para sua experiência de navegador do Intune protegida<!--5728447-->
Como estamos compartilhando no ano passado, o Microsoft Edge Mobile dá suporte ao mesmo conjunto de recursos de gerenciamento que o Managed Browser, oferecendo, ao mesmo tempo, uma experiência de usuário final muito aprimorada. Para ter uma forma de experiências robustas fornecidas no Microsoft Edge, iremos desativar o Intune Managed Browser. A partir de janeiro de 27, 2020, o Intune não dará mais suporte à Intune Managed Browser.  

#### <a name="how-does-this-affect-me"></a>Como é que isto me afeta? 
A partir de 1º de fevereiro de 2020, o Intune Managed Browser não estará mais disponível na Google Play Store ou na loja de aplicativos do iOS. Neste ponto, você ainda será capaz de direcionar novas políticas de proteção de aplicativo para a Intune Managed Browser, embora novos usuários não possam baixar o aplicativo Intune Managed Browser. Além disso, no iOS, novos clipes da Web que são enviados para o dispositivo inscrito no MDM serão abertos no Microsoft Edge em vez do Intune Managed Browser.  

Em março de 31 2020, a Intune Managed Browser será removida do console do Azure. Isso significa que você não poderá mais criar novas políticas para o Intune Managed Browser. Se você tiver políticas de Intune Managed Browser existentes em vigor, elas não serão afetadas. O Intune Managed Browser aparecerá no console como um aplicativo LOB sem ícone, e as políticas existentes serão mostradas como direcionadas para o aplicativo ainda. Neste ponto, também removeremos a opção de redirecionar o conteúdo da Web para o Intune Managed Browser na seção proteção de dados das políticas de proteção do aplicativo.  

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>O que preciso de fazer para me preparar para esta alteração? 
Para garantir uma transição tranqüila do Intune Managed Browser para o Microsoft Edge, recomendamos que você execute as seguintes etapas proativamente: 

1. Direcione o Microsoft Edge para iOS e Android com política de proteção de aplicativo (também conhecida como MAM) e definições de configuração de aplicativo. Você pode reutilizar suas políticas de Intune Managed Browser para o Microsoft Edge direcionando essas políticas existentes para o Microsoft Edge também.  
2. Verifique se todos os aplicativos protegidos por MAM em seu ambiente têm a configuração de política de proteção de aplicativo "restringir a transferência de conteúdo da Web com outros aplicativos" definida como "navegadores gerenciados por política". 
3. Direcione todos os MAM protegidos com a configuração de aplicativo gerenciado "com. Microsoft. Intune. useEdge" definida como true. A partir do próximo mês com o lançamento do 1911, você poderá realizar as etapas 2 e 3 simplesmente definindo a configuração "restringir a transferência de conteúdo da Web com outros aplicativos" para que o "Microsoft Edge" seja selecionado na seção proteção de dados de suas políticas de proteção de aplicativo . 

O suporte para clipes da Web no iOS e no Android está chegando. Quando esse suporte for lançado, você precisará redirecionar os clipes da Web pré-existentes para garantir que eles sejam abertos no Microsoft Edge em vez da Managed Browser. 

#### <a name="additional-information"></a>Informações adicionais
Visite nossos documentos sobre como [usar o Microsoft Edge com políticas de proteção de aplicativo](../apps/manage-microsoft-edge.md) para obter mais informações ou veja nossa [postagem no blog de suporte](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Use-Microsoft-Edge-for-your-Protected-Intune-Browser-Experience/ba-p/1004269).

### <a name="plan-for-change-updated-experience-when-enrolling-android-enterprise-dedicated-devices-in-intune--5198878--"></a>Planejar alterações: experiência atualizada ao registrar dispositivos Android Enterprise dedicados no Intune<!--5198878-->
Com a versão de novembro ou 1911 do Intune, estamos adicionando suporte para implantação de certificado de dispositivo SCEP em dispositivos Android Enterprise dedicados para habilitar o acesso baseado em certificado a perfis de Wi-Fi. Essa alteração também envolve algumas alterações secundárias no fluxo ao registrar dispositivos Android Enterprise dedicados.

#### <a name="how-does-this-affect-me"></a>Como é que isto me afeta?
Se você gerenciar dispositivos Android Enterprise dedicados em seu ambiente, você começará a ver algumas alterações distribuídas em novembro.

- Para novos registros de dispositivo do Android Enterprise dedicado: os usuários finais verão um conjunto diferente de etapas nos dispositivos durante o registro. O registro ainda será iniciado da maneira como faz hoje (com QR, NFC, Zero-Touch ou identificador de dispositivo), mas após a versão de novembro do serviço, haverá uma etapa de instalação de aplicativo obrigatória.
- Para dispositivos Android existentes registrados como dispositivos dedicados: o Intune começará a instalar automaticamente o aplicativo Microsoft Intune nos dispositivos, começando no início de novembro. Você não precisa realizar nenhuma ação. O aplicativo será baixado e instalado automaticamente em dispositivos. 

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>O que posso fazer para me preparar para esta alteração?
Você deve planejar a atualização das diretrizes do usuário final e permitir que sua assistência técnica conheça essa alteração. Clique em informações adicionais para obter mais detalhes e capturas de tela. Atualizaremos a página de novidades quando essa alteração começar a ser distribuída.

#### <a name="additional-information"></a>Informações adicionais
[https://aka.ms/Dedicated_devices_enrollment](https://aka.ms/Dedicated_devices_enrollment)

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
- Para todos os dispositivos que executam o Android 10 e posterior, o Google restringiu a capacidade para que os agentes de gerenciamento de administrador de dispositivos, como Portal da Empresa, acessem informações de identificador de dispositivo. Essa restrição afeta os seguintes recursos do Intune após uma atualização do dispositivo para Android 10 ou posterior:  
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
- Migre os dispositivos gerenciados de cliente de software do Intune herdados existentes para a solução recomendada pela Microsoft para gerenciar o Windows 10 usando o gerenciamento de MDM. Registre todos os novos computadores Windows 10 usando o gerenciamento de MDM para Intune no portal do Azure.

Consulte a [postagem do blog aqui](https://aka.ms/Windows7_Intune) para obter mais informações.



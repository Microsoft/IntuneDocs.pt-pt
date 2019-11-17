---
title: incluir ficheiro
description: incluir ficheiro
author: ErikjeMS
ms.service: microsoft-intune
ms.topic: include
ms.date: 11/4/2019
ms.author: erikje
ms.custom: include file
ms.openlocfilehash: 3d49d31ed08683508d3d231521e578688dd21bac
ms.sourcegitcommit: 737ad6c675deedfc6009f792023ff95981b06582
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/15/2019
ms.locfileid: "74125571"
---
Esses avisos fornecem informações importantes que podem ajudá-lo a se preparar para futuras alterações e recursos do Intune.

### <a name="intune-plan-for-change-windows-10-version-1703-company-portal-moving-out-of-support--5026679--"></a>Plano do Intune para alteração: Windows 10, versão 1703 Portal da Empresa saindo do suporte<!--5026679-->
O Windows 10, versão 1703 (também conhecido como Windows 10, RS2) foi movido para fora do serviço em 8 de outubro de 2019 para as edições Enterprise e EDU. O Intune terminará o suporte para o aplicativo de Portal da Empresa correspondente para RS2/RS1 a partir de 26 de dezembro de 2019.

#### <a name="how-does-this-affect-me"></a>Como é que isto me afeta?
Adiante, você não verá novos recursos na versão específica do aplicativo Portal da Empresa, embora possamos continuar a dar suporte a essa versão do aplicativo Portal da Empresa até 26 de dezembro de 2019, incluindo fornecer quaisquer atualizações de segurança para o aplicativo Portal da Empresa como precisa. No entanto, como o Windows 10, a versão 1703 não receberá nenhuma atualização de segurança depois de sair da manutenção, é altamente recomendável que você atualize seus dispositivos Windows para uma versão mais recente do Windows e verifique se você está no aplicativo Portal da Empresa mais recente para continuar a obter novos recursos e funcionalidades adicionais.

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>O que preciso de fazer para me preparar para esta alteração?
As etapas executadas dependem de como seu ambiente está configurado. No entanto, em geral, você deve identificar os dispositivos que têm a versão mais antiga do sistema operacional e/ou o Portal da Empresa em seu dispositivo e atualizar. Para definir os anéis de atualização do Windows 10, faça logon no Intune – > de atualizações de software – anéis de atualização do Windows 10. A versão mais recente do Portal da Empresa é a versão 10.3.5601.0. Direcione seus usuários para adquiri-lo do Microsoft Store para se manter atualizado com versões futuras. Você também pode usar o Intune para instalar a versão mais recente em seus dispositivos Windows por meio do [Microsoft Store for Business](https://docs.microsoft.com/intune/windows-store-for-business).

#### <a name="additional-information"></a>Informações adicionais
[Adicionar manualmente a aplicação Portal da Empresa do Windows 10 através do Microsoft Intune](https://docs.microsoft.com/intune/store-apps-company-portal-app)


### <a name="take-action-use-microsoft-edge-for-your-protected-intune-browser-experience--5728447--"></a>Agir: Use o Microsoft Edge para sua experiência de navegador do Intune protegida<!--5728447-->
Como estamos compartilhando no ano passado, o Microsoft Edge Mobile dá suporte ao mesmo conjunto de recursos de gerenciamento que o Managed Browser, oferecendo, ao mesmo tempo, uma experiência de usuário final muito aprimorada. Para ter uma forma de experiências robustas fornecidas no Microsoft Edge, iremos desativar o Intune Managed Browser. A partir de janeiro de 27, 2020, o Intune não dará mais suporte à Intune Managed Browser.  

#### <a name="how-does-this-affect-me"></a>Como é que isto me afeta? 
A partir de 1º de fevereiro de 2020, o Intune Managed Browser não estará mais disponível na Google Play Store ou na loja de aplicativos do iOS. Neste ponto, você ainda será capaz de direcionar novas políticas de proteção de aplicativo para a Intune Managed Browser, embora novos usuários não possam baixar o aplicativo Intune Managed Browser. Além disso, no iOS, novos clipes da Web que são enviados para o dispositivo inscrito no MDM serão abertos no Microsoft Edge em vez do Intune Managed Browser.  

Em março de 31 2020, a Intune Managed Browser será removida do console do Azure. Isso significa que você não poderá mais criar novas políticas para o Intune Managed Browser. Se você tiver políticas de Intune Managed Browser existentes em vigor, elas não serão afetadas. O Intune Managed Browser aparecerá no console como um aplicativo LOB sem ícone, e as políticas existentes serão mostradas como direcionadas para o aplicativo ainda. Neste ponto, também removeremos a opção de redirecionar o conteúdo da Web para o Intune Managed Browser na seção proteção de dados das políticas de proteção do aplicativo.  

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>O que preciso de fazer para me preparar para esta alteração? 
Para garantir uma transição tranqüila do Intune Managed Browser para o Microsoft Edge, recomendamos que você execute as seguintes etapas proativamente: 

1. Direcione o Microsoft Edge para iOS e Android com política de proteção de aplicativo (também conhecida como MAM) e definições de configuração de aplicativo. Você pode reutilizar suas políticas de Intune Managed Browser para o Microsoft Edge simplesmente direcionando as políticas existentes para o Microsoft Edge.  
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

### <a name="plan-for-change-the-server-side-logging-for-siri-commands-setting-will-be-removed-from-the-intune-console----5468501--"></a>Plano para alteração: a configuração "log do lado do servidor para comandos Siri" será removida do console do Intune <!-- 5468501-->

Planejamos remover a configuração "log do lado do servidor para comandos Siri" no console do Intune com a atualização de novembro para o serviço do Intune. Essa alteração se alinha com a Apple já ter removido a configuração no lado deles.

#### <a name="how-does-this-affect-me"></a>Como é que isto me afeta?
Quando a atualização de novembro ou 1911 for acumulada em meados de novembro, você verá que essa configuração foi removida do menu restrições de dispositivo (aplicativos internos) para perfis de configuração do iOS, no console do Intune. Ele pode aparecer em suas políticas e no perfil de gerenciamento do dispositivo de destino, mas a configuração não tem nenhum efeito em seu dispositivo. Não prevemos muito impacto na funcionalidade, pois ela atualmente não funciona em dispositivos, mesmo que você o veja no perfil de gerenciamento.

Você pode escolher um dos dois caminhos:
- Se você quiser excluir essa configuração de suas políticas, poderá ir para o perfil que tem essa configuração, fazer uma pequena edição e salvar a política. A política será recomputada no back-end e a configuração será excluída da sua política.
- Se você optar por não realizar essa ação, os usuários finais verão essa configuração no perfil de gerenciamento do dispositivo, mas a configuração não terá nenhum efeito.

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>O que posso fazer para me preparar para esta alteração?
Você pode tomar medidas de acordo com a seção acima ou deixar a política como está. Atualizaremos nossa página de novidades e a documentação quando essa alteração for distribuída.

### <a name="end-of-support-for-legacy-pc-management"></a>Fim do suporte para o gerenciamento de PC herdado

O gerenciamento de computadores herdados está ficando sem suporte em 15 de outubro de 2020. Atualize os dispositivos para o Windows 10 e registre-os novamente como dispositivos MDM para mantê-los gerenciados pelo Intune.

[Saiba mais](https://go.microsoft.com/fwlink/?linkid=2107122)

### <a name="decreasing-support-for-android-device-administrator"></a>Diminuindo o suporte para o administrador do dispositivo Android 
O administrador do dispositivo Android (às vezes chamado de gerenciamento do Android "herdado" e lançado com o Android 2,2) é uma maneira de gerenciar dispositivos Android. No entanto, a funcionalidade de gerenciamento aprimorada agora está disponível com o [Android Enterprise](../enrollment/connect-intune-android-enterprise.md) (lançado com Android 5,0). Em um esforço para migrar para o gerenciamento de dispositivos moderno, mais avançado e seguro, o Google está diminuindo o suporte ao administrador de dispositivos em novas versões do Android.

#### <a name="how-does-this-affect-me"></a>Como é que isto me afeta?
Devido a essas alterações feitas pelo Google, os usuários do Intune serão afetados das seguintes maneiras:  
- O Intune só poderá fornecer suporte para dispositivos Android gerenciados pelo administrador do dispositivo que executam o Android 10 e posterior (também conhecido como Android Q) durante o verão de 2020. Essa data é quando espera-se que a próxima versão principal do Android seja lançada.   
- Dispositivos gerenciados pelo administrador do dispositivo que executam o Android 10 ou posterior após o verão de 2020 não poderão ser totalmente gerenciados.       
- Os dispositivos Android gerenciados pelo administrador do dispositivo que permanecem em versões do Android abaixo do Android 10 não serão afetados e poderão continuar sendo totalmente gerenciados com o administrador do dispositivo.    
- Para todos os dispositivos que executam o Android 10 e posterior, o Google restringiu a capacidade para que os agentes de gerenciamento de administrador de dispositivos, como Portal da Empresa, acessem informações de identificador de dispositivo. Isso afeta os seguintes recursos do Intune após uma atualização do dispositivo para o Android 10 ou posterior:  
    - O controle de acesso à rede para VPN não funcionará mais.   
    - Identificar dispositivos como corporativos com um IMEI ou um número de série não marcará automaticamente os dispositivos como corporativos.  
    - O IMEI e o número de série não estarão mais visíveis para os administradores de ti no Intune. 
        > [!NOTE]
        > Isso afeta somente dispositivos gerenciados pelo administrador do dispositivo no Android 10 e posterior e não afeta os dispositivos gerenciados como Android Enterprise. 

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>O que preciso de fazer para me preparar para esta alteração?
Para evitar a redução na funcionalidade que entra no Verão de 2020, recomendamos o seguinte:
- Não integre novos dispositivos ao gerenciamento de administradores de dispositivos.
- Se for esperado que um dispositivo receba uma atualização para o Android 10, migre-o do gerenciamento de administradores de dispositivos para o gerenciamento do Android Enterprise e/ou políticas de proteção de aplicativo.

#### <a name="additional-information"></a>Informações adicionais
- [Diretrizes do Google para migração do administrador do dispositivo para Android Enterprise](http://static.googleusercontent.com/media/android.com/en/enterprise/static/2016/pdfs/enterprise/Android-Enterprise-Migration-Bluebook_2019.pdf)
- [Documentação do Google no plano para substituir a API de administrador do dispositivo](https://developers.google.com/android/work/device-admin-deprecation)

### <a name="update-your-android-company-portal-app-to-the-latest-version---4536963--"></a>Atualizar seu aplicativo Portal da Empresa Android para a versão mais recente <!--4536963-->
Periodicamente, o Intune lança atualizações para o aplicativo Android Portal da Empresa. Em novembro de 2018, lançamos uma atualização do portal da empresa, que incluía um comutador de back-end para se preparar para a mudança do Google de sua plataforma de notificação existente para o FCM (firebase Cloud Messaging) do Google. Quando o Google reabrir sua plataforma de notificação existente e mudar para FCM, os usuários finais precisarão ter atualizado seus Portal da Empresa aplicativo para pelo menos a versão de novembro de 2018 para continuar a se comunicar com o repositório de Google Play.

#### <a name="how-does-this-affect-me"></a>Como é que isto me afeta?
Nossa telemetria indica que você tem dispositivos com uma versão Portal da Empresa anterior a 5.0.4269.0. Se esta versão ou posterior do Portal da Empresa aplicativo não estiver instalada, as ações de dispositivo iniciadas por profissionais de ti, como apagar, Redefinir senha, instalações de aplicativos disponíveis e necessárias, e o registro de certificado poderão não funcionar conforme o esperado. Se seus dispositivos forem registrados no MDM no Intune, você poderá ver as Portal da Empresa versões e os usuários acessando aplicativos cliente – aplicativos descobertos. A seleção de versões anteriores do aplicativo Portal da Empresa permitirá que você veja quais usuários finais têm os dispositivos que não atualizaram o aplicativo Portal da Empresa.

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>O que preciso de fazer para me preparar para esta alteração?
Pergunte aos usuários finais de dispositivos Android que não foram atualizados para atualizar o aplicativo Portal da Empresa por meio de Google Play. Notifique seu suporte técnico caso um usuário não tenha mantido a atualização automática do aplicativo Portal da Empresa. Consulte o link em *informações adicionais* para saber mais sobre a plataforma FCM do Google e alterar.

#### <a name="additional-information"></a>Informações adicionais
https://firebase.google.com/docs/cloud-messaging/


### <a name="new-full-screen-experience-coming-to-intune---4593669--"></a>Nova experiência de tela inteira chegando ao Intune <!--4593669-->
Estamos implantando as experiências de criação e edição da interface do usuário no Intune no portal do Azure. Essa nova experiência simplificará os fluxos de trabalho existentes usando um formato de estilo de assistente condensado em uma folha. Essa atualização será desfeita com a "redução da folha" ou qualquer fluxo de criação e edição que exija a busca detalhada em jornadas de folha profundas. Os fluxos de trabalho de criação também serão atualizados para incluir atribuições (exceto para atribuição de aplicativo).

#### <a name="how-does-this-affect-me"></a>Como é que isto me afeta?
A experiência de tela inteira será distribuída para o Intune em portal.azure.com e devicemanagement.microsoft.com nos próximos meses. Essa atualização para a interface do usuário não afetará a funcionalidade de suas políticas e perfis existentes, mas você verá um fluxo de trabalho ligeiramente modificado. Ao criar novas políticas, por exemplo, você poderá definir algumas atribuições como parte desse fluxo, em vez de fazer isso depois de criar a política. Consulte a postagem no blog em *informações adicionais* para obter capturas de tela sobre a aparência da nova experiência no console.

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>O que posso fazer para me preparar para esta alteração?
Você não precisa realizar nenhuma ação, mas pode considerar atualizar suas diretrizes de ti-pro, se necessário. Atualizaremos nossa documentação à medida que essa experiência é distribuída para várias folhas no Intune no portal do Azure.

#### <a name="additional-information"></a>Informações adicionais 
https://aka.ms/intune_fullscreen

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

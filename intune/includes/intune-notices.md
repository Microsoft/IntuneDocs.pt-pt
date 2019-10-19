---
title: incluir ficheiro
description: incluir ficheiro
author: ErikjeMS
ms.service: microsoft-intune
ms.topic: include
ms.date: 03/28/2019
ms.author: erikje
ms.custom: include file
ms.openlocfilehash: 5ebab881a524bc361e271856b6762776974cea20
ms.sourcegitcommit: 5807f4db4a45a093ce2fd6cb0c480bec384ec1ff
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72601542"
---
Esses avisos fornecem informações importantes que podem ajudá-lo a se preparar para futuras alterações e recursos do Intune.

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


### <a name="plan-for-change-intune-app-sdk-and-app-protection-policies-for-android-moving-to-support-android-50-and-higher-in-october---4911065---"></a>Plano para alteração: SDK de aplicativo do Intune e políticas de proteção do aplicativo para Android migrando para dar suporte ao Android 5,0 e superior em outubro <!--4911065 -->
O Intune mudará para oferecer suporte a Android 5. x (pirulito) e superior em outubro. Atualize todos os aplicativos encapsulados com o SDK de aplicativos do Intune mais recente e atualize seus dispositivos.

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

### <a name="intune-plan-for-change-nearing-end-of-support-for-windows-7----3042987---"></a>Plano do Intune para alteração: próximo ao fim do suporte para o Windows 7 <!-- 3042987 -->
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

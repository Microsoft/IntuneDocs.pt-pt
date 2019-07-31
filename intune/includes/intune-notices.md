---
title: incluir ficheiro
description: incluir ficheiro
author: ErikjeMS
ms.service: microsoft-intune
ms.topic: include
ms.date: 03/28/2019
ms.author: erikje
ms.custom: include file
ms.openlocfilehash: 4423e731bc1538cd2454de32f0d50f2d08eedc69
ms.sourcegitcommit: 99b74d7849fbfc8f5cf99cba33e858eeb9f537aa
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/31/2019
ms.locfileid: "68670941"
---
Esses avisos fornecem informações importantes que podem ajudá-lo a se preparar para futuras alterações e recursos do Intune. 


### <a name="decreasing-support-for-android-device-administrator"></a>Diminuindo o suporte para o administrador do dispositivo Android 
O administrador do dispositivo Android (às vezes chamado de gerenciamento do Android "herdado" e lançado com o Android 2,2) é uma maneira de gerenciar dispositivos Android. No entanto, a funcionalidade de gerenciamento aprimorada agora está disponível com o [Android Enterprise]( https://docs.microsoft.com/intune/connect-intune-android-enterprise) (lançado com Android 5,0). Em um esforço para migrar para o gerenciamento de dispositivos moderno, mais avançado e seguro, o Google está diminuindo o suporte ao administrador de dispositivos em novas versões do Android.

#### <a name="how-does-this-affect-me"></a>Como é que isto me afeta?
Devido a essas alterações feitas pelo Google, os usuários do Intune serão afetados das seguintes maneiras: 
- O Intune só poderá fornecer suporte para dispositivos Android gerenciados pelo administrador do dispositivo que executam o Android 10 e posterior (também conhecido como Android Q) até o verão de 2020. Essa data é quando espera-se que a próxima versão principal do Android seja lançada.  
- Dispositivos gerenciados pelo administrador do dispositivo que estão executando o Android 10 ou posterior após o verão 2020 não poderão ser totalmente gerenciados.    
- Os dispositivos Android gerenciados pelo administrador do dispositivo que permanecem em versões do Android abaixo do Android 10 não serão afetados e poderão continuar sendo totalmente gerenciados com o administrador do dispositivo.  
- Para todos os dispositivos Android 10 e posteriores, o Google restringiu a capacidade para que os agentes de gerenciamento de administrador de dispositivos, como Portal da Empresa, acessem informações de identificador de dispositivo. Isso afeta os seguintes recursos do Intune após uma atualização do dispositivo para o Android 10 ou posterior: 
    - O controle de acesso à rede para VPN não funcionará mais.  
    - Identificar dispositivos como corporativos com IMEI ou número de série não marcará automaticamente os dispositivos como corporativos. 
    - IMEI e número de série não estarão mais visíveis para os administradores de ti no Intune. 
        > [!Note]
        > Isso afeta somente dispositivos gerenciados pelo administrador do dispositivo no Android 10 e posterior e não afeta os dispositivos gerenciados como Android Enterprise. 

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>O que preciso de fazer para me preparar para esta alteração?
Para evitar a redução na funcionalidade que entra no verão 2020, recomendamos o seguinte:
- Não integre novos dispositivos ao gerenciamento de administradores de dispositivos.
- Se for esperado que um dispositivo receba uma atualização para o Android 10, migre-o do gerenciamento de administradores de dispositivos para o gerenciamento do Android Enterprise e/ou políticas de proteção de aplicativo.

### <a name="update-your-android-company-portal-app-to-the-latest-version---4536963--"></a>Atualizar seu aplicativo Portal da Empresa Android para a versão mais recente <!--4536963-->
Periodicamente, o Intune lança atualizações para o aplicativo Android Portal da Empresa. Em novembro de 2018, lançamos uma atualização do portal da empresa, que incluía um comutador de back-end para se preparar para a mudança do Google de sua plataforma de notificação existente para o FCM (firebase Cloud Messaging) do Google. Quando o Google reabrir sua plataforma de notificação existente e mudar para FCM, os usuários finais precisarão ter atualizado seu aplicativo do portal da empresa para pelo menos 2018 versão de novembro para continuar a se comunicar com a Google Play Store.

#### <a name="how-does-this-affect-me"></a>Como é que isto me afeta?
Nossa telemetria indica que você tem dispositivos com uma versão Portal da Empresa anterior a 5.0.4269.0. Se esta versão ou posterior do aplicativo do portal da empresa não estiver instalada, o profissional de ti iniciou ações de dispositivo como apagar, Redefinir senha, instalações de aplicativos disponíveis e necessárias e o registro de certificado pode não funcionar conforme o esperado. Se seus dispositivos forem registrados em MDM no Intune, você poderá ver as versões e os usuários do portal da empresa acessando aplicativos cliente – aplicativos descobertos. A seleção de versões anteriores do Portal da Empresa permitirá que você veja quais usuários finais têm os dispositivos que não atualizaram o portal da empresa.

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>O que preciso de fazer para me preparar para esta alteração?
Pergunte aos usuários finais de dispositivos Android que não foram atualizados para atualizar o portal da empresa por meio do Google Play. Notifique a assistência técnica caso um usuário não tenha mantido a atualização automática do aplicativo portal da empresa. Consulte o link em informações adicionais para saber mais sobre a plataforma FCM do Google e alterar.

#### <a name="additional-information"></a>Informações adicionais
https://firebase.google.com/docs/cloud-messaging/


### <a name="new-fullscreen-experience-coming-to-intune---4593669--"></a>Nova experiência de tela inteira chegando ao Intune <!--4593669-->
Estamos implantando as experiências de criação e edição da interface do usuário no Intune no portal do Azure. Essa nova experiência simplificará os fluxos de trabalho existentes usando um formato de estilo de assistente condensado dentro de uma folha. Essa atualização será desfeita com a "redução da folha" ou qualquer fluxo de criação e edição que exija a busca detalhada em jornadas de folha profundas. Os fluxos de trabalho de criação também serão atualizados para incluir atribuições (exceto para atribuição de aplicativo).

#### <a name="how-does-this-affect-me"></a>Como é que isto me afeta?
A experiência de tela inteira será distribuída para o Intune em portal.azure.com e devicemanagement.microsoft.com nos próximos meses. Essa atualização para a interface do usuário não afetará a funcionalidade de suas políticas e perfis existentes, mas você verá um fluxo de trabalho ligeiramente modificado. Ao criar novas políticas, por exemplo, você poderá definir algumas atribuições como parte desse fluxo, em vez de fazer isso depois de criar a política. Consulte a postagem no blog em informações adicionais para obter capturas de tela sobre a aparência da nova experiência no console.

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>O que posso fazer para me preparar para esta alteração?
Você não precisa realizar nenhuma ação, mas pode considerar atualizar suas diretrizes de profissional de ti, se necessário. Atualizaremos nossa documentação, pois essa experiência é distribuída para várias folhas no Intune em portal do Azure.

#### <a name="additional-information"></a>Informações adicionais 
https://aka.ms/intune_fullscreen

### <a name="plan-for-change-intune-moving-to-support-ios-11-and-higher-in-september----4665342--"></a>Planejar alteração: O Intune está mudando para dar suporte ao iOS 11 e superior em setembro <!-- 4665342-->
Em setembro, esperamos que o iOS 13 seja lançado pela Apple. O registro do Intune, o Portal da Empresa e o Managed Browser serão movidos para dar suporte ao iOS 11 e posterior logo após a liberação do iOS 13.

#### <a name="how-does-this-affect-me"></a>Como é que isto me afeta?
Contanto que os aplicativos móveis do O365 tenham suporte no iOS 11,0 e superior, isso pode não afetar você; Você provavelmente já atualizou seu sistema operacional ou dispositivos. No entanto, se você tiver qualquer um dos dispositivos listados abaixo, ou decidir registrar qualquer um dos dispositivos listados abaixo, saiba que os dispositivos abaixo não dão suporte a um sistema operacional maior do que o iOS 10. Esses dispositivos precisarão ser atualizados para um dispositivo que ofereça suporte ao iOS 11 ou superior:

- iPhone 5
- iPhone 5c
- iPad (4ª geração)

A partir de julho, os dispositivos registrados no MDM com iOS 10 e o Portal da Empresa receberão uma solicitação para atualizar seu sistema operacional ou dispositivo. Se você usar políticas de proteção de aplicativo (aplicativo), também poderá definir a configuração de acesso "exigir o sistema operacional mínimo do iOS (somente aviso)".

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>O que preciso de fazer para me preparar para esta alteração?
Verifique seus relatórios do Intune para ver quais dispositivos ou usuários podem ser afetados. Vá para **dispositivos** > **todos os dispositivos** e filtre por sistema operacional. Você pode adicionar colunas adicionais para ajudar a identificar quem em sua organização tem dispositivos que executam o iOS 10. Solicite que os usuários finais atualizem seus dispositivos para uma versão do sistema operacional com suporte antes de setembro.

### <a name="plan-for-change-support-for-version-811-and-higher-of-intune-app-sdk-for-ios----3586942--"></a>Planejar alteração: Suporte para a versão 8.1.1 e superior do SDK de aplicativo do Intune para iOS <!-- 3586942-->
A partir de setembro de 2019, o Intune será movido para dar suporte a aplicativos iOS com o SDK de aplicativos do Intune 8.1.1 e superior. Aplicativos criados com versões do SDK inferiores a 8.1.1 não terão mais suporte. Essa alteração entrará em vigor com o lançamento da Apple do iOS 13, que deve vir em volta de setembro e também ser anunciada em MC181399.

#### <a name="how-does-this-affect-me"></a>Como é que isto me afeta?
Com o SDK de aplicativo do Intune ou integração de encapsulamento de aplicativo, você pode proteger dados corporativos de aplicativos e usuários não aprovados por meio da criptografia de dados. O SDK de aplicativo do Intune para iOS usará chaves de criptografia de 256 bits por padrão quando a criptografia for habilitada por políticas de Proteção de Aplicativo do Intune (aplicativo). Após essa alteração, todos os aplicativos iOS em versões do SDK anteriores ao 8.1.1, que usam chaves de criptografia de 128 bits, não poderão mais compartilhar dados com aplicativos integrados com o SDK 8.1.1 ou usando as chaves de 256 bits. Todos os aplicativos iOS precisarão ter uma versão do SDK 8.1.1 ou superior para permitir o compartilhamento de dados protegidos.

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>O que posso fazer para me preparar para esta alteração?
Verifique seus aplicativos Microsoft, de terceiros e de linha de negócios (LOB). Verifique se todos os aplicativos protegidos com o aplicativo do Intune estão usando o SDK versão 8.1.1 ou posterior.

- Para aplicativos LOB: Talvez seja necessário republicar seus aplicativos integrados com o SDK versão 8.1.1 ou posterior. Recomendamos a versão mais recente do SDK. Para obter informações sobre como preparar seus aplicativos LOB para políticas de proteção de aplicativo, consulte [preparar aplicativos de linha de negócios para políticas de proteção de aplicativo](../apps-prepare-mobile-application-management.md).
- Para aplicativos da Microsoft/de terceiros: Certifique-se de que você está implantando a versão mais recente desses aplicativos para seus usuários.

Você também deve atualizar sua documentação ou orientação para o desenvolvedor, se aplicável, para incluir essa alteração no suporte para o SDK.

#### <a name="additional-information"></a>Informações adicionais
https://docs.microsoft.com/intune/apps-prepare-mobile-application-management

### <a name="plan-for-change-new-windows-updates-settings-in-intune----4464404---"></a>Planejar alteração: Novas configurações de atualizações do Windows no Intune <!-- 4464404 -->
A partir da versão de agosto para o serviço do Intune ou 1908, estamos adicionando novas "configurações de prazos", que podem ser configuradas em vez das configurações "permitir que o usuário reinicie (reinício envolvido)". Planejamos desabilitar as configurações de reinicialização envolvidas na interface do usuário no 1909 ou a atualização de setembro e, em seguida, removê-las completamente do console até o final de outubro. 

#### <a name="how-does-this-affect-me"></a>Como é que isto me afeta?
Se você gerenciar dispositivos Windows 10 em seu ambiente: 
- Com a atualização do Intune de agosto ou 1908, você verá novas configurações de prazo no console, além das antigas configurações de reinicialização envolvidas.
- Quando ambas as configurações antigas e novas estiverem definidas, os valores das configurações de prazo substituirão os valores de configuração de reinício envolvidos.
- As configurações de prazo substituirão a opção "permitir que o usuário reinicie (reinício envolvido) no console do na atualização 1910.

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>O que posso fazer para me preparar para esta alteração?
Comece a usar as configurações de prazo em 1908, configurando-as com os valores desejados. Depois de fazer isso, você pode definir a configuração de reinicialização envolvida como "não configurado" para se preparar para que essas configurações sejam removidas do console em outubro.

Atualize sua documentação e todos os scripts de automação, se necessário. 

Manteremos você atualizado e poste um lembrete no centro de mensagens antes de removermos as configurações de reinicialização envolvidas.

### <a name="plan-for-change-intune-app-sdk-and-app-protection-policies-for-android-moving-to-support-android-50-and-higher-in-october---4911065---"></a>Planejar alteração: Políticas do SDK de aplicativo do Intune e de proteção do aplicativo para Android migrando para o Android 5,0 e posterior em outubro <!--4911065 -->
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
Encapsular seus aplicativos com o SDK de aplicativos do Intune mais recente. Você também pode definir a configuração de inicialização condicional "exigir versão mínima do so (somente aviso)" para notificar os usuários finais sobre os dispositivos pessoais a serem atualizados.

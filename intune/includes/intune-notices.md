---
title: incluir ficheiro
description: incluir ficheiro
author: ErikjeMS
ms.service: microsoft-intune
ms.topic: include
ms.date: 11/19/2019
ms.author: erikje
ms.custom: include file
ms.openlocfilehash: 373aeea9ab4fcbd075ac2ab18f205f3ddd191a39
ms.sourcegitcommit: 29f3ba071c9348686d3ad6f3b8864d8557e05b97
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/26/2020
ms.locfileid: "77609285"
---
Estes avisos fornecem informações importantes que podem ajudá-lo a preparar-se para futuras alterações e funcionalidades intune.

### <a name="microsoft-intune-support-for-windows-10-mobile-ending--3544938--"></a>Suporte para Microsoft Intune para o final do Windows 10 Mobile<!--3544938-->
O suporte mainstream da Microsoft para o Windows 10 Mobile terminou em dezembro de 2019. Tal como referido nesta declaração de suporte, os utilizadores do Windows 10 Mobile deixarão de poder receber novas atualizações de segurança, hotfixes não de segurança, opções de suporte assistido gratuitos ou atualizações de conteúdos técnicos online da Microsoft. Com base no suporte all-up Mobile OS, o Microsoft Intune vai agora terminar o suporte tanto para o Portal da Empresa para a aplicação Móvel Windows 10 como para o Sistema Operativo Móvel Windows 10 no dia 11 de maio de 2020.

#### <a name="how-does-this-affect-me"></a>Como é que isto me afeta?
Se tiver dispositivos Windows 10 Mobile implantados na sua organização, entre hoje e 11 de maio de 2020 pode inscrever novos dispositivos, adicionar ou remover políticas e apps ou atualizar quaisquer definições de gestão. Depois de 11 de maio, vamos parar novas matrículas e, eventualmente, remover a gestão móvel do Windows 10 do Intune UI. Os dispositivos deixarão de fazer o check-in no serviço Intune e eliminaremos os dados do dispositivo e da política.  

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>O que preciso de fazer para me preparar para esta alteração?
Pode verificar o seu relatório Intune para ver quais os dispositivos ou utilizadores que podem ser afetados. Vá a **Dispositivos** > **Todos os dispositivos** e filtrar por OS. Pode adicionar colunas adicionais para ajudar a identificar quem na sua organização tem dispositivos que executam o Windows 10 Mobile. Solicite que os seus utilizadores finais atualizem os seus dispositivos ou desistam de utilizar os dispositivos para acesso corporativo.



### <a name="plan-for-change-change-in-experience-when-enrolling-android-enterprise-dedicated-devices-in-intune--6114580--"></a>Plano para mudança: Mudança de experiência ao inscrever dispositivos dedicados ao Android Enterprise em Intune<!--6114580-->
Partilhámos no lançamento de novembro que estávamos a adicionar suporte para a implementação de certificados SCEP para dispositivos dedicados ao Android Enterprise, para permitir o acesso baseado em certificados aos perfis Wi-Fi. Esta alteração envolveu algumas pequenas alterações no fluxo de matrículas para dispositivos dedicados ao Android Enterprise. Com a próxima atualização de serviço de março ou 2003, há algumas outras alterações que gostaríamos que tivesse conhecimento.

#### <a name="how-does-this-affect-me"></a>Como é que isto me afeta?
Se gere dispositivos dedicados ao Android Enterprise no seu ambiente, começará a ver algumas mudanças lançadas em março.
- Para os dispositivos dedicados ao Android existentes matriculados antes do dia 22 de novembro de 2019 ou da atualização de serviço de 1911: Estes dispositivos têm a aplicação Microsoft Intune instalada nos mesmos. Após alterações no backend lançadas no serviço Intune em março, os certificados SCEP implantados em dispositivos e associados aos perfis Wi-Fi começarão a ser aplicados.
- Para dispositivos que foram matriculados após 22 de novembro de 2019 e antes desta alteração ser lançado em março: Estes dispositivos têm a aplicação Microsoft Intune instalada nos mesmos. Os certificados SCEP implantados em dispositivos e associados aos perfis Wi-Fi continuarão a ser aplicados.
- Para novas inscrições de dispositivos android Enterprise dedicadas após a mudança ser lançada em março: Os utilizadores finais verão um conjunto diferente de passos nos dispositivos durante a inscrição. As inscrições continuarão a começar como hoje (com QR, NFC, Zero-touch ou identificador de dispositivos), mas não haverá nenhum passo obrigatório de instalação de apps. Em vez disso, a aplicação Microsoft Intune instala-se automaticamente nos dispositivos. Além disso, os utilizadores finais não precisarão de tocar em "Enable Intune Agent" durante o fluxo. Os Certificados SCEP associados aos perfis Wi-Fi podem ser implantados nestes dispositivos.

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>O que posso fazer para me preparar para esta alteração?
Pode atualizar a sua orientação final do utilizador e informar o seu helpdesk sobre esta alteração. Atualizaremos a nossa página What's New e notificá-lo-emos através do centro de mensagens quando esta alteração começar a ser lançada.

#### <a name="additional-information"></a>Informações adicionais
[Suporte para certificados SCEP em dispositivos dedicados android enterprise](https://aka.ms/Dedicated_devices_enrollment)

### <a name="updated-support-statement-for-adobe-acrobat-reader-for-intune-mobile-app--5746776--"></a>Declaração de suporte atualizada para aplicação móvel 'Adobe Acrobat Reader for Intune'<!--5746776-->
Partilhámos no MC188653, no final de agosto, que o Adobe Acrobat Reader for Intune mobile app estava a chegar ao fim de vida a 1 de dezembro de 2019 e que a Adobe planeava apoiar as políticas de proteção de aplicações da Intune dentro da sua principal aplicação Acrobat Reader. Desde então, recebemos feedback do cliente de que precisávamos de dar mais tempo para continuar a permitir que os administradores de TI se dirigissem, e os utilizadores finais começassem a usar o Adobe Acrobat Reader para intune. Dado o elevado uso do Adobe Acrobat Reader for Intune nos dispositivos de utilizador final e a sua importância nos cenários empresariais, queremos garantir que qualquer experiência satisfaça as necessidades de proteção de aplicações da sua organização. 

Embora ainda recomendamos direcionar a aplicação móvel geral do Acrobat Reader nas suas políticas, uma vez que a aplicação móvel Acrobat Reader suporta políticas de proteção de aplicações e integrou o Intune SDK, a aplicação Adobe Acrobat Reader for Intune continuará a ser suportada até 31 de março de 2020. 

#### <a name="how-does-this-affect-me"></a>Como é que isto me afeta?
Está a receber esta mensagem porque o nosso relatório indica que uma ou mais políticas na sua organização estão a visar o Leitor Adobe Acrobat para aplicação Intune e/ou pode ter recebido a nossa comunicação Anterior EOL. 

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>O que preciso de fazer para me preparar para esta alteração?
Informe os utilizadores finais e o helpdesk sobre esta mudança. Pode utilizar a funcionalidade de [informação de suporte do Portal da Empresa](../apps/company-portal-app.md#support-information) para estabelecer um canal para questões relacionadas com o Intune.

#### <a name="additional-information"></a>Informações Adicionais
https://helpx.adobe.com/acrobat/kb/intune-app-end-of-life.html


### <a name="take-action-use-microsoft-edge-for-your-protected-intune-browser-experience--5728447--"></a>Tomar medidas: Use microsoft edge para a sua experiência de navegador intune protegida<!--5728447-->
Como temos vindo a partilhar ao longo do último ano, o microsoft Edge mobile suporta o mesmo conjunto de funcionalidades de gestão que o Managed Browser, ao mesmo tempo que proporciona uma experiência de utilizador final muito melhorada. Para dar lugar às experiências robustas fornecidas no Microsoft Edge, vamos retirar o Navegador Gerido Intune. A partir de 27 de janeiro de 2020, a Intune deixará de suportar o Navegador Gerido Intune.  

#### <a name="how-does-this-affect-me"></a>Como é que isto me afeta? 
A partir de 1 de fevereiro de 2020, o Navegador Gerido Intune deixará de estar disponível na Google Play Store ou na App Store iOS. Neste momento, ainda será possível direcionar novas políticas de proteção de aplicações para o Navegador Gerido Intune, embora os novos utilizadores não consigam descarregar a aplicação Intune Managed Browser. Além disso, no iOS, novos clips web que são empurrados para baixo para dispositivo sinuoso serão abertos no Microsoft Edge em vez do Navegador Gerido Intune.  

No dia 31 de março de 2020, o Navegador Gerido Intune será removido da consola Azure. Isto significa que já não será capaz de criar novas políticas para o Navegador Gerido intune. Se tiver as políticas existentes do Navegador Gerido intune em vigor, não serão afetadas. O Intune Managed Browser aparecerá na consola como uma aplicação LOB sem ícone, e as políticas existentes mostrarão como direcionados para a app ainda. Neste ponto, também removeremos a opção de redirecionar conteúdo web para o Navegador Gerido Intune dentro da secção de Proteção de Dados das políticas de proteção de Aplicações.  

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>O que preciso de fazer para me preparar para esta alteração? 
Para garantir uma transição suave do Navegador Gerido Intune para o Microsoft Edge, recomendamos que tome os seguintes passos de forma proativa: 

1. Target Microsoft Edge para iOS e Android com política de proteção de aplicações (também referida como MAM) e definições de config de aplicações. Pode reutilizar as suas políticas de Navegador Geridos Intune para o Microsoft Edge, direcionando também as políticas existentes para o Microsoft Edge.  
2. Certifique-se de que todas as aplicações protegidas pelo MAM no seu ambiente têm a definição de política de proteção de aplicações "Restringir a transferência de conteúdos web com outras aplicações" definida para "Navegadores geridos pela política". 
3. Direcione todos os MAM protegidos com a configuração de configuração de aplicação gerida "com.microsoft.intune.useEdge" definida como verdadeira. A partir do próximo mês com o lançamento de 1911, poderá realizar os passos 2 e 3 simplesmente configurando a definição de "Restringir a transferência de conteúdos web com outras aplicações" para ter "Microsoft Edge" selecionado na secção de Proteção de Dados das suas políticas de proteção de aplicações . 

Está a chegar suporte para web clips no iOS e Android. Quando este suporte for lançado, terá de redirecionar os web clips pré-existentes para garantir que se abrem no Microsoft Edge em vez do Navegador Gerido. 

#### <a name="additional-information"></a>Informações adicionais
Visite os nossos médicos ao utilizar o Microsoft Edge com políticas de [proteção de aplicações](../apps/manage-microsoft-edge.md) para mais informações, ou veja o nosso post de blog de [suporte](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Use-Microsoft-Edge-for-your-Protected-Intune-Browser-Experience/ba-p/1004269).


### <a name="end-of-support-for-legacy-pc-management"></a>Fim do apoio à gestão do PC legado

A gestão do LEGACY PC vai sair do apoio no dia 15 de outubro de 2020. Atualize os dispositivos para o Windows 10 e reinscreva-os como dispositivos de Gestão de Dispositivos Móveis (MDM) para mantê-los geridos pela Intune.

[Saiba mais](https://go.microsoft.com/fwlink/?linkid=2107122)

### <a name="decreasing-support-for-android-device-administrator--5857738--"></a>Diminuição do suporte para administrador de dispositivos Android<!--5857738-->
O administrador de dispositivos Android (por vezes referido para a gestão "legacy" android e lançado com o Android 2.2) é uma forma de gerir dispositivos Android. No entanto, a melhoria da funcionalidade de gestão já está disponível com [o Android Enterprise](../enrollment/connect-intune-android-enterprise.md) (lançado com o Android 5.0). Num esforço para se mudar para uma gestão moderna, mais rica e segura de dispositivos, a Google está a diminuir o suporte do administrador de dispositivos em novas versões Android.

#### <a name="how-does-this-affect-me"></a>Como é que isto me afeta?
Devido a estas alterações por parte da Google, os utilizadores intune serão impactados das seguintes formas:  
- A Intune só poderá fornecer suporte total para dispositivos Android geridos por administradorde dispositivos que executam o Android 10 e, posteriormente, através do Q2 CY2020. Os dispositivos geridos pelo administrador do dispositivo que estão a executar o Android 10 ou mais tarde depois desta altura não poderão ser totalmente geridos. Em particular, os dispositivos com impacto não receberão novos requisitos de senha.
    - Os dispositivos Samsung Knox não serão impactados neste prazo porque o suporte alargado é fornecido através da integração de Intune com a plataforma Knox. Isto dá-lhe mais tempo para planear a transição para fora da gestão de administração do dispositivo.    
- Os dispositivos Android geridos por administrador de dispositivos que permaneçam em versões Android abaixo do Android 10 não serão afetados e podem continuar a ser totalmente geridos com o administrador do dispositivo.    
- Para todos os dispositivos que executam o Android 10 e posteriormente, a Google restringiu a capacidade de agentes de gestão de administradores de dispositivos como o Portal da Empresa acederem à informação de identificador de dispositivos. Esta restrição afeta as seguintes funcionalidades Intune depois de um dispositivo ser atualizado para o Android 10 ou posteriormente:  
    - O controlo de acesso à rede para VPN deixará de funcionar.   
    - Identificar dispositivos como propriedade corporativa com um IMEI ou um número de série não marcará automaticamente os dispositivos como propriedade corporativa.  
    - O IMEI e o número de série deixarão de ser visíveis aos administradores de TI em Intune. 
        > [!NOTE]
        > Isto só afeta dispositivos geridos por administradores de dispositivos no Android 10 e posteriormente e não afeta dispositivos que estão a ser geridos como Android Enterprise. 

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>O que preciso de fazer para me preparar para esta alteração?
Para evitar a redução da funcionalidade que chega no 3º trimestre CY2020, recomendamos o seguinte:
- Não embarque em novos dispositivos na gestão de administrador de dispositivos.
- Se se espera que um dispositivo receba uma atualização para o Android 10, emigra-o da gestão do administrador do dispositivo para as políticas de gestão e/ou proteção de aplicações do Android Enterprise.

#### <a name="additional-information"></a>Informações adicionais
- [Orientação da Google para a migração de administrador de dispositivos para Android Enterprise](http://static.googleusercontent.com/media/android.com/en/enterprise/static/2016/pdfs/enterprise/Android-Enterprise-Migration-Bluebook_2019.pdf)
- [Documentação da Google sobre o plano para depreciar o administrador do dispositivo API](https://developers.google.com/android/work/device-admin-deprecation)




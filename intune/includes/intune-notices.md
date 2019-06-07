---
title: incluir ficheiro
description: incluir ficheiro
author: ErikjeMS
ms.service: microsoft-intune
ms.topic: include
ms.date: 03/28/2019
ms.author: erikje
ms.custom: include file
ms.openlocfilehash: fab8f2be48a30f6ad058b3eeb6874a44ff04e6ac
ms.sourcegitcommit: 7ceae61e036ccf8b33704751b0b39fee81944072
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/06/2019
ms.locfileid: "66744294"
---
Estes avisos fornecem importante de informações que podem ajudá-lo a se preparar para as funcionalidades e alterações futuras do Intune. 

### <a name="update-your-android-company-portal-app-to-the-latest-version---4536963--"></a>Atualizar a sua aplicação do Portal da empresa para Android para a versão mais recente <!--4536963-->
Intune periodicamente lança atualizações para a aplicação Android do Portal da empresa. Em Novembro de 2018, lançámos uma atualização do portal da empresa, que incluía um comutador de back-end para preparar a alteração da Google da sua plataforma de notificação existente da Google Firebase Cloud Messaging (FCM). Quando Google retira existente da plataforma de notificação e move-o para o FCM, final, os utilizadores terão de atualizaram a sua aplicação do portal da empresa para, pelo menos, Novembro de 2018 versão continue se comunicando com a Google play store.

#### <a name="how-does-this-affect-me"></a>Como é que isto me afeta?
Nosso telemetria indica que tiver dispositivos com uma versão anterior ao 5.0.4269.0 de Portal da empresa. Se esta versão ou posterior da aplicação portal da empresa não está instalado, ações de dispositivo iniciada profissionais de IT, como apagar, repor palavra-passe, as aplicações disponíveis e necessárias instala e inscrição de certificados pode não funcionar conforme esperado. Se os dispositivos estiverem inscritos no Intune na MDM, em seguida, pode ver as versões de portal da empresa e os utilizadores ao aceder a aplicações de cliente – aplicações detetadas. Selecionar as versões anteriores do Portal da empresa permitirá que veja quais os utilizadores finais têm os dispositivos que não tiver atualizado o portal da empresa.

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>O que preciso de fazer para me preparar para esta alteração?
Pedir os utilizadores finais de dispositivos Android que não tenham sido atualizados para atualizar o portal da empresa através do Google play. Notifique o suporte técnico, no caso de um utilizador não tem mantidos atualização automática da aplicação portal da empresa. Veja o link no informações adicionais para a plataforma FCM mais diante da Google e alterar.

#### <a name="additional-information"></a>Informações adicionais
https://firebase.google.com/docs/cloud-messaging/


### <a name="new-fullscreen-experience-coming-to-intune---4593669--"></a>Nova experiência de ecrã inteiro para o Intune <!--4593669-->
Estamos a implementar atualizados criar e editar as experiências de interface do Usuário para o Intune no portal do Azure. Esta nova experiência irá simplificar os fluxos de trabalho existentes, utilizando um formato de estilo de assistente condensado dentro de um painel. Esta atualização será fazer distância com "expansão de painel" ou qualquer criar e editar fluxos que requerem a desagregar Jornadas painel profunda. Os fluxos de trabalho de criar também serão atualizados para incluir atribuições (exceto para a atribuição de aplicações).

#### <a name="how-does-this-affect-me"></a>Como é que isto me afeta?
A experiência de ecrã inteiro será implementada ao Intune na portal.azure.com e devicemanagement.microsoft.com durante os próximos meses. Esta atualização para a interface do Usuário não irá afetar a funcionalidade de seus perfis e as políticas existentes, mas verá um fluxo de trabalho ligeiramente modificado. Ao criar novas políticas, por exemplo, será capaz de definir algumas atribuições de como parte deste fluxo, em vez de fazê-lo Depois de criar a política. Consulte o postagem no blog em informações adicionais de capturas de ecrã de aparência a nova experiência na consola do.

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>O que posso fazer para me preparar para esta alteração?
Não é necessário efetuar qualquer ação, mas pode considerar a atualizar a sua documentação de orientação de profissionais de IT, se necessário. Iremos atualizar nossa documentação como esta experiência for implementada para os vários painéis no Intune no portal do Azure.

#### <a name="additional-information"></a>Informações adicionais 
https://aka.ms/intune_fullscreen

### <a name="plan-for-change-intune-moving-to-support-ios-11-and-higher-in-september----4665342--"></a>Planear a alteração: Intune mover para suportar o iOS 11 e versões posteriores em Setembro <!-- 4665342-->
Em Setembro, podemos esperar iOS 13 que será lançado pela Apple. Inscrição no Intune, o Portal da empresa e o Managed Browser serão movido para suportar o iOS 11 e versões posteriores logo após a versão do iOS 13.

#### <a name="how-does-this-affect-me"></a>Como é que isto me afeta?
Desde que as aplicações móveis do Office 365 são suportadas no iOS 11.0 e superior, esta poderá não o afetará, provavelmente já atualizou o sistema operacional ou dispositivos. No entanto, se tiver todos os dispositivos listados abaixo, ou optar por inscrever todos os dispositivos listados abaixo, sabe que os dispositivos abaixo não suportam um SO maior que o iOS 10. Estes dispositivos têm de ser atualizado para um dispositivo que suporta o iOS 11 ou superior:

- iPhone 5
- iPhone 5c
- iPad (geração 4)

A partir de Julho, MDM inscrito dispositivos com iOS 10 e o Portal da empresa irá receber um pedido para atualizar o respetivo SO ou o dispositivo. Se utilizar políticas de proteção de aplicações (aplicação) também pode definir o definição de acesso "Exigir sistema operativo iOS mínimo (aviso apenas)".

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>O que preciso de fazer para me preparar para esta alteração?
Verifique o Intune relatórios para ver que utilizadores ou dispositivos que podem ser afetados. Aceda a **dispositivos** > **todos os dispositivos** e filtrar por SO. Pode adicionar colunas adicionais para ajudar a identificar quem na sua organização tiver dispositivos com iOS 10. Solicite que os utilizadores finais atualizarem os seus dispositivos para uma versão de SO suportada antes de Setembro.

### <a name="plan-for-change-support-for-version-811-and-higher-of-intune-app-sdk-for-ios----3586942--"></a>Planear a alteração: Suporte para versão 8.1.1 e versões posteriores do SDK da aplicação Intune para iOS <!-- 3586942-->
A partir de Setembro de 2019, Intune será movido para suportar aplicações iOS com o SDK da aplicação Intune 8.1.1 e superior. Aplicativos criados com versões do SDK inferior 8.1.1 já não ser suportados. Esta alteração irá entrar em vigor com o lançamento da Apple do iOS 13, que é esperado para Setembro são lançados e também foi anunciado em MC181399.

#### <a name="how-does-this-affect-me"></a>Como é que isto me afeta?
Com a integração do SDK da aplicação do Intune ou ao encapsular a aplicação, pode proteger dados empresariais de aplicações não aprovadas e usuários através de encriptação de dados. O SDK da aplicação Intune para iOS irá utilizar as chaves de encriptação de 256 bits por predefinição, quando a encriptação está ativada por políticas de proteção de aplicação do Intune (aplicações). Após esta alteração, todas as aplicações iOS em versões SDK antes 8.1.1, o que utilizam chaves de encriptação de 128 bits, já não será capazes de partilhar dados com aplicações integrada com SDK 8.1.1 ou utilizando as chaves de 256 bits. Todas as aplicações de iOS tem de ter um SDK versão 8.1.1 ou protegidos superior para permitir a partilha de dados.

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>O que posso fazer para me preparar para esta alteração?
Verifique as suas Microsoft, terceiros e de linha de negócio (LOB) aplicações. Deve garantir a tudo o que todas as suas aplicações protegidas com a aplicação do Intune estão a utilizar o SDK versão 8.1.1 ou posterior.

- Para aplicações LOB: Terá de voltar a publicar as suas aplicações integradas com a versão SDK 8.1.1 ou posteriores. Recomendamos que a versão mais recente do SDK. Para mais informações sobre como preparar as suas aplicações LOB para políticas de proteção de aplicações, consulte [preparar as aplicações de linha de negócio para políticas de proteção de aplicações](../apps-prepare-mobile-application-management.md).
- Para a Microsoft/terceiros aplicações: Certifique-se de que está a implementar a versão mais recente destas aplicações aos seus utilizadores.

Também deve atualizar as diretrizes de desenvolvedor ou documentação, se aplicável para incluir esta alteração no suporte para o SDK.

#### <a name="additional-information"></a>Informações adicionais
https://docs.microsoft.com/intune/apps-prepare-mobile-application-management

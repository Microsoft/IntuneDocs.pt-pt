---
title: incluir ficheiro
description: incluir ficheiro
author: ErikjeMS
ms.service: microsoft-intune
ms.topic: include
ms.date: 03/28/2019
ms.author: erikje
ms.custom: include file
ms.openlocfilehash: ffcef5b4d78856709f8563ee1f667ec7e5d993b3
ms.sourcegitcommit: d2e04a38e024b0f5afb0ca202823227de9da3ad1
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/09/2019
ms.locfileid: "65732618"
---
Estes avisos fornecem importante de informações que podem ajudá-lo a se preparar para as funcionalidades e alterações futuras do Intune. 

### <a name="change-in-enrollment-workflow-with-intune-company-portal-on-corporate-ios-devices-authenticating-with-setup-assistant----1927359---"></a>Alterar inscrição fluxo de trabalho com o Portal da empresa do Intune em dispositivos iOS empresariais, a autenticação com o Assistente de configuração <!-- 1927359 -->
Há uma futura alteração ao fluxo de trabalho para a inscrição de dispositivos iOS através de um dos dispositivo da empresa métodos de inscrição da Apple - Apple Configurator, gerente de negócios da Apple, Apple School Manager ou o Apple dispositivo programa de inscrição (DEP), ao utilizar o programa de configuração Assistente para a autenticação. Esta alteração aplica-se apenas a dispositivos inscritos com afinidade do utilizador.

#### <a name="how-does-this-affect-me"></a>Como é que isto me afeta?
Quando esta alteração é implementada, perfis de inscrição no Intune no portal do Azure serão atualizados para que pode especificar a forma como os dispositivos serão autenticados e se eles recebem a aplicação Portal da empresa. Haverá um fluxo de trabalho melhorado para inscrever dispositivos iOS através dos métodos indicados acima. 

- Quando inscrever novos dispositivos e a autenticação com o Assistente de configuração, poderá escolher se deve ou não implementar automaticamente a aplicação Portal da empresa. Os utilizadores finais já não verá a tela de "Identificar o dispositivo" e a tela de "Confirmar o seu dispositivo" no fluxo de inscrição.  
- Nos dispositivos já inscritos através do Assistente de configuração através de um dos métodos de inscrição de dispositivos da empresa da Apple, tem de tomar uma ação se pretender ativar o acesso condicional. Precisará [configure uma política de configuração de aplicações](https://aka.ms/enrollment_setup_assistant) com um xml específico para enviar por push o Portal da empresa para estes dispositivos.  Se optar por enviar por push o Portal da empresa, desta forma, os utilizadores finais já não verá a tela de "Identificar o dispositivo" e a tela de "Confirmar o seu dispositivo" no fluxo de inscrição. 
- Após esta alteração é implementada, se não tiver implementado o Portal da empresa com o perfil de configuração de aplicação mencionados acima e se a transferência dos utilizadores finais, a Portal da empresa a partir da aplicação da loja de aplicações, poderem iniciar sessão, mas irá receber uma mensagem de erro. Eles não será possível utilizar a aplicação para o acesso condicional. 

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>O que preciso de fazer para me preparar para esta alteração?
Se pretender utilizar o fluxo de trabalho modificado, poderá ser útil atualizar a sua documentação de orientação do utilizador final para indicar que:

- Os utilizadores finais já não verá os dois ecrãs mencionados acima no fluxo de inscrição. 
- Precisam de iniciar sessão no Portal da empresa quando é implementada automaticamente e não baixá-lo a partir da app store. 

Pode optar por criar uma política de configuração de aplicações agora, se for necessário, em preparação para esta alteração. Quando este novo fluxo de trabalho for implementada, verá os perfis de inscrição atualizado na consola do. Podemos irá também informar sobre esta implementação através do Centro de mensagens. Em seguida, terá de executar a ação para que os utilizadores finais podem inscrever através do DEP ao autenticar com o Assistente de configuração e pode utilizar o Portal da empresa para o acesso condicional.

#### <a name="additional-information"></a>Informações Adicionais 
[https://aka.ms/enrollment_setup_assistant](https://aka.ms/enrollment_setup_assistant)


### <a name="update-your-android-company-portal-app-to-the-latest-version---4536963--"></a>Atualizar a sua aplicação do Portal da empresa para Android para a versão mais recente <!--4536963-->
Intune periodicamente lança atualizações para a aplicação Android do Portal da empresa. Em Novembro de 2018, lançámos uma atualização do portal da empresa, que incluía um comutador de back-end para preparar a alteração da Google da sua plataforma de notificação existente da Google Firebase Cloud Messaging (FCM). Quando Google retira existente da plataforma de notificação e move-o para o FCM, final, os utilizadores terão de atualizaram a sua aplicação do portal da empresa para, pelo menos, Novembro de 2018 versão continue se comunicando com a Google play store.

#### <a name="how-does-this-affect-me"></a>Como é que isto me afeta?
Nosso telemetria indica que tiver dispositivos com uma versão anterior ao 5.0.4269.0 de Portal da empresa. Se esta versão ou posterior da aplicação portal da empresa não está instalado, ações de dispositivo iniciada profissionais de IT, como apagar, repor palavra-passe, as aplicações disponíveis e necessárias instala e inscrição de certificados pode não funcionar conforme esperado. Se os dispositivos estiverem inscritos no Intune na MDM, em seguida, pode ver as versões de portal da empresa e os utilizadores ao aceder a aplicações de cliente – aplicações detetadas. Selecionar as versões anteriores do Portal da empresa permitirá que veja quais os utilizadores finais têm os dispositivos que não tiver atualizado o portal da empresa.

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>O que preciso de fazer para me preparar para esta alteração?
Pedir os utilizadores finais de dispositivos Android que não tenham sido atualizados para atualizar o portal da empresa através do Google play. Notifique o suporte técnico, no caso de um utilizador não tem mantidos atualização automática da aplicação portal da empresa. Veja o link no informações adicionais para a plataforma FCM mais diante da Google e alterar.

#### <a name="additional-information"></a>Informações Adicionais
https://firebase.google.com/docs/cloud-messaging/
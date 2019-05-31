---
title: incluir ficheiro
description: incluir ficheiro
author: ErikjeMS
ms.service: microsoft-intune
ms.topic: include
ms.date: 03/28/2019
ms.author: erikje
ms.custom: include file
ms.openlocfilehash: c4a17abdb518daba30fbdf339090f7e24c8c26d5
ms.sourcegitcommit: a97b6139770719afbd713501f8e50f39636bc202
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/30/2019
ms.locfileid: "66412139"
---
Estes avisos fornecem importante de informações que podem ajudá-lo a se preparar para as funcionalidades e alterações futuras do Intune. 

### <a name="update-your-android-company-portal-app-to-the-latest-version---4536963--"></a>Atualizar a sua aplicação do Portal da empresa para Android para a versão mais recente <!--4536963-->
Intune periodicamente lança atualizações para a aplicação Android do Portal da empresa. Em Novembro de 2018, lançámos uma atualização do portal da empresa, que incluía um comutador de back-end para preparar a alteração da Google da sua plataforma de notificação existente da Google Firebase Cloud Messaging (FCM). Quando Google retira existente da plataforma de notificação e move-o para o FCM, final, os utilizadores terão de atualizaram a sua aplicação do portal da empresa para, pelo menos, Novembro de 2018 versão continue se comunicando com a Google play store.

#### <a name="how-does-this-affect-me"></a>Como é que isto me afeta?
Nosso telemetria indica que tiver dispositivos com uma versão anterior ao 5.0.4269.0 de Portal da empresa. Se esta versão ou posterior da aplicação portal da empresa não está instalado, ações de dispositivo iniciada profissionais de IT, como apagar, repor palavra-passe, as aplicações disponíveis e necessárias instala e inscrição de certificados pode não funcionar conforme esperado. Se os dispositivos estiverem inscritos no Intune na MDM, em seguida, pode ver as versões de portal da empresa e os utilizadores ao aceder a aplicações de cliente – aplicações detetadas. Selecionar as versões anteriores do Portal da empresa permitirá que veja quais os utilizadores finais têm os dispositivos que não tiver atualizado o portal da empresa.

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>O que preciso de fazer para me preparar para esta alteração?
Pedir os utilizadores finais de dispositivos Android que não tenham sido atualizados para atualizar o portal da empresa através do Google play. Notifique o suporte técnico, no caso de um utilizador não tem mantidos atualização automática da aplicação portal da empresa. Veja o link no informações adicionais para a plataforma FCM mais diante da Google e alterar.

#### <a name="additional-information"></a>Informações Adicionais
https://firebase.google.com/docs/cloud-messaging/

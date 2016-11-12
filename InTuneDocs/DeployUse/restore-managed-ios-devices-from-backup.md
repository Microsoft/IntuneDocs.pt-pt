---
title: "Restaurar dispositivos iOS geridos pelo Intune a partir da cópia de segurança| Microsoft Intune"
description: "Forneça orientações aos utilizadores finais acerca de como voltarem a inscrever os respetivos dispositivos depois de os restaurarem a partir da cópia de segurança."
keywords: restaurar, geridos, iOS
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 10/18/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a19e5612-8805-4bd7-a86a-b734bde293ae
ms.reviewer: esmich
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: e6bb539c87c4a13a490ba98c016d814bea5c7bbc
ms.openlocfilehash: 6395e50b3e4c06e7363acc136b5ed9eb2ef75abd


---

# Restaurar dispositivos iOS geridos pelo Intune a partir da cópia de segurança

Existirão casos em que você ou os seus utilizadores irão precisar de restaurar um dispositivo iOS a partir de uma cópia de segurança, como quando um utilizador tem um dispositivo novo. Este tópico explica-lhe os passos adicionais que pode ter de efetuar para configurar a gestão do Intune após restaurar o dispositivo.

## Restaurar cópias de segurança no mesmo dispositivo

Caso a cópia de segurança esteja a ser restaurada para o mesmo dispositivo, o estado de inscrição desse dispositivo também será restaurado. Não é necessária qualquer ação adicional.

## Restaurar cópias de segurança em dispositivos diferentes

Caso a cópia de segurança esteja a ser restaurada num dispositivo diferente, o estado da inscrição não é automaticamente restaurado no novo dispositivo. Os utilizadores têm de seguir os passos de inscrição padrão na versão 2.1.22 ou posterior da aplicação Portal da Empresa para [inscreverem o respetivo dispositivo iOS no Intune](/Intune/EndUser/enroll-your-device-in-intune-ios).

> [!NOTE]
> Caso esteja a aplicar políticas de acesso condicional aos seus utilizadores finais, estes não conseguirão aceder ao e-mail empresarial até se voltarem a inscrever.

> [!TIP]
> Um exemplo de comunicação dos seus utilizadores pode ser o seguinte: para inscrever o seu novo dispositivo, certifique-se de que a versão da aplicação Portal da Empresa é a 2.1.22 ou posterior. Para verificar a versão, abra a aplicação Portal da Empresa, toque no botão Menu no canto superior direito e, em seguida, toque em Sobre. Se estiver a utilizar uma versão anterior, saia da aplicação Portal da Empresa e abra a App Store. Toque no botão Atualizações no canto inferior direito e, em seguida, toque no botão Atualizar junto ao item Portal da Empresa na lista. Quando a atualização for concluída, inicie a aplicação Portal da Empresa e [inscreva o seu dispositivo iOS no Intune](/Intune/EndUser/enroll-your-device-in-intune-ios).

## Resolver problemas de restauro conhecidos

Os utilizadores poderão deparar-se com algumas dificuldades se tiverem restaurado o respetivo dispositivo e iniciado a aplicação Portal da Empresa com a versão 2.1.21 ou posterior da mesma. É possível resolver estas dificuldades ao seguir os passos adequados à situação concreta do utilizador.

### Para os utilizadores que apenas utilizam o seu novo dispositivo
Inicie a aplicação Portal da Empresa e anule a sua inscrição ao selecionar o mosaico do dispositivo atual e ao tocar no botão __Remover__. Após a remoção, siga os passos de inscrição padrão para [inscrever um dispositivo iOS no Intune](/Intune/EndUser/enroll-your-device-in-intune-ios).

### Para os utilizadores que vão utilizar dispositivos novos e antigos
Limpe os cookies do Safari ao tocar em __Definições__ > __Safari__ > __Limpar Dados do Histórico e de Sites__. Ao concluir a limpeza, desinstale e volte a instalar a aplicação Portal da Empresa e, em seguida, siga os passos de inscrição padrão para [inscrever um dispositivo iOS no Intune](/Intune/EndUser/enroll-your-device-in-intune-ios).



<!--HONumber=Oct16_HO3-->



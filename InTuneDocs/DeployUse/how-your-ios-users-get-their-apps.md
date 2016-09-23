---
title: "Como os utilizadores de dispositivos iOS obtêm as aplicações | Microsoft Intune"
description: "Métodos para disponibilizar aplicações iOS aos utilizadores finais"
keywords: 
author: Staciebarker
manager: angrobe
ms.date: 08/24/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 7e3135c1-df26-48c9-aa4c-cdab6168897a
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 52b9e786fe22b04081441db88a3629062fc85668
ms.openlocfilehash: a215d547507dcc460e83009cc6a04baf3fd8f4a4


---


# Como os utilizadores de dispositivos iOS obtêm as aplicações

Utilize estas informações para saber como e onde é que os seus utilizadores finais podem obter as aplicações que distribuir através do Microsoft Intune.

**Aplicações obrigatórias** - aplicações exigidas pelo administrador e que são instaladas nos dispositivos com envolvimento mínimo do utilizador, dependendo da plataforma.

**Aplicações disponíveis** - aplicações fornecidas na lista de aplicações do Portal da Empresa e que os utilizadores podem optar por instalar.

**Aplicações geridas** - aplicações que podem ser geridas através de políticas e que foram "encapsuladas" pelo Intune ou incorporadas no Software Development Kit (SDK) do Intune Mobile Application Management (MAM). Estas aplicações podem ser geridas pelo Intune e podem ser aplicadas políticas de aplicação às mesmas.

**aplicações não geridas** - aplicações que podem ser geridas através de políticas e que não foram encapsuladas pelo Intune ou que não incorporam o SDK do Intune MAM. Não é possível aplicar políticas de aplicação a estas aplicações.

As restrições da Apple proíbem as aplicações da App Store geridas e as aplicações de linha de negócio de serem indicadas na aplicação Portal da Empresa. Para resolver este problema, os mosaicos de aplicações na aplicação Portal da Empresa para iOS apontam os utilizadores para diferentes vistas numa única localização (o site do Portal da Empresa) para todas as suas aplicações, da seguinte forma:

- O mosaico **Aplicações da Empresa** apontava anteriormente para uma lista de todas as aplicações no separador TODOS do [site do Portal da Empresa](http://portal.manage.microsoft.com) e irá continuar a funcionar da mesma forma. O nome do mosaico foi alterado para **Todas as Aplicações**.

- O mosaico **Outras Aplicações** apontava anteriormente para uma vista, dentro da aplicação Portal da Empresa, que indicava todas as aplicações que a Apple permite que a aplicação do Portal da Empresa apresente. O nome do mosaico foi alterado para **Aplicações Em Destaque** e tocar no mosaico irá direcionar os utilizadores para o separador EM DESTAQUE do site do Portal da Empresa.

-  O mosaico **Categorias** apontava anteriormente para uma vista, dentro da aplicação Portal da Empresa, que indicava categorias de aplicações. O nome do mosaico não foi alterado, mas agora aponta para o separador CATEGORIAS do site do Portal da Empresa.
Pode encontrar capturas de ecrã atualizadas [aqui](https://gallery.technet.microsoft.com/Improvements-in-how-iOS-d1104186).



###Consulte também
[Como os utilizadores de dispositivos Android obtêm as aplicações](how-your-android-users-get-their-apps.md)</br>
[Como os utilizadores de dispositivos Windows obtêm as aplicações](how-your-windows-users-get-their-apps.md)



<!--HONumber=Sep16_HO3-->



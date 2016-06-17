---
# required metadata

title: Atualizar aplicações | Microsoft Intune
description:
keywords:
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: beee6933-876a-4be0-b395-4c24cfbd519b

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Atualizar aplicações com o Microsoft Intune
O Microsoft Intune pode ajudá-lo a gerir as atualizações de aplicações. Utilize as informações contidas neste tópico para compreender como pode atualizar aplicações quando é necessária uma nova versão.

## Como atualizar aplicações
Quando for lançada uma nova versão de uma aplicação que implementou, o Intune permite-lhe atualizar e implementar uma versão mais recente da aplicação. Apenas pode substituir uma implementação por uma versão mais recente da mesma aplicação (utilizando o mesmo identificador). Não pode utilizar atualizações de aplicações para atualizar uma implementação com um pacote de aplicações diferente.

> [!IMPORTANT]
> Quando implementa uma aplicação com uma ação de implementação de **Instalação necessária** e, posteriormente, altera a ação de implementação para **Instalação disponível**, as atualizações da aplicação não são instaladas automaticamente em dispositivos que instalaram a aplicação antes de ter sido efetuada a alteração da implementação. Para corrigir este problema, pode efetuar o seguinte:
> 
> -   Fazer com o que utilizador do dispositivo aceda ao portal da empresa, selecione a aplicação instalada e clique em **Instalar**.
> -   Altere a ação de implementação para **Desinstalar**e, depois de a aplicação estar desinstalada, volte a implementar a aplicação com uma ação de implementação de **Instalação Disponível**.

### Para atualizar uma aplicação

1.  Na [consola de administrador do Microsoft Intune](https://manage.microsoft.com), clique em **Aplicações** &gt; **Aplicações**.

2.  Na lista **Aplicações** , selecione a aplicação que pretende atualizar e, em seguida, clique em **Editar**.

3.  No assistente para **Editar Software** , forneça os detalhes novos do pacote de aplicações.

4.  Quando tiver terminado, clique em **Atualizar**.

Quando os dispositivos voltarem a verificar as aplicações disponíveis, a aplicação será atualizada automaticamente para a versão mais recente.





<!--HONumber=May16_HO2-->



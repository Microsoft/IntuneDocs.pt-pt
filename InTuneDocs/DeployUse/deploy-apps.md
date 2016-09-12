---
title: "Implementar aplicações | Microsoft Intune"
description: "Este tópico explica os conceitos que tem de compreender antes de iniciar a implementação de aplicações com o Intune."
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 08/29/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ad5ea85c-aa2e-4110-a184-172cd0b8f270
ms.reviewer: mghadial
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 727d28cff074124b5401f6c2931f87df3a9d2d23
ms.openlocfilehash: ef042e24af2300250cf2bd1bf9803678e252b773


---

# Implementar aplicações com o Microsoft Intune

Este tópico explica alguns dos conceitos que tem de compreender antes de iniciar a implementação de aplicações com o Microsoft Intune.


## Ações de implementação de aplicações
Ao implementar aplicações, pode escolher uma das seguintes ações de implementação:

-   **Instalação obrigatória** – A aplicação é instalada no dispositivo, sem ser necessária intervenção do utilizador.

    > [!TIP]
    > Para os dispositivos iOS que não estejam no modo supervisionado e para todos os dispositivos Android, o utilizador tem de aceitar a oferta da aplicação antes da instalação da mesma.
    >
    >  Se um utilizador desinstalar uma aplicação que implementou como uma instalação obrigatória, o Intune reinstala automaticamente a aplicação após o próximo ciclo de inventário, que normalmente ocorre a cada 7 dias.

-   **Instalação disponível** – A aplicação é apresentada no portal da empresa e os utilizadores podem instalá-la a pedido.

-   **Desinstalar** – A aplicação é desinstalada do dispositivo.

-   **Não aplicável** – A aplicação não é apresentada no portal da empresa e não é instalada em nenhum dispositivo.

#### Compreender as ações de implementação que estão disponíveis para cada tipo de instalador

|Tipo de instalador|Instalação necessária|Instalação disponível|Desinstalar|Não aplicável|
|------------------|--------------------|---------------------|-------------|------------------|
|Pacote de aplicações do Windows (implementado num grupo de utilizadores)|Sim|Sim|Sim|Sim|
|Pacote de aplicações do Windows (implementado num grupo de dispositivos)|Sim|Não|Sim|Sim|
|Pacote de aplicações para dispositivos móveis (implementado num grupo de utilizadores)|Sim|Sim|Sim|Sim|
|Pacote de aplicações para dispositivos móveis (implementado num grupo de dispositivos)|Sim|Não|Sim|Sim|
|Windows Installer (implementado num grupo de utilizadores)|Não|Sim|Não|Sim|
|Windows Installer (implementado num grupo de dispositivos)|Sim|Não|Sim|Sim|
|Ligação externa (implementada num grupo de utilizadores)|Não|Sim|Não|Sim|
|Ligação externa (implementada num grupo de dispositivos)|Não|Não|Não|Não|
|Aplicação iOS gerida da loja de aplicações (implementada num grupo de utilizadores)|Sim|Sim|Sim|Sim|
|Aplicação iOS gerida da loja de aplicações (implementada num grupo de dispositivos)|Sim|Não|Sim|Sim|
> [!TIP]
> Quando implementa aplicações, se selecionar grupos de utilizadores e de dispositivos, só pode implementar a aplicação como **Instalação disponível**.

## Conflitos de implementação
Quando duas implementações com a mesma ação de implementação são recebidas por um dispositivo, aplicam-se as seguintes regras:

-   As implementações num grupo de dispositivos têm prioridade sobre as implementações num grupo de utilizadores. No entanto, se uma aplicação for implementada num grupo de utilizadores com uma ação de implementação de **Disponível** e a mesma aplicação for também implementada num grupo de dispositivos com a ação de implementação de **Não Aplicável**, a aplicação será disponibilizada no portal da empresa para instalação por parte dos utilizadores.

-   Uma ação de instalação tem prioridade sobre uma ação de desinstalação.

-   Se uma instalação obrigatória e uma instalação disponível forem recebidas por um dispositivo, as ações são combinadas. Por outras palavras, o utilizador pode instalar a aplicação disponível a partir do portal da empresa antes de começar a instalação obrigatória.


## Passos seguintes

Saiba como [implementar aplicações no Microsoft Intune](deploy-apps-in-microsoft-intune.md).



<!--HONumber=Aug16_HO5-->



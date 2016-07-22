---
title: "Implementar aplicações | Microsoft Intune"
description: 
keywords: 
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ad5ea85c-aa2e-4110-a184-172cd0b8f270
ms.reviewer: mghadial
ms.suite: ems
ms.sourcegitcommit: e6b995118e66fd146a68b49ce4decdcbd1fe3572
ms.openlocfilehash: a68cb85602bd585539147c7d7d38c0d906f2b1f7


---

# Implementar aplicações com o Microsoft Intune

Este tópico explica alguns dos conceitos que tem de compreender antes de iniciar a implementação de aplicações com o Microsoft Intune.


## Ações de implementação de aplicações
Ao implementar aplicações, pode escolher uma das seguintes ações de implementação:

-   **Instalação necessária** – A aplicação é instalada no dispositivo, sem ser necessária intervenção do utilizador final.

    > [!TIP]
    > [!TIP] Para os dispositivos iOS que não estejam no modo supervisionado e para todos os dispositivos Android, o utilizador tem de aceitar a oferta da aplicação antes da instalação da mesma.
    > 
    >  Se um utilizador final desinstalar uma aplicação que implementou como uma instalação necessária, o Intune reinstala automaticamente a aplicação após o próximo ciclo de inventário, que normalmente ocorre a cada 7 dias.

-   **Instalação disponível** – A aplicação é apresentada no portal da empresa e os utilizadores finais podem instalá-la a pedido.

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
> [!TIP] Quando implementa aplicações, se selecionar grupos de utilizadores e de dispositivos, só pode implementar a aplicação como uma **Instalação disponível**.

## Conflitos de implementação
Quando duas aplicações com a mesma ação de implementação são recebidas por um dispositivo, aplicam-se as seguintes regras:

-   As implementações num grupo de dispositivos têm prioridade sobre as implementações num grupo de utilizadores. No entanto, se uma aplicação for implementada num grupo de utilizadores com uma ação de implementação de **Disponível** e a mesma aplicação for também implementada num grupo de dispositivos com a ação de implementação de **Não Aplicável**, a aplicação será disponibilizada no portal da empresa para instalação por parte dos utilizadores.

-   Uma ação de instalação tem prioridade sobre uma ação de desinstalação.

-   Se forem recebidas uma instalação disponível e uma necessária por um dispositivo, as ações são combinadas (a aplicação é tanto necessária como disponível, ou seja, o utilizador final pode instalá-lo no portal da empresa antes da instalação obrigatória ser iniciada).


## Passos seguintes

Saiba como [implementar aplicações no Microsoft Intune](deploy-apps-in-microsoft-intune.md).



<!--HONumber=Jul16_HO2-->



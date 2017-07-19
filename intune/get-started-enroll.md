---
title: "Introdução à inscrição de dispositivos"
titleSuffix: Intune on Azure
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 06/27/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: b595848d-c451-43ab-812d-b22e0170fb7a
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 36e658cebdfd23547e3c376124289046f81acc1f
ms.sourcegitcommit: fd2e8f6f8761fdd65b49f6e4223c2d4a013dd6d9
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/03/2017
---
# <a name="getting-started-enrolling-devices"></a>Introdução à inscrição de dispositivos

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

![Dispositivo iOS a mostrar a aplicação do portal da empresa. o primeiro ecrã apresentado ao utilizador do processo de inscrição.](/intune-user-help/media/ios-enroll-1a-comp-access-setup.png)

O Microsoft Intune ajuda a sua força de trabalho a ser produtiva em dispositivos móveis, mantendo os seus dados empresariais protegidos. Uma vez que os seus utilizadores finais irão interagir com o Intune nos respetivos dispositivos ao invés de o fazerem na consola de administrador, deve certificar-se de que está familiarizado com a experiência de inscrição. Desta forma, pode aliar políticas de conformidade bem delineadas à sua experiência e mostrar empatia para com os seus utilizadores. Isto é especialmente importante porque os seus utilizadores saberão exatamente qual o tipo de informações que poderá ver enquanto administrador:

## <a name="what-it-cannot-see"></a>O que o administrador de TI não pode ver
* Histórico de chamadas e navegação na Web
* Localização
* E-mail pessoal
* Mensagens de texto
* Contactos
* Palavras-passe das suas contas pessoais
* Eventos do calendário
* Imagens, incluindo o que está na aplicação de fotografias ou câmara

## <a name="what-it-can-see"></a>O que o administrador de TI pode ver
* Modelo
* Número de série
* Versão do sistema operativo
* Nomes das aplicações
* Proprietário
* Nome do dispositivo
* Fabricante (para dispositivos não fabricados pela Apple)
* Número de telefone (para os dispositivos de trabalho, o número inteiro. Para os dispositivos pessoais, apenas os últimos quatro dígitos).

## <a name="how-do-i-enroll-a-device"></a>Como posso inscrever um dispositivo?

A inscrição de um dispositivo é a primeira experiência que muitos utilizadores finais terão ao aceder aos recursos da empresa. [Compreender essa experiência](end-user-educate.md) pode ajudar a melhorar uma experiência potencialmente desagradável.

1. Abra a **App Store** e procure o **Portal da Empresa do Intune**.
2. Transfira a aplicação **Portal da Empresa do Microsoft Intune**.
3. Abra a aplicação **Portal da Empresa**, introduza o seu endereço de e-mail e palavra-passe de utilizador de teste e, em seguida, toque em **Iniciar sessão**.
4. Atualize a palavra-passe temporária para uma nova.
5. Na página **Configuração do Acesso da Empresa**, toque em **Inscrição de Dispositivos**.
6. Na página **Porquê inscrever o seu dispositivo?**, leia mais sobre aquilo que um utilizador pode fazer ao inscrever o seu dispositivo e, em seguida, toque em **Continuar**.
7. Reveja uma lista do tipo de acesso que os utilizadores recebem ao efetuar a inscrição e, em seguida, toque em **Continuar**.
8. Reveja o que os administradores de TI podem ou não ver num dispositivo e, em seguida, toque em **Continuar**.
9. Na página **O que vem a seguir**, leia mais sobre o que acontece durante a inscrição e, em seguida, toque em **Inscrever**.
10. Na página **Instalar Perfil**, toque em **Instalar** e, em seguida, introduza o código de acesso do dispositivo se este lhe for pedido.
11. Toque em **Instalar**.
12. Toque novamente em **Instalar** para indicar que leu o aviso.
13. No pop-up **Aviso**, toque em **Confiar**.
14. Quando o ecrã mudar para mostrar que o perfil concluiu a instalação, toque em **Concluído**.
15. A mensagem "A inscrever o dispositivo" é apresentada no ecrã, seguida de outra mensagem a indicar que o dispositivo foi inscrito com êxito. Será apresentado um pop-up a pedir para abrir a página no Portal da Empresa. Toque em **Abrir**.
16. Irá regressar ao ecrã **Configuração do Acesso à Empresa**. Se não tiver configurado políticas de teste, o dispositivo deverá aparecer como estando em conformidade. Se tiver políticas de teste, ao tocar em **Conformidade do Dispositivo** será apresentada uma lista de tarefas a fazer que terá de concluir para tornar o dispositivo seguro.

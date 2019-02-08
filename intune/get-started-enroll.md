---
title: Compreender a experiência de inscrições de dispositivos iOS
titlesuffix: Microsoft Intune
description: Conheça a experiência de inscrição ao efetuar uma experiência de inscrição completa de um dispositivo iOS.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/31/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: b595848d-c451-43ab-812d-b22e0170fb7a
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 487ad607bc34d5fc2137f1b3903b0711e793658d
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/07/2019
ms.locfileid: "55840573"
---
# <a name="understand-the-users-experience-enrolling-an-ios-device"></a>Compreender a experiência do utilizador que está a inscrever um dispositivo iOS

O Microsoft Intune ajuda a sua força de trabalho a ser produtiva em dispositivos móveis, mantendo os seus dados empresariais protegidos. Uma vez que os seus utilizadores finais irão interagir com o Intune nos respetivos dispositivos ao invés de o fazerem na consola de administrador, deve certificar-se de que está familiarizado com a experiência de inscrição. Desta forma, pode aliar políticas de conformidade bem delineadas à sua experiência e mostrar empatia para com os seus utilizadores. Isto é especialmente importante porque os seus utilizadores saberão exatamente qual o tipo de informações que poderá ver enquanto administrador:

| O que o administrador de TI não pode ver | O que o administrador de TI pode ver |
|---|---|
| Histórico de chamadas e navegação na Web | Modelo |
| Localização | Número de série |
| E-mail pessoal | Versão do sistema operativo |
| Mensagens de texto | Nomes das aplicações |
| Contactos | Owner |
| Palavras-passe das suas contas pessoais | Nome do dispositivo |
| Eventos do calendário | Fabricante (para dispositivos não fabricados pela Apple) |
| Imagens, incluindo o que está na aplicação de fotografias ou câmara | Número de telefone (para os dispositivos de trabalho, o número inteiro. Para os dispositivos pessoais, apenas os últimos quatro dígitos). |

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

## <a name="next-steps"></a>Passos Seguintes

[Introdução à adição de aplicações](get-started-apps.md) – localize e adicione aplicações a dispositivos para que os seus funcionários comecem a trabalhar.

## <a name="learn-more"></a>Saiba mais

* [Opções de inscrição do Intune](enrollment-options.md)
* [Ativar a funcionalidade Bring Your Own Device (Traga o Seu Próprio Dispositivo) com o Intune](byod-enable.md)
* [Informar os seus utilizador finais sobre a inscrição e gestão de dispositivos](end-user-educate.md)

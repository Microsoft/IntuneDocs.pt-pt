---
title: "Cenários de proteção de e-mail"
description: "Alguns cenários de exemplo e como podem ser implementados com o acesso condicional."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 01/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 454eab79-b620-42c9-b8e6-fada6e719fcd
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 1ca486ca9eab1ebb8a446b560ff5e265eb4d2712
ms.sourcegitcommit: 1a54bdf22786aea1cf1b497d54024470e1024aeb
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/10/2017
---
# <a name="protect-access-to-email-with-microsoft-intune-example-scenarios"></a>Proteger o acesso ao e-mail com o Microsoft Intune: cenários de exemplo

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

## <a name="scenario-1-block-users-from-using-noncompliant-devices-to-access-exchange-online"></a>Cenário 1: impedir os utilizadores de utilizarem dispositivos não conformes para aceder ao Exchange Online
### <a name="scenario-requirements"></a>Requisitos do cenário
- Todos os utilizadores no grupo de segurança **Contabilidade** do Azure Active Directory têm de ser impedidos de aceder ao Exchange Online se o respetivo dispositivo não for conforme com uma política de conformidade implementada por si.
- Se existirem utilizadores neste grupo cujos dispositivos não sejam suportados pelo Intune, terão de ser impedidos de aceder ao Exchange Online nesse dispositivo.
- Os utilizadores no grupo de segurança **Finanças** do Azure Active Directory têm de estar excluídos da política, mesmo que também estejam no grupo de segurança **Contabilidade**.

Para tal, configure uma política de acesso condicional para o Exchange Online com as seguintes definições:

- Escolha **Ativar política de acesso condicional**.

- Escolha as plataformas a partir das quais pretende permitir o acesso das aplicações com autenticação moderna.
- Para aplicações do Exchange ActiveSync, escolha **Bloquear dispositivos não conformes em plataformas suportadas pelo Microsoft Intune** e **Bloquear todos os outros dispositivos em plataformas não suportadas pelo Microsoft Intune.**
-   Na secção **Grupo visado**, em **Grupos de segurança selecionados**, escolha o grupo de utilizadores **Contabilidade**.

-   Na secção **Grupo excluído**, em **Grupos de segurança selecionados**, escolha o grupo de utilizadores **Finanças**.


No cenário é utilizado o seguinte fluxo para decidir quais os dispositivos que podem aceder ao Exchange Online:

![Fluxo de acesso a dispositivos](./media/ConditionalAccess8-5.png)

## <a name="scenario-2-all-ios-devices-that-access-exchange-on-premises-must-be-managed-by-intune"></a>Cenário 2: todos os dispositivos iOS que acedem ao Exchange no local têm de ser geridos pelo Intune
### <a name="scenario-requirements"></a>Requisitos do cenário
- Apenas os dispositivos que executam o iOS devem ter permissão para aceder ao Exchange no local.
- Os dispositivos também têm de estar inscritos no Intune e cumprir as regras de política de conformidade antes de poderem ser utilizados para aceder ao Exchange.

Para tal, configure a política de acesso condicional seguinte para o Exchange no local com as seguintes definições:

-   Escolha a opção **Impedir que as aplicações de e-mail acedam ao Exchange no local se o dispositivo não estiver em conformidade ou não estiver inscrito no Microsoft Intune**. Ao escolher esta opção, ativa a política de acesso condicional, o que requer que todos os dispositivos estejam inscritos no Microsoft Intune e cumpram as regras de política de conformidade antes de poderem aceder ao Exchange.

-   Para definições avançadas do Exchange Active Sync, crie:

  -   Uma exceção de plataforma que permite aos dispositivos que executam o iOS aceder ao Exchange.   

  -   Uma regra predefinida que especifique que quando um dispositivo não está abrangido pela regra de exceção da plataforma, deve ser impedido de aceder ao Exchange. Esta regra assegura que os dispositivos que não estejam a executar o iOS sejam impedidos de aceder ao Exchange.

É utilizado o fluxo seguinte para decidir quais os dispositivos que podem aceder ao Exchange:

![Fluxo de acesso a dispositivos](./media/ConditionalAccess8-3.png)

## <a name="scenario-3-no-android-devices-can-access-exchange-on-premises"></a>Cenário 3: nenhum dispositivo Android pode aceder ao Exchange no local
### <a name="scenario-requirements"></a>Requisitos do cenário
- Todos os dispositivos Android devem ser impedidos de aceder ao Exchange.
- Todos os outros dispositivos suportados podem aceder ao Exchange, desde que sejam geridos pelo Intune.

Para tal, configure uma política de acesso condicional para o Exchange no local com as seguintes definições:

-   Escolha a opção **Impedir que as aplicações de e-mail acedam ao Exchange no local se o dispositivo não estiver em conformidade ou não estiver inscrito no Microsoft Intune**. Ao escolher esta opção, requer que todos os dispositivos têm de estar inscritos no Intune e cumprir as regras de política de conformidade.

- Para definições avançadas do Exchange Active Sync, crie:
  -   Uma exceção de plataforma que impede os dispositivos que executam o Android de aceder ao Exchange. Esta regra assegura que os dispositivos Android não podem servir para aceder ao Exchange.

  -   Uma regra predefinida que especifica que, se um dispositivo não estiver abrangido por outras regras, deve ter permissão para aceder ao Exchange. Esta regra predefinida assegura que os dispositivos que executam plataformas que não sejam o Android, mas que são suportadas pelo Microsoft Intune, podem servir para aceder ao Exchange. No entanto, têm de estar inscritos no Intune e cumprir as regras de política de conformidade.

É utilizado o fluxo seguinte para decidir quais os dispositivos que podem aceder ao Exchange:

![Fluxo de acesso a dispositivos](./media/ConditionalAccess8-4.png)

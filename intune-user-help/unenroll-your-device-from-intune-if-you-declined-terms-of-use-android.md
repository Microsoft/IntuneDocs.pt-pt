---
title: Remover o seu dispositivo da gestão caso tenha recusado os Termos de Utilização | Microsoft Docs
description: ''
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 03/23/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: 4278f000-0258-4de5-93a1-195b48e5061e
searchScope:
- User help
ROBOTS: ''
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-enduser
ms.collection: ''
ms.openlocfilehash: f54f0d9453e93ad54a1d2a96ff25051f3d8bd3a1
ms.sourcegitcommit: caee3c3fa77586314aa8040b0caf32a0527b669e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/10/2020
ms.locfileid: "75857678"
---
# <a name="remove-your-device-from-management-if-you-declined-terms-of-use"></a>Remover o seu dispositivo da gestão caso tenha recusado os "Termos de Utilização"

Se recusou os termos de utilização ao tentar iniciar sessão na aplicação Portal da Empresa, será impedido de iniciar sessão na mesma em tentativas futuras, por isso terá de utilizar estas instruções de "solução" para remover o seu dispositivo do Intune.

Ao desinstalar a aplicação Portal da Empresa, também removerá o seu dispositivo do Intune. O seu dispositivo já não poderá aceder aos recursos da empresa. Para obter mais informações sobre o que acontece quando remove o seu dispositivo da gestão, veja [O que acontece se anular a inscrição do seu dispositivo no Intune?](what-happens-if-you-unenroll-your-device-from-intune-android.md).

Antes de poder desinstalar a aplicação do Portal da Empresa, terá de aceder à definição **Administradores de dispositivos** e desativar o **Portal da Empresa**. Os passos poderão variar um pouco, consoante o seu dispositivo Android.

## <a name="removing-the-device-from-the-company-portal-app"></a>Remover o dispositivo da aplicação Portal da Empresa

Para remover o seu dispositivo do Intune e desinstalar a aplicação Portal da Empresa:

1. Vá para **configurações** &gt; **segurança &amp; bloqueio de tela** &gt; **Administradores do dispositivo**.

    A conclusão deste passo anula imediatamente a inscrição do seu dispositivo.

2. Desmarque a caixa de junto a **Portal da Empresa** ou desative-a.

    Já pode desinstalar a aplicação do portal da Empresa.

## <a name="removing-data-collected-by-the-company-portal-app"></a>Remover dados recolhidos pela aplicação Portal da Empresa

Para remover todos os dados que a aplicação Portal da Empresa para Android armazena no seu dispositivo:

- Limpe os dados da aplicação em Aplicações, clique na aplicação e, em seguida, no botão "Limpar dados"
- Elimine a pasta "\storage\internal storage\Android\data\com.microsoft.windowsintune.companyportal"


Ainda precisa de ajuda? Contacte o suporte da empresa (verifique as informações de contacto no [site do Portal da Empresa](https://go.microsoft.com/fwlink/?linkid=2010980)) ou escreva para a <a href="mailto:wintunedroidfbk@microsoft.com?subject=I'm having unenrolling my Android device&body=Describe the issue you're experiencing here.">equipa Android da Microsoft</a>.

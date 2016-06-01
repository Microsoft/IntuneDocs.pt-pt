---
# required metadata

title: Nomes de domínio para o Microsoft Intune | Microsoft Intune
description:
keywords:
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: c3c136f0-330d-432a-a91f-16f7dd097e55

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---



# Nomes de domínio para o Microsoft Intune

Antes de configurar o Microsoft Intune, reveja este tópico e outros requisitos listados em [O que deve saber antes de iniciar o Microsoft Intune](what-to-know-before-you-start-microsoft-intune.md)

Quando a sua organização se inscreve num serviço Microsoft baseado na nuvem, como o Intune, é-lhe fornecido um nome de domínio inicial, parecido com **contoso.onmicrosoft.com**. Neste exemplo, **contoso** é o nome de domínio que escolheu quando se inscreveu e **onmicrosoft.com** é o sufixo atribuído às contas que adicionar à sua subscrição. Depois de concluir o processo de inscrição, não poderá alterar esse nome de domínio. No entanto, enquanto administrador global, pode adicionar os seus próprios nomes de domínio personalizados para que a sua organização os utilize com o serviço ou pode remover domínios que adicionou anteriormente.

Por predefinição, quando utiliza o domínio onmicrosoft, cada utilizador que importar receberá o sufixo **onmicrosoft.com** no respetivo nome principal de utilizador (UPN).

Para utilizar um nome de domínio do qual é proprietário em vez daquele que lhe foi fornecido durante a inscrição, pode adicionar esse nome de domínio ao Azure Active Directory. Depois de adicionar o domínio, e após a verificação para confirmar que é proprietário do mesmo, poderá criar contas e grupos que incluam esse nome de domínio ao alterar os registos de recursos DNS no seu fornecedor de alojamento DNS. Para simplificar a gestão das contas de utilizadores quando planeia utilizar um domínio personalizado, configure um nome de domínio personalizado à sua subscrição antes de iniciar a sincronização de utilizadores a partir do seu Active Directory local.

A configuração de nomes de domínio e registos de recursos DNS para o Intune é igual aos outros inquilinos do Azure Active Directory. Consulte [Adicionar o seu nome de domínio personalizado para simplificar o início de sessão com o Azure Active Directory](https://azure.microsoft.com/documentation/articles/active-directory-add-domain/) para obter instruções.

### Consulte também
[What to know before you start Microsoft Intune (O que deve saber antes de iniciar o Microsoft Intune)](what-to-know-before-you-start-microsoft-intune.md)


<!--HONumber=May16_HO2-->



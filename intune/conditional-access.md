---
title: "O que é o acesso condicional?"
titleSuffix: Intune Azure preview
description: "Pré-visualização do Azure no Intune: saiba como definir as condições que os utilizadores e os dispositivos têm de reunir para aceder aos recursos da empresa na pré-visualização do Azure no Microsoft Intune."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 12/07/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a1973f38-ea55-43eb-a151-505fb34a8afb
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 8ab6d782460a857a0901abd9bd567365ee2e3f70
ms.contentlocale: pt-pt
ms.lasthandoff: 05/23/2017


---

# <a name="what-is-conditional-access"></a>O que é o acesso condicional?


[!INCLUDE[azure_preview](./includes/azure_preview.md)]


Neste tópico vamos descrever o acesso condicional e de que forma se aplica ao Enterprise Mobility + Security e, em seguida, as funcionalidades de acesso condicional no Intune.

O acesso condicional do Enterprise Mobility + Security (EMS) tira partido das potencialidades do Azure Active Directory Premium e do Microsoft Intune para lhe proporcionar o controlo de que precisa para manter os seus dados empresariais protegidos, ao transmitir à sua equipa uma experiência que lhe permite trabalhar da melhor forma a partir de qualquer dispositivo.

Com o acesso condicional, pode definir as condições que limitam o acesso aos dados da empresa com base na localização, no estado do dispositivo e do utilizador, bem como na sensibilidade das aplicações.

Na perspetiva do dispositivo, o Intune e o Azure Active Directory funcionam em conjunto para garantir que apenas os dispositivos geridos e compatíveis têm acesso ao e-mail e aos serviços do Office 365. Por exemplo, pode definir uma política no Azure Active Directory para permitir que apenas os computadores que estão associados a um domínio ou os dispositivos móveis inscritos numa aplicação de gestão de dispositivos móveis como o Intune, têm a capacidade de aceder aos serviços do Office 365. Pode utilizar o Intune para configurar um perfil de conformidade de dispositivos que avalie o estado de compatibilidade do dispositivo. O estado de conformidade é comunicado ao Azure Active Directory a utilizar para a imposição da política no Azure Active Directory quando o utilizador tenta aceder aos recursos da empresa. Para obter mais informações sobre a conformidade de dispositivos no Intune, veja [O que é a conformidade de dispositivos?](device-compliance.md)

O acesso condicional para aplicações na cloud, como o Exchange Online, pode ser configurado através do Azure Active Directory. Para obter mais informações, veja este [artigo](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal).

## <a name="on-premises-conditional-access-in-intune"></a>Acesso condicional no local no Intune

O acesso condicional no Intune pode servir para permitir ou bloquear o acesso ao **Exchange no local** com base na gestão e na inscrição de dispositivos.

As definições do perfil de conformidade do dispositivo servem para avaliar a conformidade do mesmo. O acesso condicional utiliza a avaliação para permitir ou bloquear o acesso ao Exchange no local. Quando o acesso condicional é utilizado em combinação com um perfil de conformidade de dispositivos, apenas os dispositivos compatíveis têm permissão para aceder ao Exchange no local. Pode configurar definições avançadas do acesso condicional para um controlo mais granular, tais como: permitir ou bloquear determinadas plataformas ou bloquear imediatamente dispositivos que não sejam geridos pelo Intune.

O perfil de conformidade do dispositivo e o acesso condicional são atribuídos ao utilizador. Qualquer dispositivo que o utilizador utilize para aceder ao Exchange no local é analisado relativamente à conformidade. Tenha em atenção que o utilizador que está a utilizar o dispositivo tem de ter um perfil de conformidade atribuído para que o dispositivo seja avaliado em termos de conformidade. Se não estiver implementada nenhuma política de conformidade para o utilizador, o dispositivo será tratado como compatível e não serão aplicadas restrições de acesso.

Quando os dispositivos não cumprem as condições definidas, o utilizador final é orientado através do processo de inscrição do dispositivo e da correção do problema que está fazer com que o dispositivo não seja compatível.

## <a name="next-steps"></a>Próximos passos

[Como criar uma política de acesso condicional para o Exchange no local](conditional-access-exchange-create.md)

[Como configurar o acesso condicional no Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)


---
title: Resolver o conjunto de restrições de ponto de acesso no Intune
description: Consulte as três mensagens frequentes das políticas de restrição de ponto de acesso do Intune e saiba como as resolver
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 05/28/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
searchScope:
- User help
ROBOTS: ''
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: aefde274ec7ca925d45dd101ee0ebef1083f7f19
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/14/2019
ms.locfileid: "55851275"
---
# <a name="resolve-access-point-restrictions"></a>Resolver restrições de ponto de acesso

As organizações podem restringir as localizações a partir das quais os dispositivos acedem aos dados empresariais.
Para configurar estas *restrições de ponto de acesso*, têm de especificar e definir as localizações de rede aprovadas.  

Ao tentar ligar a uma rede não reconhecida ou não aprovada, poderá receber uma ou mais das seguintes mensagens:

* As restrições de ponto de acesso não estão configuradas.
* Não está ligado a uma rede aprovada.
* Ocorreu um erro e não foi possível impor as restrições de ponto de acesso.

 As tabelas abaixo apresentam cada mensagem, o que significa e como aceder aos seus recursos de trabalho novamente.

## <a name="access-point-restrictions-not-set-up"></a>Restrições de ponto de acesso não configuradas  
| Mensagem do Portal da Empresa | O que significa esta mensagem | O que deve fazer                                                               
|------------------------|--------------------------|--------------------------|
| **As restrições de ponto de acesso não estão configuradas – as restrições de ponto de acesso estão ativas e têm de ser configuradas.** | A sua empresa aplicou restrições de ponto de acesso ao seu dispositivo. Esta definição exige que a aplicação Portal da Empresa verifique algumas definições de rede no seu dispositivo. | Toque em **Resolver**. A aplicação Portal da Empresa irá certificar-se de que está ligado a uma rede aprovada pela empresa. |

## <a name="not-connected-to-an-approved-network"></a>Não está ligado a uma rede aprovada  

| Mensagem do Portal da Empresa | O que significa esta mensagem | O que deve fazer                                                                   
|------------------------|-----------------------------------|--------------------------|
| **O dispositivo não está ligado a uma rede aprovada – ligue-se a uma rede sem fios aprovada.** | Está ligado a uma rede que não foi aprovada para o acesso a recursos de trabalho. Enquanto estiver ligado a esta rede, não conseguirá aceder ao e-mail do trabalho, aplicações e outros recursos empresariais protegidos. | Ligue-se a uma rede aprovada pela empresa. Em seguida, toque em **Resolver** para tentar novamente. |

## <a name="restrictions-couldnt-be-enforced"></a>Não foi possível impor as restrições  

| Mensagem do Portal da Empresa | O que significa esta mensagem | O que deve fazer                                                                      
|------------------------|-----------------------------------|--------------------------|
| **Não foi possível impor as restrições de ponto de acesso – o Portal da Empresa detetou um erro.** | O Intune não consegue determinar se está ligado a uma rede aprovada. Este erro poderá ser o resultado de uma conectividade de rede fraca, de bateria fraca, do modo de poupança de bateria ou de um erro do Portal da Empresa. | Verifique se tem uma receção de rede forte. Desative o modo de poupança de bateria e certifique-se de que tem pelo menos 30% de bateria. Em seguida, toque em **Resolver** para tentar novamente. 

Ainda precisa de ajuda? Recomendamos que contacte o suporte da sua empresa para obter ajuda. Para obter informações de contacto específicas, aceda ao [site do Portal da Empresa](https://portal.manage.microsoft.com/#HelpDeskDialog).

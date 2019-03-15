---
title: O que acontece se anular a inscrição do seu dispositivo Windows? | Microsoft Docs
description: ''
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 01/23/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 47e03edb-0c57-4e25-8e89-4a1069267b8c
searchScope:
- User help
ROBOTS: ''
ms.reviewer: priyar
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5c28d5b122bda537d4707bc0fdc2bfc74bcb823a
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/14/2019
ms.locfileid: "55847289"
---
# <a name="what-happens-if-you-unenroll-your-windows-device-from-intune"></a>O que acontece se anular a inscrição do seu dispositivo Windows no Intune?

Utilize as ligações no lado direito desta página, em **Neste artigo** para encontrar informações acerca do tipo de dispositivo que está a utilizar.


## <a name="windows-10-windows-81-windows-8-windows-7-windows-vista"></a>Windows 10, Windows 8.1, Windows 8, Windows 7, Windows Vista

-   O seu dispositivo não aparece no Portal da Empresa e deixa de poder instalar aplicações a partir do Portal da Empresa.

-   Se instalou o software cliente do Intune, este é removido do computador.

-   O software do Endpoint Protection do Intune é removido do computador. Se o seu computador tiver outro software de proteção contra vírus instalado e este estiver desativado, esse software poderá ser reativado após a remoção do Endpoint Protection do Intune. Analise o seu computador depois de ser removido do Portal da Empresa.

    > [!IMPORTANT]
    > Se o outro software de proteção contra vírus não for novamente ativado ou não existir outro software de proteção contra vírus instalado, o seu computador pode estar vulnerável a vírus e software maligno.

-   Todas as definições que tenham sido alteradas no seu dispositivo quando o adicionou (por exemplo, a desativação da câmara) deixam de ser aplicáveis.

-   O seu computador deixará de receber atualizações de software automáticas ou atualizações de software antivírus do serviço do Intune. No entanto, dependendo da configuração, o seu computador poderá continuar a receber atualizações do Windows Server Update Services, Windows Update ou Microsoft Update.

Além disso, no Windows 8.1:

-   Deixará de poder utilizar aplicações e dados da empresa no seu dispositivo.

-   Algumas aplicações de e-mail, como o Windows Mail, deixam de conseguir aceder aos e-mails da empresa armazenados no seu dispositivo.

-   Pode não conseguir ligar-se à rede da sua empresa através de Wi-Fi ou de uma rede privada virtual.

-   É possível que deixe de ter acesso a alguns recursos da empresa, como partilhas de ficheiros ou sites internos, no seu dispositivo.

## <a name="windows-10-mobile-and-windows-phone-81"></a>Windows 10 para dispositivos móveis e Windows Phone 8.1

-   A aplicação Portal da Empresa é desinstalada do seu dispositivo. Isto significa que o dispositivo já não aparece no Portal da Empresa e deixa de poder instalar aplicações a partir da aplicação Portal da Empresa ou do site do Portal da Empresa.

-   Deixará de poder utilizar aplicações e dados da empresa no seu dispositivo.

-   As definições alteradas no seu dispositivo quando o adicionou (por exemplo, a desativação da câmara ou o comprimento necessário específico de uma palavra-passe) deixam de ser aplicáveis.

    > [!IMPORTANT]
    > A única exceção são as políticas de encriptação, que ainda são aplicáveis. Se a política da sua empresa exige a encriptação do seu Windows Phone, a única forma de desencriptar o seu telemóvel implica a reposição do mesmo através do menu **Definições**.

## <a name="windows-rt-running-windows-81"></a>Windows RT a executar o Windows 8.1

-   A aplicação Portal da Empresa é desinstalada do seu dispositivo. Isto significa que o dispositivo não aparece no Portal da Empresa e deixa de poder instalar aplicações a partir do Portal da Empresa.

-   Deixará de poder utilizar aplicações e dados da empresa no seu dispositivo.

-   As definições alteradas no seu dispositivo quando o adicionou (por exemplo, a desativação da câmara ou o comprimento necessário específico de uma palavra-passe) deixam de ser aplicáveis.

-   É possível que deixe de conseguir ligar-se à rede da sua empresa através de Wi-Fi ou de uma rede privada virtual.

-   É possível que deixe de ter acesso a alguns recursos da empresa, como partilhas de ficheiros ou sites internos, no seu dispositivo.

-   Algumas aplicações de e-mail, como o Windows Mail, deixam de conseguir aceder aos e-mails da empresa armazenados no seu dispositivo.

Ao remover o seu dispositivo Windows RT, ocorrerá o seguinte:

-   A aplicação Portal da Empresa é desinstalada do seu dispositivo. Isto significa que o dispositivo não aparece no Portal da Empresa e deixa de poder instalar aplicações a partir do Portal da Empresa.

-   Deixará de poder utilizar aplicações e dados da empresa no seu dispositivo.

-   As definições alteradas no seu dispositivo quando o adicionou (por exemplo, a desativação da câmara ou o comprimento necessário específico de uma palavra-passe) deixam de ser aplicáveis.

Se tiver dúvidas, contacte o suporte da sua empresa. Para encontrar as informações de contacto dele, verifique o [site do Portal da Empresa](https://go.microsoft.com/fwlink/?linkid=2010980).

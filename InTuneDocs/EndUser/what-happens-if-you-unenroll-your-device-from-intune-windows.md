---
# required metadata

title: What happens if you unenroll your device from Intune? (O que acontece se anular a inscrição do dispositivo no Intune?) | Microsoft Intune
description:
keywords:
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 47e03edb-0c57-4e25-8e89-4a1069267b8c

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: priyar
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---


# What happens if you unenroll your device from Intune? (O que acontece se anular a inscrição do dispositivo no Intune?)

Para informações adicionais sobre o que acontece, utilize a ligação, mostrada na secção “Neste artigo” acima, que corresponde ao tipo de dispositivo que utiliza.

- [Windows 10 Mobile, 8.1, Windows 8, Windows 7, Vista](#windows-10-mobile--8-1,-windows-8,-windows-7,-vista)
- [Windows 10, Windows 8.1 ou Windows Phone 8](#windows-10--windows-8-1-or-windows-phone-8)
- [Windows RT com o Windows 8.1 ou o Windows RT](#windows-rt-running-windows-8-1-or-windows-rt)


## Windows 10, Windows 8.1, Windows 8, Windows 7, Vista

-   O dispositivo deixa de aparecer no Portal da Empresa e deixa de poder instalar aplicações a partir do Portal da Empresa.

-   Se instalou o software cliente do Intune, este é removido do computador.

-   O software do Endpoint Protection do Intune é removido do computador. Se o seu computador tiver outro software de proteção contra vírus instalado e este estiver desativado, esse software poderá ser reativado após a remoção do Endpoint Protection do Intune. Deve analisar o seu computador depois de ser removido do Portal da Empresa.

    > [!IMPORTANT] Se o outro software de proteção contra vírus não for reativado ou não estiver instalado outro software de proteção contra vírus, o seu computador pode estar vulnerável a vírus e software maligno.

-   As definições que tenham sido eventualmente alteradas no seu dispositivo quando o adicionou, por exemplo, a desativação da câmara, deixam de ser aplicáveis.

-   O seu computador deixará de receber atualizações de software automáticas ou atualizações de software antivírus do serviço do Intune. No entanto, dependendo da configuração, o seu computador poderá continuar a receber atualizações do Windows Server Update Services, Windows Update ou Microsoft Update.

Além disso, no Windows 8.1:

-   Deixará de poder utilizar aplicações e dados da empresa no seu dispositivo.

-   Algumas aplicações de e-mail, como o Windows Mail, deixarão de conseguir aceder ao e-mails da empresa armazenados no seu dispositivo.

-   Pode não conseguir ligar-se à rede da sua empresa através de Wi-Fi ou de uma Rede Privada Virtual (VPN).

-   É possível que deixe de ter acesso a alguns recursos da empresa, como partilhas de ficheiros ou web sites internos, no seu dispositivo.

## Windows 10 Mobile, Windows Phone 8.1 ou Windows Phone 8

-   A aplicação Portal da Empresa é desinstalada no dispositivo, o que significa que este deixa de aparecer no Portal da Empresa, e não poderá instalar aplicações a partir da aplicação Portal da Empresa ou do Web site Portal da Empresa.

-   Deixará de poder utilizar aplicações e dados da empresa no seu dispositivo.

-   As definições alteradas no seu dispositivo quando o adicionou, por exemplo, a desativação da câmara ou o comprimento necessário específico de uma palavra-passe, deixam de ser aplicáveis.

    > [!IMPORTANT]
    > A única exceção são as políticas de encriptação, que ainda são aplicáveis. Se a política da sua empresa exigir a encriptação do seu Windows Phone, a única forma de desencriptar o telemóvel implica repô-lo através do menu **Definições** do Windows Phone.

## Windows RT com o Windows 8.1 ou o Windows RT

-   A aplicação Portal da Empresa é desinstalada no dispositivo, o que significa que este deixa de aparecer no portal da empresa, e não poderá instalar aplicações a partir da aplicação Portal da Empresa.

-   Deixará de poder utilizar aplicações e dados da empresa no seu dispositivo.

-   As definições alteradas no seu dispositivo quando o adicionou, por exemplo, a desativação da câmara ou o comprimento necessário específico de uma palavra-passe, deixam de ser aplicáveis.

-   É possível que deixe de conseguir ligar-se à rede da sua empresa através de Wi-Fi ou de uma Rede Privada Virtual (VPN).

-   É possível que deixe de ter acesso a alguns recursos da empresa, como partilhas de ficheiros ou web sites internos, no seu dispositivo.

-   Algumas aplicações de e-mail, como o Windows Mail, deixarão de conseguir aceder ao e-mails da empresa armazenados no seu dispositivo.

Ao remover o seu dispositivo Windows RT, ocorrerá o seguinte:

-   A aplicação Portal da Empresa é desinstalada no dispositivo, o que significa que este deixa de aparecer no portal da empresa, e não poderá instalar aplicações a partir da aplicação Portal da Empresa.

-   Deixará de poder utilizar aplicações e dados da empresa no seu dispositivo.

-   As definições alteradas no seu dispositivo quando o adicionou, por exemplo, a desativação da câmara ou o comprimento necessário específico de uma palavra-passe, deixam de ser aplicáveis.

Se tiver dúvidas, contacte o administrador de TI. Para encontrar as informações de contacto dele, verifique o [Web site do Portal da Empresa](http://portal.manage.microsoft.com).

### Consulte também
[Utilizar o dispositivo Windows com o Intune](using-your-windows-device-with-intune.md)

<!--HONumber=Jun16_HO2-->



---
title: "Dispositivos móveis e browsers suportados | Microsoft Intune"
description: Apresenta listas de dispositivos suportados e os browsers que podem executar o Intune
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 12/01/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: aeeccfa4-0f14-447e-a3df-c8435c8a4bb2
ms.reviewer: damionw
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: eeb85a28ea6f99a0123ec5df3b0d476a678b85cb
ms.openlocfilehash: b0eab195c00aae4b593fff535179a1b993c36dde


---

# <a name="supported-devices-and-web-browsers-for-intune"></a>Dispositivos e browsers suportados pelo Intune

Como administrador do Intune, pode gerir um intervalo de dispositivos a partir de um browser. Este tópico proporciona:

- [Lista de plataformas de dispositivos suportados](#intune-supported-devices)
- [Lista de browsers suportados que utilizam o Intune](#intune-supported-web-browsers)

## <a name="intune-supported-devices"></a>Dispositivos suportados pelo Intune

Pode gerir os seguintes dispositivos com a gestão de dispositivos móveis do Intune:

[!INCLUDE[mdm-supported-devices](../includes/mdm-supported-devices.md)]

O Intune não pode servir para gerir os sistemas operativos Windows Server.

A gestão de dispositivos do Intune proporciona [estas capacidades](mobile-device-management-capabilities-in-microsoft-intune.md).

### <a name="windows-pc-software-client"></a>Software cliente em PC com Windows

Um [software cliente do Intune](/intune/deploy-use/manage-windows-pcs-with-microsoft-intune) pode ser implementado e instalado em PCs com Windows como um método alternativo de inscrição. Pode utilizar o software cliente do Intune para gerir PCs com Windows 7 e versões posteriores, exceto o Windows 10 Home edition. A gestão de PCs com o software de cliente fornece [estas funcionalidades](windows-pc-management-capabilities-in-microsoft-intune.md).

### <a name="exchange-activesync-management"></a>Gestão do Exchange ActiveSync

Pode gerir [dispositivos do Exchange ActiveSync](/intune/deploy-use/mobile-device-management-with-exchange-activesync-and-microsoft-intune) na consola do Intune. Esta opção proporciona um conjunto limitado de capacidades de gestão, em comparação com os outros métodos. Ver [Capabilities of built-in Mobile Device Management in Office 365](https://support.office.com/article/Capabilities-of-built-in-Mobile-Device-Management-for-Office-365-a1da44e5-7475-4992-be91-9ccec25905b0) (Capacidades de Gestão de Dispositivos Móveis Incorporada no Office 365) para obter uma lista de dispositivos suportados.

## <a name="intune-supported-web-browsers"></a>Browsers suportados do Intune

As diferentes tarefas administrativas necessitam que utilize um dos seguintes sites administrativos.

- [Portal do Office 365](http://go.microsoft.com/fwlink/p/?LinkId=698854)
- [Consola do administrador do Microsoft Intune](https://admin.manage.microsoft.com/)

|Funcionalidade do Intune |Browsers suportados|
|---------|---------|
|**Consola de Administração do Intune**     |  Internet Explorer 10 ou posterior<br /><br />Google Chrome (versões anteriores à versão 42)<br /><br />Mozilla Firefox com o Silverlight ativado<br />**Nota:** o Mozilla irá remover o suporte do Silverlight a partir de março de 2017. [Saiba mais](https://go.microsoft.com/fwlink/?linkid=836872). |
|**Portal de Administração do Office 365**     |Todos os browsers, incluindo browsers para dispositivos móveis e browsers geridos  |
|**Site do Portal da Empresa**     |**Em dispositivos móveis:** utilize o browser predefinido de cada plataforma suportada   <br /><br />**Em PCs com Windows:** Internet Explorer 10 ou posterior ou o Microsoft Edge<br /><br />**Em Mac OS X 10.9 ou posterior:** Apple Safari    |

> [!Note]
> O Microsoft Edge e os browsers para dispositivos móveis não são suportados na consola de administração porque não suportam o [Microsoft Silverlight](https://msdn.microsoft.com/en-us/library/cc838158(v=vs.95).aspx). A consola do Intune está a abandonar a experiência do Silverlight ao longo de um período de tempo; eventualmente, todas as funcionalidades de gestão de aplicações e dispositivos móveis do Intune serão [disponibilizadas no novo portal do Microsoft Azure](https://blogs.technet.microsoft.com/enterprisemobility/2015/11/17/enhancing-managed-mobile-productivity/).


Apenas os utilizadores com permissões de administrador de serviços ou administradores inquilinos com a função de administrador global podem iniciar sessão neste portal. Para aceder à consola de administração, a sua conta tem de ter uma licença para utilizar o Intune e o estado de início de sessão definido como **Permitido**.
>[!div class="step-by-step"]

>[&larr; **Pré-requisitos**](what-to-know-before-you-start-microsoft-intune.md)     [**Redes** &rarr;](network-bandwidth-use.md)  



<!--HONumber=Dec16_HO2-->



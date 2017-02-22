---
title: "Dispositivos suportados – Microsoft Intune | Documentos da Microsoft"
description: "Apresenta uma lista de plataformas de dispositivos e browsers suportados para a gestão de dispositivos no Intune"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 02/07/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5d1ac59c-a885-4276-8576-f3cf81c2d268
ms.reviewer: angrobe
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: b3732d0c6461f9fb8462ae5584055204d597aae0
ms.openlocfilehash: 0af4f49713a65900079d69a09f20d210797c935c


---

# <a name="supported-devices-and-browsers"></a>Dispositivos e browsers suportados

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Este artigo destina-se a administradores de sistemas responsáveis pela gestão de dispositivos na empresa. Para obter ajuda na instalação do Intune no seu telefone, veja [Utilizar dispositivos geridos para trabalhar](https://docs.microsoft.com/intune/enduser/company-portal-frequently-asked-questions).

Antes de começar a configurar o Microsoft Intune, reveja os seguintes requisitos:

- [Dispositivos e computadores suportados](#intune-supported-devices)
- [Lista de browsers suportados que utilizam o Intune](#intune-supported-web-browsers)

Também deverá estar familiarizado com a [utilização de largura de banda de rede do Intune](network-bandwidth-use.md).

## <a name="intune-supported-devices"></a>Dispositivos suportados pelo Intune

Pode gerir os seguintes dispositivos com a gestão de dispositivos móveis do Intune:

[!INCLUDE[mdm-supported-devices](../includes/mdm-supported-devices.md)]

O Intune não pode servir para gerir os sistemas operativos Windows Server.

A gestão de dispositivos do Intune proporciona [estas capacidades](mobile-device-management-capabilities-in-microsoft-intune.md).

### <a name="windows-pc-software-client"></a>Software cliente em PC com Windows

Um [software cliente do Intune](/intune/deploy-use/manage-windows-pcs-with-microsoft-intune) pode ser implementado e instalado em PCs com Windows como um método alternativo de inscrição. Pode utilizar o cliente do software Intune para gerir computadores com o Windows 7 e posterior, com a exceção da edição Windows 10 Home. A gestão de PCs com o software de cliente fornece [estas funcionalidades](windows-pc-management-capabilities-in-microsoft-intune.md).

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

>[**Rede** &rarr;](network-bandwidth-use.md)  



<!--HONumber=Feb17_HO2-->



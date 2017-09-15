---
title: "Dispositivos suportados – Microsoft Intune"
description: "Apresenta uma lista de plataformas de dispositivos e browsers suportados para a gestão de dispositivos no Intune"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 06/23/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5d1ac59c-a885-4276-8576-f3cf81c2d268
ms.reviewer: angrobe
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 00fc685062c090b40e20ed3dfa30afbeeb5c9780
ms.sourcegitcommit: e10dfc9c123401fabaaf5b487d459826c1510eae
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/09/2017
---
# <a name="supported-devices-and-browsers"></a>Dispositivos e browsers suportados

[!INCLUDE[both-portals](./includes/note-for-both-portals.md)]

Este artigo destina-se a administradores de sistemas responsáveis pela gestão de dispositivos na empresa. Para obter ajuda na instalação do Intune no seu telefone, veja [Utilizar dispositivos geridos para trabalhar](/intune-user-help/company-portal-frequently-asked-questions).

Antes de começar a configurar o Microsoft Intune, reveja os seguintes requisitos:

- [Dispositivos e computadores suportados](#intune-supported-devices)
- [Lista de browsers suportados que utilizam o Intune](#intune-supported-web-browsers)

Também deverá estar familiarizado com a [utilização de largura de banda de rede do Intune](network-bandwidth-use.md) ([portal clássico](/intune-classic/get-started/network-bandwidth-use)).

## <a name="intune-supported-devices"></a>Dispositivos suportados pelo Intune

Pode gerir os seguintes dispositivos com a gestão de dispositivos móveis do Intune:

[!INCLUDE[mdm-supported-devices](./includes/mdm-supported-devices.md)]

O Intune não pode servir para gerir os sistemas operativos Windows Server.

### <a name="windows-pc-software-client"></a>Software cliente em PC com Windows

Um [software cliente do Intune](/intune-classic/deploy-use/manage-windows-pcs-with-microsoft-intune) pode ser implementado e instalado em PCs com Windows como um método alternativo de inscrição. Esta funcionalidade está apenas disponível com o portal clássico do Intune. Pode utilizar o cliente do software Intune para gerir computadores com o Windows 7 e posterior, com a exceção da edição Windows 10 Home.

<!--  ### Exchange ActiveSync management

You can manage [Exchange ActiveSync devices](/intune-classic/deploy-use/mobile-device-management-with-exchange-activesync-and-microsoft-intune) from the Intune console. This option provides a limited set of management capabilities when compared to the other methods. See [Capabilities of built-in Mobile Device Management in Office 365](https://support.office.com/article/Capabilities-of-built-in-Mobile-Device-Management-for-Office-365-a1da44e5-7475-4992-be91-9ccec25905b0) for a list of supported devices.  -->

## <a name="intune-supported-web-browsers"></a>Browsers suportados do Intune

As diferentes tarefas administrativas necessitam que utilize um dos seguintes sites administrativos.

- [Portal do Office 365](http://go.microsoft.com/fwlink/p/?LinkId=698854)
- [Portal do Azure](https://portal.azure.com/)

Os seguintes browsers são suportados para estes portais:
- Microsoft Edge (versão mais recente)
- Microsoft Internet Explorer 11
- Safari (versão mais recente, apenas Mac)
- Chrome (versão mais recente)
- Firefox (versão mais recente)

### <a name="intune-classic-portal"></a>Portal clássico do Intune

As funcionalidades só clássicas do Intune, tais como o cliente de software de PC do Intune e a integração com os parceiros de Defesa Contra Ameaças a Dispositivos Móveis, só estão disponíveis no portal clássico do Intune (https://manage.microsoft.com). O portal clássico do Intune necessita do suporte do browser Silverlight.

Os seguintes browsers Silverlight suportam a consola do Intune:
- Internet Explorer 10 ou posterior
- Google Chrome (versões anteriores à versão 42)
- Mozilla Firefox com o Silverlight ativado – [Saiba mais](https://go.microsoft.com/fwlink/?linkid=836872)

> [!Note]
> O Microsoft Edge e os browsers para dispositivos móveis não são suportados no portal clássico do Intune porque não suportam o [Microsoft Silverlight](https://msdn.microsoft.com/library/cc838158(v=vs.95).aspx).

Apenas os utilizadores com permissões de administrador de serviços ou administradores inquilinos com a função de administrador global podem iniciar sessão neste portal. Para aceder à consola de administração, a sua conta tem de ter uma licença para utilizar o Intune e o estado de início de sessão definido como **Permitido**.

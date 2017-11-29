---
title: "Dispositivos suportados – Microsoft Intune"
description: "Apresenta uma lista de plataformas de dispositivos e browsers suportados para a gestão de dispositivos no Intune"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 11/06/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5d1ac59c-a885-4276-8576-f3cf81c2d268
ms.reviewer: angrobe
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: b168cbf5282b4e016133d071c56c8abd54c2e23b
ms.sourcegitcommit: dc2595bec05206a826cd10cb834bf6043145c917
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/14/2017
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

### <a name="supported-samsung-knox-standard-devices"></a>Dispositivos Samsung KNOX Standard suportados

A aplicação Portal da Empresa tenta apenas a ativação do Samsung KNOX durante a inscrição MDM se o dispositivo for apresentado na [lista de dispositivos KNOX suportados](https://www.samsungknox.com/knox-supported-devices/knox-workspace). Isto ajuda a evitar erros de ativação de KNOX que impedem a inscrição MDM. Os dispositivos que não suportam a ativação do Samsung KNOX são inscritos como dispositivos Android padrão. Um dispositivo Samsung pode ter alguns números de modelo que suportem o KNOX, enquanto outros não. Verifique a compatibilidade com o KNOX junto do revendedor do seu dispositivo antes da compra e implementação de dispositivos Samsung.

A seguinte lista de modelos de dispositivos Samsung não suporta KNOX e são inscritos como dispositivos Android nativos pela aplicação Portal da Empresa para Android:

| **Nome do Dispositivo** | **Números de Modelo do Dispositivo** |
| --- | --- |
| Galaxy Avant | SM-G386T |
| Galaxy Core 2/Core 2 Duos | SM-G355H<br>SM-G355M |
| Galaxy Core Lite | SM-G3588V |
| Galaxy Core Prime | SM-G360H |
| Galaxy Core LTE | SM-G386F<br>SM-G386W |
| Galaxy Grand | GT-I9082L<br>GT-I9082<br>GT-I9080L |
| Galaxy Grand 3 | SM-G7200 |
| Galaxy Grand Neo | GT-I9060I |
| Galaxy Grand Prime Value Edition | SM-G531H |
| Galaxy J Max | SM-T285YD |
| Galaxy J1 | SM-J100H<br>SM-J100M<br>SM-J100ML |
| Galaxy J1 Ace | SM-J110F<br>SM-J110H |
| Galaxy J1 Mini | SM-J105M |
| Galaxy J2/J2 Pro | SM-J200H<br>SM-J210F |
| Galaxy J3 | SM-J320F<br>SM-J320FN<br>SM-J320H<br>SM-J320M |
| Galaxy K Zoom | SM-C115 |
| Galaxy Light | SGH-T399N |
| Galaxy Note 3 | SM-N9002<br>SM-N9009 |
| Galaxy Note 7/Note 7 Duos | SM-N930S<br>SM-N9300<br>SM-N930F<br>SM-N930T<br>SM-N9300<br>SM-N930F<br>SM-N930S<br>SM-N930T |
| Galaxy Note 10.1 3G | SM-P602 |
| Galaxy S2 Plus | GT-I9105P |
| Galaxy S3 Mini | SM-G730A<br>SM-G730V |
| Galaxy S3 Neo | GT-I9300<br>GT-I9300I |
| Galaxy S4 | SM-S975L |
| Galaxy S4 Neo | SM-G318ML |
| Galaxy S5 | SM-G9006W |
| Galaxy S6 Edge | 404SC |
| Galaxy Tab A 7.0&quot; | SM-T280<br>SM-T285 |
| Galaxy Tab 3 7&quot;/Tab 3 Lite 7&quot; | SM-T116<br>SM-T210<br>SM-T211 |
| Galaxy Tab 3 8.0&quot; | SM-T311 |
| Galaxy Tab 3 10.1&quot; | GT-P5200<br>GT-P5210<br>GT-P5220 |
| Galaxy Trend 2 Lite | SM-G318H |
| Galaxy V Plus | SM-G318HZ |
| Galaxy Young 2 Duos | SM-G130BU |

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

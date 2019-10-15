---
title: Sistemas operacionais e navegadores com suporte do Microsoft Intune
titleSuffix: ''
description: Lista os navegadores e plataformas de dispositivo com suporte para o gerenciamento de dispositivos do Intune
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 07/29/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 5d1ac59c-a885-4276-8576-f3cf81c2d268
ms.reviewer: dougeby
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2d2777f2caabc24a457fc407b3e47facb1f6fc3c
ms.sourcegitcommit: 45d7c76e760c5117bf134fb57f7e248e5b6c4ad5
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72314604"
---
# <a name="supported-operating-systems-and-browsers-in-intune"></a>Sistemas operacionais e navegadores com suporte no Intune

Antes de configurar Microsoft Intune, examine os sistemas operacionais e navegadores com suporte.

Para obter ajuda para instalar o Intune em seu dispositivo, consulte [usando dispositivos gerenciados para realizar o trabalho](https://docs.microsoft.com/intune-user-help/company-portal-frequently-asked-questions) e [uso de largura de banda de rede do Intune](network-bandwidth-use.md).

Para obter mais informações sobre o suporte ao provedor de serviços de configuração, visite a [referência do provedor de serviços de configuração](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference).

## <a name="intune-supported-operating-systems"></a>Sistemas operacionais com suporte do Intune

Você pode gerenciar dispositivos que executam os seguintes sistemas operacionais:

[!INCLUDE [mdm-supported-devices](../../intune-classic/includes/mdm-supported-devices.md)]

### <a name="supported-samsung-knox-standard-devices"></a>Dispositivos Samsung Knox Standard com suporte

Para evitar erros de ativação do Knox que impedem o registro de MDM, o aplicativo Portal da Empresa só tentará a ativação do Samsung Knox durante o registro do MDM se o dispositivo aparecer na [lista de dispositivos Knox com suporte](https://www.samsungknox.com/knox-supported-devices/knox-workspace). Dispositivos que não dão suporte à ativação do Samsung Knox se registram como dispositivos Android padrão. Um dispositivo Samsung pode ter alguns números de modelo que dão suporte a Knox, enquanto outros não. Verifique a compatibilidade do Knox com o revendedor do dispositivo antes de comprar e implantar dispositivos Samsung.

> [!NOTE]
> O registro de dispositivos Samsung Knox pode exigir que você [habilite o acesso aos servidores Samsung](https://support.samsungknox.com/hc/articles/115013833108-Our-corporate-devices-are-behind-a-firewall-How-do-I-enable-Knox-Workspace-devices-to-contact-Samsung-servers). 

A lista a seguir dos modelos de dispositivo Samsung não oferece suporte a Knox. Eles são registrados como dispositivos Android nativos pelo aplicativo Portal da Empresa para Android:

| **Nome do dispositivo** | **Números de modelo do dispositivo** |
| --- | --- |
| Muito do Galaxy | SM-G386T |
| Galaxy Core 2/Core 2 duos | SM-G355H<br>SM-G355M |
| Galaxy Core Lite | SM-G3588V |
| Prime principal do Galaxy | SM-G360H |
| Galaxy Core LTE | SM-G386F<br>SM-G386W |
| Geral do Galaxy | GT-I9082L<br>GT-I9082<br>GT-I9080L |
| Galaxy global 3 | SM-G7200 |
| Neo geral do Galaxy | GT-I9060I |
| Edição de valor principal do Galaxy | SM-G531H |
| Galaxy J Max | SM-T285YD |
| J1 do Galaxy | SM-J100H<br>SM-J100M<br>SM-J100ML |
| Ace J1 do Galaxy | SM-J110F<br>SM-J110H |
| Mini J1 do Galaxy | SM-J105M |
| Galaxy J2/J2 pro | SM-J200H<br>SM-J210F |
| J3 do Galaxy | SM-J320F<br>SM-J320FN<br>SM-J320H<br>SM-J320M |
| Zoom do Galaxy K | SM-C115 |
| Luz do Galaxy | SGH-T399N |
| Observação do Galaxy 3 | SM-N9002<br>SM-N9009 |
| Observação do Galaxy 7/observação 7 duos | SM-N930S<br>SM-N9300<br>SM-N930F<br>SM-N930T<br>SM-N9300<br>SM-N930F<br>SM-N930S<br>SM-N930T |
| Observação do Galaxy 10,1 3G | SM-P602 |
| Galaxy S2 Plus | GT-I9105P |
| Galaxy S3 mini | SM-G730A<br>SM-G730V |
| Galaxy S3 neo | GT-I9300<br>GT-I9300I |
| S4 do Galaxy | SM-S975L |
| Neo do Galaxy S4 | SM-G318ML |
| Galaxy S5 | SM-G9006W |
| Borda do Galaxy S6 | 404SC |
| Guia do Galaxy A 7.0 @ no__t-0 | SM-T280<br>SM-T285 |
| Guia Galaxy 3 7 @ no__t-0/Tab 3 Lite 7 @ no__t-1 | SM-T116<br>SM-T210<br>SM-T211 |
| Guia Galaxy 3 8.0 @ no__t-0 | SM-T311 |
| Guia Galaxy 3 10.1 @ no__t-0 | GT-P5200<br>GT-P5210<br>GT-P5220 |
| Tendência do Galaxy 2 Lite | SM-G318H |
| Galaxy V Plus | SM-G318HZ |
| Galaxy Young 2 duos | SM-G130BU |


### <a name="windows-pc-software-client"></a>Cliente de software do computador Windows

Um [cliente de software do Intune](../manage-windows-pcs-with-microsoft-intune.md) pode ser implantado e instalado em computadores Windows como um método de registro alternativo. Essa funcionalidade só está disponível usando o portal clássico do Intune. Você pode usar o cliente de software do Intune para gerenciar computadores com Windows 7 e posteriores, com exceção do Windows 10 Home Edition.

<!--  ### Exchange ActiveSync management

You can manage [Exchange ActiveSync devices](../enrollment/device-enrollment.md#mobile-device-management-with-exchange-activesync-and-intune) from the Intune console. This option provides a limited set of management capabilities when compared to the other methods. See [Capabilities of built-in Mobile Device Management in Office 365](https://support.office.com/article/Capabilities-of-built-in-Mobile-Device-Management-for-Office-365-a1da44e5-7475-4992-be91-9ccec25905b0) for a list of supported devices.  -->

## <a name="intune-supported-web-browsers"></a>Navegadores da Web com suporte do Intune

Diferentes tarefas administrativas exigem que você use um dos seguintes sites administrativos.

- [Centro de administração do Microsoft 365](http://go.microsoft.com/fwlink/p/?LinkId=698854)
- [Portal do Azure](https://portal.azure.com/)

Os seguintes navegadores têm suporte para estes portais:
- Microsoft Edge (versão mais recente)
- Microsoft Internet Explorer 11
- Safari (última versão, somente Mac)
- Chrome (versão mais recente)
- Firefox (versão mais recente)




### <a name="intune-classic-portal"></a>Portal clássico do Intune

O portal clássico do Intune é usado somente para gerenciar dispositivos registrados com o cliente de software de computador do Intune (https://manage.microsoft.com). O portal clássico do Intune requer suporte ao navegador do Silverlight.

Os seguintes navegadores do Silverlight dão suporte ao console do Intune:
- Internet Explorer 10 ou posterior
- Google Chrome (versões anteriores à versão 42)
- Mozilla Firefox com Silverlight habilitado (versões anteriores à versão 56)

> [!Note]
> O Microsoft Edge e navegadores móveis não têm suporte para o portal clássico do Intune porque não dão suporte ao [Microsoft Silverlight](https://msdn.microsoft.com/library/cc838158(v=vs.95).aspx).

Somente usuários com permissões de administrador de serviço ou administradores de locatário com a função de administrador global podem entrar neste portal. Para acessar o console de administração, sua conta deve ter uma licença para usar o Intune e um status de entrada de **permitido**.

---
title: Em desenvolvimento-Microsoft Intune
titleSuffix: ''
description: Recursos de Microsoft Intune em desenvolvimento
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 12/19/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.assetid: 25b3c26e-cf4e-4152-8306-bf4be4af2ad1
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 35e4612c9aa482204ea61c46c5cc56051874e6de
ms.sourcegitcommit: e166b9746fcf0e710e93ad012d2f52e2d3ed2644
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/19/2019
ms.locfileid: "75207405"
---
# <a name="in-development-for-microsoft-intune---december-2019"></a>Em desenvolvimento para Microsoft Intune-dezembro de 2019

Para ajudar na preparação e no planejamento, esta página lista as atualizações da interface do usuário do Intune e os recursos que estão em desenvolvimento, mas ainda não foram lançados. Além das informações nesta página:

- Se prevemos que você precisará tomar medidas antes de uma alteração, publicaremos uma postagem complementar no centro de mensagens do Office.
- Quando um recurso entra em produção, seja uma visualização ou geralmente disponível, a descrição do recurso passará dessa [página para as novidades.](whats-new.md)
- Esta página e a página [novidades](whats-new.md) são atualizadas periodicamente. Volte a consultar posteriormente para obter mais atualizações.
- Consulte o [roteiro de Microsoft 365](https://www.microsoft.com/microsoft-365/roadmap?rtc=2&filters=EMS) para resultados estratégicos e cronogramas.

> [!NOTE]
> Esta página reflete nossas expectativas atuais sobre os recursos do Intune em uma versão futura. As datas e os recursos individuais podem mudar. Esta página não descreve todos os recursos no desenvolvimento.

**RSS feed**: descubra quando essa página é atualizada copiando e colando a seguinte URL em seu leitor de feed: `https://docs.microsoft.com/api/search/rss?search=%22in+development+-+microsoft+intune%22&locale=en-us`

<!--
## What's coming to Intune in the Azure portal 
## What's coming to Intune apps
## Notices
-->

<!-- Common categories:  
## App management
## Device configuration
## Device enrollment
## Device management
## Intune apps
## Monitor and troubleshoot
## Role-based access control
## Security

-->
 
<!-- ***********************************************-->
## <a name="app-management"></a>Gestão de aplicações

### <a name="user-licensed-vpp-apps-for-user-enrollment-ios-devices---5619268---"></a>Aplicativos de VPP licenciados pelo usuário para dispositivos iOS de registro de usuário<!-- 5619268 -->
Para dispositivos iOS de registro de usuário, os usuários finais não serão mais apresentados com aplicativos VPP licenciados para dispositivos implantados como disponíveis. No entanto, os usuários finais continuarão a ver todos os aplicativos VPP licenciados pelo usuário dentro do Portal da Empresa. Para obter mais informações sobre aplicativos VPP, consulte [como gerenciar aplicativos Ios e MacOS adquiridos por meio de Apple Volume Purchase Program com Microsoft Intune](~/apps/vpp-apps-ios.md).

### <a name="retrieve-personal-recovery-key-from-mem-encrypted-macos-devices---4851745---"></a>Recuperar a chave de recuperação pessoal de dispositivos macOS criptografados com memória<!-- 4851745 -->
Os usuários finais poderão recuperar sua chave de recuperação pessoal (FileVault Key) usando o aplicativo Portal da Empresa do iOS. O dispositivo que tem a chave de recuperação pessoal deve ser registrado com o Intune e criptografado com o FileVault por meio do Intune. Usando o aplicativo Portal da Empresa do iOS, um usuário final pode abrir o modo de exibição da Web do Safari e recuperar sua chave de recuperação pessoal. No Intune, selecione **dispositivos** > *o dispositivo MacOS criptografado e registrado* > **obter a chave de recuperação**. Para obter mais informações sobre FileVault, consulte [criptografia FileVault para MacOS](~/protect/encrypt-devices.md#filevault-encryption-for-macos).

### <a name="display-notifications-for-the-company-portal-app-on-windows---1808082----"></a>Exibir notificações para o aplicativo Portal da Empresa no Windows<!-- 1808082  -->
Atualizaremos o aplicativo Portal da Empresa em dispositivos Windows para exibir notificações do sistema para os usuários, mesmo quando o aplicativo for fechado. A atualização mostrará notificações para aplicativos disponíveis somente quando o status da instalação for concluído ou com falha. O aplicativo Portal da Empresa não mostrará notificações para os aplicativos necessários.

### <a name="display-installation-status-messages-for-the-company-portal-app---2514416----"></a>Exibir mensagens de status de instalação para o aplicativo Portal da Empresa<!-- 2514416  -->
O aplicativo Portal da Empresa mostrará mensagens de status de instalação de aplicativo adicionais aos usuários finais. As seguintes condições serão aplicadas a novos recursos de dependência do Win32:
- Falha ao instalar o aplicativo. As dependências definidas pelo administrador não foram atendidas.

<!-- ***********************************************-->
## <a name="device-configuration"></a>Configuração do dispositivo

### <a name="add-automatic-proxy-settings-to-wi-fi-profiles-for-android-enterprise-work-profiles---4490822-idready---"></a>Adicionar configurações de proxy automáticas a perfis de Wi-Fi para perfis de trabalho do Android Enterprise<!-- 4490822 idready -->
Em dispositivos Android Enterprise de perfil de trabalho, você pode criar perfis de Wi-Fi. Ao escolher o tipo de empresa Wi-Fi, você também pode inserir o tipo de protocolo EAP (Extensible Authentication Protocol) usado em sua rede Wi-Fi.

Em uma atualização futura, ao escolher o tipo Enterprise, você poderá inserir configurações de proxy automáticas, incluindo uma URL do servidor proxy, como `proxy.contoso.com`.

Para ver as configurações de Wi-Fi atuais que você pode configurar, vá para [Adicionar configurações de Wi-Fi para dispositivos que executam o Android Enterprise e Android quiosque no Microsoft Intune](../configuration/wi-fi-settings-android-enterprise.md).

Aplica-se a:
- Perfil de trabalho do Android Enterprise

### <a name="wired-network-device-configuration-profiles-for-macos-devices---3508686----"></a>Perfis de configuração de dispositivo de rede com fio para dispositivos macOS<!-- 3508686  -->
Um novo perfil de configuração de dispositivo macOS estará disponível para configurar redes com fio (**configuração de dispositivo** > **perfis** > **Criar perfil** > **MacOS** para plataforma > **rede com fio** para o tipo de perfil). Use esse recurso para criar perfis 802.1 x para gerenciar redes com fio e implantar essas redes com fio em seus dispositivos macOS.

Aplica-se a:
- macOS


<!-- ***********************************************-->
<!--## Device enrollment-->

<!-- ***********************************************-->
<!--## Device management-->


<!-- ***********************************************-->
<!--## Intune apps-->
 

<!-- ***********************************************-->

<!--
## Monitoring and troubleshooting
-->


<!-- ***********************************************-->
<!--## Role-based access control-->


<!-- ***********************************************-->

<!--
## Security
-->

<!-- ***********************************************-->
## <a name="notices"></a>Avisos

[!INCLUDE [Intune notices](../includes/intune-notices.md)]

## <a name="see-also"></a>Consulte também
Para obter detalhes sobre os desenvolvimentos recentes, consulte [What ' s New in Microsoft Intune](whats-new.md).



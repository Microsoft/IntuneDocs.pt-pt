---
title: Recursos de gerenciamento de dispositivo no Microsoft Intune
description: Leia este tópico para saber como o Intune pode ajudá-lo a gerenciar dispositivos registrados.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/16/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: dougeby
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: bf862e59e135a875f5f18af731c581f3e5ea89d5
ms.sourcegitcommit: dd6755383ba89824d1cc128698a65fde6bb2de55
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/14/2019
ms.locfileid: "72306612"
---
# <a name="enrolled-device-management-capabilities-of-microsoft-intune"></a>Recursos de gerenciamento de dispositivos registrados do Microsoft Intune

Microsoft Intune permite que você gerencie uma variedade de dispositivos *registrando* -os no serviço. Você pode registrar alguns tipos de dispositivo por conta própria ou os usuários podem se registrar usando o aplicativo do *portal da empresa* . O registro permite que eles naveguem e instalem aplicativos, certifique-se de que seus dispositivos estejam em conformidade com as políticas da empresa e entrem em contato com o suporte de ti.

Este artigo fornece uma lista completa dos recursos que você obtém depois que os dispositivos são registrados.

Gerenciamento, inventário, implantação de aplicativo, provisionamento e desativação são tratados por meio do Intune no portal do Azure.

Os usuários têm acesso ao portal da empresa, que permite que eles instalem aplicativos, registrem e removam dispositivos e entrem em contato com seu departamento de ti ou assistência técnica.



## <a name="device-security-and-configuration"></a>Configuração e segurança do dispositivo

|Capacidade|Detalhes|Mais informações|
|--------------|-----------|--------------------|
|Políticas de configuração<br><br>Políticas personalizadas| Permite que você gerencie muitas configurações e recursos em dispositivos móveis em sua organização. Por exemplo, você pode exigir uma senha, limitar o número de tentativas com falha, limitar a quantidade de tempo antes que a tela seja bloqueada, definir a expiração da senha e evitar senhas usadas anteriormente. Você também pode controlar o uso de recursos de hardware e software, como a câmera do dispositivo ou o navegador da Web.<br><br>Use políticas personalizadas quando as políticas de configuração não contiverem as configurações necessárias. Para dispositivos iOS, você pode importar as configurações exportadas da ferramenta Apple Configurator. Para outros dispositivos, você pode usar as configurações de OMA-URI (Open Mobile Alliance Uniform Resource Identifier) para definir as configurações e os recursos no dispositivo.|[Gerenciar configurações e recursos em seus dispositivos com políticas de Microsoft Intune](../protect/device-compliance-get-started.md)|
|Apagamento remoto, bloqueio remoto e redefinição de senha|Apaga dados confidenciais quando um dispositivo é perdido ou roubado. Por exemplo, você pode bloquear o dispositivo remotamente, restaurá-lo para as configurações de fábrica ou apagar apenas os dados corporativos.<br><br>Você pode redefinir senhas se os usuários perderem o acesso ao dispositivo, bloquear dispositivos ausentes ou roubados ou até mesmo apagar dados de dispositivos ausentes ou roubados.|Ajudar a proteger seus dispositivos com [bloqueio remoto](../remote-actions/device-remote-lock.md) e [redefinição de senha](../remote-actions/device-passcode-reset.md)|
|Modo de quiosque|Permite bloquear determinados recursos de dispositivos móveis, como capturas de tela e interruptores. Também permite restringir os dispositivos para executar um único aplicativo que você especificar. |[configurações de política de configuração do iOS no Microsoft Intune](../configuration/device-restrictions-ios.md)|
|Redefinição do AutoPilot|Envia uma tarefa para o dispositivo para iniciar o processo de redefinição remotamente, evitando a necessidade da equipe de ti ou de outros administradores de visitar cada computador para iniciar o processo. Quando a redefinição do AutoPilot é usada em um dispositivo, o usuário primário do dispositivo será removido. O próximo usuário que entrar após a redefinição será definido como o usuário primário.|[Redefinição do Windows AutoPilot remoto](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-autopilot-reset#reset-devices-with-remote-windows-autopilot-reset)|

## <a name="app-management"></a>Gerenciamento de aplicativos

|Capacidade|Detalhes|Mais informações|
|--------------|-----------|--------------------|
|Implantação e gerenciamento de aplicativos|Fornece uma variedade de ferramentas para ajudá-lo a gerenciar aplicativos móveis por meio de seu ciclo de vida, incluindo a implantação de aplicativos de arquivos de instalação e lojas de aplicativos, monitoramento detalhado do status do aplicativo e remoção do aplicativo.|[Implantar aplicativos no Microsoft Intune](../apps/apps-deploy.md)|
|Aplicativos em conformidade e em não conformidade|Permite que você especifique listas de aplicativos compatíveis (que os usuários têm permissão para instalar) e aplicativos incompatíveis (que os usuários não têm permissão para instalar).|[configurações de política do iOS no Microsoft Intune](../configuration/device-restrictions-ios.md)|
|Gestão de aplicações móveis|Configura as restrições para aplicativos usando o gerenciamento de aplicativos móveis para todos os dispositivos gerenciados com o Intune e não gerenciados com o Intune. Você pode aumentar a segurança dos dados da empresa restringindo operações, como copiar e colar, backup externo de dados e a transferência de dados entre aplicativos.|[Configurar e implantar políticas de gerenciamento de aplicativos móveis no console do Microsoft Intune](../developer/app-wrapper-prepare-android.md)|
|configuração de aplicativo móvel iOS|Usa políticas de configuração de aplicativo móvel para fornecer configurações para aplicativos iOS que podem ser necessários quando o usuário executa o aplicativo. Por exemplo, um aplicativo pode exigir que o usuário especifique um número de porta ou informações de logon. Você pode simplificar a configuração do aplicativo e reduzir o número de chamadas de suporte.|[Configurar aplicativos iOS com as políticas de configuração de aplicativo móvel no Microsoft Intune](../apps/app-configuration-policies-use-ios.md)|
|perfis de provisionamento de aplicativo móvel iOS|Ajuda a implantar perfis de provisionamento em aplicativos iOS que estão se aproximando da expiração. |[Usar políticas de perfil de provisionamento móvel do iOS para impedir que seus aplicativos expirem](../apps/app-provisioning-profile-ios.md)|
|Navegador gerenciado|Configura políticas de navegador gerenciado para controlar os sites que os usuários do dispositivo podem visitar. Além disso, você também pode aplicar políticas de gerenciamento de aplicativo móvel ao navegador gerenciado.|[Gerenciar o acesso à Internet usando políticas de navegador gerenciado com o Microsoft Intune](../apps/app-configuration-managed-browser.md)|
|Windows Hello para Empresas|Permite a integração com o Windows Hello for Business, que é um método de entrada alternativo para o Windows 10 que usa Active Directory local ou Azure Active Directory para substituir senhas, cartões inteligentes ou cartões inteligentes virtuais.|[Controlar as configurações do Windows Hello para empresas em dispositivos com Microsoft Intune](../protect/windows-hello.md)|
|Aplicativos comprados por volume|Ajuda a gerenciar aplicativos adquiridos por meio de um programa de compra por volume, importando as informações de licença da loja de aplicativos, acompanhando quantas licenças você usou e impedindo a instalação de mais cópias do aplicativo do que você possui.|[Gerenciar aplicativos adquiridos por volume usando o Microsoft Intune](../apps/vpp-apps.md)|

## <a name="company-resource-access"></a>Acesso aos recursos da empresa

|Capacidade|Detalhes|Mais informações|
|--------------|-----------|--------------------|
|Perfis de certificado|Cria e implanta perfis de certificado confiáveis e certificados de protocolo SCEP (SCEP), que podem ser usados para proteger e autenticar perfis de Wi-Fi, VPN e email.|[Proteger o acesso a recursos com perfis de certificados no Microsoft Intune](../protect/certificates-configure.md)|
|Perfis de Wi-Fi|Implanta configurações de rede sem fio para seus usuários. Ao implantar essas configurações, você minimiza o esforço do usuário necessário para se conectar à rede corporativa.|[Ligações Wi-Fi no Microsoft Intune](../configuration/wi-fi-settings-configure.md)|
|Perfis de email|Cria e implanta configurações de email em dispositivos para que os usuários possam acessar o email corporativo em seus dispositivos pessoais sem qualquer configuração necessária de sua parte.|[Configurar o acesso a e-mail empresarial através de perfis de e-mail com o Microsoft Intune](../configuration/email-settings-configure.md)|
|Perfis de VPN|Implanta configurações de VPN para usuários e dispositivos na sua organização. Ao implantar essas configurações, você minimiza o esforço do usuário necessário para se conectar aos recursos na rede da empresa.|[Ligações VPN no Microsoft Intune](../configuration/device-profiles.md#vpn)|
|Políticas de acesso condicional|Gerencia o acesso ao email do Microsoft Exchange e ao SharePoint Online de dispositivos que não são gerenciados pelo Intune.|[Restringir o acesso ao email e ao SharePoint com Microsoft Intune](../protect/app-based-conditional-access-intune.md)|

## <a name="next-steps"></a>Passos seguintes

[Consulte uma lista de dispositivos que você pode gerenciar](../remote-actions/device-management.md).

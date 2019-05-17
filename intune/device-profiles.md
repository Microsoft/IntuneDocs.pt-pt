---
title: Funcionalidades e definições do dispositivo no Microsoft Intune – Azure | Microsoft Docs
description: Descrição geral dos diferentes perfis de dispositivo do Microsoft Intune. Obtenha informações sobre funcionalidades, restrições, e-mail, Wi-Fi, VPN, educação, certificados, atualização do Windows 10, BitLocker e Windows Defender, Windows Information Protection, modelos administrativos e definições de configuração de dispositivos personalizadas no portal do Azure. Utilize estes perfis para gerir e proteger os dados e os dispositivos na sua empresa.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/08/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4e099470140672a45948391cb0cf7c243f6fb84d
ms.sourcegitcommit: 1cae690ca2ac6cc97bbcdf656f54b31878297ae8
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/22/2019
ms.locfileid: "59894614"
---
# <a name="apply-features-and-settings-on-your-devices-using-device-profiles-in-microsoft-intune"></a>Aplicar definições e funcionalidades nos dispositivos com perfis de dispositivo no Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

O Microsoft Intune inclui definições e funcionalidades que pode ativar ou desativar em diferentes dispositivos na sua organização. Estas definições e funcionalidades são adicionadas aos “perfis de configuração”. Pode criar perfis para diferentes dispositivos e diferentes plataformas, incluindo iOS, Android e Windows. Em seguida, utilizar o Intune para aplicar ou “atribuir” o perfil aos dispositivos.

Como parte da solução de gestão de dispositivos móveis (MDM), utilize estes perfis de configuração para concluir diferentes tarefas. Alguns exemplos de perfil incluem:

- Em dispositivos Windows 10, utilize um modelo de perfil que bloqueia os controlos ActiveX no Internet Explorer.
- Em dispositivos iOS e macOS, permita que os utilizadores utilizem impressoras AirPrint na sua organização.
- Permita ou bloqueie o acesso ao Bluetooth no dispositivo.
- Crie um perfil Wi-Fi ou VPN para conceder acesso à sua rede organizacional a diferentes dispositivos.
- Faça a gestão das atualizações de software, incluindo a altura em que são instaladas.
- Execute um dispositivo Android como dispositivo de quiosque dedicado que pode executar uma aplicação ou executar muitas aplicações.

Este artigo fornece uma descrição geral dos diferentes tipos de perfis que pode criar. Utilize estes perfis para permitir ou bloquear algumas funcionalidades nos dispositivos.

## <a name="administrative-templates-preview"></a>Modelos administrativos (Pré-visualização)

Os [modelos administrativos](administrative-templates-windows.md) incluem centenas de definições que pode configurar para o Internet Explorer, OneDrive, ambiente de trabalho remoto, Word, Excel e outros programas do Office.

Estes modelos oferecem aos administradores uma vista simplificada das configurações semelhante à política de grupo, mas são 100% baseados na cloud.

Esta funcionalidade suporta:

- Windows 10 e posterior

## <a name="device-features"></a>Funcionalidades do dispositivo

As [funcionalidades do dispositivo](device-features-configure.md) controlam as funcionalidades nos dispositivos iOS e macOS como o AirPrint, as notificações e as mensagens de bloqueio de ecrã.

Esta funcionalidade suporta:

- iOS 
- macOS

## <a name="device-restrictions"></a>Restrições de dispositivos

As [restrições de dispositivos](device-restrictions-configure.md) controlam a segurança, hardware, partilha de dados e mais definições nos dispositivos. Por exemplo, pode criar um perfil de restrição do dispositivo para impedir que os utilizadores dos dispositivos iOS utilizem a câmara do dispositivo. 

Esta funcionalidade suporta:

- Android
- Android Enterprise
- iOS
- macOS
- Windows 10 e posterior
- Windows 10 Team

## <a name="delivery-optimization"></a>Otimização da entrega

A [otimização da entrega](delivery-optimization-windows.md) oferece uma melhor experiência na entrega de atualizações de software. Estas definições estão a substituir as definições **Atualizações de Software** > **Cadência de atualizações do Windows 10**.

Utilize estas definições para controlar a forma como as atualizações de software são transferidas para os dispositivos na sua organização. Por exemplo, pode permitir que os utilizadores obtenham as suas próprias atualizações ou obtenham as atualizações através dos serviços cloud de otimização de entrega num perfil de dispositivo.

Esta funcionalidade suporta:

- Windows 10 e posterior

## <a name="endpoint-protection"></a>Proteção de ponto final

As [definições de proteção de ponto final para o Windows 10](endpoint-protection-windows-10.md) configuram as definições do BitLocker e Windows Defender para dispositivos com o Windows 10.

Para carregar a Proteção Avançada Contra Ameaças do Windows Defender (WDATP) com o Microsoft Intune, veja [Configure endpoints using Mobile Device Management (MDM) tools](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/configure-endpoints-mdm-windows-defender-advanced-threat-protection) (Configurar pontos finais através das ferramentas da Gestão de Dispositivos Móveis [MDM]).

Esta funcionalidade suporta:

- Windows 10 e posterior

## <a name="identity-protection"></a>Proteção de identidade

A [proteção de identidade](identity-protection-configure.md) controla a experiência do Windows Hello para Empresas em dispositivos com o Windows 10 e Windows 10 Mobile. Configure estas definições para fazer com que o Windows Hello para Empresas fique disponível para utilizadores e dispositivos, bem como para especificar os requisitos de PIN e gestos de dispositivos.  

Esta funcionalidade suporta:  

- Windows 10 e posterior
- Windows Holographic for Business  

## <a name="kiosk"></a>Modo de Local Público

O perfil [Definições de quiosque](kiosk-settings.md) configura um dispositivo para que execute uma aplicação ou execute várias aplicações. Também pode personalizar outras funcionalidades no modo de quiosque, incluindo o menu Iniciar e um browser.

Esta funcionalidade suporta:

- Windows 10 e posterior

As definições de quiosque estão também disponíveis como restrições de dispositivo para [Android](device-restrictions-android.md#kiosk), [Android Enterprise](device-restrictions-android-for-work.md#dedicated-device-settings) e [iOS](device-restrictions-ios.md#kiosk-supervised-only).

## <a name="email"></a>E-mail

As [definições de e-mail](email-settings-configure.md) criam, atribuem e monitorizam as definições de e-mail do Exchange ActiveSync nos dispositivos. Os perfis de e-mail ajudam na consistência, reduzem as chamadas de suporte e permitem que os utilizadores finais acedam ao e-mail da empresa nos seus dispositivos pessoais sem precisarem de efetuar qualquer configuração. 

Esta funcionalidade suporta: 

- Android
- Android Enterprise
- iOS
- Windows Phone 8.1
- Windows 10 e posterior

## <a name="vpn"></a>VPN

As [definições de VPN](vpn-settings-configure.md) atribuem perfis VPN a utilizadores e dispositivos na sua organização, para que possam ligar-se de forma fácil e segura à rede. 

As redes virtuais privadas (VPN) permitem-lhe conceder aos utilizadores acesso remoto protegido à rede da sua empresa. Os dispositivos utilizam um perfil de ligação VPN para iniciar uma ligação com o seu servidor VPN. 

Esta funcionalidade suporta: 

- Android
- Android Enterprise
- iOS
- macOS
- Windows Phone 8.1
- Windows 8.1
- Windows 10 e posterior

## <a name="wi-fi"></a>Wi-Fi

As [definições de Wi-Fi](wi-fi-settings-configure.md) atribuem definições de rede sem fios a utilizadores e dispositivos. Quando atribui um perfil Wi-Fi, os utilizadores obtêm acesso ao seu Wi-Fi empresarial sem necessidade de configuração. 

Esta funcionalidade suporta: 

- Android
- Android Enterprise
- iOS
- macOS
- Windows 8.1 (importar apenas)
- Windows 10 e posterior

## <a name="esim-cellular---public-preview"></a>Rede celular eSIM – pré-visualização pública

Os [perfis celulares eSIM](esim-device-configuration.md) permitem que os administradores configurem planos de dados via rede móvel nos dispositivos geridos para acesso à Internet e aos dados. Após obter os códigos de ativação junto do seu operador móvel, utilize o Intune para importar esses códigos de ativação e, em seguida, atribuí-los aos dispositivos compatíveis com eSIM.

Esta funcionalidade suporta:
- O Windows 10 Fall Creators Update e posterior

## <a name="education"></a>Educação

As [definições de educação para Windows 10](education-settings-configure.md) configuram as opções da [aplicação Fazer um Teste do Windows](https://education.microsoft.com/gettrained/win10takeatest). Quando configurar estas opções, não pode executar qualquer outra aplicação no dispositivo até o teste estar concluído.

As [definições de educação para iOS](education-settings-configure-ios-shared.md) utilizam a aplicação Sala de Aula para iOS para orientar a aprendizagem e controlar os dispositivos dos estudantes na sala de aula. Pode configurar dispositivos iPad para que vários estudantes possam partilhar um único dispositivo.

## <a name="edition-upgrade"></a>Atualização de edição

As [atualizações de edição do Windows 10](edition-upgrade-configure-windows-10.md) atualizam automaticamente os dispositivos que executam algumas versões do Windows 10 para uma edição mais recente.

Esta funcionalidade suporta: 
- Windows 10 e posterior

## <a name="update-policies"></a>Políticas de atualização

As [políticas de atualização do iOS](software-updates-ios.md) mostram-lhe como criar e atribuir políticas para iOS para instalar atualizações de software nos seus dispositivos iOS. Também pode rever o estado de instalação.

Para obter as políticas de atualização em dispositivos Windows, veja [Otimização da entrega](delivery-optimization-windows.md). 

Esta funcionalidade suporta:
- iOS

## <a name="certificates"></a>Certificados

Os [certificados](certificates-configure.md) configuram certificados fidedignos, SCEP e PKCS que são atribuídos aos dispositivos. Estes certificados autenticam os perfis de Wi-Fi, VPN e e-mail.

Esta funcionalidade suporta: 

- Android
- Android Enterprise
- iOS
- macOS
- Windows Phone 8.1
- Windows 8.1
- Windows 10 e posterior

## <a name="windows-information-protection-profile"></a>Perfil do Windows Information Protection

O [Windows Information Protection](windows-information-protection-configure.md) ajuda a proteger contra a fuga de dados sem interferir com a experiência do empregado. Também ajuda a proteger as aplicações e os dados da empresa contra fugas de dados acidentais em dispositivos pertencentes à empresa e em dispositivos pessoais que os funcionários utilizem no trabalho. Para utilizar o Windows Information Protection, não precisa de alterar o seu ambiente nem outras aplicações.

Esta funcionalidade suporta:

- Windows 10 e posterior

## <a name="shared-multi-user-device"></a>Dispositivo multiutilizador partilhado

[Windows 10](shared-user-device-settings-windows.md) e [Windows Holographic for Business](shared-user-device-settings-windows-holographic.md) incluem definições para gerir dispositivos com vários utilizadores, também conhecidos como dispositivos partilhados ou PCs partilhados. Quando um utilizador inicia sessão no dispositivo, pode escolher se o utilizador pode alterar as opções de suspensão ou pode guardar ficheiros no dispositivo. Noutro exemplo, para economizar espaço, pode criar um perfil para eliminar as credenciais inativas de dispositivos HoloLens do Windows.

Estas definições de dispositivos partilhados para múltiplos utilizadores permitem que um administrador controle algumas das funcionalidades dos dispositivos e faça a gestão destes dispositivos partilhados através do Intune.

Esta funcionalidade suporta:

- Windows 10 e posterior
- Windows Holographic for Business

## <a name="zebra-mobility-extensions-mx"></a>Extensões de Mobilidade (MX) da Zebra

As [Extensões de Mobilidade (MX) da Zebra](android-zebra-mx-overview.md) permite aos administradores utilizar e gerir os dispositivos Zebra no Intune. Pode criar perfis StageNow com as suas definições e, em seguida, utilizar o Intune para atribuir e implementar estes perfis nos dispositivos Zebra. [Registos e problemas comuns do StageNow](android-zebra-mx-logs-troubleshoot.md) é um ótimo recurso para resolver problemas de perfis e ver alguns possíveis problemas quando utiliza o StageNow.

Esta funcionalidade suporta:

- Android (Extensões de Mobilidade)

## <a name="oemconfig"></a>OEMConfig

[OEMConfig](android-oem-configuration-overview.md) é uma norma que permite que os OEMs (fabricantes originais do equipamento) e EMMs (gestão de mobilidade empresarial) criem e ofereçam suporte a recursos específicos do OEM de forma padronizada em dispositivos Android Enterprise. Com o OEMConfig, um OEM cria um esquema que define as funcionalidades de gestão específicas do OEM e incorpora-as numa aplicação carregada no Google Play. O Intune lê o esquema na aplicação e, em seguida, permite que os administradores do Intune configurem as definições no esquema.

Esta funcionalidade suporta:

- Android Enterprise (OEMConfig)

## <a name="custom-profile"></a>Perfil personalizado

As [definições personalizadas](custom-settings-configure.md) permitem que os administradores atribuam definições de dispositivo que não estejam incorporadas no Intune. Em dispositivos Android, pode introduzir valores OMA-URI. Para dispositivos iOS, pode importar um ficheiro de configuração que criou no Apple Configurator.

Esta funcionalidade suporta:

- Android
- Android Enterprise
- iOS
- macOS
- Windows Phone 8.1

## <a name="manage-and-troubleshoot"></a>Gestão e resolução de problemas

[Faça a gestão dos seus perfis](device-profile-monitor.md) para verificar o estado dos dispositivos e os perfis atribuídos. Ver as definições que causam um conflito e os perfis que incluem essas definições também poderá ajudá-lo a resolver conflitos. [Problemas comuns e resoluções](device-profile-troubleshoot.md) ajuda os administradores a trabalhar com perfis. Descreve o que acontece quando se elimina um perfil, o que faz com que sejam enviadas notificações para os dispositivos e muito mais.

## <a name="next-steps"></a>Próximos passos

Escolher a plataforma e começar.

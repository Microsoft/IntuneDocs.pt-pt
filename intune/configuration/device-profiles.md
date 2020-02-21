---
title: Funcionalidades e definições do dispositivo no Microsoft Intune – Azure | Microsoft Docs
description: Descrição geral dos diferentes perfis de dispositivo do Microsoft Intune. Obtenha informações sobre funcionalidades, restrições, e-mail, wifi, VPN, educação, certificados, upgrade Windows 10, BitLocker e Microsoft Defender, Proteção de Informações do Windows, modelos administrativos e configurações de configuração de dispositivos personalizados na Microsoft Centro de administração do Endpoint Manager. Utilize estes perfis para gerir e proteger os dados e os dispositivos na sua empresa.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/18/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: karthib
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 951d3df8b842f1a0e76f875ea9fc7921c413494f
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/20/2020
ms.locfileid: "77513080"
---
# <a name="apply-features-and-settings-on-your-devices-using-device-profiles-in-microsoft-intune"></a>Aplicar definições e funcionalidades nos dispositivos com perfis de dispositivo no Microsoft Intune



O Microsoft Intune inclui definições e funcionalidades que pode ativar ou desativar em diferentes dispositivos na sua organização. Estas definições e funcionalidades são adicionadas aos “perfis de configuração”. Pode criar perfis para diferentes dispositivos e diferentes plataformas, incluindo iOS/iPadOS, Android e Windows. Em seguida, utilizar o Intune para aplicar ou “atribuir” o perfil aos dispositivos.

Como parte da solução de gestão de dispositivos móveis (MDM), utilize estes perfis de configuração para concluir diferentes tarefas. Alguns exemplos de perfil incluem:

- Em dispositivos Windows 10, utilize um modelo de perfil que bloqueia os controlos ActiveX no Internet Explorer.
- Nos dispositivos iOS/iPadOS e macOS, os utilizadores utilizam impressoras AirPrint na sua organização.
- Permita ou bloqueie o acesso ao Bluetooth no dispositivo.
- Crie um perfil Wi-Fi ou VPN para conceder acesso à sua rede organizacional a diferentes dispositivos.
- Faça a gestão das atualizações de software, incluindo a altura em que são instaladas.
- Execute um dispositivo Android como dispositivo de quiosque dedicado que pode executar uma aplicação ou executar muitas aplicações.

Este artigo fornece uma descrição geral dos diferentes tipos de perfis que pode criar. Utilize estes perfis para permitir ou bloquear algumas funcionalidades nos dispositivos.

## <a name="administrative-templates"></a>Administrative templates (Modelos administrativos)

Os [modelos administrativos](administrative-templates-windows.md) incluem centenas de definições que pode configurar para o Internet Explorer, OneDrive, ambiente de trabalho remoto, Word, Excel e outros programas do Office.

Estes modelos oferecem aos administradores uma vista simplificada das configurações semelhante à política de grupo, mas são 100% baseados na cloud.

Esta funcionalidade suporta:

- Windows 10 e posterior

## <a name="certificates"></a>Certificados

Os [certificados](../protect/certificates-configure.md) configuram certificados fidedignos, SCEP e PKCS que são atribuídos aos dispositivos. Estes certificados autenticam os perfis de Wi-Fi, VPN e e-mail.

Esta funcionalidade suporta: 

- Android
- Android Enterprise
- iOS/iPadOS
- macOS
- Windows Phone 8.1
- Windows 8,1
- Windows 10 e posterior

## <a name="custom-profile"></a>Perfil personalizado

As [definições personalizadas](custom-settings-configure.md) permitem que os administradores atribuam definições de dispositivo que não estejam incorporadas no Intune. Em dispositivos Android, pode introduzir valores OMA-URI. Para dispositivos iOS/iPadOS, pode importar um ficheiro de configuração que criou no Configurator Apple.

Esta funcionalidade suporta:

- Android
- Android Enterprise
- iOS/iPadOS
- macOS
- Windows Phone 8.1

## <a name="delivery-optimization"></a>Otimização da entrega

A [otimização da entrega](delivery-optimization-windows.md) oferece uma melhor experiência na entrega de atualizações de software. Estas definições estão a substituir as definições **Atualizações de Software** > **Cadência de atualizações do Windows 10**.

Utilize estas definições para controlar a forma como as atualizações de software são transferidas para os dispositivos na sua organização. Por exemplo, pode permitir que os utilizadores obtenham as suas próprias atualizações ou obtenham as atualizações através dos serviços cloud de otimização de entrega num perfil de dispositivo.

Esta funcionalidade suporta:

- Windows 10 e posterior

## <a name="device-features"></a>Funcionalidades do dispositivo

[O dispositivo possui](device-features-configure.md) funcionalidades de controlo em dispositivos iOS/iPadOS e macOS, tais como AirPrint, notificações e mensagens de ecrã de bloqueio.

Esta funcionalidade suporta:

- iOS/iPadOS
- macOS

## <a name="device-firmware-configuration-interface"></a>Interface de configuração de firmware de dispositivo

A interface de configuração do [firmware](device-firmware-configuration-interface-windows.md) do dispositivo (DFCI) permite que os administradores ativem ou desativem as definições da UEFI (BIOS) utilizando o Intune. Utilize estas configurações para aumentar a segurança ao nível do firmware, que é tipicamente mais resistente a ataques maliciosos.

Esta funcionalidade suporta:

- Windows 10 1809 e mais tarde em firmware suportado

## <a name="device-restrictions"></a>Restrições de dispositivos

As [restrições de dispositivos](device-restrictions-configure.md) controlam a segurança, hardware, partilha de dados e mais definições nos dispositivos. Por exemplo, criar um perfil de restrição do dispositivo que impeça os utilizadores do dispositivo iOS/iPadOS de utilizarem a câmara do dispositivo. 

Esta funcionalidade suporta:

- Android
- Android Enterprise
- iOS/iPadOS
- macOS
- Windows 10 e posterior
- Windows 10 Team

## <a name="edition-upgrade"></a>Atualização de edição

As [atualizações de edição do Windows 10](edition-upgrade-configure-windows-10.md) atualizam automaticamente os dispositivos que executam algumas versões do Windows 10 para uma edição mais recente.

Esta funcionalidade suporta:

- Windows 10 e posterior

## <a name="education"></a>Educação

As [definições de educação para Windows 10](education-settings-configure.md) configuram as opções da [aplicação Fazer um Teste do Windows](https://education.microsoft.com/gettrained/win10takeatest). Quando configurar estas opções, não pode executar qualquer outra aplicação no dispositivo até o teste estar concluído.

[Definições de educação - iOS/iPadOS](../fundamentals/education-settings-configure-ios-shared.md) utiliza a aplicação iOS/iPadOS Classroom para orientar a aprendizagem e controlar os dispositivos estudantis na sala de aula. Pode configurar dispositivos iPad para que vários estudantes possam partilhar um único dispositivo.

## <a name="email"></a>E-mail

As [definições de e-mail](email-settings-configure.md) criam, atribuem e monitorizam as definições de e-mail do Exchange ActiveSync nos dispositivos. Os perfis de e-mail ajudam na consistência, reduzem as chamadas de suporte e permitem que os utilizadores finais acedam ao e-mail da empresa nos seus dispositivos pessoais sem precisarem de efetuar qualquer configuração. 

Esta funcionalidade suporta: 

- Android
- Android Enterprise
- iOS/iPadOS
- Windows Phone 8.1
- Windows 10 e posterior

## <a name="endpoint-protection"></a>Proteção de ponto final

As definições de proteção de [pontofinal para as definições](../protect/endpoint-protection-windows-10.md) bitLocker e Microsoft Defender do Windows 10 configurações para dispositivos Windows 10.

Para embarcar na Microsoft Defender Advanced Threat Protection (WDATP) com a Microsoft Intune, consulte os [pontos finais da Configuração utilizando ferramentas de Gestão de Dispositivos Móveis (MDM).](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/configure-endpoints-mdm)

Esta funcionalidade suporta:

- Windows 10 e posterior

## <a name="esim-cellular---public-preview"></a>Rede celular eSIM – pré-visualização pública

Os [perfis celulares eSIM](esim-device-configuration.md) permitem que os administradores configurem planos de dados via rede móvel nos dispositivos geridos para acesso à Internet e aos dados. Após obter os códigos de ativação junto do seu operador móvel, utilize o Intune para importar esses códigos de ativação e, em seguida, atribuí-los aos dispositivos compatíveis com eSIM.

Esta funcionalidade suporta:

- O Windows 10 Fall Creators Update e posterior

## <a name="extensions"></a>Extensões

[As extensões kernel](kernel-extensions-overview-macos.md) permitem que os administradores adicionem funcionalidades ou programas ao nível do kernel em dispositivos macOS. Configure estas definições para confiar em todas as extensões de um programador ou parceiro específico, ou permitir extensões específicas de kernel.

Esta funcionalidade suporta:

- macOS

## <a name="identity-protection"></a>Proteção de identidade

A [proteção de identidade](../protect/identity-protection-configure.md) controla a experiência do Windows Hello para Empresas em dispositivos com o Windows 10 e Windows 10 Mobile. Configure estas definições para fazer com que o Windows Hello para Empresas fique disponível para utilizadores e dispositivos, bem como para especificar os requisitos de PIN e gestos de dispositivos.  

Esta funcionalidade suporta:  

- Windows 10 e posterior
- Windows Holographic for Business  

## <a name="kiosk"></a>Modo de Local Público

O perfil [Definições de quiosque](kiosk-settings.md) configura um dispositivo para que execute uma aplicação ou execute várias aplicações. Também pode personalizar outras funcionalidades no modo de quiosque, incluindo o menu Iniciar e um browser.

Esta funcionalidade suporta:

- Windows 10 e posterior

As definições de quiosque também estão disponíveis como restrições de dispositivos para [Android,](device-restrictions-android.md#kiosk) [Android Enterprise,](device-restrictions-android-for-work.md#dedicated-device-settings)e [ios/iPadOS.](device-restrictions-ios.md#kiosk)

## <a name="oemconfig"></a>OEMConfig

[OEMConfig](android-oem-configuration-overview.md) é uma norma que permite que os OEMs (fabricantes originais do equipamento) e EMMs (gestão de mobilidade empresarial) criem e ofereçam suporte a recursos específicos do OEM de forma padronizada em dispositivos Android Enterprise. Com o OEMConfig, um OEM cria um esquema que define as funcionalidades de gestão específicas do OEM e incorpora-as numa aplicação carregada no Google Play. O Intune lê o esquema na aplicação e, em seguida, permite que os administradores do Intune configurem as definições no esquema.

Esta funcionalidade suporta:

- Android Enterprise (OEMConfig)

## <a name="powershell-scripts"></a>Scripts PowerShell

[Os scripts PowerShell nos dispositivos Windows 10](../apps/intune-management-extension.md) utilizam a Extensão de Gestão Intune para carregar os scripts PowerShell em Intune e, em seguida, executar estes scripts nos seus dispositivos. Consulte também o que é necessário para usar a extensão, como adicioná-las a Intune, e outras informações importantes.


Esta funcionalidade suporta:

- Windows 10 e posterior
- Windows Holographic for Business

## <a name="shared-multi-user-device"></a>Dispositivo multiutilizador partilhado

[Windows 10](shared-user-device-settings-windows.md) e [Windows Holographic for Business](shared-user-device-settings-windows-holographic.md) incluem definições para gerir dispositivos com vários utilizadores, também conhecidos como dispositivos partilhados ou PCs partilhados. Quando um utilizador inicia sessão no dispositivo, pode escolher se o utilizador pode alterar as opções de suspensão ou pode guardar ficheiros no dispositivo. Noutro exemplo, para economizar espaço, pode criar um perfil para eliminar as credenciais inativas de dispositivos HoloLens do Windows.

Estas definições de dispositivos partilhados para múltiplos utilizadores permitem que um administrador controle algumas das funcionalidades dos dispositivos e faça a gestão destes dispositivos partilhados através do Intune.

Esta funcionalidade suporta:

- Windows 10 e posterior
- Windows Holographic for Business

## <a name="update-policies"></a>Políticas de atualização

As políticas de [atualização iOS/iPadOS](../protect/software-updates-ios.md) mostram como criar e atribuir políticas iOS/iPadOS para instalar atualizações de software nos seus dispositivos iOS/iPadOS. Também pode rever o estado de instalação.

Para obter as políticas de atualização em dispositivos Windows, veja [Otimização da entrega](delivery-optimization-windows.md). 

Esta funcionalidade suporta:

- iOS/iPadOS

## <a name="vpn"></a>VPN

As [definições de VPN](vpn-settings-configure.md) atribuem perfis VPN a utilizadores e dispositivos na sua organização, para que possam ligar-se de forma fácil e segura à rede. 

As redes virtuais privadas (VPN) permitem-lhe conceder aos utilizadores acesso remoto protegido à rede da sua empresa. Os dispositivos utilizam um perfil de ligação VPN para iniciar uma ligação com o seu servidor VPN. 

Esta funcionalidade suporta: 

- Android
- Android Enterprise
- iOS/iPadOS
- macOS
- Windows Phone 8.1
- Windows 8,1
- Windows 10 e posterior

## <a name="wi-fi"></a>Wi-Fi

As [definições de Wi-Fi](wi-fi-settings-configure.md) atribuem definições de rede sem fios a utilizadores e dispositivos. Quando atribui um perfil Wi-Fi, os utilizadores obtêm acesso ao seu Wi-Fi empresarial sem necessidade de configuração. 

Esta funcionalidade suporta: 

- Android
- Android Enterprise
- iOS/iPadOS
- macOS
- Windows 8.1 (importar apenas)
- Windows 10 e posterior

## <a name="windows-information-protection-profile"></a>Perfil do Windows Information Protection

O [Windows Information Protection](../protect/windows-information-protection-configure.md) ajuda a proteger contra a fuga de dados sem interferir com a experiência do empregado. Também ajuda a proteger as aplicações e os dados da empresa contra fugas de dados acidentais em dispositivos pertencentes à empresa e em dispositivos pessoais que os funcionários utilizem no trabalho. Para utilizar o Windows Information Protection, não precisa de alterar o seu ambiente nem outras aplicações.

Esta funcionalidade suporta:

- Windows 10 e posterior

## <a name="zebra-mobility-extensions-mx"></a>Extensões de Mobilidade (MX) da Zebra

As [Extensões de Mobilidade (MX) da Zebra](android-zebra-mx-overview.md) permite aos administradores utilizar e gerir os dispositivos Zebra no Intune. Pode criar perfis StageNow com as suas definições e, em seguida, utilizar o Intune para atribuir e implementar estes perfis nos dispositivos Zebra. [Registos e problemas comuns do StageNow](android-zebra-mx-logs-troubleshoot.md) é um ótimo recurso para resolver problemas de perfis e ver alguns possíveis problemas quando utiliza o StageNow.

Esta funcionalidade suporta:

- Android (Extensões de Mobilidade)

## <a name="manage-and-troubleshoot"></a>Gestão e resolução de problemas

[Faça a gestão dos seus perfis](device-profile-monitor.md) para verificar o estado dos dispositivos e os perfis atribuídos. Ver as definições que causam um conflito e os perfis que incluem essas definições também poderá ajudá-lo a resolver conflitos. [Problemas comuns e resoluções](device-profile-troubleshoot.md) ajuda os administradores a trabalhar com perfis. Descreve o que acontece quando se elimina um perfil, o que faz com que sejam enviadas notificações para os dispositivos e muito mais.

## <a name="next-steps"></a>Próximos passos

Escolher a plataforma e começar.

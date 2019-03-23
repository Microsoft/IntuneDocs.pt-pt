---
title: Funcionalidades do dispositivo e definições no Microsoft Intune – Azure | Documentos da Microsoft
description: Descrição geral dos diferentes perfis de dispositivo do Microsoft Intune. Obtenha informações sobre funcionalidades, restrições, e-mail, Wi-Fi, VPN, educação, certificados, atualização do Windows 10, BitLocker e o Windows defender, Windows Information Protection, modelos administrativos e definições de configuração de dispositivo personalizado no portal do Azure. Utilize estes perfis para gerir e proteger os dados e dispositivos na sua empresa.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/12/2019
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
ms.openlocfilehash: df8cc8c921b685ba7fa0b957685836d059a677e0
ms.sourcegitcommit: 1069b3b1ed593c94af725300aafd52610c7d8f04
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2019
ms.locfileid: "58394991"
---
# <a name="apply-features-and-settings-on-your-devices-using-device-profiles-in-microsoft-intune"></a>Aplicar definições e funcionalidades nos seus dispositivos com perfis de dispositivos no Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

O Microsoft Intune inclui definições e funcionalidades, pode ativar ou desativar em diferentes dispositivos na sua organização. Estas definições e funcionalidades são adicionadas para "perfis de configuração". Pode criar perfis para diferentes dispositivos e plataformas diferentes, incluindo iOS, Android e Windows. Em seguida, utilize o Intune para aplicar ou "atribuir" o perfil aos dispositivos.

Como parte da sua solução de gestão (MDM) de dispositivos móveis, utilize estes perfis de configuração para concluir tarefas diferentes. Alguns exemplos de perfil incluem:

- Em dispositivos Windows 10, utilize um modelo de perfil bloquear controles ActiveX no Internet Explorer.
- Em dispositivos iOS e macOS, permitir aos utilizadores utilizar impressoras com o AirPrint na sua organização.
- Permitir ou impedir o acesso a bluetooth no dispositivo.
- Crie um perfil de Wi-Fi ou VPN que dá a diferentes dispositivos acesso à sua rede empresarial.
- Gerir atualizações de software, incluindo quando são instaladas.
- Execute um dispositivo Android como dispositivo de quiosque dedicado que pode executar uma aplicação ou executar muitos aplicativos.

Este artigo fornece uma descrição geral dos diferentes tipos de perfis que pode criar. Utilize estes perfis para permitir ou bloquear algumas funcionalidades nos dispositivos.

## <a name="administrative-templates-preview"></a>Modelos administrativos (pré-visualização)

[Modelos administrativos](administrative-templates-windows.md) incluem centenas de definições que pode configurar para o Internet Explorer, OneDrive, ambiente de trabalho remoto, Word, Excel e outros programas do Office.

Estes modelos oferecem aos administradores uma vista simplificada de configurações semelhantes à diretiva de grupo, mas eles são 100% baseado na nuvem.

Esta funcionalidade suporta:

- Windows 10 e posterior

## <a name="device-features"></a>Funcionalidades do dispositivo

[Funcionalidades do dispositivo](device-features-configure.md) controlam as funcionalidades nos dispositivos iOS e macOS, como mensagens de ecrã de bloqueio, notificações e AirPrint.

Esta funcionalidade suporta:

- iOS 
- macOS

## <a name="device-restrictions"></a>Restrições de dispositivos

As [restrições de dispositivos](device-restrictions-configure.md) controlam a segurança, hardware, partilha de dados e mais definições nos dispositivos. Por exemplo, pode criar um perfil de restrição do dispositivo para impedir que os utilizadores dos dispositivos iOS utilizem a câmara do dispositivo. 

Esta funcionalidade suporta:

- Android
- Android enterprise
- iOS
- macOS
- Windows 10 e posterior
- Windows 10 Team

## <a name="delivery-optimization"></a>Otimização da entrega

[Otimização da entrega](delivery-optimization-windows.md) possibilita uma melhor experiência para entrega de atualizações de software. Estas definições são substituindo a **atualizações de Software** > **cadência de atualização do Windows 10** definições.

Utilize estas definições para controlar a forma como as atualizações de software são transferidas para dispositivos na sua organização. Por exemplo, pode permitir que os utilizadores obtêm as próprias atualizações ou obter as atualizações existentes usando os serviços de cloud de otimização de entrega num perfil de dispositivo.

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

[Definições de local público](kiosk-settings.md) perfil configura um dispositivo execute uma aplicação, ou executar muitos aplicativos. Também pode personalizar outras funcionalidades no modo de quiosque, incluindo o menu Iniciar e um browser.

Esta funcionalidade suporta:

- Windows 10 e posterior

Definições de local público também disponíveis como restrições de dispositivos para [Android](device-restrictions-android.md#kiosk), [Android Enterprise](device-restrictions-android-for-work.md#dedicated-device-settings), e [ios](device-restrictions-ios.md#kiosk-supervised-only).

## <a name="email"></a>Email

[Definições de e-mail](email-settings-configure.md) cria, atribui e monitoriza as definições de e-mail do Exchange ActiveSync nos dispositivos. Ajuda de perfis de e-mail com a consistência, reduzem as chamadas de suporte e permitem que os utilizadores finais acesso da empresa e-mail nos seus dispositivos pessoais, sem qualquer configuração necessária por parte dos mesmos. 

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

[perfis de rede móvel de eSIM](esim-device-configuration.md) permite aos administradores configurar planos de dados via rede móvel nos seus dispositivos geridos para acesso à internet e os dados. Após obter códigos de ativação do seu operador móvel, utilize o Intune para importar estes códigos de ativação e, em seguida, atribuir a seus dispositivos com capacidade para eSIM.

Esta funcionalidade suporta:
- O Windows 10 Fall Creators Update e posterior

## <a name="education"></a>Educação

As [definições de educação para Windows 10](education-settings-configure.md) configuram as opções da [aplicação Fazer um Teste do Windows](https://education.microsoft.com/gettrained/win10takeatest). Quando configurar estas opções, não pode executar qualquer outra aplicação no dispositivo até o teste estar concluído.

As [definições de educação para iOS](education-settings-configure-ios-shared.md) utilizam a aplicação Sala de Aula para iOS para orientar a aprendizagem e controlar os dispositivos dos estudantes na sala de aula. Pode configurar dispositivos iPad para que estudantes muitos podem partilhar um único dispositivo.

## <a name="edition-upgrade"></a>Atualização de edição

As [atualizações de edição do Windows 10](edition-upgrade-configure-windows-10.md) atualizam automaticamente os dispositivos que executam algumas versões do Windows 10 para uma edição mais recente.

Esta funcionalidade suporta: 
- Windows 10 e posterior

## <a name="update-policies"></a>Políticas de atualização

As [políticas de atualização do iOS](software-updates-ios.md) mostram-lhe como criar e atribuir políticas para iOS para instalar atualizações de software nos seus dispositivos iOS. Também pode rever o estado de instalação.

Para obter as políticas de atualização em dispositivos Windows, consulte [Otimização da entrega](delivery-optimization-windows.md). 

Esta funcionalidade suporta:
- iOS

## <a name="certificates"></a>Certificados

[Certificados](certificates-configure.md) configurar fidedigno, SCEP e PKCS certificados que são atribuídos aos dispositivos. Estes certificados autenticar Wi-Fi, VPN e perfis de e-mail.

Esta funcionalidade suporta: 

- Android
- Android Enterprise
- iOS
- Windows Phone 8.1
- Windows 8.1
- Windows 10 e posterior

## <a name="windows-information-protection-profile"></a>Perfil do Windows Information Protection

O [Windows Information Protection](windows-information-protection-configure.md) ajuda a proteger contra a fuga de dados sem interferir com a experiência do empregado. Ele também ajuda a proteger aplicações empresariais e os dados contra fugas de dados acidentais em dispositivos pertencentes à empresa e dispositivos pessoais que os empregados utilizem no trabalho. Com o Windows Information Protection não requer alterações ao seu ambiente ou outras aplicações.

Esta funcionalidade suporta:

- Windows 10 e posterior

## <a name="shared-multi-user-device"></a>Dispositivo multiutilizador partilhado

[Windows 10](shared-user-device-settings-windows.md) e [Windows Holographic for Business](shared-user-device-settings-windows-holographic.md) inclui definições para gerir dispositivos com vários utilizadores, dispositivos partilhados também conhecido como ou PCs partilhados. Quando um utilizador inicia sessão no dispositivo, pode escolher se o utilizador pode alterar as opções de suspensão ou guardar ficheiros no dispositivo. Noutro exemplo, para economizar espaço, pode criar um perfil que elimina Inativas credenciais de dispositivos HoloLens do Windows.

Estas definições de dispositivos de vários utilizadores partilhados permitem que um administrador controlar alguns dos recursos de dispositivo e gerir estes dispositivos partilhados, através do Intune.

Esta funcionalidade suporta:

- Windows 10 e posterior
- Windows Holographic for Business

## <a name="zebra-mobility-extensions-mx"></a>As riscas das extensões de mobilidade (MX)

[As riscas das mobilidade extensões (MX)](android-zebra-mx-overview.md) permite aos administradores utilizar e gerir as riscas das dispositivos no Intune. Criar perfis de StageNow com as suas definições e, em seguida, utilizar o Intune para atribuir e implantar estes perfis para os seus dispositivos as riscas das. O [StageNow registos e os problemas comuns](android-zebra-mx-logs-troubleshoot.md) é um ótimo recurso para resolver problemas de perfis e ver alguns possíveis problemas quando utiliza o StageNow.

Esta funcionalidade suporta:

- Android

## <a name="custom-profile"></a>Perfil personalizado

[Definições personalizadas](custom-settings-configure.md) permitem que os administradores atribuir definições de dispositivos que não estão incorporadas Intune. Em dispositivos Android, pode introduzir valores OMA-URI. Para dispositivos iOS, pode importar um ficheiro de configuração que criou no Apple Configurator.

Esta funcionalidade suporta:

- Android
- Android Enterprise
- iOS
- macOS
- Windows Phone 8.1

## <a name="manage-and-troubleshoot"></a>Gestão e resolução de problemas

[Faça a gestão dos seus perfis](device-profile-monitor.md) para verificar o estado dos dispositivos e os perfis atribuídos. Também ajudam a resolver conflitos, mostrando as definições de causam um conflito e os perfis que incluem estas definições. [Problemas comuns e resoluções](device-profile-troubleshoot.md) ajuda os administradores de trabalhar com perfis. Ele descreve o que acontece quando a eliminação de um perfil, o que faz com que notificações a serem enviadas para dispositivos e muito mais.

## <a name="next-steps"></a>Passos Seguintes

Escolha a sua plataforma e começar a utilizar.

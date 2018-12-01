---
title: Perfis de dispositivo no Microsoft Intune – Azure | Microsoft Docs
description: Descrição geral dos diferentes perfis de dispositivo do Microsoft Intune, incluindo funcionalidades, restrições, e-mail, Wi-Fi, VPN, educação, certificados, atualização do Windows 10, BitLocker e Windows Defender, Windows Information Protection e definições de configuração de dispositivos personalizadas no portal do Azure. Utilize este perfil para gerir e proteger dados e dispositivos na sua empresa.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/19/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.openlocfilehash: c9a3146b1ad5f6f7c439d2e49cf534e14d154f76
ms.sourcegitcommit: ecd6aebe50b1440a282dfdda771e37fbb8750d42
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/01/2018
ms.locfileid: "52728706"
---
# <a name="what-are-microsoft-intune-device-profiles"></a>O que são os perfis de dispositivos do Microsoft Intune?

O Microsoft Intune inclui definições e funcionalidades que pode ativar ou desativar em diferentes dispositivos na sua organização. Estas definições e funcionalidades são geridas com perfis. Alguns exemplos de perfil incluem: 

- Um perfil Wi-Fi que dá a diferentes dispositivos acesso ao seu Wi-Fi empresarial
- Um perfil VPN que dá a diferentes dispositivos acesso ao seu servidor VPN na sua rede empresarial

Este artigo fornece uma descrição geral dos diferentes perfis que pode criar para os seus dispositivos. Utilize estes perfis para permitir ou bloquear algumas funcionalidades nos dispositivos.

## <a name="before-you-begin"></a>Antes de começar

Para ver as funcionalidades disponíveis, abra o [portal do Azure](https://portal.azure.com) e abra o seu recurso do Intune. 

A **configuração do dispositivo** inclui as seguintes opções:

- **Descrição geral**: indica o estado dos seus perfis e fornece detalhes adicionais sobre os perfis que atribuiu aos utilizadores e dispositivos
- **Gestão**: crie perfis de dispositivo e carregue [Scripts do PowerShell](intune-management-extension.md) personalizados para executar no perfil
- **Monitorização**: verifique o estado de um perfil e veja registos dos seus perfis
- **Configuração**: adicione uma autoridade de certificação (SCEP ou PFX) ou ative a Gestão de Despesas de Telecomunicação no perfil

## <a name="create-the-profile"></a>Criar o perfil

A opção [Criar perfis de dispositivo](device-profile-create.md) fornece orientação passo a passo para criar um perfil. 

## <a name="device-features---ios-and-macos"></a>Funcionalidades do dispositivo – iOS e macOS

As [funcionalidades do dispositivo](device-features-configure.md) controlam as funcionalidades nos dispositivos iOS e macOS como configurações de dispositivos partilhados, notificações e AirPrint.

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
- Windows 10
- Equipe do Windows 10

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

Definições de local público também disponíveis como restrições de dispositivos para [Android](device-restrictions-android.md#kiosk), [Android Enterprise](device-restrictions-android-for-work.md#kiosk-settings), e [ios](device-restrictions-ios.md#kiosk-supervised-only).

## <a name="email"></a>E-mail

[Definições de e-mail](email-settings-configure.md) cria, atribui e monitoriza as definições de e-mail do Exchange ActiveSync nos dispositivos. Ajuda de perfis de e-mail com a consistência, reduzem as chamadas de suporte e permitem que os utilizadores finais acesso da empresa e-mail nos seus dispositivos pessoais, sem qualquer configuração necessária por parte dos mesmos. 

Esta funcionalidade suporta: 

- Android
- iOS
- Windows Phone 8.1
- Windows 10

## <a name="vpn"></a>VPN

As [definições de VPN](vpn-settings-configure.md) atribuem perfis VPN a utilizadores e dispositivos na sua organização, para que possam ligar-se de forma fácil e segura à rede. 

As redes virtuais privadas (VPN) permitem-lhe conceder aos utilizadores acesso remoto protegido à rede da sua empresa. Os dispositivos utilizam um perfil de ligação VPN para iniciar uma ligação com o seu servidor VPN. 

Esta funcionalidade suporta: 

- Android
- iOS
- macOS
- Windows Phone 8.1
- Windows 8.1
- Windows 10

## <a name="wi-fi"></a>Wi-Fi

As [definições de Wi-Fi](wi-fi-settings-configure.md) atribuem definições de rede sem fios a utilizadores e dispositivos. Quando atribui um perfil Wi-Fi, os utilizadores obtêm acesso ao seu Wi-Fi empresarial sem necessidade de configuração. 

Esta funcionalidade suporta: 

- Android
- iOS
- macOS
- Windows 8.1 (importar apenas)

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

Esta funcionalidade suporta:
- iOS

## <a name="certificates"></a>Certificados

[Certificados](certificates-configure.md) configura fidedigno, SCEP e PKCS certificados que são atribuídos aos dispositivos e utilizado para autenticar Wi-Fi, VPN e perfis de e-mail.

Esta funcionalidade suporta: 

- Android
- iOS
- Windows Phone 8.1
- Windows 8.1
- Windows 10

## <a name="windows-information-protection-profile"></a>Perfil do Windows Information Protection

O [Windows Information Protection](windows-information-protection-configure.md) ajuda a proteger contra a fuga de dados sem interferir com a experiência do empregado. Ele também ajuda a proteger aplicações empresariais e os dados contra fugas de dados acidentais em dispositivos pertencentes à empresa e dispositivos pessoais que os empregados utilizem no trabalho. Com o Windows Information Protection não requer shanges ao seu ambiente ou outras aplicações.

Esta funcionalidade suporta:
- Windows 10 e posterior

## <a name="custom-profile"></a>Perfil personalizado

[Definições personalizadas](custom-settings-configure.md) permite que os administradores atribuir definições de dispositivo que não estão incorporadas no Intune. Por exemplo, em dispositivos Android, pode introduzir valores OMA-URI. Para dispositivos iOS, pode importar um ficheiro de configuração que criou no Apple Configurator. 

Esta funcionalidade suporta:

- Android
- iOS
- macOS
- Windows Phone 8.1

## <a name="manage-and-troubleshoot"></a>Gestão e resolução de problemas

[Faça a gestão dos seus perfis](device-profile-monitor.md) para verificar o estado dos dispositivos e os perfis atribuídos. Ver as definições que causam um conflito e os perfis que contêm essas definições também poderá ajudá-lo a resolver conflitos. [Problemas comuns e resoluções](device-profile-troubleshoot.md) fornece uma perguntas e respostas para o ajudar a notificações de trabalho com perfis, incluindo o que acontece quando um perfil é eliminado, o que faz com que sejam enviados para os dispositivos e muito mais.

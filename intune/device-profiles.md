---
title: Perfis de dispositivo no Microsoft Intune – Azure | Microsoft Docs
description: Descrição geral dos diferentes perfis de dispositivo do Microsoft Intune, incluindo funcionalidades, restrições, e-mail, Wi-Fi, VPN, educação, certificados, atualização do Windows 10, BitLocker e Windows Defender, Windows Information Protection e definições de configuração de dispositivos personalizadas no portal do Azure. Utilize este perfil para gerir e proteger dados e dispositivos na sua empresa.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/22/2018
ms.topic: get-started-article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: e92a10f51fb403c802c1c6d3ea79ccf49a1e93fb
ms.sourcegitcommit: a22309174e617e59ab0cdd0a55abde38711a5f35
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/23/2018
---
# <a name="what-are-microsoft-intune-device-profiles"></a>O que são os perfis de dispositivos do Microsoft Intune?

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

O Microsoft Intune inclui definições e funcionalidades que pode ativar ou desativar em diferentes dispositivos na sua organização. Estas definições e funcionalidades são geridas com perfis. Alguns exemplos de perfil incluem: 

- Um perfil Wi-Fi que dá a diferentes dispositivos acesso ao seu Wi-Fi empresarial
- Um perfil VPN que dá a diferentes dispositivos acesso ao seu servidor VPN na sua rede empresarial

Este tópico fornece uma descrição geral dos diferentes perfis que pode criar para os seus dispositivos. Utilize estes perfis para permitir ou bloquear algumas funcionalidades nos dispositivos.

## <a name="before-you-begin"></a>Antes de começar
Para ver as funcionalidades disponíveis, abra o [portal do Azure](https://portal.azure.com) e abra o seu recurso do Intune. 

A **configuração do dispositivo** inclui as seguintes opções:

- **Descrição geral**: indica o estado dos seus perfis e fornece detalhes adicionais sobre os perfis que atribuiu aos utilizadores e dispositivos
- **Gestão**: crie perfis de dispositivo e carregue [Scripts do PowerShell](intune-management-extension.md) personalizados para executar no perfil
- **Monitorização**: verifique o estado de um perfil e veja registos dos seus perfis
- **Configuração**: adicione uma autoridade de certificação (SCEP ou PFX) ou ative a Gestão de Despesas de Telecomunicação no perfil

## <a name="create-the-profile"></a>Criar o perfil

A opção [Criar perfis de dispositivo](device-profile-create.md) fornece orientação passo a passo para criar um perfil. 

## <a name="device-features-profile"></a>Perfil de funcionalidades do dispositivo

As [funcionalidades do dispositivo](device-features-configure.md) controlam as funcionalidades nos dispositivos iOS e macOS como configurações de dispositivos partilhados, notificações e AirPrint.

Esta funcionalidade suporta:  
- iOS 
- macOS

## <a name="device-restrictions-profile"></a>Perfil de restrições de dispositivos
As [restrições de dispositivos](device-restrictions-configure.md) controlam a segurança, hardware, partilha de dados e mais definições nos dispositivos. Por exemplo, pode criar um perfil de restrição do dispositivo para impedir que os utilizadores dos dispositivos iOS utilizem a câmara do dispositivo. 

Esta funcionalidade suporta: 

- Android
- iOS
- macOS
- Windows 10
- Windows 10 Team

## <a name="email-profile"></a>Perfil de e-mail
O perfil de [definições de e-mail](email-settings-configure.md) cria, atribui e monitoriza as definições de e-mail do Exchange ActiveSync nos dispositivos. Os perfis de e-mail ajudam a assegurar a consistência, reduzem as chamadas de suporte e permitem que os utilizadores finais acedam ao e-mail da empresa nos respetivos dispositivos pessoais sem precisarem de efetuar qualquer configuração. 

Esta funcionalidade suporta: 

- Android
- iOS
- Windows Phone 8.1
- Windows 10

## <a name="wi-fi-profile"></a>Perfil Wi-Fi
As [definições de Wi-Fi](wi-fi-settings-configure.md) atribuem definições de rede sem fios a utilizadores e dispositivos. Quando atribui um perfil Wi-Fi, os utilizadores obtêm acesso ao seu Wi-Fi empresarial sem necessidade de configuração. 

Esta funcionalidade suporta: 

- Android
- iOS
- macOS
- Windows 8.1 (importar apenas)

## <a name="vpn-profile"></a>Perfil VPN
As [definições de VPN](vpn-settings-configure.md) atribuem perfis VPN a utilizadores e dispositivos na sua organização, para que possam ligar-se de forma fácil e segura à rede. 

As redes virtuais privadas (VPN) permitem-lhe conceder aos utilizadores acesso remoto protegido à rede da sua empresa. Os dispositivos utilizam um perfil de ligação VPN para iniciar uma ligação com o servidor VPN. 

Esta funcionalidade suporta: 

- Android
- iOS
- macOS
- Windows Phone 8.1
- Windows 8.1
- Windows 10

## <a name="education-profile"></a>Perfil de educação
As [definições de educação](education-settings-configure.md) configuram as opções da [aplicação Fazer um Teste do Windows](https://education.microsoft.com/gettrained/win10takeatest). Quando configurar estas opções, não pode executar qualquer outra aplicação no dispositivo até o teste estar concluído.

## <a name="certificates-profile"></a>Perfil de certificados
Os [certificados](certificates-configure.md) configuram certificados SCEP e PKCS fidedignos que podem ser atribuídos aos dispositivos e que servem para autenticar perfis Wi-Fi, VPN e de e-mail.

Esta funcionalidade suporta: 

- Android
- iOS
- Windows Phone 8.1
- Windows 8.1
- Windows 10

## <a name="edition-upgrade-profile"></a>Perfil de atualização de edição
As [atualizações de edição do Windows 10](edition-upgrade-configure-windows-10.md) atualizam automaticamente os dispositivos que executam algumas versões do Windows 10 para uma edição mais recente.

Esta funcionalidade suporta: apenas o Windows 10

## <a name="endpoint-protection-profile"></a>Perfil de proteção de ponto final
As [definições de proteção de ponto final para o Windows 10](endpoint-protection-windows-10.md) configuram as definições do BitLocker e Windows Defender para dispositivos com o Windows 10.

Para carregar a Proteção Avançada Contra Ameaças do Windows Defender (WDATP) com o Microsoft Intune, veja [Configure endpoints using Mobile Device Management (MDM) tools](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/configure-endpoints-mdm-windows-defender-advanced-threat-protection) (Configurar pontos finais através das ferramentas da Gestão de Dispositivos Móveis [MDM]).

Esta funcionalidade suporta: apenas o Windows 10

## <a name="windows-information-protection-profile"></a>Perfil do Windows Information Protection
O [Windows Information Protection](windows-information-protection-configure.md) ajuda a proteger contra a fuga de dados sem interferir com a experiência do empregado. Também ajuda a proteger aplicações e dados da empresa contra fugas de dados acidentais em dispositivos pertencentes à empresa e em dispositivos pessoais que os empregados utilizem no trabalho, sem que seja necessário fazer alterações ao seu ambiente ou a outras aplicações.

Esta funcionalidade suporta: apenas o Windows 10

## <a name="custom-profile"></a>Perfil personalizado
As [definições personalizadas](custom-settings-configure.md) incluem a capacidade de atribuir definições de dispositivo que não estejam incorporadas no Intune. Por exemplo, em dispositivos Android, pode introduzir valores OMA-URI. Para dispositivos iOS, pode importar um ficheiro de configuração que criou no Apple Configurator. 

Esta funcionalidade suporta:

- Android
- iOS
- macOS
- Windows Phone 8.1
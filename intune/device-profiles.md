---
title: "O que são perfis de dispositivo no Microsoft Intune?"
titlesuffix: Azure portal
description: Saiba mais sobre os perfis de dispositivo do Intune e de que forma podem ajudar a gerir e a proteger os dispositivos na sua empresa."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 08/23/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 1053ddf4195e8481cf383c441664e07c02dacdec
ms.sourcegitcommit: e10dfc9c123401fabaaf5b487d459826c1510eae
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/09/2017
---
# <a name="what-are-microsoft-intune-device-profiles"></a>O que são os perfis de dispositivos do Microsoft Intune?

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Utilize a carga de trabalho **Configuração de dispositivos** do Microsoft Intune para gerir as definições e as funcionalidades em todos os dispositivos geridos por si. Esta é a carga de trabalho que mais utiliza para criar perfis de dispositivos, que lhe permitem gerir e controlar uma série inteira de diferentes funcionalidades nos dispositivos.

Quando abrir esta carga de trabalho, verá as seguintes opções:

- **Descrição Geral** – Esta página apresenta-lhe os estados e os relatórios que o ajudam a monitorizar as configurações dos dispositivos que atribuiu a utilizadores e a dispositivos.
- **Gerir Perfis** – esta secção permite criar perfis de configuração de dispositivos. Segue-se uma lista de todos os tipos de perfis que pode criar posteriormente neste tópico.
- **Configurar Autoridade de Certificação** – este fluxo de trabalho orienta-o ao longo dos passos necessários para configurar perfis de certificados do Intune.

## <a name="getting-started"></a>Introdução

O fluxo de trabalho para a criação de perfis de dispositivo é semelhante para todos os perfis. Leia [Como criar perfis de configuração de dispositivos do Microsoft Intune](device-profile-create.md) para obter mais informações. Continue a ler para obter informações específicas sobre a criação de definições para cada tipo de perfil.

Pode gerir as seguintes funcionalidades nos seus dispositivos:

## <a name="device-features"></a>Funcionalidades do dispositivo

As funcionalidades do dispositivo permitem-lhe controlar as funcionalidades nos dispositivos iOS e macOS como configurações de dispositivos partilhados, notificações e AirPrint.
Para obter mais informações, veja [Como configurar definições de funcionalidades do dispositivo](device-features-configure.md) Suporta: iOS e macOS.

## <a name="device-restrictions"></a>Restrições de dispositivos
As restrições de dispositivos permitem-lhe controlar muitas definições nos dispositivos que gere em várias categorias, incluindo definições de partilha de dados, segurança e hardware. Por exemplo, pode criar um perfil de restrição de dispositivo para impedir que os utilizadores dos dispositivos iOS de acedam à câmara do dispositivo.
Para obter mais informações, veja [Como configurar as definições de restrições de dispositivos](device-restrictions-configure.md). Suporta: Android, iOS, macOS, Windows 10 e Windows 10 Team.

## <a name="email"></a>E-mail
Os perfis de e-mail permitem-lhe criar, atribuir e monitorizar definições de e-mail do Exchange ActiveSync em dispositivos geridos por si. Os perfis de e-mail ajudam a assegurar a consistência, reduzem as chamadas de suporte e permitem que os utilizadores finais acedam ao e-mail da empresa nos respetivos dispositivos pessoais sem precisarem de efetuar qualquer configuração.
Para obter mais informações, veja [Como configurar definições de e-mail](email-settings-configure.md). Suporta: Android, iOS, Windows Phone 8.1 e Windows 10.

## <a name="wi-fi"></a>Wi-Fi
Utilize perfis de Wi-Fi para atribuir definições de redes sem fios a utilizadores e dispositivos na sua organização. Quando atribui um perfil Wi-Fi, os utilizadores obtêm acesso ao seu Wi-Fi empresarial sem necessidade de configuração.
Para obter mais informações, veja [Como configurar definições de Wi-Fi](wi-fi-settings-configure.md). Suporta: Android, iOS, macOS e Windows 8.1 (apenas de importação).

## <a name="vpn"></a>VPN
As Redes Virtuais Privadas (VPN) permitem-lhe conceder aos seus utilizadores acesso remoto protegido à rede da sua empresa. Os dispositivos utilizam um perfil de ligação VPN para iniciar uma ligação com o servidor VPN. Atribua perfis VPN a utilizadores e dispositivos na sua organização para que possam ligar-se de forma fácil e segura à rede.
Para obter mais informações, veja [Como configurar definições de VPN](vpn-settings-configure.md).
Suporta: Android, iOS, macOS, Windows Phone 8.1, Windows 8.1 e Windows 10.

## <a name="education"></a>Educação
Permite-lhe configurar as opções da aplicação Fazer um Teste do Windows. Quando configurar estas opções, não pode executar qualquer outra aplicação no dispositivo até o teste estar concluído.
Para obter mais informações, veja [Como configurar definições de educação](education-settings-configure.md)

## <a name="certificates"></a>Certificados
Este tipo de perfil permite-lhe configurar certificados SCEP e PKCS fidedignos que podem ser atribuídos aos dispositivos e que servem para autenticar perfis de Wi-Fi, de VPN e de e-mail.
Para obter mais informações, veja [Como configurar certificados](certificates-configure.md). Suporta: Android, iOS, Windows Phone 8.1, Windows 8.1 e Windows 10.

## <a name="edition-upgrade"></a>Atualização de edição
Este tipo de perfil permite-lhe atualizar automaticamente dispositivos que executam algumas versões do Windows 10 para uma edição mais recente.
Para obter mais informações, veja [Como configurar atualizações de edição do Windows 10](edition-upgrade-configure-windows-10.md). Suporta: apenas o Windows 10.

## <a name="endpoint-protection"></a>Proteção de ponto final
Este tipo de perfil permite-lhe configurar as definições do BitLocker e do Windows Defender para dispositivos com o Windows 10.
Para obter mais informações, veja [Definições de proteção de ponto final para o Windows 10](endpoint-protection-windows-10.md). Suporta: apenas o Windows 10.

## <a name="windows-information-protection"></a>Windows Information Protection
O Windows Information Protection ajuda a proteger contra a fuga de dados sem interferir com a experiência do empregado. Também ajuda a proteger aplicações e dados da empresa contra fugas de dados acidentais em dispositivos pertencentes à empresa e em dispositivos pessoais que os empregados utilizem no trabalho, sem que seja necessário fazer alterações ao seu ambiente ou a outras aplicações.
Para obter mais informações, veja [Como configurar o Windows Information Protection](windows-information-protection-configure.md). Suporta: apenas o Windows 10.

## <a name="custom"></a>Personalizar
As definições personalizadas permitem-lhe atribuir definições de dispositivo que não estejam incorporadas no Intune. Por exemplo, em dispositivos Android, pode especificar valores OMA-URI para configurar o dispositivo. Para dispositivos iOS, pode importar um ficheiro de configuração que criou no Apple Configurator.
Para obter mais informações, veja [Como configurar definições personalizadas](custom-settings-configure.md). Suporta: Android, iOS, macOS e Windows Phone 8.1.

## <a name="next-steps"></a>Passos seguintes
Selecione um dos tipos de perfil na lista para começar a configurar os dispositivos.

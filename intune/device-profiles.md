---
title: "O que são perfis de dispositivo no Microsoft Intune? | Documentos da Microsoft"
titleSuffix: Intune Azure preview
description: "Pré-visualização do Azure no Intune: saiba mais sobre os perfis de dispositivo do Intune e de que forma podem ajudar a gerir e a proteger os dispositivos na sua empresa."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 03/16/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 54b20d405613a67e54e9d22df45a3055f093fafa
ms.contentlocale: pt-pt
ms.lasthandoff: 05/23/2017


---

# <a name="what-are-microsoft-intune-device-profiles"></a>O que são os perfis de dispositivos do Microsoft Intune?

[!INCLUDE[azure_preview](./includes/azure_preview.md)]

Utilize a carga de trabalho **Configuração de dispositivos** do Microsoft Intune para gerir as definições e as funcionalidades em todos os dispositivos geridos por si. Esta é a carga de trabalho que utilizará principalmente para criar perfis de dispositivos, que lhe permitem gerir e controlar uma série inteira de diferentes funcionalidades nos dispositivos que gerir.

Quando abrir esta carga de trabalho, verá as seguintes opções:

- **Descrição Geral** – Esta página apresenta-lhe os estados e os relatórios que o ajudam a monitorizar as configurações dos dispositivos que atribuiu a utilizadores e a dispositivos.
- **Gerir Perfis** – Esta secção permite criar perfis de configuração de dispositivos. Segue-se uma lista de todos os tipos de perfis que pode criar.
- **Configurar Autoridade de Certificação** – Este fluxo de trabalho orienta-o pelos passos necessários para configurar certificados. Terá de realizar este procedimento se quiser trabalhar com perfis de certificado do Intune.

## <a name="getting-started"></a>Introdução

O fluxo de trabalho para a criação de perfis de dispositivo é semelhante para todos os perfis. Leia [Como criar perfis de configuração de dispositivos do Microsoft Intune](device-profile-create.md) para obter mais informações sobre como criar perfis. Continue a ler para obter informações específicas sobre a criação de definições para cada tipo de perfil.

Pode gerir as seguintes funcionalidades nos seus dispositivos:

## <a name="device-features"></a>Funcionalidades do dispositivo

As funcionalidades do dispositivo permitem-lhe controlar as funcionalidades nos dispositivos iOS e macOS como configurações de dispositivos partilhados, notificações e AirPrint.
Para obter mais informações, veja [Como configurar definições de funcionalidades do dispositivo](device-features-configure.md) Suporta: iOS e macOS.

## <a name="device-restrictions"></a>Restrições de dispositivos
As restrições de dispositivos permitem-lhe controlar uma grande variedade de definições nos dispositivos que gere através de uma variedade de categorias, incluindo definições de partilha de dados, segurança, browser e hardware. Por exemplo, pode criar um perfil de restrição de dispositivo para impedir que os utilizadores dos dispositivos iOS de acedam à câmara do dispositivo.
Para obter mais informações, veja [Como configurar as definições de restrições de dispositivos](device-restrictions-configure.md). Suporta: Android, iOS, macOS, Windows 10 e Windows 10 Team.

## <a name="email"></a>E-mail
Os perfis de e-mail permitem-lhe criar, atribuir e monitorizar definições de e-mail do Exchange ActiveSync em dispositivos geridos por si. Ao atribuir estas definições, assegura a consistência, reduz as chamadas de suporte e permite que os utilizadores finais acedam ao e-mail da empresa nos dispositivos pessoais deles sem precisarem de efetuar qualquer configuração.
Para obter mais informações, veja [Como configurar definições de e-mail](email-settings-configure.md). Suporta: Android, iOS, Windows Phone 8.1 e Windows 10.

## <a name="wi-fi"></a>Wi-Fi
Utilize perfis de Wi-Fi para atribuir definições de redes sem fios a utilizadores e dispositivos na sua organização. Quando atribui um perfil Wi-Fi, os utilizadores terão acesso ao seu Wi-Fi empresarial sem qualquer necessidade de configuração.
Para obter mais informações, veja [Como configurar definições de Wi-Fi](wi-fi-settings-configure.md). Suporta: Android, iOS, macOS e Windows 8.1 (apenas de importação).

## <a name="vpn"></a>VPN
As Redes Virtuais Privadas (VPN) permitem-lhe conceder aos seus utilizadores acesso remoto protegido à rede da sua empresa. Os dispositivos utilizam um perfil de ligação VPN para iniciar uma ligação com o servidor VPN. Utilize os perfis VPN para atribuir definições de VPN a utilizadores e dispositivos na sua organização, para que possam ligar-se de forma fácil e segura à rede.
Para obter mais informações, veja [Como configurar definições de VPN](vpn-settings-configure.md).
Suporta: Android, iOS, macOS, Windows Phone 8.1, Windows 8.1 e Windows 10.

## <a name="education"></a>Educação
Permite-lhe configurar as opções da aplicação Fazer um Teste do Windows. Quando configurar estas opções, não pode executar qualquer outra aplicação no dispositivo até o teste estar concluído.
Para obter mais informações, veja [Como configurar definições de educação](education-settings-configure.md)

## <a name="certificates"></a>Certificados
Este tipo de perfil permite-lhe configurar certificados SCEP e PKCS fidedignos que podem ser atribuídos aos dispositivos e que servem para autenticar perfis de Wi-Fi, de VPN e de e-mail.
Para obter mais informações, veja [Como configurar certificados](certificates-configure.md). Suporta: Android, iOS, Windows Phone 8.1, Windows 8.1 e Windows 10.

## <a name="edition-upgrade"></a>Atualização de edição
Este tipo de perfil permite-lhe atualizar automaticamente dispositivos que executam algumas versões do Windows 10 para uma edição mais recente. Para obter mais informações, veja [Como configurar atualizações de edição do Windows 10](edition-upgrade-configure-windows-10.md). Suporta: apenas o Windows 10.

## <a name="windows-information-protection"></a>Windows Information Protection
O Windows Information Protection ajuda a proteger contra a fuga de dados sem interferir com a experiência do empregado. Também ajuda a proteger aplicações e dados da empresa contra fugas de dados acidentais em dispositivos pertencentes à empresa e em dispositivos pessoais que os empregados utilizem no trabalho, sem que seja necessário fazer alterações ao seu ambiente ou a outras aplicações.
Para obter mais informações, veja [Como configurar o Windows Information Protection](windows-information-protection-configure.md). Suporta: apenas o Windows 10.

## <a name="custom"></a>Personalizar
As definições personalizadas permitem-lhe atribuir definições de dispositivo que não estejam incorporadas no Intune. Por exemplo, em dispositivos Android, pode especificar valores OMA-URI para configurar o dispositivo. Para dispositivos iOS, pode importar um ficheiro de configuração que criou no Apple Configurator.
Para obter mais informações, veja [Como configurar definições personalizadas](custom-settings-configure.md). Suporta: Android, iOS, macOS e Windows Phone 8.1.

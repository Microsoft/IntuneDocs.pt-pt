---
title: Funcionalidades do dispositivo e definições no Microsoft Intune – Azure | Documentos da Microsoft
description: Descrição geral dos diferentes do perfis de dispositivo Microsoft Intune, incluindo funcionalidades, restrições, e-mail, Wi-Fi, VPN, educação, certificados, atualizar o Windows 10, BitLocker e o Windows defender, o Windows Information Protection, modelos administrativos, e definições de configuração de dispositivo personalizado no portal do Azure. Utilize estes perfis para gerir e proteger os dados e dispositivos na sua empresa.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/29/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.openlocfilehash: cf2bfbc992d4577e345b73f07ec465990feac317
ms.sourcegitcommit: 0142020a7cd75348c6367facf072ed94238e667f
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/29/2019
ms.locfileid: "55229989"
---
# <a name="apply-features-settings-on-your-devices-using-device-profiles-in-microsoft-intune"></a>Aplicar definições de funcionalidades nos seus dispositivos com perfis de dispositivos no Microsoft Intune

O Microsoft Intune inclui definições e funcionalidades, pode ativar ou desativar em diferentes dispositivos na sua organização. Estas definições e funcionalidades são adicionadas para "perfis de configuração". Pode criar perfis para diferentes dispositivos, plataformas diferentes, incluindo iOS, Android e Windows e, em seguida, utilize o Intune para aplicar o perfil a dispositivos na sua organização.

Alguns exemplos de perfil incluem:

- Em dispositivos Windows 10, utilize um modelo de perfil bloquear controles ActiveX no Internet Explorer.
- Em dispositivos iOS e macOS, permitir aos utilizadores utilizar impressoras com o AirPrint na sua organização.
- Permitir ou impedir o acesso a bluetooth no dispositivo.
- Crie um perfil de Wi-Fi ou VPN que dá a diferentes dispositivos acesso à sua rede empresarial.
- Gerir atualizações de software, incluindo quando são instaladas.
- Execute um dispositivo de quiosque dedicado que pode executar uma aplicação ou executar muitas aplicações de um dispositivo Android.

Este artigo apresenta os passos para criar um perfil e proporcione uma descrição geral dos diferentes tipos de perfis que pode criar. Utilize estes perfis para permitir ou bloquear algumas funcionalidades nos dispositivos.

## <a name="create-the-profile"></a>Criar o perfil

1. Na [portal do Azure](https://portal.azure.com), selecione **todos os serviços** > Filtrar **Intune** > selecione **Intune**.

2. Selecione **Configuração do dispositivo**. Tem as seguintes opções:

    - **Descrição geral**: Indica o estado dos seus perfis e fornece detalhes adicionais sobre os perfis que atribuiu a utilizadores e dispositivos.
    - **Gerir**: Criar perfis de dispositivo, carregue o custom [scripts do PowerShell](intune-management-extension.md) para executar no perfil e adicionar os planos de dados em dispositivos com o [eSIM](esim-device-configuration.md).
    - **Monitor**: Verifique o estado de um perfil para o êxito ou falha e veja registos dos seus perfis.
    - **Configuração**: Adicionar uma autoridade de certificado SCEP ou PFX ou ativar [gestão de despesas de telecomunicações](telecom-expenses-monitor.md) no perfil.

3. Selecione **perfis** > **criar perfil**. Introduza as seguintes propriedades:

   - **Nome**: Introduza um nome descritivo para o perfil.
   - **Descrição**: Introduza uma descrição para o perfil. Esta definição é opcional, mas recomendada.
   - **Plataforma**: Escolha a plataforma dos seus dispositivos. As opções são:  

       - **Android**
       - **Android Enterprise**
       - **iOS**
       - **macOS**
       - **Windows Phone 8.1**
       - **Windows 8.1 e posterior**
       - **Windows 10 e posterior**

   - **Tipo de perfil**: Selecione o tipo de definições que pretende criar. A lista apresentada depende da **plataforma** que escolher:

       - [Modelos administrativos](administrative-templates-windows.md)
       - [Personalizado](custom-settings-configure.md)
       - [Otimização da entrega](delivery-optimization-windows.md)
       - [Funcionalidades do dispositivo](device-features-configure.md)
       - [Restrições de dispositivos](device-restrictions-configure.md)
       - [Comutador de atualização e o modo de edição](edition-upgrade-configure-windows-10.md)
       - [Educação](education-settings-configure.md)
       - [e-mail](email-settings-configure.md)
       - [Proteção de ponto final](endpoint-protection-configure.md)
       - [Proteção de identidade](identity-protection-configure.md)  
       - [Modo de Quiosque](kiosk-settings.md)
       - [Certificado PKCS](certficates-pfx-configure.md)
       - [Certificado SCEP](certificates-scep-configure.md)
       - [Certificado fidedigno](certificates-configure.md)
       - [Políticas de atualização](software-updates-ios.md)
       - [VPN](vpn-settings-configure.md)
       - [Wi-Fi](wi-fi-settings-configure.md)
       - [O Windows Defender ATP](advanced-threat-protection.md)
       - [Windows Information Protection](windows-information-protection-configure.md)

     Por exemplo, se selecionar **iOS** para a plataforma, as opções de tipo de perfil ter um aspeto semelhantes ao seguinte:

     ![Criar perfil de iOS no Intune](./media/create-device-profile.png)

4. Selecione **definições**. As definições são organizadas por categoria. Selecione uma categoria para ver uma lista de todas as definições que pode configurar.

5. Quando terminar, selecione **OK** > **criar** para guardar as alterações.

Para saber mais sobre os tipos de perfil diferente, leia as secções seguintes neste artigo.

## <a name="administrative-templates-preview"></a>Modelos administrativos (pré-visualização)

[Modelos administrativos](administrative-templates-windows.md) inclui centenas de definições que pode configurar para o Internet Explorer, OneDrive, ambiente de trabalho remoto, Word, Excel e outros programas do Office e muito mais.

Estes modelos oferecem aos administradores uma vista simplificada e fácil de configurações semelhantes à diretiva de grupo, mas são 100% baseado na nuvem. 

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

Definições de local público também disponíveis como restrições de dispositivos para [Android](device-restrictions-android.md#kiosk), [Android Enterprise](device-restrictions-android-for-work.md#kiosk-settings), e [ios](device-restrictions-ios.md#kiosk-supervised-only).

## <a name="email"></a>Email

[Definições de e-mail](email-settings-configure.md) cria, atribui e monitoriza as definições de e-mail do Exchange ActiveSync nos dispositivos. Ajuda de perfis de e-mail com a consistência, reduzem as chamadas de suporte e permitem que os utilizadores finais acesso da empresa e-mail nos seus dispositivos pessoais, sem qualquer configuração necessária por parte dos mesmos. 

Esta funcionalidade suporta: 

- Android
- iOS
- Windows Phone 8.1
- Windows 10 e posterior

## <a name="vpn"></a>VPN

As [definições de VPN](vpn-settings-configure.md) atribuem perfis VPN a utilizadores e dispositivos na sua organização, para que possam ligar-se de forma fácil e segura à rede. 

As redes virtuais privadas (VPN) permitem-lhe conceder aos utilizadores acesso remoto protegido à rede da sua empresa. Os dispositivos utilizam um perfil de ligação VPN para iniciar uma ligação com o seu servidor VPN. 

Esta funcionalidade suporta: 

- Android
- iOS
- macOS
- Windows Phone 8.1
- Windows 8.1
- Windows 10 e posterior

## <a name="wi-fi"></a>Wi-Fi

As [definições de Wi-Fi](wi-fi-settings-configure.md) atribuem definições de rede sem fios a utilizadores e dispositivos. Quando atribui um perfil Wi-Fi, os utilizadores obtêm acesso ao seu Wi-Fi empresarial sem necessidade de configuração. 

Esta funcionalidade suporta: 

- Android
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

[Certificados](certificates-configure.md) configura fidedigno, SCEP e PKCS certificados que são atribuídos aos dispositivos e utilizado para autenticar Wi-Fi, VPN e perfis de e-mail.

Esta funcionalidade suporta: 

- Android
- iOS
- Windows Phone 8.1
- Windows 8.1
- Windows 10 e posterior

## <a name="windows-information-protection-profile"></a>Perfil do Windows Information Protection

O [Windows Information Protection](windows-information-protection-configure.md) ajuda a proteger contra a fuga de dados sem interferir com a experiência do empregado. Ele também ajuda a proteger aplicações empresariais e os dados contra fugas de dados acidentais em dispositivos pertencentes à empresa e dispositivos pessoais que os empregados utilizem no trabalho. Com o Windows Information Protection não requer alterações ao seu ambiente ou outras aplicações.

Esta funcionalidade suporta:

- Windows 10 e posterior

## <a name="shared-multi-user-device"></a>Dispositivo multiutilizador partilhado

[Windows 10](shared-user-device-settings-windows.md) e [Windows Holographic for Business](shared-user-device-settings-windows-holographic.md) inclui definições para gerir dispositivos com vários utilizadores, dispositivos partilhados também conhecido como ou PCs partilhados. Quando um utilizador inicia sessão no dispositivo, pode escolher se o utilizador pode alterar as opções de suspensão ou guardar ficheiros no dispositivo. Noutro exemplo, pode criar uma política que elimina Inativas credenciais de dispositivos HoloLens do Windows para economizar espaço.

Estas definições de dispositivos de vários utilizadores partilhados permitem que um administrador controlar alguns dos recursos de dispositivo e gerir estes dispositivos partilhados, através do Intune.

Esta funcionalidade suporta:

- Windows 10 e posterior
- Windows Holographic for Business

## <a name="custom-profile"></a>Perfil personalizado

[Definições personalizadas](custom-settings-configure.md) permite que os administradores atribuir definições de dispositivo que não estão incorporadas no Intune. Por exemplo, em dispositivos Android, pode introduzir valores OMA-URI. Para dispositivos iOS, pode importar um ficheiro de configuração que criou no Apple Configurator. 

Esta funcionalidade suporta:

- Android
- iOS
- macOS
- Windows Phone 8.1

## <a name="manage-and-troubleshoot"></a>Gestão e resolução de problemas

[Faça a gestão dos seus perfis](device-profile-monitor.md) para verificar o estado dos dispositivos e os perfis atribuídos. Ver as definições que causam um conflito e os perfis que contêm essas definições também poderá ajudá-lo a resolver conflitos. [Problemas comuns e resoluções](device-profile-troubleshoot.md) fornece uma perguntas e respostas para o ajudar a notificações de trabalho com perfis, incluindo o que acontece quando um perfil é eliminado, o que faz com que sejam enviados para os dispositivos e muito mais.

## <a name="next-steps"></a>Passos Seguintes
Selecione a sua plataforma para começar:


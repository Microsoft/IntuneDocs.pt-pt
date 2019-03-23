---
title: Criar perfis de dispositivo no Microsoft Intune – Azure | Microsoft Docs
description: Adicionar ou configurar um perfil de configuração do dispositivo no Microsoft Intune. Selecione o tipo de plataforma, configure as definições e adicionar uma etiqueta de âmbito.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/21/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: d98aceff-eb35-4e3e-8e40-5f300e7335cc
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 066508ba62d4b0ece3fe5a5e95b709a12832f1a0
ms.sourcegitcommit: 1069b3b1ed593c94af725300aafd52610c7d8f04
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2019
ms.locfileid: "58394917"
---
# <a name="create-a-device-profile-in-microsoft-intune"></a>Criar um perfil de dispositivo no Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Perfis de dispositivos permitem-lhe adicionar e configurar as definições e, em seguida, enviar estas definições para dispositivos na sua organização. [Aplicar definições e funcionalidades nos seus dispositivos através de perfis de dispositivo](device-profiles.md) apresenta mais detalhes, incluindo o que pode fazer.

Este artigo:

- Lista os passos para criar um perfil.
- Mostra-lhe como adicionar uma etiqueta de âmbito para o perfil "Filtrar".
- Lista a atualização de entrada quando os dispositivos recebem perfis e quaisquer atualizações de perfil de tempos de ciclos.

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

   - **Tipo de perfil**: Selecione o tipo de definições que pretende criar. A lista apresentada depende da **plataforma** que escolher.
   - **Definições**: Os seguintes artigos descrevem as definições para cada tipo de perfil:

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

     Por exemplo, se selecionar **iOS** para a plataforma, as opções de tipo de perfil ter um aspeto semelhantes ao seguinte perfil:

     ![Criar perfil de iOS no Intune](./media/create-device-profile.png)

4. Quando terminar, selecione **OK** > **criar** para guardar as alterações. O perfil é criado e apresentado na lista.

## <a name="scope-tags"></a>Scope tags (Etiquetas de âmbito)

Depois de adicionar as definições, também pode adicionar uma etiqueta de âmbito para o perfil. Etiquetas de âmbito atribuam e filtrar políticas a grupos específicos, como os funcionários de RH ou todos os E.U.A. por NC.

Para obter mais informações sobre etiquetas de âmbito e o que pode fazer, consulte [RBAC de utilização e as etiquetas de âmbito para distribuídos IT](scope-tags.md).

### <a name="add-a-scope-tag"></a>Adicionar uma etiqueta de âmbito

1. Selecione **âmbito (etiquetas)**.
2. Selecione **adicionar** para criar uma nova etiqueta de âmbito. Em alternativa, selecione uma etiqueta de âmbito existente na lista.
3. Selecione **OK** para guardar as alterações.

## <a name="refresh-cycle-times"></a>Tempos de ciclos de atualização

O Intune utiliza os ciclos de atualização seguinte para verificar a existência de atualizações para perfis de configuração:

| Plataforma | Ciclo de atualização|
| --- | --- |
| iOS | A cada 6 horas |
| macOS | A cada 6 horas |
| Android | A cada 8 horas |
| PCs com o Windows 10 inscritos como dispositivos | A cada 8 horas |
| Windows Phone | A cada 8 horas |
| Windows 8.1 | A cada 8 horas |

Se o dispositivo inscrito recentemente, o check-in é executado com mais frequência:

| Plataforma | Frequência |
| --- | --- |
| iOS | A cada 15 minutos durante 6 horas e, em seguida, a cada 6 horas |  
| macOS | A cada 15 minutos durante 6 horas e, em seguida, a cada 6 horas | 
| Android | A cada 3 minutos durante 15 minutos, depois a cada 15 minutos durante 2 horas e, em seguida, a cada 8 horas | 
| PCs com o Windows 10 inscritos como dispositivos | A cada 3 minutos durante 30 minutos e, em seguida, a cada 8 horas | 
| Windows Phone | A cada 5 minutos durante 15 minutos, depois a cada 15 minutos durante 2 horas e, em seguida, a cada 8 horas | 
| Windows 8.1 | A cada 5 minutos durante 15 minutos, depois a cada 15 minutos durante 2 horas e, em seguida, a cada 8 horas | 

Em qualquer altura, os utilizadores podem abrir a aplicação Portal da empresa e sincronizar o dispositivo para verificar imediatamente a existência de atualizações de perfil.

## <a name="next-steps"></a>Passos Seguintes

[Atribua o perfil](device-profile-assign.md) e [monitorize o respetivo estado](device-profile-monitor.md).

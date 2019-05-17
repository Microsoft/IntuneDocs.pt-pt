---
title: Criar perfis de dispositivo no Microsoft Intune – Azure | Microsoft Docs
description: Adicione ou configure um perfil de configuração de dispositivos no Microsoft Intune. Selecione o tipo de plataforma, configure as definições e adicione uma etiqueta de âmbito.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/03/2019
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
ms.openlocfilehash: 08c6ece37a4ff6eceaa4df735f365453a4bc7d88
ms.sourcegitcommit: 1cae690ca2ac6cc97bbcdf656f54b31878297ae8
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/22/2019
ms.locfileid: "59898858"
---
# <a name="create-a-device-profile-in-microsoft-intune"></a>Criar um perfil de dispositivo no Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Os perfis de dispositivo permitem-lhe adicionar e configurar definições e, em seguida, enviar essas definições para dispositivos na sua organização. Veja [Aplicar definições e funcionalidades aos dispositivos com perfis de dispositivo](device-profiles.md) para obter mais detalhes, incluindo o que pode fazer.

Este artigo:

- Apresenta os passos para criar um perfil.
- Mostra-lhe como adicionar uma etiqueta de âmbito para “filtrar” o perfil.
- Apresenta os tempos de ciclos de atualização de entrada quando os dispositivos recebem perfis e atualizações de perfis.

## <a name="create-the-profile"></a>Criar o perfil

1. No [portal do Azure](https://portal.azure.com), selecione **Todos os Serviços** > filtre o **Intune** > selecione  **Intune**.

2. Selecione **Configuração do dispositivo**. Tem as seguintes opções:

    - **Descrição geral**: indica o estado dos perfis e fornece detalhes adicionais sobre os perfis que atribuiu aos utilizadores e dispositivos.
    - **Gerir**: crie perfis de dispositivo, carregue [scripts do PowerShell](intune-management-extension.md) personalizados para executar no perfil e adicione planos de dados aos dispositivos com o [eSIM](esim-device-configuration.md).
    - **Monitorizar**: verifique o estado de um perfil e veja os registos dos perfis.
    - **Configurar**: adicione uma autoridade de certificação (SCEP ou PFX) ou ative a [Gestão de Despesas de Telecomunicação](telecom-expenses-monitor.md) no perfil.

3. Selecione **Perfis** > **Criar Perfil**. Introduza as seguintes propriedades:

   - **Nome**: introduza um nome descritivo para o perfil. Atribua nomes aos perfis de forma que possa identificá-los facilmente mais tarde. Por exemplo, um bom nome de perfil é **Perfil de e-mail WP para toda a empresa**.
   - **Descrição**: introduza uma descrição para o perfil. Esta definição é opcional, mas recomendada.
   - **Plataforma**: escolha a plataforma dos dispositivos. As opções são:  

       - **Android**
       - **Android Enterprise**
       - **iOS**
       - **macOS**
       - **Windows Phone 8.1**
       - **Windows 8.1 e posterior**
       - **Windows 10 e posterior**

   - **Tipo de perfil**: selecione o tipo de definições que quer criar. A lista apresentada depende da **plataforma** que escolher.
   - **Definições**: Os seguintes artigos descrevem as definições para cada tipo de perfil:

       - [Modelos administrativos](administrative-templates-windows.md)
       - [Personalizar](custom-settings-configure.md)
       - [Otimização da entrega](delivery-optimization-windows.md)
       - [Funcionalidades do dispositivo](device-features-configure.md)
       - [Restrições de dispositivos](device-restrictions-configure.md)
       - [Atualização da edição e alteração do modo ](edition-upgrade-configure-windows-10.md)
       - [Educação](education-settings-configure.md)
       - [E-mail](email-settings-configure.md)
       - [Proteção de ponto final](endpoint-protection-configure.md)
       - [Proteção de identidade](identity-protection-configure.md)  
       - [Modo de Quiosque](kiosk-settings.md)
       - [Certificado PKCS](certficates-pfx-configure.md)
       - [Certificado SCEP](certificates-scep-configure.md)
       - [Certificado fidedigno](certificates-configure.md)
       - [Políticas de atualização](software-updates-ios.md)
       - [VPN](vpn-settings-configure.md)
       - [Wi-Fi](wi-fi-settings-configure.md)
       - [Windows Defender ATP](advanced-threat-protection.md)
       - [Windows Information Protection](windows-information-protection-configure.md)

     Por exemplo, se selecionar **iOS** para a plataforma, as opções de tipo de perfil terão um aspeto semelhante ao seguinte perfil:

     ![Criar um perfil iOS no Intune](./media/create-device-profile.png)

4. Quando terminar, selecione **OK** > **Criar** para guardar as alterações. O perfil é criado e apresentado na lista.

## <a name="scope-tags"></a>Scope tags (Etiquetas de âmbito)

Depois de adicionar as definições, também pode adicionar uma etiqueta de âmbito ao perfil. As etiquetas de âmbito são uma ótima forma de atribuir e filtrar políticas para grupos específicos, tais como RH ou Todos os funcionários dos EUA.

Para obter mais informações sobre etiquetas de âmbito e o que pode fazer, veja [Utilizar RBAC e etiquetas de âmbito para TI distribuídas](scope-tags.md).

### <a name="add-a-scope-tag"></a>Adicionar etiqueta de âmbito

1. Selecionar **Âmbito (Etiquetas)**.
2. Selecione **Adicionar** para criar uma nova etiqueta de âmbito. Em alternativa, selecione uma etiqueta de âmbito existente na lista.
3. Selecione **OK** para guardar as alterações.

## <a name="refresh-cycle-times"></a>Tempos de ciclos de atualização

O Intune utiliza os seguintes ciclos de atualização para verificar a existência de atualizações para os perfis de configuração:

| Platform | Ciclo de atualização|
| --- | --- |
| iOS | A cada 6 horas |
| macOS | A cada 6 horas |
| Android | A cada 8 horas |
| PCs com o Windows 10 inscritos como dispositivos | A cada 8 horas |
| Windows Phone | A cada 8 horas |
| Windows 8.1 | A cada 8 horas |

Se o dispositivo tiver sido inscrito recentemente, a entrada é executada com mais frequência:

| Platform | Frequência |
| --- | --- |
| iOS | A cada 15 minutos durante 6 horas e, em seguida, a cada 6 horas |  
| macOS | A cada 15 minutos durante 6 horas e, em seguida, a cada 6 horas | 
| Android | A cada 3 minutos durante 15 minutos, depois a cada 15 minutos durante 2 horas e, em seguida, a cada 8 horas | 
| PCs com o Windows 10 inscritos como dispositivos | A cada 3 minutos durante 30 minutos e, em seguida, a cada 8 horas | 
| Windows Phone | A cada 5 minutos durante 15 minutos, depois a cada 15 minutos durante 2 horas e, em seguida, a cada 8 horas | 
| Windows 8.1 | A cada 5 minutos durante 15 minutos, depois a cada 15 minutos durante 2 horas e, em seguida, a cada 8 horas | 

Em qualquer altura, os utilizadores podem abrir a aplicação do Portal da Empresa e sincronizar o dispositivo para verificarem imediatamente se existem as atualizações de perfis.

## <a name="next-steps"></a>Próximos passos

[Atribua o perfil](device-profile-assign.md) e [monitorize o respetivo estado](device-profile-monitor.md).

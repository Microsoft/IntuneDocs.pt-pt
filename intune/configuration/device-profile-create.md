---
title: Criar perfis de dispositivo no Microsoft Intune – Azure | Microsoft Docs
description: Adicione ou configure um perfil de configuração de dispositivos no Microsoft Intune. Selecione o tipo de plataforma, defina as configurações, adicione uma marca de escopo.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/04/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.assetid: d98aceff-eb35-4e3e-8e40-5f300e7335cc
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 51ec328a60ef2737c776bf6cf5d4b8dc1b32460c
ms.sourcegitcommit: 1a7f04c80548e035be82308d2618492f6542d3c0
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/07/2019
ms.locfileid: "73755311"
---
# <a name="create-a-device-profile-in-microsoft-intune"></a>Criar um perfil de dispositivo no Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Os perfis de dispositivo permitem-lhe adicionar e configurar definições e, em seguida, enviar essas definições para dispositivos na sua organização. Veja [Aplicar definições e funcionalidades aos dispositivos com perfis de dispositivo](device-profiles.md) para obter mais detalhes, incluindo o que pode fazer.

Este artigo:

- Apresenta os passos para criar um perfil.
- Mostra-lhe como adicionar uma etiqueta de âmbito para “filtrar” o perfil.
- Descreve as regras de aplicabilidade em dispositivos Windows 10 e mostra como criar uma regra.
- Apresenta os tempos de ciclos de atualização de entrada quando os dispositivos recebem perfis e atualizações de perfis.

## <a name="create-the-profile"></a>Criar o perfil

1. Entre no centro de [Administração do Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Selecione **dispositivos** > **perfis de configuração**. Você tem as seguintes opções:

    - **Visão geral**: lista o status de seus perfis e fornece detalhes adicionais sobre os perfis atribuídos a usuários e dispositivos.
    - **Gerenciar**: criar perfis de dispositivo, carregar [scripts](../apps/intune-management-extension.md) personalizados do PowerShell para execução dentro do perfil e adicionar planos de dados a dispositivos usando o [Esim](esim-device-configuration.md).
    - **Monitor**: Verifique o status de um perfil de êxito ou falha e também exiba os logs em seus perfis.
    - **Configuração**: Adicione uma autoridade de certificação SCEP ou pfx ou habilite o [Gerenciamento de despesas de telecomunicações](telecom-expenses-monitor.md) no perfil.

3. Selecione **Criar perfil**. Introduza as seguintes propriedades:

   - **Nome**: Insira um nome descritivo para o perfil. Atribua nomes aos perfis de forma que possa identificá-los facilmente mais tarde. Por exemplo, um bom nome de perfil é **Perfil de e-mail WP para toda a empresa**.
   - **Descrição:** introduza uma descrição para o perfil. Esta definição é opcional, mas recomendada.
   - **Plataforma**: escolha a plataforma dos seus dispositivos. As opções são:  

       - **Android**
       - **Android Enterprise**
       - **iOS/iPadOS**
       - **macOS**
       - **Windows Phone 8.1**
       - **Windows 8.1 e posterior**
       - **Windows 10 e posterior**

   - **Tipo de perfil**: selecione o tipo de configurações que você deseja criar. A lista apresentada depende da **plataforma** que escolher.
   - **Configurações**: os seguintes artigos descrevem as configurações para cada tipo de perfil:

       - [Modelos administrativos](administrative-templates-windows.md)
       - [Personalizar](../custom-settings-configure.md)
       - [Otimização da entrega](../delivery-optimization-windows.md)
       - [Funcionalidades do dispositivo](../device-features-configure.md)
       - [Restrições de dispositivos](device-restrictions-configure.md)
       - [Atualização da edição e alteração do modo ](edition-upgrade-configure-windows-10.md)
       - [Educação](education-settings-configure.md)
       - [Email](email-settings-configure.md)
       - [Proteção de ponto final](../protect/endpoint-protection-configure.md)
       - [Proteção de identidade](../protect/identity-protection-configure.md)  
       - [Modo de Quiosque](kiosk-settings.md)
       - [Certificado PKCS](../protect/certficates-pfx-configure.md)
       - [Certificado importado PKCS](../protect/certificates-imported-pfx-configure.md)
       - [Certificado SCEP](../protect/certificates-scep-configure.md)
       - [Certificado fidedigno](../protect/certificates-configure.md)
       - [Políticas de atualização](../software-updates-ios.md)
       - [VPN](vpn-settings-configure.md)
       - [Wi-Fi](wi-fi-settings-configure.md)
       - [Windows Defender ATP](../protect/advanced-threat-protection.md)
       - [Windows Information Protection](../protect/windows-information-protection-configure.md)

     Por exemplo, se você selecionar **Ios/iPadOS** para a plataforma, suas opções de tipo de perfil são semelhantes ao seguinte perfil:

     ![Criar um perfil iOS no Intune](./media/device-profile-create/create-device-profile.png)

4. Quando terminar, selecione **OK** > **Criar** para guardar as alterações. O perfil é criado e apresentado na lista.

## <a name="scope-tags"></a>Scope tags (Etiquetas de âmbito)

Depois de adicionar as definições, também pode adicionar uma etiqueta de âmbito ao perfil. As etiquetas de âmbito são uma ótima forma de atribuir e filtrar políticas para grupos específicos, tais como RH ou Todos os funcionários dos EUA.

Para obter mais informações sobre etiquetas de âmbito e o que pode fazer, veja [Utilizar RBAC e etiquetas de âmbito para TI distribuídas](../fundamentals/scope-tags.md).

### <a name="add-a-scope-tag"></a>Adicionar etiqueta de âmbito

1. Selecionar **Âmbito (Etiquetas)** .
2. Selecione **Adicionar** para criar uma nova etiqueta de âmbito. Em alternativa, selecione uma etiqueta de âmbito existente na lista.
3. Selecione **OK** para guardar as alterações.

## <a name="applicability-rules"></a>Regras de aplicabilidade

Aplica-se a:

- Windows 10 e posterior

As regras de aplicabilidade permitem que os administradores direcionem dispositivos em um grupo que atenda a critérios específicos. Por exemplo, você cria um perfil de restrições de dispositivo que se aplica ao grupo **todos os dispositivos Windows 10** . E, você só quer o perfil atribuído a dispositivos que executam o Windows 10 Enterprise.

Para executar essa tarefa, crie uma **regra de aplicabilidade**. Essas regras são ótimas para os seguintes cenários:

- Você usa o Windows 10 Education (EDU). Na faculdade Bellows, você deseja direcionar todos os dispositivos EDU do Windows 10 entre RS3 e RS4.
- Você deseja ter como alvo todos os usuários em recursos humanos na contoso, mas quer apenas dispositivos Windows 10 Professional ou Enterprise.

Para abordar esses cenários, você:

- Crie um grupo de dispositivos que inclua todos os dispositivos na faculdade Bellows. No perfil, adicione uma regra de aplicabilidade para que ela se aplique se a versão mínima do so for `16299` e a versão máxima for `17134`. Atribua esse perfil ao grupo de dispositivos do Bellows College.

  Quando atribuído, o perfil se aplica a dispositivos entre as versões mínima e máxima inseridas. Para dispositivos que não estão entre as versões mínima e máxima inseridas, seu status aparece como **não aplicável**.

- Crie um grupo de usuários que inclua todos os usuários em recursos humanos (RH) na contoso. No perfil, adicione uma regra de aplicabilidade para que ela se aplique a dispositivos que executam o Windows 10 Professional ou Enterprise. Atribua esse perfil ao grupo de usuários de RH.

  Quando atribuído, o perfil se aplica a dispositivos que executam o Windows 10 Professional ou Enterprise. Para dispositivos que não estão executando essas edições, seu status aparece como **não aplicável**.

- Se houver dois perfis com as mesmas configurações exatas, o perfil sem uma regra de aplicabilidade será aplicado. 

  Por exemplo, o outfilea tem como destino o grupo de dispositivos Windows 10, habilita o BitLocker e não tem uma regra de aplicabilidade. ProfileB tem como alvo o mesmo grupo de dispositivos Windows 10, habilita o BitLocker e tem uma regra de aplicabilidade para aplicar apenas o perfil ao Windows 10 Enterprise.

  Quando ambos os perfis são atribuídos, o perfila é aplicado porque ele não tem uma regra de aplicabilidade. 

Quando você atribui o perfil aos grupos, as regras de aplicabilidade agem como um filtro e apenas direcionam os dispositivos que atendem aos seus critérios.

### <a name="add-a-rule"></a>Adicionar uma regra

1. Selecione **regras de aplicabilidade**. Você pode escolher a **regra**, a **Propriedade**e a **edição do sistema operacional**:

    ![Adicionar uma regra de aplicabilidade a um perfil de configuração de dispositivo no Microsoft Intune](./media/device-profile-create/applicability-rules.png)

2. Em **regra**, escolha se deseja incluir ou excluir usuários ou grupos. As opções são:

    - **Atribuir perfil se**: inclui usuários ou grupos que atendem aos critérios inseridos.
    - **Não atribuir perfil se**: excluir usuários ou grupos que atendam aos critérios inseridos.

3. Em **Propriedade**, escolha seu filtro. As opções são: 

    - **Edição do sistema operacional**: na lista, verifique as edições do Windows 10 que você deseja incluir (ou excluir) em sua regra.
    - **Versão do so**: Insira os números de versão **mín** e **máx** do Windows 10 que você deseja incluir (ou excluir) em sua regra. Ambos os valores são obrigatórios.

      Por exemplo, você pode inserir `10.0.16299.0` (RS3 ou 1709) para a versão mínima e `10.0.17134.0` (RS4 ou 1803) para a versão máxima. Ou, você pode ser mais granular e inserir `10.0.16299.001` para a versão mínima e `10.0.17134.319` para a versão máxima.

4. Selecione **Adicionar** para salvar as alterações.

## <a name="refresh-cycle-times"></a>Tempos de ciclos de atualização

O Intune usa ciclos de atualização diferentes para verificar se há atualizações de perfis de configuração. Se o dispositivo tiver sido registrado recentemente, o check-in será executado com mais frequência. [Ciclos de atualização de política e perfil](device-profile-troubleshoot.md#how-long-does-it-take-for-devices-to-get-a-policy-profile-or-app-after-they-are-assigned) lista os tempos de atualização estimados.

Em qualquer altura, os utilizadores podem abrir a aplicação do Portal da Empresa e sincronizar o dispositivo para verificarem imediatamente se existem as atualizações de perfis.

## <a name="next-steps"></a>Próximos passos

[Atribua o perfil](../device-profile-assign.md) e [monitorize o respetivo estado](device-profile-monitor.md).

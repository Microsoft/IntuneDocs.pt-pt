---
title: Criar perfis de dispositivo no Microsoft Intune – Azure | Microsoft Docs
description: Adicione ou configure um perfil de configuração de dispositivos no Microsoft Intune. Selecione o tipo de plataforma, configure as definições, adicione uma etiqueta de âmbito.
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
ms.assetid: d98aceff-eb35-4e3e-8e40-5f300e7335cc
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6dff94a9bfeb21f09b8a8c629e10ba562d7e642b
ms.sourcegitcommit: 25e4847ead0f56c269cfefe1e01c1b9106a28cf1
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/05/2020
ms.locfileid: "78369416"
---
# <a name="create-a-device-profile-in-microsoft-intune"></a>Criar um perfil de dispositivo no Microsoft Intune

Os perfis de dispositivo permitem-lhe adicionar e configurar definições e, em seguida, enviar essas definições para dispositivos na sua organização. Veja [Aplicar definições e funcionalidades aos dispositivos com perfis de dispositivo](device-profiles.md) para obter mais detalhes, incluindo o que pode fazer.

Este artigo:

- Apresenta os passos para criar um perfil.
- Mostra-lhe como adicionar uma etiqueta de âmbito para “filtrar” o perfil.
- Descreve regras de aplicabilidade em dispositivos Windows 10 e mostra-lhe como criar uma regra.
- Apresenta os tempos de ciclos de atualização de entrada quando os dispositivos recebem perfis e atualizações de perfis.

## <a name="create-the-profile"></a>Criar o perfil

1. Inscreva-se no centro de administração do [Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Selecione **Dispositivos** > perfis de **configuração**. Tem as seguintes opções:

    - **Visão geral**: Lista o estado dos seus perfis e fornece detalhes adicionais sobre os perfis que atribuiu aos utilizadores e dispositivos.
    - **Gerir**: Criar perfis de dispositivos, carregar [scripts PowerShell personalizados](../apps/intune-management-extension.md) para executar dentro do perfil e adicionar planos de dados aos dispositivos que utilizem [eSIM](esim-device-configuration.md).
    - **Monitor**: Verifique o estado de um perfil para obter sucesso ou falha e consulte também os registos nos seus perfis.
    - **Configuração**: Adicione uma autoridade de certificadoS SCEP ou PFX ou ative a Gestão de [Despesas](telecom-expenses-monitor.md) da Telecom no perfil.

3. Selecione **Criar perfil**. Introduza as seguintes propriedades:

   - **Nome**: Introduza um nome descritivo para o perfil. Atribua nomes aos perfis de forma que possa identificá-los facilmente mais tarde. Por exemplo, um bom nome de perfil é **Perfil de e-mail WP para toda a empresa**.
   - **Descrição:** introduza uma descrição para o perfil. Esta definição é opcional, mas recomendada.
   - **Plataforma**: Escolha a plataforma dos seus dispositivos. As opções são:  

       - **Android**
       - **Android Enterprise**
       - **iOS/iPadOS**
       - **macOS**
       - **Windows Phone 8.1**
       - **Windows 8.1 e posterior**
       - **Windows 10 e posterior**

   - Tipo de **perfil:** Selecione o tipo de definições que pretende criar. A lista apresentada depende da **plataforma** que escolher.
   - **Definições**: Os seguintes artigos descrevem as definições para cada tipo de perfil:

       - [Modelos administrativos](administrative-templates-windows.md)
       - [Personalizar](../custom-settings-configure.md)
       - [Otimização da entrega](../delivery-optimization-windows.md)
       - [Funcionalidades do dispositivo](../device-features-configure.md)
       - [Restrições de dispositivos](device-restrictions-configure.md)
       - [Atualização da edição e alteração do modo ](edition-upgrade-configure-windows-10.md)
       - [Educação](education-settings-configure.md)
       - [E-mail](email-settings-configure.md)
       - [Proteção de ponto final](../protect/endpoint-protection-configure.md)
       - [Proteção de identidade](../protect/identity-protection-configure.md)  
       - [Modo de Quiosque](kiosk-settings.md)
       - [Certificado PKCS](../protect/certficates-pfx-configure.md)
       - [Certificado importado PKCS](../protect/certificates-imported-pfx-configure.md)
       - [Arquivo de preferência](preference-file-settings-macos.md)
       - [Certificado SCEP](../protect/certificates-scep-configure.md)
       - [Certificado fidedigno](../protect/certificates-configure.md)
       - [Políticas de atualização](../software-updates-ios.md)
       - [VPN](vpn-settings-configure.md)
       - [Wi-Fi](wi-fi-settings-configure.md)
       - [Microsoft Defender ATP](../protect/advanced-threat-protection.md)
       - [Windows Information Protection](../protect/windows-information-protection-configure.md)

     Por exemplo, se selecionar **iOS/iPadOS** para a plataforma, as opções do tipo de perfil são semelhantes ao seguinte perfil:

     ![Criar perfil iOS/iPadOS em Intune](./media/device-profile-create/create-device-profile.png)

4. Quando terminar, selecione **OK** > **Criar** para guardar as alterações. O perfil é criado e apresentado na lista.

## <a name="scope-tags"></a>Scope tags (Etiquetas de âmbito)

Depois de adicionar as definições, também pode adicionar uma etiqueta de âmbito ao perfil. As etiquetas de âmbito filtram perfis para grupos de TI específicos, tais como `US-NC IT Team` ou `JohnGlenn_ITDepartment`.

Para obter mais informações sobre etiquetas de âmbito e o que pode fazer, veja [Utilizar RBAC e etiquetas de âmbito para TI distribuídas](../fundamentals/scope-tags.md).

### <a name="add-a-scope-tag"></a>Adicionar etiqueta de âmbito

1. Selecionar **Âmbito (Etiquetas)** .
2. Selecione **Adicionar** para criar uma nova etiqueta de âmbito. Em alternativa, selecione uma etiqueta de âmbito existente na lista.
3. Selecione **OK** para guardar as alterações.

## <a name="applicability-rules"></a>Regras de aplicabilidade

Aplica-se a:

- Windows 10 e posterior

As regras de aplicabilidade permitem que os administradores direcionem dispositivos num grupo que satisfaça critérios específicos. Por exemplo, cria um perfil de restrições de dispositivos que se aplica ao grupo de **dispositivos All Windows 10.** E, só quer o perfil atribuído aos dispositivos que executam o Windows 10 Enterprise.

Para fazer esta tarefa, crie uma regra de **aplicabilidade.** Estas regras são ótimas para os seguintes cenários:

- Utiliza o Windows 10 Education (EDU). No Bellows College, você quer direcionar todos os dispositivos EDU do Windows 10 entre RS3 e RS4.
- Você quer direcionar todos os utilizadores em Recursos Humanos em Contoso, mas apenas quer dispositivos Profissionais ou Empresariais do Windows 10.

Para abordar estes cenários, você:

- Crie um grupo de dispositivos que inclua todos os dispositivos no Bellows College. No perfil, adicione uma regra de aplicabilidade para que se aplique se a versão mínima do SO for `16299` e a versão máxima for `17134`. Atribuir este perfil ao grupo de dispositivos da Escola Bellows.

  Quando é atribuído, o perfil aplica-se a dispositivos entre as versões mínima seleções mínimas e máximas que introduz. Para dispositivos que não estejam entre as versões mínima seleção e o máximo que introduz, o seu estado mostra **que não**é aplicável .

- Crie um grupo de utilizadores que inclua todos os utilizadores em Recursos Humanos (RH) na Contoso. No perfil, adicione uma regra de aplicabilidade para que se aplique a dispositivos que executem o Windows 10 Professional ou Enterprise. Atribuir este perfil ao grupo de utilizadores de RH.

  Quando é atribuído, o perfil aplica-se a dispositivos que executam o Windows 10 Professional ou Enterprise. Para dispositivos que não estejam a executar estas edições, o seu estado mostra **como Não aplicável**.

- Se houver dois perfis com as mesmas definições, então o perfil sem uma regra de aplicabilidade é aplicado. 

  Por exemplo, o ProfileA tem como alvo o grupo de dispositivos Windows 10, permite o BitLocker e não tem uma regra de aplicabilidade. O ProfileB tem como alvo o mesmo grupo de dispositivos Windows 10, permite o BitLocker, e tem uma regra de aplicabilidade para aplicar apenas o perfil ao Windows 10 Enterprise.

  Quando ambos os perfis são atribuídos, o ProfileA é aplicado porque não tem uma regra de aplicabilidade. 

Ao atribuir o perfil aos grupos, as regras de aplicabilidade funcionam como um filtro e apenas visam os dispositivos que cumprem os seus critérios.

### <a name="add-a-rule"></a>Adicione uma regra

1. Selecione Regras de **Aplicabilidade**. Pode escolher a **regra,** **propriedade**e **edição osso:**

    ![Adicione uma regra de aplicabilidade a um perfil de configuração do dispositivo no Microsoft Intune](./media/device-profile-create/applicability-rules.png)

2. Regra, escolha se pretende incluir ou excluir utilizadores ou grupos. As opções são:

    - **Atribuir perfil se**: Inclui utilizadores ou grupos que satisfaçam os critérios em que entra.
    - **Não designe o perfil se**: Excluir utilizadores ou grupos que satisfaçam os critérios em que insere.

3. Em **Propriedade,** escolha o seu filtro. As opções são: 

    - **Edição OS**: Na lista, consulte as edições do Windows 10 que pretende incluir (ou excluir) na sua regra.
    - **Versão OS**: Introduza os números da versão **min** e **max** Windows 10 que pretende incluir (ou excluir) na sua regra. Ambos os valores são necessários.

      Por exemplo, pode introduzir `10.0.16299.0` (RS3 ou 1709) para versão mínima e `10.0.17134.0` (RS4 ou 1803) para versão máxima. Ou, pode ser mais granular e introduzir `10.0.16299.001` para versão mínima e `10.0.17134.319` para versão máxima.

4. Selecione **Adicionar** para guardar as suas alterações.

## <a name="refresh-cycle-times"></a>Tempos de ciclos de atualização

Intune usa diferentes ciclos de atualização para verificar se há atualizações nos perfis de configuração. Se o dispositivo se matriculou recentemente, o check-in funciona com mais frequência. Os ciclos de atualização de políticas e perfis listam os [tempos estimados](device-profile-troubleshoot.md#how-long-does-it-take-for-devices-to-get-a-policy-profile-or-app-after-they-are-assigned) de atualização.

Em qualquer altura, os utilizadores podem abrir a aplicação do Portal da Empresa e sincronizar o dispositivo para verificarem imediatamente se existem as atualizações de perfis.

## <a name="recommendations"></a>Recomendações

Ao criar perfis, considere as seguintes recomendações:

- Diga o nome das suas políticas para saber o que são e o que fazem. Todas as políticas de [conformidade](../protect/create-compliance-policy.md) e perfis de [configuração](../configuration/device-profile-create.md) têm uma propriedade de **Descrição** opcional. Em **Descrição,** seja específico e inclua informações para que outros saibam o que a política faz.

  Alguns exemplos de perfil de configuração incluem:

  **Nome do perfil**: Modelo de administrador - perfil de configuração OneDrive para todos os utilizadores do Windows 10  
  **Descrição do perfil**: Perfil de modelo de administrador OneDrive que inclui as definições mínimas e base para todos os utilizadores do Windows 10. Criado por user@contoso.com para impedir que os utilizadores partilhem dados organizacionais para contas pessoais do OneDrive.

  **Nome do perfil**: Perfil VPN para todos os utilizadores iOS/iPadOS  
  **Descrição do perfil**: Perfil VPN que inclui as definições mínimas e base para todos os utilizadores iOS/iPadOS para ligar à VPN Contoso. Criado souser@contoso.com para que os utilizadores autentiquem automaticamente à VPN, em vez de pedirem aos utilizadores o seu nome de utilizador e palavra-passe.

- Crie o seu perfil através da sua tarefa, como configurar as definições do Microsoft Edge, ativar as definições antivírus do Microsoft Defender, bloquear dispositivos de jailbroken iOS/iPadOS, e assim por diante.

- Crie perfis que se apliquem a grupos específicos, tais como Marketing, Vendas, Administradores de TI ou por localização ou sistema escolar.

- Separe as políticas de utilizador das políticas do dispositivo.

  Por exemplo, os [modelos administrativos em Intune](administrative-templates-windows.md) têm centenas de configurações ADMX. Estes modelos mostram se uma definição se aplica a utilizadores ou dispositivos. Ao criar modelos de administração, atribua as definições dos seus utilizadores a um grupo de utilizadores e atribua as definições do seu dispositivo a um grupo de dispositivos.

  A imagem que se segue mostra um exemplo de uma definição que pode aplicar-se aos utilizadores e/ou aplicar-se aos dispositivos:

  ![Modelo de administração intonizado que se aplica ao utilizador e dispositivos](./media/device-profile-create/setting-applies-to-user-and-device.png)

- Sempre que criar uma política restritiva, comunique esta alteração aos seus utilizadores. Por exemplo, se estiver a alterar o requisito de código de acesso de 4 caracteres para 6 caracteres, informe os seus utilizadores antes de atribuir a apólice.

## <a name="next-steps"></a>Próximos passos

[Atribua o perfil](../device-profile-assign.md) e [monitorize o respetivo estado](device-profile-monitor.md).

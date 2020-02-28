---
title: Ativar o conector de defesa de ameaças móveis para dispositivos não matriculados
titleSuffix: Microsoft Intune
description: Ative o conector mobile threat defense no Microsoft Intune para dispositivos não matriculados.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/20/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: 25d7c357c0ea313891f80433f33cd4ac57cfad2c
ms.sourcegitcommit: 045ca42cad6f86024af9a38a380535f42a6b4bef
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/28/2020
ms.locfileid: "77782094"
---
# <a name="enable-the-mobile-threat-defense-connector-in-intune-for-unenrolled-devices"></a>Ativar o conector de defesa de ameaças móveis em Intune para dispositivos não matriculados

Durante a configuração da Mobile Threat Defense (MTD), configuraste uma política para classificar ameaças na consola de parceiros de Defesa de Ameaças Móveis e criaste a política de proteção de aplicações em Intune. Se já configurar o conector Intune na consola de parceiros MTD, pode agora ativar a ligação MTD para aplicações parceiras MTD.

> [!NOTE]
> Este artigo aplica-se a todos os parceiros de Defesa de Ameaças Móveis que apoiam políticas de proteção de aplicações:
>
> - Melhor Móvel (Android,iOS/iPadOS)
> - Zimperium (Android,iOS/iPadOS)
> - Procura de trabalho (Android,iOS/iPadOS)

## <a name="classic-conditional-access-policies-for-mtd-apps"></a>Políticas clássicas de acesso condicional para aplicações MTD

Quando integra uma nova aplicação para intune Mobile Threat Defense e permite a ligação a Intune, Intune cria uma política clássica de acesso condicional no Diretório Ativo Azure. Cada aplicação MTD que integra, incluindo [o Defender ATP](advanced-threat-protection.md) ou qualquer um dos [nossos parceiros mTD](mobile-threat-defense.md#mobile-threat-defense-partners)adicionais, cria uma nova política clássica de acesso condicional. Estas políticas podem ser ignoradas, mas não devem ser editadas, eliminadas ou desativadas.

Se a política clássica for eliminada, terá de apagar a ligação ao Intune que foi responsável pela sua criação e, em seguida, instalá-la novamente. Este processo recria a política clássica. Não é suportado para migrar políticas clássicas para aplicações MTD para o novo tipo de política para acesso condicional.

Políticas clássicas de acesso condicional para aplicações MTD:

- São utilizados pela Intune MTD para exigir que os dispositivos estejam registados em Azure AD para que tenham um ID de dispositivo antes de comunicarem com os parceiros MTD. O ID é necessário para que os dispositivos e possam reportar com sucesso o seu estado a Intune.

- Não tenha qualquer efeito em quaisquer outras aplicações ou Recursos cloud.

- São diferentes das políticas de acesso condicional que pode criar para ajudar a gerir o MTD.

- Por defeito, não interaja com outras políticas de acesso condicional que utiliza para avaliação.

Para ver as políticas clássicas de acesso condicional, em [Azure,](https://portal.azure.com/#home)vá ao **Azure Ative Directory** > **Acesso Condicional** > **Políticas Clássicas.**

## <a name="to-enable-the-mtd-connector"></a>Para ativar o conector da MTD

1. Inscreva-se no [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Selecione **a administração do Inquilino** > **Conectores e fichas** > **Defesa de Ameaças Móveis.**

3. No painel **Defesa Contra Ameaças para Dispositivos Móveis**, selecione **Adicionar**.

4. Selecione a sua solução de MTD, como o **conector de Defesa Contra Ameaças para Dispositivos Móveis a configurar** na lista pendente.

    <!-- ![MTD setup in Intune](PLACEHOLDER, need a new screenshot of this page) -->

5. Ative as opções de alternância de acordo com os requisitos da sua organização. As opções de alternância visíveis variam consoante o parceiro MTD.

## <a name="mobile-threat-defense-toggle-options"></a>Opções de alternância da Defesa de Ameaças Móveis

Pode decidir quais as opções de alternância da MTD que necessita de ativar de acordo com os requisitos da sua organização. Veja a seguir mais detalhes:

**Definições de política de proteção de aplicativos**

- **Conecte os dispositivos Android da versão 4.4 e superior ao *\<nome de parceiro MTD>* para avaliação**da política de proteção de aplicações : Quando ativar esta opção, as políticas de proteção de aplicações utilizando a regra do Nível de Ameaça de Dispositivo avaliarão dispositivos, incluindo dados deste conector.

- **Conecte os dispositivos iOS na versão 11 e superior ao *nome de parceiro mTD\<MTD>* para avaliação**da política de proteção de aplicações : Quando ativar esta opção, as políticas de proteção de aplicações utilizando a regra do Nível de Ameaça de Dispositivo avaliarão dispositivos, incluindo dados deste conector.

**Definições comuns partilhadas**

- **Número de dias até o parceiro ficar não responsivo**: número de dias de inatividade antes de o Intune considerar o parceiro como não responsivo devido a perda da ligação. O Intune ignora o estado de conformidade para parceiros MTD não responsivos.

> [!TIP]
> Pode ver o **Estado da ligação** e a hora da **Última sincronização** entre o Intune e o parceiro MTD no painel de Defesa Contra Ameaças para Dispositivos Móveis.

## <a name="next-steps"></a>Passos Seguintes

- Crie a política de proteção de [aplicações mobile Threat Defense (MTD) com intune](~/protect/mtd-app-protection-policy.md).

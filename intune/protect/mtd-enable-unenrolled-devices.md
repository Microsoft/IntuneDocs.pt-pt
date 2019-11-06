---
title: Habilitar o conector de defesa contra ameaças móveis para dispositivos não registrados
titleSuffix: Microsoft Intune
description: Habilite o conector de defesa contra ameaças móveis em Microsoft Intune para dispositivos não registrados.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/21/2019
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
ms.openlocfilehash: b2744a27a733824bab9d920f4de0b49e951c1c34
ms.sourcegitcommit: a4c7339ec9ff5b1b846cb3cca887cf91b5cd4baa
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/05/2019
ms.locfileid: "73627647"
---
# <a name="enable-the-mobile-threat-defense-connector-in-intune-for-unenrolled-devices"></a>Habilitar o conector de defesa contra ameaças móveis no Intune para dispositivos não registrados

Durante a instalação da MTD (defesa contra ameaças móveis), você configurou uma política para classificar ameaças em seu console do parceiro de defesa contra ameaças móveis e criou a política de proteção do aplicativo no Intune. Se você já configurou o conector do Intune no console do parceiro do MTD, agora você pode habilitar a conexão MTD para aplicativos de parceiro MTD.

> [!NOTE] 
> Este artigo se aplica a todos os parceiros de defesa contra ameaças móveis que dão suporte a políticas de proteção de aplicativo: melhores dispositivos móveis (Android), Zimperium (iOS), Lookout for Work (Android/iOS).

## <a name="to-enable-the-mtd-connector"></a>Para ativar o conector da MTD

1. Entre no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).

2. No **Dashboard do Intune**, selecione **Conformidade do dispositivo** e, em seguida, **Proteção Contra Ameaças para Dispositivos Móveis**, na secção **Configuração**.

3. No painel **Defesa Contra Ameaças para Dispositivos Móveis**, selecione **Adicionar**.

4. Selecione a sua solução de MTD, como o **conector de Defesa Contra Ameaças para Dispositivos Móveis a configurar** na lista pendente.

    <!-- ![MTD setup in Intune](PLACEHOLDER, need a new screenshot of this page) -->

5. Ative as opções de alternância de acordo com os requisitos da sua organização. As opções de alternância visíveis variam consoante o parceiro MTD.

## <a name="mtd-toggle-options"></a>Opções de alternância da MTD

Pode decidir quais as opções de alternância da MTD que necessita de ativar de acordo com os requisitos da sua organização. Veja a seguir mais detalhes:

**Configurações de política de proteção de aplicativo**
- **Conecte dispositivos Android da versão 4,4 e superior para *\<nome do parceiro MTD >* para avaliação da política de proteção de aplicativo**: quando você habilitar essa opção, as políticas de proteção de aplicativo que usam a regra de nível de ameaça do dispositivo avaliarão dispositivos, incluindo dados deste conector.
- **Conecte os dispositivos IOS versão 11 e superior ao *\<nome do parceiro MTD >* para avaliação da política de proteção de aplicativo**: ao habilitar essa opção, as políticas de proteção de aplicativo que usam a regra de nível de ameaça do dispositivo avaliarão os dispositivos, incluindo dados de Este conector.

**Configurações compartilhadas comuns**
- **Número de dias até o parceiro ficar não responsivo**: número de dias de inatividade antes de o Intune considerar o parceiro como não responsivo devido a perda da ligação. O Intune ignora o estado de conformidade para parceiros MTD não responsivos.

> [!TIP]
> Pode ver o **Estado da ligação** e a hora da **Última sincronização** entre o Intune e o parceiro MTD no painel de Defesa Contra Ameaças para Dispositivos Móveis.

> [!NOTE] 
> Quando você habilita a conexão de defesa contra ameaças móveis ao Intune, o Intune cria uma política de acesso condicional clássica em Azure Active Directory. Cada aplicativo MTD que você integra, incluindo o [defender ATP](advanced-threat-protection.md) ou qualquer um de nossos [parceiros MTD](mobile-threat-defense.md#mobile-threat-defense-partners)adicionais, cria uma nova política de acesso condicional clássico. **Essas políticas podem ser ignoradas, mas não devem ser editadas, excluídas ou desabilitadas.**
> 
> Políticas de acesso condicional clássico para aplicativos MTD: 
> - São usados pelo Intune MTD para exigir que os dispositivos sejam registrados no Azure AD para que tenham uma ID de dispositivo antes de se comunicarem com os parceiros do MTD. A ID é necessária para que os dispositivos e possam relatar com êxito seu status ao Intune.  
> - Não têm nenhum efeito sobre outros aplicativos ou recursos de nuvem.  
> - São diferentes das políticas de acesso condicional que você pode criar para ajudar a gerenciar o MTD ou para exigir a AC de proteção do aplicativo
> - Por padrão, não interaja com outras políticas de acesso condicional usadas para avaliação.  
>
> Para exibir políticas de acesso condicional clássico, no [Azure](https://portal.azure.com/#home), acesse **Azure Active Directory** > **políticas clássicas**de**acesso** > .

## <a name="next-steps"></a>Passos Seguintes

- [Criar política de proteção de aplicativo MTD (defesa contra ameaças móveis) com o Intune](~/protect/mtd-app-protection-policy.md).

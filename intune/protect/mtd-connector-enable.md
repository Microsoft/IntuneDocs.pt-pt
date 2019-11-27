---
title: Ativar o conector da Defesa Contra Ameaças para Dispositivos Móveis no Microsoft Intune
titleSuffix: Microsoft Intune
description: Ative o conector entre o seu parceiro de Defesa Contra Ameaças para Dispositivos Móveis (MTD) e o Microsoft Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/19/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: dbb6a37e-ba47-4b69-922c-d25e66c279f6
ms.reviewer: davidra
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: b8243ae4014660a76c6327afd9c970ce8a9eae58
ms.sourcegitcommit: 960ffb2214c35d75ad219fa2571a999529a0abd4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/25/2019
ms.locfileid: "74478849"
---
# <a name="enable-the-mobile-threat-defense-connector-in-intune"></a>Ativar o conector da Defesa Contra Ameaças para Dispositivos Móveis no Intune

Durante a instalação da MTD (defesa contra ameaças móveis), você configurou uma política para classificar ameaças em seu console de parceiro de defesa contra ameaças móveis e criou a política de conformidade do dispositivo no Intune. Se você já configurou o conector do Intune no console do parceiro do MTD, agora você pode habilitar a conexão MTD para aplicativos de parceiro MTD.

> [!NOTE]
> Este tópico aplica-se a todos os parceiros de Defesa Contra Ameaças para Dispositivos Móveis.

## <a name="classic-conditional-access-policies-for-mtd-apps"></a>Políticas de acesso condicional clássico para aplicativos MTD

Quando você integra um novo aplicativo à defesa contra ameaças móveis do Intune e habilita a conexão com o Intune, o Intune cria uma política de acesso condicional clássica em Azure Active Directory. Cada aplicativo MTD que você integra, incluindo o [defender ATP](advanced-threat-protection.md) ou qualquer um de nossos [parceiros MTD](mobile-threat-defense.md#mobile-threat-defense-partners)adicionais, cria uma nova política de acesso condicional clássico. Essas políticas podem ser ignoradas, mas não devem ser editadas, excluídas ou desabilitadas.

Se a política clássica for excluída, você precisará excluir a conexão com o Intune responsável por sua criação e, em seguida, configurá-la novamente. Esse processo recria a política clássica. Não há suporte para migrar políticas clássicas para aplicativos MTD para o novo tipo de política para acesso condicional.

Políticas de acesso condicional clássico para aplicativos MTD:

- São usados pelo Intune MTD para exigir que os dispositivos sejam registrados no Azure AD para que tenham uma ID de dispositivo antes de se comunicarem com os parceiros do MTD. A ID é necessária para que os dispositivos e possam relatar com êxito seu status ao Intune.

- Não têm nenhum efeito sobre outros aplicativos ou recursos de nuvem.

- São diferentes das políticas de acesso condicional que você pode criar para ajudar a gerenciar o MTD.

- Por padrão, não interaja com outras políticas de acesso condicional usadas para avaliação.

Para exibir as políticas de acesso condicional clássico, no [Azure](https://portal.azure.com/#home), acesse **Azure Active Directory** > **acesso condicional** > **políticas clássicas**.

## <a name="to-enable-the-mobile-threat-defense-connector"></a>Para habilitar o conector de defesa contra ameaças móveis

1. Entre no centro de [Administração do Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Selecione **Administração de locatários** > **conectores e tokens** > **defesa contra ameaças móveis**.

3. No painel **defesa contra ameaças móveis** , selecione **Adicionar**.

4. Para **instalar o conector de defesa contra ameaças móveis**, selecione sua solução do MTD na lista suspensa.

5. Ative as opções de alternância de acordo com os requisitos da sua organização. As opções de alternância visíveis variam consoante o parceiro MTD.  Por exemplo, a imagem a seguir mostra as opções disponíveis para o Symantec Endpoint Protection:

   ![Configuração da MTD do Intune no portal do Azure](./media/mtd-connector-enable/enable-mtd-connector-1.png)

## <a name="mobile-threat-defense-toggle-options"></a>Opções de alternância da defesa contra ameaças móveis

Pode decidir quais as opções de alternância da MTD que necessita de ativar de acordo com os requisitos da sua organização. Nem todas as opções a seguir têm suporte de todos os parceiros de defesa de thread móvel:

**Configurações de política de conformidade do MDM**

- **Conectar dispositivos Android da versão _\<versões com suporte >_ para _\<nome do parceiro MTD >_** : ao habilitar essa opção, você pode fazer com que os dispositivos Android 4.1 + relatem o risco de segurança para o Intune.

- **Conecte a versão dos dispositivos iOS _\<versões com suporte >_ _\<nome do parceiro MTD >_** : ao habilitar essa opção, você pode ter os dispositivos IOS 8.0 + relatando o risco de segurança de volta para o Intune.

- **Ativar Sincronização de Aplicações para Dispositivos iOS**: permite que o parceiro de Defesa Contra Ameaças para Dispositivos Móveis peça metadados de aplicações iOS a partir do Intune para utilizar para fins de análise de ameaças.

- **Bloquear versões do SO não suportadas**: bloquear se o dispositivo estiver a executar um sistema operativo inferior à versão mínima suportada.

**Configurações de política de proteção de aplicativo**

- **Conecte dispositivos Android da versão *\<versões com suporte >* para *\<nome de parceiro MTD >* para avaliação de política de proteção de aplicativo**: quando você habilitar essa opção, as políticas de proteção de aplicativo que usam a regra de nível de ameaça do dispositivo avaliarão os dispositivos, incluindo os dados desse conector.

- **Conecte a versão dos dispositivos iOS *\<versões com suporte >* *\<nome do parceiro MTD >* para avaliação da política de proteção do aplicativo**: ao habilitar essa opção, as políticas de proteção de aplicativo que usam a regra de nível de ameaça do dispositivo avaliarão os dispositivos, incluindo os dados desse conector.

Para saber mais sobre como usar conectores de defesa contra ameaças móveis para obter Proteção de Aplicativo do Intune avaliação de política, confira [Configurar a defesa contra ameaças móveis para dispositivos não registrados](~/protect/mtd-enable-unenrolled-devices.md).

**Configurações compartilhadas comuns**

- **Número de dias até o parceiro ficar não responsivo**: número de dias de inatividade antes de o Intune considerar o parceiro como não responsivo devido a perda da ligação. O Intune ignora o estado de conformidade para parceiros MTD não responsivos.

> [!IMPORTANT]
> Quando possível, recomendamos que você adicione e atribua os aplicativos MTD antes de criar a conformidade do dispositivo e as regras de política de acesso condicional. Isso ajuda a garantir que o aplicativo MTD esteja pronto e disponível para que os usuários finais instalem antes que possam obter acesso ao email ou a outros recursos da empresa.

> [!TIP]
> Pode ver o **Estado da ligação** e a hora da **Última sincronização** entre o Intune e o parceiro MTD no painel de Defesa Contra Ameaças para Dispositivos Móveis.

## <a name="next-steps"></a>Passos Seguintes

- [Criar política de proteção de aplicativo MTD (defesa contra ameaças móveis) com o Intune](~/protect/mtd-app-protection-policy.md).

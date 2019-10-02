---
title: Ativar o conector da Defesa Contra Ameaças para Dispositivos Móveis no Microsoft Intune
titleSuffix: Microsoft Intune
description: Ative o conector entre o seu parceiro de Defesa Contra Ameaças para Dispositivos Móveis (MTD) e o Microsoft Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 07/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: dbb6a37e-ba47-4b69-922c-d25e66c279f6
ms.reviewer: davidra
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9ac49edcd4ea71bdbc83cfa093f2bb5e42aefd54
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/02/2019
ms.locfileid: "71729564"
---
# <a name="enable-the-mobile-threat-defense-connector-in-intune"></a>Ativar o conector da Defesa Contra Ameaças para Dispositivos Móveis no Intune

> [!NOTE] 
> Este tópico aplica-se a todos os parceiros de Defesa Contra Ameaças para Dispositivos Móveis.

Durante a configuração da Defesa Contra Ameaças para Dispositivos Móveis (MTD), configurou uma política para classificar ameaças na sua consola do parceiro MTD e criou a política de conformidade de dispositivos no Intune. Se você já configurou o conector do Intune no console do parceiro do MTD, agora você pode habilitar a conexão MTD para aplicativos de parceiro MTD.

Quando você integra um novo aplicativo à defesa contra ameaças móveis do Intune e habilita a conexão com o Intune, o Intune cria uma política de acesso condicional clássica em Azure Active Directory. Cada aplicativo MTD que você integra, incluindo o [defender ATP](advanced-threat-protection.md) ou qualquer um de nossos [parceiros MTD](mobile-threat-defense.md#mobile-threat-defense-partners)adicionais, cria uma nova política de acesso condicional clássico. Essas políticas podem ser ignoradas, mas não devem ser editadas, excluídas ou desabilitadas.

Políticas de acesso condicional clássico para aplicativos MTD: 

- São usados pelo Intune MTD para exigir que os dispositivos sejam registrados no Azure AD para que tenham uma ID de dispositivo antes de se comunicarem com os parceiros do MTD. A ID é necessária para que os dispositivos e possam relatar com êxito seu status ao Intune.  
- Não têm nenhum efeito sobre outros aplicativos ou recursos de nuvem.  
- São diferentes das políticas de acesso condicional que você pode criar para ajudar a gerenciar o MTD.
- Por padrão, não interaja com outras políticas de acesso condicional usadas para avaliação.  

Para exibir políticas de acesso condicional clássico, no [Azure](https://portal.azure.com/#home), acesse **Azure Active Directory** > **políticas clássicas**de**acesso** > condicional.


## <a name="to-enable-the-mtd-connector"></a>Para ativar o conector da MTD

1. Entre no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).

4. No **Dashboard do Intune**, selecione **Conformidade do dispositivo** e, em seguida, **Proteção Contra Ameaças para Dispositivos Móveis**, na secção **Configuração**.

5. No painel **Defesa Contra Ameaças para Dispositivos Móveis**, selecione **Adicionar**.

6. Selecione a sua solução de MTD, como o **conector de Defesa Contra Ameaças para Dispositivos Móveis a configurar** na lista pendente.

    ![Configuração da MTD do Intune no portal do Azure](./media/mtd-connector-enable/enable-mtd-connector-1.png)

7. Ative as opções de alternância de acordo com os requisitos da sua organização. As opções de alternância visíveis variam consoante o parceiro MTD.

## <a name="mtd-toggle-options"></a>Opções de alternância da MTD

Pode decidir quais as opções de alternância da MTD que necessita de ativar de acordo com os requisitos da sua organização. Veja a seguir mais detalhes:

- **Conecte dispositivos Android 4.1 + ao [nome do parceiro do MTD] for Work MTD**: Ao habilitar essa opção, você pode fazer com que os dispositivos Android 4.1 + relatem o risco de segurança para o Intune.
  - **Marcar como não compatível se nenhum dado for recebido**: Se o Intune não receber dados sobre um dispositivo nesta plataforma do parceiro MTD, considere o dispositivo não compatível.
<br></br>
- **Conecte dispositivos IOS 8.0 + ao [nome do parceiro do MTD] for Work MTD**: Ao habilitar essa opção, você pode fazer com que os dispositivos iOS 8.0 + relatem o risco de segurança para o Intune.
  - **Marcar como não compatível se nenhum dado for recebido**: Se o Intune não receber dados sobre um dispositivo nesta plataforma do parceiro MTD, considere o dispositivo não compatível.
<br></br>
- **Habilitar a sincronização de aplicativos para dispositivos IOS**: Permite que este parceiro de defesa contra ameaças móveis solicite metadados de aplicativos iOS do Intune para serem usados para fins de análise de ameaças.

- **Bloquear versões de sistema operacional sem suporte**: Bloquear se o dispositivo estiver executando um sistema operacional inferior à versão mínima com suporte.

- **Número de dias até que o parceiro não responda**: Número de dias de inatividade antes de o Intune considerar que o parceiro não está respondendo, pois a conexão foi perdida. O Intune ignora o estado de conformidade para parceiros MTD não responsivos.

> [!IMPORTANT] 
> Quando possível, recomendamos que você adicione e atribua os aplicativos MTD antes de criar a conformidade do dispositivo e as regras de política de acesso condicional. Isso ajuda a garantir que o aplicativo MTD esteja pronto e disponível para que os usuários finais instalem antes que possam obter acesso ao email ou a outros recursos da empresa.

> [!TIP]
> Pode ver o **Estado da ligação** e a hora da **Última sincronização** entre o Intune e o parceiro MTD no painel de Defesa Contra Ameaças para Dispositivos Móveis.
